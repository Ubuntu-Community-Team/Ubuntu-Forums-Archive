---
title: "Installing GRUB help"
date: 2007-06-13
forum: Installation &amp; Upgrades
---

### Post by Jono04 on 2007-06-13
I'm new to Ubuntu so I'm still trying to get my head around some things.

I have a 160g hdd partitioned into 2 80gig partitions.

Partition 1 has Ubuntu installed on it.
Partition 2 has Windows XP installed on it.

I installed Ubuntu first then installed XP, When I finished setting up XP and rebooted I was never giver an option to boot into Ubuntu. I also never created a boot floppy for Ubuntu which I think I'm going to regret.

Do I need to install Grub to allow me to choose between OS on boot up? If so how can this be done?

Cheers Jono.

---

### Post by confused57 on 2007-06-13
You can use the live cd to reinstall grub:
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

Then add an entry to boot Windows...boot into Ubuntu, open a terminal(Applications---Accessories--Terminal):
```
cd /boot/grub
sudo cp menu.lst menu.lst_backup
gksudo gedit menu.lst
```

Then add an entry to the very bottom of the menu.lst file:

```
title   Windows XP
root   (hd0,1)
savedefault
makeactive
chainloader +1
```
quit & save

If you're not sure which partition your Windows is on:
```
sudo fdisk -l
```
the -l is a lowercase "L"

for example, sda2 would be (hd0,1)...sda3 is (hd0,2)...you get the picture.

---

