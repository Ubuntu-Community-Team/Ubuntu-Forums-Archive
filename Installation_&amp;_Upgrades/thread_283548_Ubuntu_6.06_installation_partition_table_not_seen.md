---
title: "Ubuntu 6.06 installation: partition table not seen"
date: 2006-10-24
forum: Installation &amp; Upgrades
---

### Post by zakhooi on 2006-10-24
Hi,

I've been reading through several threads about this but none was similar to my situation.
I've a system that already has running linux and win xp (dual boot).
THe system has only one HD.

When I boot from the Ubuntu 6.06 (Dapper, desktop version) and open a terminal in gnome and execute 'sudo fdisk -l /dev/hda' it will show me my partitions.

However, when I try to install ubuntu on this system at the point where I need to configure my partitions (I choose the option to partition my disk manually) it doesn't show any partitions and the only option I've got is to repartion the entire disk.

I only want to install ubuntu on the existing ext3 partion. So I don't want to change partitions at all.

Any idea how to overcome this?

Thanks in advance

---

### Post by taurus on 2006-10-24
Try the alternate CD since it gives you more control over the partition part.

---

### Post by mcdonaghm on 2006-10-24
What is the alternate CD ?

I have tried to install Ubuntu, but when I get to the partioning section, none of the existing partitions are shown.

From the desktop, if I use GParted I get the same result; but if I use Disks Manager I can see the partitions on the disk (and the free space ready for Ubuntu).  Any ideas ?


thanks


Martin

---

### Post by taurus on 2006-10-24
> **mcdonaghm said:**
> What is the alternate CD ?

Martin

Okay, here's a link for you.  Just scroll down until you get to Alternate install CD section and read it.  Then, you can download the alternate CD further down of that page...

[http://ubuntu-releases.cs.umn.edu//6.06/](http://ubuntu-releases.cs.umn.edu//6.06/)

---

### Post by mcdonaghm on 2006-10-25
thanks, it worked a treat; now up & running

---

### Post by ribena on 2006-10-28
I'm having similar issues with 6.10 but have tried the alternative cd and haven't had any luck...

[http://ubuntuforums.org/showthread.php?p=1676755](http://ubuntuforums.org/showthread.php?p=1676755)

---

### Post by markymark on 2006-10-28
similar problems here too
[http://ubuntuforums.org/showthread.php?t=286931](http://ubuntuforums.org/showthread.php?t=286931)
have tried install cd for edgy,
alternative boot cd for dapper and gparted; and latest test of
debian etch and the same problem occurs; parted/gparted
is not reading the partition on the disk, which was
previously written using cfdisk
best wishes,
Mark

---

### Post by zakhooi on 2006-10-29
For me, the 6.10 CD using gparted did work.
But I noticed that booting again from the CD might help as well (looks like that this problem doesn't occur every boot)

---

### Post by yhom on 2006-11-14
Hi,

I'm experiencing the same problem with ubundu edgy desktop :
2 partitions exist, winxp "root" + swap + previous ubuntu dapper + winxp "home" , but here comes gparted that do not detect any partition, and i'm stuck in the beginning of install.
I remember having the same problem with dapper desktop, then finally used the alternate cd -but i'm not that sure...

So I'll try the alternate method ; however, it's annoying for beginner user, because it's a typical double boot install with which you're starting with ;-).

If anybody want's more details to go on with bug fixing... 

Yhom

---

