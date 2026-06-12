---
title: "I can't install VMware player due to ..."
date: 2013-11-04
forum: Installation &amp; Upgrades
---

### Post by psyclone on 2013-11-04
hi all,
I can't install the VMware player due to " unable to locate package ", I can download the 64bit version from VMware's site, but I'm unable to run the installation. The same statement is produced when i enter " sudo apt-get install update ". At th moment I'm running a dual boot of win7 & Ubuntu (both 64). 

Can anyone help!

---

### Post by ian-weisser on 2013-11-04
Please show us *exactly* how you try to install VMware player. Show us the entire terminal session.

---

### Post by psyclone on 2013-11-05
e-desktop@ubuntu:~$ sudo apt-get install vmware
[sudo] password for e-desktop: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package vmware
e-desktop@ubuntu:

---

### Post by ian-weisser on 2013-11-05
That's right, there is no package called "vmware"
Your system is not broken. VMware is not packaged for Ubuntu.

To install VMware, see the instructions at [https://help.ubuntu.com/community/VMware/Player](https://help.ubuntu.com/community/VMware/Player)

---

### Post by psyclone on 2013-11-05
That's Great i got it working. Thanks Ian. But another problem has arisen just before i complete the installation process, to do with memory. Which says the following:

"The current amount of free space on the hard disk (1.1 GB) is not enough  to create the specified disk file. Please choose a different location or  specify a smaller disk size."

because according to the "Details in Settings": I have the following capacity.

Memory 3.8 GiB
Disk: 18.3 GB

I have a hard drive partition of 256GB for Ubuntu. And windows7 requires 60GB to function. 
How do i adjust the memory to allow for the 60GB?

---

### Post by ian-weisser on 2013-11-05
Unfortunately, that I do not know. I don't use VMware.
So I will let somebody who uses VMware answer that.

---

