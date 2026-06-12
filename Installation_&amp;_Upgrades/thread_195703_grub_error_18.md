---
title: "grub error 18"
date: 2006-06-13
forum: Installation &amp; Upgrades
---

### Post by flightcrank on 2006-06-13
i have a older computer i want to install ubuntu on.

after i installed it i get a "grub error 18" and it wont boot.

i googled that i have to mak a /boot partition for it to work

this is what i need, a /boot partition a "/" root partition and a swap area.

how do i go about doing this, 
what partitons need to be logical and primary ? 
what ones should have bootable flags on ?
how big should the /boot partition be ?
how do i install grub on the /boot partition ?
How the the hell do i get this to work ?

---

### Post by Rui Pais on 2006-06-13
hi,
grub don't care if is partitions are primary or a logical ones.
If you have a empty hard disk try

Primary: hda1 -> /boot (~30M)
Primary: hda2 -> /       (it will depend on disc space, but 1.5 G is the minimum to be confortable, more if possible)
Primary: hda3 -> /home (the rest of it)
Extended: hda4
Logical: hda5 -> /swap (~500M)

or if you do not plan to have other partitions:
Primary: hda4 -> /swap (~500M)
(note that if you choose this one will be hard to change later if you decided to add more partitions, since 4 is the limit for primary partitions)

check the Wiki on Grub install:
[https://wiki.ubuntu.com/GrubHowto]("https://wiki.ubuntu.com/GrubHowto")

---

### Post by clemkonan on 2006-06-13
I just reinstalled ubuntu 5.10 and got the same message strangely I did not have this issue on the first install. with referecne to the commands you liste above 

rimary: hda1 -> /boot (~30M)
Primary: hda2 -> / (it will depend on disc space, but 1.5 G is the minimum to be confortable, more if possible)
Primary: hda3 -> /home (the rest of it)
Extended: hda4
Logical: hda5 -> /swap (~500M)

where are these being entered?

My drive is 250G

---

### Post by flightcrank on 2006-06-13
How dose grub know to install in the /boot partition, what about the bootable flag where should this be set.

i got a 
primary 500mb "/boot" ext3 bootable flag set on ON
primary 7.9 GB "/" ext3 bootable flag set on OFF
500mb swap

---

### Post by Rui Pais on 2006-06-14
[QUOTE=clemkonan]I just reinstalled ubuntu 5.10 and got the same message strangely I did not have this issue on the first install. with referecne to the commands you liste above 

rimary: hda1 -> /boot (~30M)
Primary: hda2 -> / (it will depend on disc space, but 1.5 G is the minimum to be confortable, more if possible)
Primary: hda3 -> /home (the rest of it)
Extended: hda4
Logical: hda5 -> /swap (~500M)

where are these being entered?

My drive is 250G[/QUOTE]
Hi, 
if you install Breezy at a certain point of install process you should have to  config and format your partitions. I never install breezy, just dist-upgrade my old hoary, so i don't know exactly but should be an initial option on a ncurses (those simulates graphical interfaces with lot of red and blue) program/wizard.

anyway you can enter those definition on fdisk or even better on cfdisk, that are easier ot work. If you want to try dapper you got nice guis and gparted that make it easy to visualize the all process. For example:
> sudo cfdisk /dev/hda
should gives acces to your hd and allow to make the partitions. parted or plain mke2fs will allow you to format them after created. But install wizards have subprograms that do both automatically for you.


But back to your problem. 
You got an old computer with a big (BIG) HD. Thats the guilty one.
Old bios sometimes have problem to deal with the new HDs bigger then 8G, here some infos: 
[http://wiki.linuxquestions.org/index.php?title=GRUB#Error_18]("http://wiki.linuxquestions.org/index.php?title=GRUB&printable=yes#Error_18")
and at [wiki.ubuntu.com]("https://wiki.ubuntu.com/WartyWarthogInstallNotes")
here are some threads on it:
[http://www.ubuntuforums.org/showthread.php?t=16625]("http://www.ubuntuforums.org/showthread.php?t=16625")
[http://www.ubuntuforums.org/showthread.php?t=6448]("http://www.ubuntuforums.org/showthread.php?t=6448")
and probabilly there exist new ones around...

Seems that most people solve the problem by setting bootable partition on the beginning of HD (1st partition) and/or change setting on BIOS (enable/disable LBA or AUTO detection mode). And check if there is motherboard specific upgrades 
(i had bad experiences with upgrade motherdoards bios, i only look at this if anything else failed)

Good luck

---

