---
title: "Upgradation failure when installing Ubuntu server 22.04"
date: 2022-09-29
forum: Installation &amp; Upgrades
---

### Post by voidravels on 2022-09-29
HI,

I am trying to install an Ubuntu server edition 22.04.1 on a device with following requirements

* 2GB RAM
* 3.8 GB memory card
* running on an x86 platform 64 bit 

There is a 16.04 server edition already installed since it is reaching the End Of Life, I need to upgrade it to the latest

Requirements :

* custom partition the memory card with root file system which should be an encrypted volume
* set up an EFI system partition


Issue:

* I am able to do this without much effort on the 16.04 but on 22.04 it isnt allowing to create such partitions
* Any suggestions on how i should go about it and will the 3.8 GB disk space be sufficient for installation ?
* what server version would be most suitable ?

Thanks,
Ratnavel

---

### Post by deadflowr on 2022-09-29
*Thread moved to **Installation and Upgrades***
The development phase of 22.04(.1) is over.

---

### Post by MAFoElffen on 2022-09-30
Your system is just under the requirements for a minimal install....
> 
The recommended system requirements are:
 
[LIST]
[*]CPU: 1 gigahertz or better 
[*]RAM: 1 gigabyte or more 
[*]Disk: a minimum of 2.5 gigabytes 
[/LIST]

Even though it says 1GB of RAM, that is minimum after it is installed. The installer will peg that 2GB while installing.

Encryption is not out of the box and is using the command line:
[https://ubuntuforums.org/showthread.php?t=2465735&p=14053144#post14053144](https://ubuntuforums.org/showthread.php?t=2465735&p=14053144#post14053144)

---

### Post by voidravels on 2022-10-18
Thanks for the info. Will try the commandline way

---

