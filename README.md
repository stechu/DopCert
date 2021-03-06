# DopCert
DopCert is a framework for formally verifying query optimization. 
Our website: http://dopcert.cs.washington.edu/.

Our coq code has been tested using [HoTT](https://github.com/HoTT/HoTT) library with Coq 8.5pl1. To save from building HoTT library and Coq, we recommend docker based development environment described below:

## Install Docker
A detailed documentation could be found [here](https://docs.docker.com/engine/understanding-docker/).

## Build Project

Build project and call it `dopcert` with:

    docker build -t dopcert .
 
## Develop Project
 
Run development environment named `dopcert` with:

    docker run -d --name dopcert -v $(pwd)/src/:/src/ dopcert sleep infinity
 
Build changes to the project with:

    docker exec dopcert make -C src

Connect to the docker process with emacs and edit Coq files using ProofGeneral.
Emacs must have `docker-tramp` installed, and `enable-remote-dir-locals` enabled.

    emacs /docker:dopcert:/hott/UnivalentSemantics.v

To connect to the docker process on another machine, run:

    emacs "/ssh:user@machine|docker:dopcert:/hott/UnivalentSemantics.v"


Remove development environment with:
    
    docker rm -f dopcert

Remove all old docker containers with:

    docker rm -f $(docker ps -aq)
