---
title: "I don't understand How to make partitions?"
date: 2009-11-27
forum: Installation &amp; Upgrades
---

### Post by pandurang_m on 2009-11-27
Hi everyone,

I am user of Windows and thought to completely switchover to Ubuntu and I bought 1TB of internal HDD for Ubuntu and want to install only Ubuntu no Dual Booting.

The first time I installed Ubuntu I selected the option to completely use my entire HDD, now I thought if Ubuntu crashes like Windows what shall I do to my 1TB HDD...So I thought to create partitions...Now I don't don't understand how to create partitions...

I am not able to understand, / , /boot , /home, /var ,etc I get these options when I want to create partitions...What are all these things?? and getting confused.

What is SWAP???

With 1TB of HDD which is the way to install Ubuntu, only Ubuntu.
Whether to use partition or not??
I just want to have 2 partitions. 

Which is the best way to install Ubuntu??? 

Please help me, I am in the middle of the installation.

---

### Post by pandurang_m on 2009-11-27
Please help me.....

---

### Post by darkod on 2009-11-27
If you want to have only Ubuntu on the drive I would suggest to read about LVM (Logical Volume Manager). In short, you dedicate all of your hdd space to it, but it allows you to create small partitions and then expand them when you want without losing the data, without the need to reformat them, etc.
Some basic guides are here:
[http://linuxbsdos.com/2008/11/11/lvm-configuration-in-ubuntu-810/all/1/](http://linuxbsdos.com/2008/11/11/lvm-configuration-in-ubuntu-810/all/1/)
[http://www.ibm.com/developerworks/library/l-lvm/](http://www.ibm.com/developerworks/library/l-lvm/)
[http://www.ibm.com/developerworks/library/l-lvm2.html](http://www.ibm.com/developerworks/library/l-lvm2.html)

The only thing is that for LVM you need to use Alternate Install CD, not Desktop. It will still install desktop version but the installer is text based without GUI. And make sure you select to install gnome-desktop so you don't end up with text based system.

With LVM you don't have to worry how big to create the partitions, because you can resize them later.

PS. If all of that is too much for you, just use the Use Whole Disk option and let ubuntu create the partitions for you the way it wants.

---

### Post by audiomick on 2009-11-27
Make a swap a bit bigger than your RAM. That is where the computer puts stuff it is using at the moment when the RAM gets full. It need to be at least as big as RAM for the suspend functions to work, but not too much bigger, maybe 4.5 for 4GB RAM

Make a partition about 10 - 15 GB and mount it at /

this is where the operating system itself will be. It will probaly have less than 3GB in it after the install.

You can then make the rest of the space into one partition and mount it at /home, or some of the rest for a partition for /home, and another partition for data or backups or what have you, that you can mount for instance in /media/backups.

It is good to have /home on it's own partition, because then, if you have to re-install, you can just re-mount it, and all your files and config stuff is still there.

---

### Post by audiomick on 2009-11-27
If you want to take time to read what Darko posted, you can break off the installation without any worries. :p

---

### Post by pandurang_m on 2009-11-27
What is "/Home" "/Boot" "/Var" etc what exactly does it mean???

---

### Post by darkod on 2009-11-27
I don't want to sound rude, but there are at least hundreds of tutorials about /home and /boot to read on google. You are not talking about specific problem here, you are asking about something you can easily find to read.
If you decided to go for Ubuntu, and only Ubuntu on your computer, you should spend some time to read the basic info about it and linux in general.

PS. If you have specific question how to create some partitions, just ask. But we can not make the choice for you whether you want separate /home, /boot or /var partitions. Usually it's better to have separate /home but others are not needed for general home use. It all depends what you want to do with it, and only you know that.

---

### Post by oldfred on 2009-11-27
I have saved a few of the links on partitioning.

[https://help.ubuntu.com/community/InstallingANewHardDrive](https://help.ubuntu.com/community/InstallingANewHardDrive)
[https://help.ubuntu.com/community/HowtoPartition/OperatingSystemsAndPartitions](https://help.ubuntu.com/community/HowtoPartition/OperatingSystemsAndPartitions)
[http://ubuntuforums.org/showthread.php?t=282018&highlight=separate+%2Fdata+partition](http://ubuntuforums.org/showthread.php?t=282018&highlight=separate+%2Fdata+partition)
[http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning)
Screenshots of using gparted
[http://www.howtoforge.com/partitioning_with_gparted](http://www.howtoforge.com/partitioning_with_gparted)
[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)
[http://www.howtoplaza.com/how-to-install-ubuntu-904-on-a-manually-created-partition](http://www.howtoplaza.com/how-to-install-ubuntu-904-on-a-manually-created-partition)

---

### Post by raymondh on 2009-11-27
[http://ubuntuforums.org/showthread.php?t=282018](http://ubuntuforums.org/showthread.php?t=282018)

Post back if you need a guide on how to create partitions beforehand and using a "manual" install.

Root is /.  That is your system files.
/home is where your config and personal files reside
Swap is .... a temporary place that can be accessed easily (not necessarily fast).

Regards and welcome :)

---

