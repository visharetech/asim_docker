## User Guide

### Build the Docker Image
```console
# Download the Dockerfile and place into new directory
# Build the docker image
# In Linux environment,
#   option 1. you have to build the docker image with sudo
#   option 2. create a Unix group called docker and add $USER to it (https://docs.docker.com/engine/install/linux-postinstall/)
cd docker
docker build -t vishare .

# Create a directory to share data between host and container
mkdir workspace
```

### Run the Container
```console

#simply run the docker
#docker run -it vishare

# The -v option in Docker is used to create a volume mount, which allows you to share files between your host machine and a Docker container.
# Below example demonstrates how to mount the current workspace directory in Windows host to the /mnt/workspace
# For example, in windows, mount .\workspace to /mnt/workspace:
docker run -v .\workspace:/mnt/workspace -it vishare
```

### Run the helloworld example
```console
cd ~/asim_helloworld_example

#build the project
cd build/riscv-sim
./make-Makefiles.sh

#run the simulator with profile
asim_prof --elfFileName example.elf

#copy the profile info to the shared directory
cp -r out /mnt/workspace/
```

### Docker info
user name: vishare<br >
password: vishare

The docker included below packages:
* riscv32-unknown-elf cross-compile toolchain
* asim
* asim helloworld example

