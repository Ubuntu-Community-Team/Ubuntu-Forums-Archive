---
title: "Virtual Box upgrade broke guest additions"
date: 2010-02-16
forum: Installation &amp; Upgrades
---

### Post by ebjsbjc on 2010-02-16
I am new to Linux (Ubuntu).  I am currently running it in a virtual machine in Sun Virtualbox ver. 3.1.4r57640, Linux Kernal 2.6.31-19-generic Ubuntu 9.10 AMDx64 - I have just updated to the most recent version of virtual box and now the guest additions are not working anymore.  I tried to reinstall the guest additions and I get the following error: "Makefile:23: *** Error: unable to find the sources of your current Linux kernel. Specify KERN_DIR=<directory> and run Make again..  Stop."
Read some forum articles and everyone has something different to do, and I am to new to get what they are saying.  Please help, how do I fix this.  I guess one way would be to go back to the previous addition of VBOX, but would like to fix in the new version.  Thank you for any suggestion to fix, thank you.

---

### Post by entangled on 2010-11-30
You probably just need to install 'linux-headers-generic' and then try again with the vbox guest additions script. The 'build-essential' package is also required, but you seem to have that because the 'make' utility reported an error.

---

