---
title: "Upgrade from 7.10 to 8.04 from CD"
date: 2008-05-14
forum: Installation &amp; Upgrades
---

### Post by zoqaeski on 2008-05-14
Hello everyone
I recently acquired the 8.04 disk in the mail, hoping that I would be able to use that one to perform some kind of upgrade on my existing set up. You see, although my computer is connected to the internet, doing any kind of updating uses up all of my internet credit, which I need for my other work. I was wondering if there is some way to use the Shipit supplied CD to somehow upgrade my system without losing my existing settings. I’ve got the common sense to have a separate /home partition, but there are other settings which are vital to the functioning of this machine as it is; a fresh install will wipe those.

Can anyone give me some tips as to how I can get around this and upgrade without using much of my internet credit?

---

### Post by logos34 on 2008-05-14
You can't use the live/desktop cd--you need the 8.04 text-mode Alternate install CD.  Maybe try downloading it at an internet cafe or public library that has broadband connection.  Save it to usb stick.  Burn it to cd at home and [upgrade]("http://www.ubuntu.com/getubuntu/upgrading#head-7311a7de9fdf1ca310c6937460c0a9d33f54279d").


If you have to reinstall check out [this guide.]("http://techknack.blogspot.com/2008/05/upgrade-ubuntu.html")

In either case make sure to specify but NOT format your separate /home partition.

---

### Post by Sef on 2008-05-14
> You can't use the live/desktop cd--you need the 8.04 text-mode Alternate install CD

With the alternate cd, you still wipe out the old settings.

> I was wondering if there is some way to use the Shipit supplied CD to somehow upgrade my system without losing my existing settings

Not to my knowledge.

---

### Post by logos34 on 2008-05-14
> **Sef said:**
> With the alternate cd, you still wipe out the old settings.

Obviously things like sources.list and xorg.conf get changed, but doesn't a lot remain roughly the same, like fstab, menu.lst (just the new kernel gets added), hdparm.conf etc?  Doesn't it also leave untouched stuff in /opt and /usr/local?

---

### Post by zoqaeski on 2008-05-14
I got a copy of the alternate cd, and did an upgrade... or so I thought. Now the system seems to be partially broken, because it doesn’t seem to have upgraded properly. Some applications, such as Epiphany, are consistently spitting the dummy.

---

### Post by logos34 on 2008-05-14
try running 

sudo dpkg --configure -a

---

