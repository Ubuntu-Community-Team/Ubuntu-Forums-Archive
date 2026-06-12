---
title: "Uninstalling GRUB"
date: 2010-02-27
forum: Installation &amp; Upgrades
---

### Post by Grykus1 on 2010-02-27
All right, so I've gotten my self in one mighty big mess.
I've been **Dual-Booting Windows Vista Home Premium 32-bit** and **Linux Ubuntu 9.04** for a while now. And just today I decided I didn't want Ubuntu any more. So I loaded up in to Vista and deleted the Ubuntu partition. I then extended the Vista partition to fill up the new 70 GB of unallocated space.

After running a Defrag I restarted my computer, but it still tries to load **GRUB 1.5**. And every time it end up getting **Error 22**. I can no longer access Windows and I'm on these forums thanks to a **Linux Live-CD**.

I need a way to get rid of GRUB for good.

_**My PC Specs:**_
[B]80GB Hard Drive + 160GB Hard Drive
Windows Vista Home Premium 32-bit Upgrade Disc
2GB RAM
Nvidia GeForce 7300 GS[/B]
**Intel Pentium D 2.66 GHz**
[RIGHT]Thanks,
Will
[/RIGHT]

---

### Post by darkod on 2010-02-27
There are two ways, using a vista install dvd (or repair cd), but it's easier using the ubuntu cd.
Boot into live desktop as you are doing, and execute:

sudo apt-get install lilo
sudo lilo -M /dev/sda mbr

In the above I assume you have a single hdd which is /dev/sda. If unsure execute first:

sudo fdisk -l

and note the name of the hdd.

That will install generic mbr on the hdd and after restart it should boot vista directly.

---

### Post by dmj99 on 2010-02-27
Correct.  You need to re-install the Vista bootloader.  Even though you have deleted the linux partition, grub is still on your MBR.  Here is a good reference:

[http://neosmart.net/wiki/display/EBCD/Recovering+the+Vista+Bootloader+from+the+DVD](http://neosmart.net/wiki/display/EBCD/Recovering+the+Vista+Bootloader+from+the+DVD)

---

### Post by Grykus1 on 2010-02-27
Hmm, well I use 2 Hard Drives. As mentioned in the first post. But I'll try.
And I've already tried the Startup Repair, it claims there was no problem. But the problem was still there. I'll try the manual fix though.
Thanks for the reply.

---

### Post by darkod on 2010-02-27
> **Grykus1 said:**
> Hmm, well I use 2 Hard Drives. As mentioned in the first post. But I'll try.
And I've already tried the Startup Repair, it claims there was no problem. But the problem was still there. I'll try the manual fix though.
Thanks for the reply.

You can use the command on both drives, it will be no harm. There is a way to see where is it installed exactly if you want. Follow these instructions for the boot info script:
[http://ubuntuforums.org/showpost.php?p=8844901&postcount=4](http://ubuntuforums.org/showpost.php?p=8844901&postcount=4)

---

