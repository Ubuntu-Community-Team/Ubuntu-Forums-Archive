---
title: "Ext3 problem"
date: 2006-06-02
forum: Installation &amp; Upgrades
---

### Post by alien13 on 2006-06-02
Hello,

I am new to linux and have heard alot of good things about ubuntu so i decided to try it out. I want to put it on a 10GB drive just to mess around with, i followed the guide at h**p://www.pcmech.com/show/os/903/  and i get the error " The attempt to mount a file system with type ext3 in IDE1 slave, partition #1 (hdb1) at / failed". Is there a way to fix this:confused: 

                                                Thanks :)

---

### Post by pellgarlic on 2006-06-07
ok, a couple of questions:

1. is the 10gb drive the only one you have connected to the computer? if not, please list all drives, and the ide channels they occupy (primary/secondary, master/slave), and what is on each drive
2. does ubuntu boot, or does this error stop the bootup process, and if so, at what point?

---

### Post by alien13 on 2006-06-07
Hey,

Thanks for the reply. 

1) No, i also have a 80gb hard drive(primary/master) with windows XP Home on it as the main OS.
The 10gb hard drive is the slave hard drive. (i want it to let me choose what system to boot up)

2) I get this error when i am installing ubuntu. It happens at the partitioning step.

---

### Post by pellgarlic on 2006-06-07
i'm assuming you're using the newest live cd (6.06 - dapper drake)? if you are not, get it first.

it sounds like the partition has not been formatted as ext3 properly. i would guess the 10gb hard drive was formatted before, either as fat32 or ntfs. linux needs to format the hard drive as ext3 in order to be able to use it. this should be possible within the partitioner that runs as part of the install process - when you select a partition to install "/" to, you should make sure it is set to be formatted as ext3. also, if you are creating a "swap" partition, you should make sure it is set to be formatted as "swap" (if i remember correctly, this happens automatically when you change the type to "swap").

if the install still gives you that error, you could try formatting the partitions using "gparted", which is included in the live cd - click on the "system" menu, then "administration", then "gparted". it's quite similar to the "disk management" feature in windows. if you are familiar with that, you should have no problem. the main difference is, you have to click the "apply" button (the one with a "tick" on it) to commit the changes you make. 

just make sure not to change your primary "windows" hard drive, which will most likely be labelled "hda" (you can check by looking at the size of the drives). your 10gb drive will most likely be "hdb". each partition you add will labelled "hdbx" where "x" is an incrementing number. i would recommend making a 4.5gb ext3 partition for "/" and a 5gb ext3 partition for "/home" and a 512mb partition for "swap". these actions can all be accessed by rght-clicking on the drive/partition you want to apply it to. once you have made the changes in gparted, and clicked the "apply" button, retry the installation process - you will no longer need to make partitions, only select the ones you made in gparted.

when you get to the point that the installer is installing grub (which lets you choose whether to boot into windows or linux at boot-time), it should find your windows installation, and ask something like "is this all the operating systems you want to add?". say yes. you can choose whether to install grub to a partition, or to the mbr. i always choose the mbr option. don't know if it makes much difference, but i've never had any problems with it.

---

