# my_docker
Collection of dockerfile and scripts related to ROS, PX4, UAV, etc.

## Environment Setup
   Before you begin, verify that you have sufficient storage
   space available on your device. We recommend at least **30 GB**, to
   account for the size of the container and datasets.

1. **On x86_64 platforms**: Install the ``nvidia-container-runtime``
   following https://github.com/NVIDIA/nvidia-container-runtime#installation.

2. Configure ``nvidia-container-runtime`` as the default runtime for
   Docker.

   Using your text editor of choice, add the following items by
   ``vim /etc/docker/daemon.json``.

   ```
      {
          "runtimes": {
              "nvidia": {
                  "path": "nvidia-container-runtime",
                  "runtimeArgs": []
              }
          },
          "default-runtime": "nvidia"
      }
    ```

3. Then, restart Docker:

   ```
   sudo systemctl daemon-reload && sudo systemctl restart docker
   ```

      

4. Install [Git LFS](https://git-lfs.github.com/) to pull
   down all large files:

   ```
    sudo apt-get install git-lfs
    git lfs install --skip-repo
    ```



5. Create a ROS 2 workspace for experimenting with Isaac ROS:

   ```
      mkdir -p  ~/workspaces/my_ros-dev
      echo "export MY_ROS_WS=${HOME}/workspaces/my_ros-dev/" >> ~/.bashrc
      source ~/.bashrc   
   ```

   We expect to use the ``MY_ROS_WS`` environmental variable
   to refer to this ROS 2 workspace directory, in the future.


To further customize your development environment, check out [this guide](https://nvidia-isaac-ros.github.io/repositories_and_packages/isaac_ros_common/index.html#isaac-ros-docker-development-environment).