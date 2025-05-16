FROM fedora:42

RUN dnf install -y --setopt=install_weak_deps=False python3 pip3 nodejs nodejs-npm

RUN useradd notebook
USER notebook

RUN mkdir -p /home/notebook/app /home/notebook/.local /home/notebook/.jupyter
ENV PATH="$PATH:/home/notebook/.local/bin"
RUN npm config set prefix /home/notebook/.local

RUN pip install jupyterlab notebook
RUN npm install -g tslab javascript-typescript-langserver
RUN tslab install

RUN jupyter notebook --generate-config
CMD ["jupyter", "notebook", "--ServerApp.root_dir=/home/notebook/app", "--ServerApp.ip=0.0.0.0"]
WORKDIR "/home/notebook/app"
