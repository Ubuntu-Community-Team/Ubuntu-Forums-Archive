---
title: "i need help with ubuntu next to vista install"
date: 2009-12-03
forum: Installation &amp; Upgrades
---

### Post by atgreen1 on 2009-12-03
a friend brings me over a pc it has vista on it and he tried to install ubuntu 8.10 next to vista but in the middle of the install he shut it off thinking it was stuck (it was not stuck it had 320 gig hard drive os it would take some time to finish) os now he wants me to fix it .???? anyone know what to do at this point? he would like to save all the stuff on vista but he did not back it up before starting this quest of his.i was thinking maybe use alive cd to get the save info off from vista part of hard drive and save to a usb.then reinstall the hole thing all over.   what do ya think? maybe thanks in advence you guys are great around here.. atgreen1

---

### Post by lykwydchykyn on 2009-12-03
What state is the computer in at this point?  

What happens when you turn it on?  

If you boot to the liveCD and look at a partition editor, how many/what kind of partitions do you see?

---

### Post by halj32 on 2009-12-03
you could try to re install & manualy do the partitions

---

### Post by darkod on 2009-12-03
> **lykwydchykyn said:**
> What state is the computer in at this point?  

What happens when you turn it on?  

If you boot to the liveCD and look at a partition editor, how many/what kind of partitions do you see?

+1

Definitely first thing to try. Boot with the LiveCD, Try Ubuntu option, see what partitions exist, whether it can open the ntfs vista partitions etc. If it can best to copy all needed data to usb hdd straight away. After you have the data safe, you can decide whether to start all over including clean install of both vista and ubuntu, or just try another ubuntu install.

---

### Post by oldfred on 2009-12-03
If it was in the middle of repartitioning the partition table may need fixing. One program is testdisk, that is one many repair LiveCD or can be downloaded from the repositories. If you want to recover files do not write anything to the drive, the more changes the harder it will be to recover anything.

If testdisk can recover the partitions, you may have to reinstall the Vista boot loader and or run Vista's repair. It is best to use Vista's partition tool to resize Vista to make room for Ubuntu rather than letting Ubuntu resize it to add the new install. If you let gparted/ubuntu resize Vista you have to run the Vista repairs to get it working again anyway.

repairs including testdisk info & link to testdisk
[http://members.iinet.net.au/~herman546/p21.html](http://members.iinet.net.au/~herman546/p21.html)
download TestDisk [http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)
As described, it has an option to "Recover NTFS boot sector from its backup"
Instructions
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)

---

