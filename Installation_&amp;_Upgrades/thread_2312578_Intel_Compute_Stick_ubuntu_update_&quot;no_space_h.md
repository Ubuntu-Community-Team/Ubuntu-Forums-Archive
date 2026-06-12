---
title: "Intel Compute Stick ubuntu update &quot;no space howto extend partition to USB partition?&quot;"
date: 2016-02-05
forum: Installation &amp; Upgrades
---

### Post by jonas-thornvall on 2016-02-05
I have run out of space on my Intel compute stick only 5 GB on root partition, is there an easy way to extend  the partition to another USB stick or USB HDD so it will let me update?

---

### Post by jonas-thornvall on 2016-02-05
Found this about logical disk volumes using lvm2 but i was hoping for something far simpler and i am not even sure this approach will work will it?
[https://linuxconfig.org/linux-lvm-logical-volume-manager](https://linuxconfig.org/linux-lvm-logical-volume-manager)

---

### Post by jonas-thornvall on 2016-02-05
Did the ugly solution removed the swap partition and moved to USB but if someone know howto to it i am still interested i would like to extend the root partition over the SD card.

---

### Post by Dennis N on 2016-02-05
The lvm method will work. You can use combine several partitions on your system into a single volume group, then make one or more logical volumes out of that space. Problem is, this is destructive of any data already on those partitions.

There are how-tos to be found on the Internet.

---

### Post by C.S.Cameron on 2016-02-05
I have an old EEEPC with 4GB drive.
I installed Ubuntu to a SD card and ran the EEE from that.
Speed is not an issue if only a few programs are running, as they should be running in RAM.
A proper SD card should have wear leveling and be able to last many years if not decades.
First try installing the 32 bit version either as Persistent or Full install.
Booting will take a little longer with a Persistent install.
You should not have to worry about messing up the current install, pressing [F8] during boot will activate "Operating System Recovery" and you can reset the stick to Factory spec's.

---

### Post by jonas-thornvall on 2016-02-06
Thank you Dennis, i found another solution someone has already managed to make a forked 14.04 distro with the missing drivers. I downloaded it and installed it upon HDD.
And i am a bit afraid to accidently **** up the factory reset partition that guess is the FAT32 one on the stick.

So i am all keen to go, now i would just like to make some deb packages out of drivers so i can use them with other distros.

---

### Post by jonas-thornvall on 2016-02-06
The problem was that the drivers iwas missing, not open source but i found a CD image where someone forked them.
So i got it running from HDD my SD card seems slower to write to so i use it to install the distros from using unetbootin.

But i would like to know how i can extact the drivers from ISO and make debs out of them.

---

