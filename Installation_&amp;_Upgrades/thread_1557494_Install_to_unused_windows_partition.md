---
title: "Install to unused windows partition"
date: 2010-08-20
forum: Installation &amp; Upgrades
---

### Post by holiday on 2010-08-20
I have Ubuntu 9.10 running in one partition and XP in another partition. I no longer use the XP partition because I've been meeting my XP requirements using VirtualBox. I need XP just for some simple work stuff. 

I would like to install Ubuntu 10.4 to some part of the XP partition, turn my existing Ubuntu partition into my /home partition, and turn what I can of the remaining ex-XP partition into another Ubuntu partition. 

The problem I see is that I would then have two boot partitions.

Please, how do I approach this problem? Links will be appreciated, of course, but some solid guidance is what I'm hoping for.

Thank you.

---

### Post by presence1960 on 2010-08-20
why don't you back up your data to an external hard disk and just delete the entire xp partition using gparted and create your partitions from the unallocated space that came from the former xp partition. then install ubuntu 10.04 and choose manual setup. Choose your /home partition by highlighting it and clicking change or edit. Choose the file system type and then under mount point use the drop down box to select /home. NOTE: failure to do this will result in your intended /home partition not auto mounting at boot of 10.04. If you want it to auto mount for karmic you will have to edit the fstab file in 9.10

Then highlight your intended ubuntu 10.04 / partition and do the same thing- except this time choose / as the mount point. 

You may want to set up a swap partition also if you don't already have one.

Proceed with the install.

Now put your data from the external disk to your /home partition.

---

### Post by holiday on 2010-08-21
That is practical and straightforward advice. Thank you.

---

