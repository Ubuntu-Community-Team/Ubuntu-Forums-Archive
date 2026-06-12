---
title: "ubuntu 10.04 netbook remix on Acer aspire one zg5 model"
date: 2010-07-30
forum: Installation &amp; Upgrades
---

### Post by ReV0h on 2010-07-30
Hi guys, i'm pretty new to all this and have just tried to install ubuntu 10.04 to the hard drive of my netbook as i prefer it greatly over the standard linpus one. 

The operating system booted fine from a bootable usb drive and so i thought if i install it it should run.

so...i got to work installing the system...it completed and asked me to restart, which i did.

From there the boot up screen comes on for the pc.....the one where it says press f2 for setup and f12 for boot priority....then goes to a black screen.

on this black screen i have a message which says...
             
               "error: no such device: 992fddd7-54c1-45e0-b990-7220c6fa9005
                grub rescue>"

If anyone has any ideas on this subject i'd greatly appreciate any help i can get to solve my problem.

thanks in advance

ReV0h

---

### Post by ReV0h on 2010-07-30
i've managed to sort it, however i would like to use the entire HDD for ubuntu. Ideally formatting the entire HDD so that the full 160gb is available for me to use with ubuntu.

I don't know if this is possible though as it is my first pc which i haven't built myself. are the HDD locked from manufacturers or are they able to be low level formatted etc?

thanks

ReV0h

---

### Post by PC_load_letter on 2010-08-11
I don't think this should be a problem. Just make a bootable live USB drive and reboot. Once you are logged in the Live Ubuntu session, open the terminal and run ```
$ sudo gparted
``` just hit enter if prompted for a password. 
Using Gparted you can do whatever you want w/ the hdd. Once you're done deleting the existing partitions (don't forget to backup any important files), click on the install icon on the desktop and you can then install Ubuntu on the whole drive w/ the option to use the largest free disk space for the installation.

---

