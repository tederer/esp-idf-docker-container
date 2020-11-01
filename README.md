# esp-idf-docker-image
This repository containes all you need to build a docker image that can be used to compile and transfer your ESP32 project onto the ESP32. The idea is to installs the Espressif IoT Development Framework V4.2 ([ESP-IDF](https://docs.espressif.com/projects/esp-idf/en/latest/esp32/)) and its dependencies in a docker image. The project code resides in your file system and gets mounted into the docker container. 

# building the docker image

Clone this repository and execute `buildDockerImage.sh`. This script creates a docker image with the tag "esp32dev".

# using the docker image / compiling your ESP32 project

Open `startDevEnvInDocker.sh` in an editor and adapt the values of following variables to match with your setup.

|variable|description|
|----------------------|------------------------------------------------------|
|projectRootInHost     |The path to the folder containing your project.       |
|projectRootInContainer|The path of your project in the docker container.     |
|deviceForFlashing     |The device that shall get used for flashing the ESP32.|


After adapting the settings, execute `startDevEnvInDocker.sh` and the console output should look like this ...


```
developer@esp32dev:~/esp32/esp-idf-docker-image$ ./startDevEnvInDocker.sh 

[sudo] password for developer: 
Setting IDF_PATH to '/root/esp/esp-idf'
Adding ESP-IDF tools to PATH...
Using Python interpreter in /root/.espressif/python_env/idf4.2_py3.6_env/bin/python
Checking if Python packages are up to date...
Python requirements from /root/esp/esp-idf/requirements.txt are satisfied.
Added the following directories to PATH:
  /root/esp/esp-idf/components/esptool_py/esptool
  /root/esp/esp-idf/components/espcoredump
  /root/esp/esp-idf/components/partition_table
  /root/esp/esp-idf/components/app_update
  /root/.espressif/tools/xtensa-esp32-elf/esp-2020r2-8.2.0/xtensa-esp32-elf/bin
  /root/.espressif/tools/xtensa-esp32s2-elf/esp-2020r2-8.2.0/xtensa-esp32s2-elf/bin
  /root/.espressif/tools/esp32ulp-elf/2.28.51-esp-20191205/esp32ulp-elf-binutils/bin
  /root/.espressif/tools/esp32s2ulp-elf/2.28.51-esp-20191205/esp32s2ulp-elf-binutils/bin
  /root/.espressif/tools/openocd-esp32/v0.10.0-esp32-20200420/openocd-esp32/bin
  /root/.espressif/python_env/idf4.2_py3.6_env/bin
  /root/esp/esp-idf/tools
Done! You can now compile ESP-IDF projects.
Go to the project directory and run:

  idf.py build

root@005b6076c28f:~/esp/windsensor#
```

To build you project, go to the project directory and run `idf.py build`.

To build and flash you project onto the ESP32, go to the project directory and run `idf.py flash`.
