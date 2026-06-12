---
title: "DMRAID hangs with Jmicron fakeraid"
date: 2007-05-14
forum: Installation &amp; Upgrades
---

### Post by dvazriel on 2007-05-14
I have 2 320 Gigs in Raid0. Its running a jmicron chip ( Gigabyte DS3-P965 mobo ). I have XP and Vista installed on the drive no problem.


I followed the instructions and got dmraid, but once it downloads and installs it get stuck for like 10-15 mins in the *SETTING UP RAID DRIVES*, then it closes.

this is what i get...

ubuntu@ubuntu:~$ sudo dmraid -r
/dev/sda: jmicron, "jmicron_GRAID           ", stripe, ok, 625082368 sectors, data@ 0
/dev/sdb: jmicron, "jmicron_GRAID           ", stripe, ok, 625082368 sectors, data@ 0

if i try to activate them via
sudo dmraid -ay
it again gets stuck for about 10-15mins.

gparted still shows sda/sdb 320 each, i dont see the /dev/mapper/xxxxx anywhere.

Help?

---

### Post by dvazriel on 2007-05-14
bump

---

### Post by psusi on 2007-05-14
What version of Ubuntu are you using?

---

### Post by dvazriel on 2007-05-14
7.04.

Tried both 32bit and 64 bit ( i have core 2 duo )

---

### Post by psusi on 2007-05-14
What if you install dmraid and run sudo dmraid -ay from the livecd?

---

### Post by dvazriel on 2007-05-14
> **psusi said:**
> What if you install dmraid and run sudo dmraid -ay from the livecd?

Thats what i have been doing, and everytime, it just hangs. =(

---

