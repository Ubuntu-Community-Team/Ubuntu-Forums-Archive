---
title: "Super Grub CD"
date: 2007-11-04
forum: Installation &amp; Upgrades
---

### Post by brc on 2007-11-04
Hi,

I'm about to try Ubuntu on my desktop, (in dual boot with XP Sp2)

if i understand correctly what i read on this forum whenever i would like to uninstall Ubuntu from my system it should be a piece of cake with this "Super Grub CD" or I am wrong ?

I'm just a bit scared that something goes wrong and i have to format my entire disk, losing al my data (including the one on my XP-partition)

thx 4 the help


grtz

Bram

---

### Post by Pumalite on 2007-11-04
Super Grub is more for 'rescue missions'.
[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)
[http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning)
[http://www.howtoforge.com/dual_boot_windows_xp_vista_ubuntu_feisty_p2?](http://www.howtoforge.com/dual_boot_windows_xp_vista_ubuntu_feisty_p2?)
Use Gparted Live CD for your partitioning: [http://gparted.sourceforge.net/download.php](http://gparted.sourceforge.net/download.php)

---

### Post by criskat777 on 2007-11-04
If all you wan't to do is try iT Download Gutsy and try it as a LIVE CD. you will be able to use it just like if it was installed. Or you could try Festy using Wubi (go to Wubi web page for more info) What wubi dose i installs ubuntu on you windows os as a file so you don't have to patition the HD or anything but what u will like the most is that to uninstall u just go to add and remove prog. on WIndows and you can remove it. Wubi will setup every thing even dual boot .

---

### Post by brc on 2007-11-04
i would like to install it and give it a good try, but i just want to know what the most safest way is to uninstall it if needed

Ubuntu changes the mbr etc when installing..
so what is the most safest way to uninstall if needed ?

---

### Post by Pumalite on 2007-11-04
You can erase the Ubuntu partition and the fix your MBR with Windows installation CD or Super Grub: [http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)

---

### Post by DaveRowell on 2007-11-04
If you look carefully there is a thread on "correctly" dual booting XP and Linux.  It suggests placing the start-up code in the root of the Linux partition, editing the XP boot loader so that it will start Grub -> Linux.  Nice thing is that it doesn't mess with the Windoze partition at all.  I can attest to the success of this procedure - works like a charm through several Ubuntu updates! ;-)  

I can't put my hands on the how-to right now but if you can't find it e-mail me and I'll see what I can do for you.

---

### Post by sandysandy on 2007-11-04
> **brc said:**
> i would like to install it and give it a good try, but i just want to know what the most safest way is to uninstall it if needed

Ubuntu changes the mbr etc when installing..
so what is the most safest way to uninstall if needed ?

you must definitely backup your mbr, no doubt about that.
 back up code is

sudo dd if=/dev/sdb bs=446 count=1 of=backup04nov07sdb-mbr

(assuming sdb (second drive) mbr u want to backup, incase of first drive use sda)

to restore mbr the code is

sudo dd if=/home/ubuntu/backup04nov07sdb-mbr of=/dev/sdb bs=446

(where backup04nov07sdb-mbr  is the name of  mbr backup file)

this backup file should be in your home folder incase ur using live cd.

regards

---

