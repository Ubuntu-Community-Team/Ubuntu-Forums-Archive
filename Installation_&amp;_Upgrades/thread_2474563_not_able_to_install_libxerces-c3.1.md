---
title: "not able to install libxerces-c3.1"
date: 2022-05-03
forum: Installation &amp; Upgrades
---

### Post by renjithp78 on 2022-05-03
I am trying to compile netbee/src in ubuntu 20.04.4 LTS (Focal Fossa) it is giving error message as follows,

```
CMake Warning (dev) at nbnetvm/CMakeLists.txt:883 (GET_TARGET_PROPERTY):
  Policy CMP0026 is not set: Disallow use of the LOCATION target property.
  Run "cmake --help-policy CMP0026" for policy details.  Use the cmake_policy
  command to set the policy and suppress this warning.

  The LOCATION property should not be read from target "makenetilscanner".
  Use the target name directly with add_custom_command, or use the generator
  expression $<TARGET_FILE>, as appropriate.

This warning is for project developers.  Use -Wno-dev to suppress it.

CMake Warning (dev) at nbnetvm/CMakeLists.txt:884 (GET_TARGET_PROPERTY):
  Policy CMP0026 is not set: Disallow use of the LOCATION target property.
  Run "cmake --help-policy CMP0026" for policy details.  Use the cmake_policy
  command to set the policy and suppress this warning.

  The LOCATION property should not be read from target "makeopcodetable".
  Use the target name directly with add_custom_command, or use the generator
  expression $<TARGET_FILE>, as appropriate.

This warning is for project developers.  Use -Wno-dev to suppress it.

CMake Warning (dev) at nbnetvm/CMakeLists.txt:885 (GET_TARGET_PROPERTY):
  Policy CMP0026 is not set: Disallow use of the LOCATION target property.
  Run "cmake --help-policy CMP0026" for policy details.  Use the cmake_policy
  command to set the policy and suppress this warning.

  The LOCATION property should not be read from target "netvmburg".  Use the
  target name directly with add_custom_command, or use the generator
  expression $<TARGET_FILE>, as appropriate.

This warning is for project developers.  Use -Wno-dev to suppress it.

CMake Error: The following variables are used in this project, but they are set to NOTFOUND.
Please set them or make sure they are set and tested correctly in the CMake files:
XERCES_INCLUDE_DIR
   used as include directory in directory /home/iist/netbee/src/nbprotodb
   used as include directory in directory /home/iist/netbee/src/nbprotodb
   used as include directory in directory /home/iist/netbee/src/nbprotodb

-- Configuring incomplete, errors occurred!
See also "/home/iist/netbee/src/CMakeFiles/CMakeOutput.log".
```


On trying to install libxerces-c3.1, the system is giving following error.


```
sudo apt-get install libxerces-c3.1

Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package libxerces-c3.1
E: Couldn't find any package by glob 'libxerces-c3.1'
E: Couldn't find any package by regex 'libxerces-c3.1'

```
Please guide me

---

