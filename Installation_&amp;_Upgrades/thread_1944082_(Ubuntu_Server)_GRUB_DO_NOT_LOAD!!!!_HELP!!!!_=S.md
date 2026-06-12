---
title: "(Ubuntu Server) GRUB DO NOT LOAD!!!! HELP!!!! =S"
date: 2012-03-20
forum: Installation &amp; Upgrades
---

### Post by progman128 on 2012-03-20
Hello, I am an Ubuntu user for 2 years, I never had any problem, I use uCLinux too, I am a Mechatronics Eng. and I am an UAV developer. Now we are working with an SGI (Silicon Graphics Interface) that is a supercomputer compossed by 8 servers connected by Infiniband and Ethernet with Mellanox and Cisco Switches. I install Ubuntu Server 11.10 on one of the nodes and it runs correctly, it boots and the GRUB Load too. I found a guide to make a cluster using MPIH2 and SSH server with a daemon structure, but only runs correctly on Ubuntu 10.04LTS, thats why I install after Ubuntu 11.10 the version 10.04LTS, but when I reboot the PC and the BIOS ends its functions, I onely saw a cursor on a black screen, then I poweroff my server and when boot I push the shift button to load the GRUB, but I only saw a message that said ""GRUB LOADING..."" but it do not make anything, I reinstall ubuntu 11.10 but I get the same result (I can not boot Ubuntu and do not load GRUB), the partition configuration is like this:

    - SWAP    4GB(8GB RAM / 2)       AT TOP
    - /           16GB                          AT TOP      EXT4
    - /home   400GB                        AT TOP      EXT4
    - /boot     4GB                           AT TOP       EXT2

I try too to install Ubuntu without making manualy the partitions and geting them from the automatic installation, but I get the same result.

Now I am frustrated because I can not run Ubuntu 11.10 (that it runs correctly before installing 10.04LTS) and I can not run Ubuntu 10.04LTS.

I try too to make a NUKE to the HD but It do not works, I get the same result. I reinstall the GRUB with the Live CD but I get the same result. I install the Ubuntu in other servers that had another SO yet and I get the same result. Onely works correctly with HD that do not had any SO yet in the past. I suspect that the problem resides on the MBR that is do not been formated correctly or something like that, I do not know realy.

What can I do????? HELP PLEASE!!!! =S

---

### Post by progman128 on 2012-03-20
I solved the problem (finaly!!!) y use rescatux and it works!!!!!!! =D... here is the link: [http://www.supergrubdisk.org/rescatux/](http://www.supergrubdisk.org/rescatux/).... I make an USB bootable stick with the ISO file using the xbootvs1 software, here is the link: [http://sites.google.com/site/shamurxboot/download](http://sites.google.com/site/shamurxboot/download)... I use the option ""find GRUB installed (even if it is overwritted)"" and it repair my GRUB and boot my OS... =)))

---

