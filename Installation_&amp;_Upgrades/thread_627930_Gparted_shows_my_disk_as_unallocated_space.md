---
title: "Gparted shows my disk as unallocated space"
date: 2007-11-30
forum: Installation &amp; Upgrades
---

### Post by puttputt on 2007-11-30
I am trying to install Ubuntu, but Gparted shows my disk as unallocated space. 
But I know for sure that I have two NTFS partions, one ext3 and one swap.
Gparted shoews my disk like this
[ATTACH]51888[/ATTACH]
But it should look like this
[ATTACH]51889[/ATTACH]
I would like to install it on the existing ext3 partion, but the installer don't give me that as a choise
Please help me

---

### Post by Pumalite on 2007-11-30
Post your specs.

---

### Post by puttputt on 2007-11-30
I have a Fujitsu Amilo M 1425 with &#8206;Intel(R) Pentium(R) M processor 1.80GHz
and a Toshiba harddrive Model: &#8206;MK6025GAS with the following Partitions
Primary partitions: &#8206;2 (hda1, hda3)
Extended partitions: &#8206;2 (hda5, hda6)
Running windows XP and PClinuxOS 2007

---

### Post by Shazaam on 2007-11-30
You get this running the Ubuntu live cd? I have had that happen with disasterous results (caused by ME panicking). Try this= shut your pc down completely and do a COLD boot with the live cd in the drive and post back with your results.
IMHO the cause is that the livecd loads Ubuntu into ram and sometimes you can run across this glitch.

edit...
MANDRIVA! I had that happen before with it already installed. Go here=

[http://gparted.sourceforge.net/download.php](http://gparted.sourceforge.net/download.php)

and download/burn a gparted livecd. This is the ONLY way I could get a correct view of my partitions when I had Mandriva installed.

---

### Post by puttputt on 2007-12-01
Ok, I solved it.

I found a program Testdisk at [http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk) 
This showed me that there was a space conflict between two partitions.
So, I backed up everything with Acronis True Image, Repartitioned the whole disk with Acronis Disk Director, and put everything back with Acronis True Image

And now, everything works fine with Gparted

---

### Post by Pumalite on 2007-12-01
Good luck!

---

