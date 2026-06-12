---
title: "Can 9.10 and lucid 10.04 LTS run on the same machine"
date: 2010-03-27
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by hoboy on 2010-03-27
I have 9.10 running I will like to keep it that way, because i like it.
I want to install 10.04LTS on the same machine.
How can I do this ?
I am already using dual booting vista--9.10. on the the machine, that i want to install 10.04 LTS.

---

### Post by ubername on 2010-03-27
Yes.
I have 9.10, 2 versions of 10.04, a soon-to-expire Win7 and Vista all running on the same machine.

Simply boot from a 10.04 CD and when you get to the partition step choose either 'install alongside' (or whatever the exact words are) or, if you are comfortable with it, manually set up the partitions you want. Do NOT select the 'use entire disk' option, obviously. 

Or you could buy an(other) external HDD and install to that.

---

### Post by Roosje on 2010-03-27
> **hoboy said:**
> I have 9.10 running I will like to keep it that way, because i like it.
I want to install 10.04LTS on the same machine.
How can I do this ?
I am already using dual booting vista--9.10. on the the machine, that i want to install 10.04 LTS.

You free op some HD space, create 2 partitions (/ & /home) and install 10.4 there, just triple boot now.. Somehow the impression that is not what you where asking for, but anyway, have been working with 7+ OS's on my system for years (atm. Ubuntu flavors Jaunty/Karmic/Lucid, Fedora, Suze, XP, Debian Stable) Only some minor issues because more then 10 partitions seems to be a slight problem (for some software, like Storage device manager). 

Hope you are not intending to share /Home for both, can not see anything good coming from that ;-)

Wilco

---

### Post by hoboy on 2010-03-27
> **Roosje said:**
> You free op some HD space, create 2 partitions (/ & /home) and install 10.4 there, just triple boot now.. Somehow the impression that is not what you where asking for, but anyway, have been working with 7+ OS's on my system for years (atm. Ubuntu flavors Jaunty/Karmic/Lucid, Fedora, Suze, XP, Debian Stable) Only some minor issues because more then 10 partitions seems to be a slight problem (for some software, like Storage device manager). 

Hope you are not intending to share /Home for both, can not see anything good coming from that ;-)

Wilco

Tks guy I just want to keep 9.10 while testing 10.04LTS, ok nice to know that it can be installed on external harddisk

---

### Post by Roosje on 2010-03-27
> **hoboy said:**
> Tks guy I just want to keep 9.10 while testing 10.04LTS, ok nice to know that it can be installed on external harddisk

With USB creator you can make a usb-stick with the iso from 10.4 with room for small installs and settings, that works rather nice, and less hassle then installing it on a external drive.

Just my 2 cents ;-)

---

### Post by hoboy on 2010-03-27
> **Roosje said:**
> With USB creator you can make a usb-stick with the iso from 10.4 with room for small installs and settings, that works rather nice, and less hassle then installing it on a external drive.

Just my 2 cents ;-)

ok, i have an usb that is 32 giga so you mean that one can use that insteas of installing it ?

---

### Post by hoboy on 2010-03-27
> **Roosje said:**
> You free op some HD space, create 2 partitions (/ & /home) and install 10.4 there, just triple boot now.. Somehow the impression that is not what you where asking for, but anyway, have been working with 7+ OS's on my system for years (atm. Ubuntu flavors Jaunty/Karmic/Lucid, Fedora, Suze, XP, Debian Stable) Only some minor issues because more then 10 partitions seems to be a slight problem (for some software, like Storage device manager). 

Hope you are not intending to share /Home for both, can not see anything good coming from that ;-)

Wilco

create 2 partitions (/ & /home) ?
how do I do that ?

---

### Post by Roosje on 2010-03-27
> **hoboy said:**
> create 2 partitions (/ & /home) ?
how do I do that ?

Boot with live CD, from System>Administration use Gparted, choose hd that you want to use, make a partition with resize smaller that has the room apply the options, when ready (can take long time) in the free space create 2 new partitions, one smallish (i use 10 GB) to be used as root (/) Ext4
 system, and one larger (30+ ish) as your /home (also Ext4) after applying and ready, close Gparted.

Then start the installer choose manual when you are presented with partition choice, set the partitions as shown above, and continue the installation.

But, if you have never done this before, and have no experience with partitions etc. maybe you better let it as-is. Take a USB stick that is not in use (4+ Gb) use USB-Startup Disk creator to make a boot-able system (using the 10.4 beta ISO) on the usb stick when asked, set a persistent user space of reasonable size, set usb as boot option in your bios as first and when you want to use it, insert stick and reboot.. also very handy when a system crash has happened ;-)

---

### Post by hoboy on 2010-03-27
> **Roosje said:**
> Boot with live CD, from System>Administration use Gparted, choose hd that you want to use, make a partition with resize smaller that has the room apply the options, when ready (can take long time) in the free space create 2 new partitions, one smallish (i use 10 GB) to be used as root (/) Ext4
 system, and one larger (30+ ish) as your /home (also Ext4) after applying and ready, close Gparted.

Then start the installer choose manual when you are presented with partition choice, set the partitions as shown above, and continue the installation.

But, if you have never done this before, and have no experience with partitions etc. maybe you better let it as-is. Take a USB stick that is not in use (4+ Gb) use USB-Startup Disk creator to make a boot-able system (using the 10.4 beta ISO) on the usb stick when asked, set a persistent user space of reasonable size, set usb as boot option in your bios as first and when you want to use it, insert stick and reboot.. also very handy when a system crash has happened ;-)

Tks very much

---

### Post by Aname on 2010-03-27
Just to point out you don't need to make a separate /home partition, you can just install it onto one partition, set as root ("/") when you make the partition. Though there are some advantages to having a separate /home partition, this could be shared between different Ubuntu installations for example. I just use the one partition myself.

---

