DigistumpArduino for FOSSEE Laptop
===================================

To manually install
-------------------

- Download this Repo
- unpack & cd to master folder
- ./arduino


To compile
----------

To compile tools  from scratch use:

- `Arduino 1.5.X (1.5.8+) <https://github.com/arduino/Arduino>`_.

- `Digistump <https://github.com/digistump/DigistumpArduino>`_.

- `Micronucleus <https://github.com/micronucleus/micronucleus/tree/80419704f68bf0783c5de63a6a4b9d89b45235c7>`_. 

- `AVR-Dummy <https://github.com/digistump/avr-dummy>`_.

- `Astyle <https://github.com/arduino/astyle>`_.

- `Avr-toolchain <https://github.com/arduino/toolchain-avr>`_.


Compiling Arduino 1.5.x
***********************

- Unzip the source and cd to Arduino-master/build

- Make the following changes to build.xml file
  ::
    1. Remove the "check os" dependency in linux32 target
    2. Remove the "build" dependency in linux-dist target.

- Run the following command for compiling the Arduino
  ::
    ant -buildfile build.xml -Dplatform=linux32


Compiling Astyle
******************
- cd to astyle source folder
- ./bash-setup
- cd astyle-code/Astyle/build/gcc
- make clean
- make java
- rename the libastyle-2.x.x.so in astyle-code/Astyle/build/gcc/bin to libastylej.so 
- copy it to Arduino-master/build/linux/work/lib/


Compiling Micronucleus and Avr-dummy
************************************

- Compile the micronucleus commandline tool (commandline directory) and avr-dummy ("make all" for both) - which will produce executables named micronucleus and avrdude 

- Copy the digistump folder from this Digistump repo  to Arduino-master/build/linux/work/hardware. 

- Copy micronucleus and avrdude executables to the Arduino-master/build/linux/work/hardware/digistump/avr/tools.



Compiling Avr-tool chain
************************

- git clone git://github.com/arduino/toolchain-avr

- sudo apt-get install build-essential gperf bison subversion texinfo zip automake flex libusb-dev libusb-1.0-0-dev libtinfo-dev pkg-config
- cd toolchain-avr
- ./build.all.bash
- output gives avr and avrdude-x.x.x directories
- before copying toolchain compiled for arm,need to remove the tool chain already downloded for for x86 by build.xml in Arduino-master/build/linux/work/hardware/tools/avr/  *except* the **builtin_tools_versions.txt**
- copy the toolchain-avr/avr/*  to Arduino-master/build/linux/work/hardware/tools/avr/
- copy the avrdude-x.x.x/bin/* to Arduino-master/build/linux/work/hardware/tools/avr/bin/
- copy the avrdude-x.x.x/lib/* to Arduino-master/build/linux/work/hardware/tools/avr/lib/
- copy the avrdude-x.x.x/include/* to Arduino-master/build/linux/work/hardware/tools/avr/include/
- copy the avrdude-x.x.x/etc to Arduino-master/build/linux/work/hardware/tools/avr/

Now your DigistumpArduino is ready at Arduino-master/build/linux/work.Only work directery is needed.

:Authors:
    Padmakar Reddy Thatikonda
   
:version: 1.5.8 of 2015/04/20






