---
title: "Vista Dual Boot with Ubuntu 10.04 (now removed) GRUB Error"
date: 2011-11-07
forum: Installation &amp; Upgrades
---

### Post by overcast on 2011-11-07
I was trying to upgrade the ubuntu from 10.04 to 10.10 yesterday and my brother formatted partition on which ubuntu existed from Vista's Disk management. Now both ubuntu and vista are inaccessible. GRUB is throwing partition related error (no such partition). 

How am i suppose to fix this ? 
[I]
(**Big Trouble** - Vista is OEM installation on this laptop, No DVD from HP and recovery partition was used for the ubuntu installation, so i lost the one-click vista recovery prompt during boot. I only have Ubuntu 10.04 live CD and there are no ways i can create boot CD or borrow from some other folks as there are no computers around town.)[/I]

---

### Post by fantab on 2011-11-07
> **overcast said:**
> I was trying to upgrade the ubuntu from 10.04 to 10.10 yesterday and my brother formatted partition on which ubuntu existed from Vista's Disk management. Now both ubuntu and vista are inaccessible. GRUB is throwing partition related error (no such partition). 

How am i suppose to fix this ? 
[I]
(**Big Trouble** - Vista is OEM installation on this laptop, **No DVD from HP and recovery partition was used for the ubuntu installation,** so i lost the one-click vista recovery prompt during boot. I only have Ubuntu 10.04 live CD and there are no ways i can create boot CD or borrow from some other folks as there are no computers around town.)[/I]

The Simplest solution is, since you have Ubuntu 10.04 Intallation CD/LiveCD , **Reinstall Ubuntu 10.04** where it was before and  the reinstalled GRUB will find and restore your Windows Vista.

Good Luck.

---

### Post by overcast on 2011-11-08
question reposted in recent reply, edit button wasn't working. hope some moderator deleted this reply.

---

### Post by overcast on 2011-11-08
Thanks.

One more question: is it possible to fix GRUB by booting into live CD and without installing ubuntu ? I want to install 11.10 on that partition and waiting for torrent downloads slow but will get there somehow. So it'll be pain to reformat and install ubuntu again especially when i have nothing to boot into.

---

### Post by darkod on 2011-11-08
Get the vista repair disc here:
[http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/](http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/)

It's not a full install (it would be illegal to post it) but it only allows you to repair existing installation boot problems. Note: it fits on a cd, you don't need to waste dvd, like I said it's not full vista install.

That will sort out Vista boot. When you have your new ubuntu cd, just install as you did earlier.

---

### Post by Quackers on 2011-11-08
Installing 11-10 should get both systems booting again.
If you want to get Windows booting on its own you could install lilo.

Enable universe repository in live cd desktop
Open a terminal and run ```
sudo apt-get install lilo
``` then ```
sudo lilo -M /dev/sda mbr
``` (assuming that /dev/sda is the hard drive to be booted - change if not).
This may give error messages but you can ignore them as you only need the MBR part.

---

### Post by overcast on 2011-11-08
Is it possible to reinstall ubuntu 10.04 to fix and to use entire partition of 8GB for ubuntu ? do i need to change some stuff during live cd install ?

---

### Post by darkod on 2011-11-08
> **overcast said:**
> Is it possible to reinstall ubuntu 10.04 to fix and to use entire partition of 8GB for ubuntu ? do i need to change some stuff during live cd install ?

If you want to use an existing partition, you need to select Manual in the partitioning step. The from the list of partitions on the disk you select the one you want to use, hit the Change button below.
In the window that opens, change the "do not use" option to ext4, the mount point to / and tick the format box.
If you have swap partition existing on the disk, ubuntu will use it automatically. If not, and you want to use one, you need to create it yourself.

And that should be it.

But you don't need to reinstall just to fix the windows boot. Look at my previous post with the link for the vista repair disc. Then when you are ready install the latest 11.10 if that's what you want.

---

### Post by overcast on 2011-11-08
THanks darko. I followed your instructions and made only one mistake of not creating swap partition. now when i check the free command in terminal. I get  000 for swap parition. 

> free
             total       used       free     shared    buffers     cached
Mem:        507992     445360      62632          0       5564     133936
-/+ buffers/cache:     305860     202132
Swap:            0          0          0
Now is there any way to create swap parition ? or allocate some space from existing swap file ?

---

### Post by darkod on 2011-11-09
You can resize your root partition to make space to create a swap partition, but sometimes that may break the OS on root.
Since this is a brand new install, it's probably easier to simply install once more.
When you reach the partitioning step, use manual again, first select the current root partition and delete it.
After it shows as unallocated space (free), create the root and swap partitions from that space. And that's it.

---

### Post by overcast on 2011-11-11
Thanks darko, just reinstalled with 1770MB for swap parition. hope things work out.

---

