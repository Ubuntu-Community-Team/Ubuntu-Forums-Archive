---
title: "Failed Dependencies"
date: 2007-06-30
forum: Installation &amp; Upgrades
---

### Post by tmloos on 2007-06-30
Hi,
I just switched over to Ubuntu 7.04 from the Fedora camp!  I am trying to configure my system with the cdk4msp430 tools so I can do embedded programming for TI's msp430 family of processors.  Attempting the installation of a handful of RPMs has brought my biggest deficiency as a Linux user to light again.  I love the apt-get install tool, but there are still instances, like with the cdk4msp430, where I have to use RPMs and I have failed dependencies.  Here is what I am getting when I try to install the JTAG programming support RPM:

root@frogger:~/programs/cdk4msp# sudo rpm -Uhv cdk-msp-jtag-lib-20031101cvs-20031102.i386.rpm
error: Failed dependencies:
        python >= 2.1 is needed by cdk-msp-jtag-lib-20031101cvs-20031102.i386
        ld-linux.so.2 is needed by cdk-msp-jtag-lib-20031101cvs-20031102.i386
        libc.so.6 is needed by cdk-msp-jtag-lib-20031101cvs-20031102.i386
        libc.so.6(GLIBC_2.0) is needed by cdk-msp-jtag-lib-20031101cvs-20031102.i386
        libc.so.6(GLIBC_2.1.3) is needed by cdk-msp-jtag-lib-20031101cvs-20031102.i386
root@frogger:~/programs/cdk4msp# 

I have no idea where to start to remedy this problem.  Please help me become a better Linux user!

Thanks,
Tom

---

### Post by machinemode on 2007-07-23
I am also having issues with cdk4msp, mainly because I am new (as of last night) to linux (Ubuntu 7.04) in general.  I did manage to install the appropriate packages by converting each of the .rpm's to .deb's via 'alien'.

For example: 
sudo alien -k cdk-msp-jtag-lib-20031101cvs-20031102.i386.rpm
sudo dpkg -i cdk-msp-jtag-lib_20031101cvs-20031102_i386.deb

All were installed and placed in '/opt', but now I am unable to compile in the terminal.  I tried using msp430-gcc, and the command is not found.  Any help would be appreciated.

Regards,
Cesar

---

