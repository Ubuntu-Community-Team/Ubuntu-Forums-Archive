---
title: "How to: Install/Dual Boot Windows on an existing ubuntu"
date: 2007-12-26
forum: Installation &amp; Upgrades
---

### Post by shafin on 2007-12-26
I've answered in two very similar threads in this topic today in the beginners forum and could not find one How to in search.So I thought,I'd better compile my answers into a How to myself.

In many cases,you might need to install windows over your ubuntu machine or dual boot windows with your ubuntu machine.In that case,I hope this how to will help.But I know very few people will need this ;)

Anyway,you will normally be able to use wine to run the specific application or virtualbox to run windows itself under ubuntu. If that fails to do the work,here goes the guide:

To Install/Dual Boot windows:

1. If you dont have a ubuntu live CD download and burn one.

2. Boot from Live CD

3. run system>administration>GpartED

4.In GpartED,You'll have your Drives listed in a way like this:
Partition_____Filesystem ____Size ______Used______Unused____Flags
/dev/sds1 ____ext3 __________71.45gb____7.73gb____63.71gb___boot
/dev/sda2 ____extended ______3.08gb
/dev/sda5 ____linux-swap ____3.08gb
Here the ext3 drive is your linux drive and the linux-swap drive is your swap drive.There can be other ext3 drives as well as ext2,FAT32 or NTFS drives also.In that case,The drive with the boot flag will be your linux drive

5.Select the drive that have some unused space, select resize and take out spaces for your windows drive.

6.If you want to use all space from another drive for windows,you'll just need to move any data from that to the linux partition.

7.Then boot from windows installation CD,you'll have some unpartitioned space , create and format a drive from the unpartitioned space.

8.After booting,you'll see only windows,but no ubuntu. This is where the burned LiveCD comes in.

9.To fix it,Boot form Linux live CD.mount your primary partition in the terminal type sudo grub-install /dev/hda
a better guide on this step can be found [here](http://ubuntuforums.org/showthread.php?t=224351).Or you can simply re install ubuntu from the Live CD,if you have not customized your installation.If you reinstall,you'll lose all data in your linux drive.

10.If you need to use windows only,boot from ubuntu live CD, select the data you want to get from the ubuntu partition,and move them to xp partition.Afterwards,use xp disk manager form control panel>administrative tools to erase/resize/merge and format your ubuntu and swap disk.

Hope you'll not need it.

---

### Post by K.Mandla on 2007-12-26
Moved to Installation and Upgrades.

---

