---
title: "Installing NetBeans to program C++"
date: 2007-08-25
forum: Installation &amp; Upgrades
---

### Post by XtremeLinuxNaruto on 2007-08-25
Hi guys I installed NetBeans latest version with C++ package to run in Ubuntu and I can't run my programs. I'm using the GCC compilers that Ubuntu 7.4 brings within to compile the programs and I have the following error message in the output window..

Running "/usr/bin/make -f Makefile CONF=Debug" in /home/andy/Welcome_1

/usr/bin/make -f nbproject/Makefile-Debug.mk SUBPROJECTS= .build-conf
make[1]: Entering directory `/home/andy/Welcome_1'
mkdir -p build/Debug/GNU-Linux-x86
c -g -o build/Debug/GNU-Linux-x86/welcome.o welcome.cc
make[1]: c: Command not found
make[1]: [build/Debug/GNU-Linux-x86/welcome.o] Error 127 (ignored)
mkdir -p dist/Debug
o dist/Debug/welcome build/Debug/GNU-Linux-x86/welcome.o 
make[1]: o: Command not found
make[1]: [dist/Debug/welcome] Error 127 (ignored)
make[1]: Leaving directory `/home/andy/Welcome_1'

Build successful. Exit value 0.

Running "/usr/bin/gnome-terminal --disable-factory --hide-menubar --title="dist/Debug/welcome \"arg 1\" \"arg 2\"" -e "\"/home/andy/netbeans-5.5.1/cnd1/bin/dorun.sh\" \"[Press Enter to close window] \" dist/Debug/welcome \"arg 1\" \"arg 2\""" in /home/andy/Welcome_1


Run successful. Exit value 0.

and then I have this one in the black console :

/home/andy/netbeans-5.5.1/cnd1/bin/dorun.sh: 38: ./dist/Debug/welcome: not found
[Press Enter to close window]

What can I do for it...Any suggestion...Or do I have to find another IDE...:(

---

### Post by hansi70 on 2008-01-19
Hi,

I had exactly the same problem. Here is what you need to do:

1. In Netbeans IDE 6, goto Tools>Options>select the C/C++ tab

2. Under the C complier drop-down
   Choose Add and select the file gcc-4.2 from the usr/bin directory

3. 2. Under the C++ complier drop-down
   Choose Add and select the file g++-4.1 from the usr/bin directory

4. Choose OK

Regards,

Hansi

---

### Post by hansi70 on 2008-01-19
Of course, for step 2 and 3, make sure that  you select those files as your default. Also, if these files are not available download them using the Synaptic Package Manager.

Hansi

---

