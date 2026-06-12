---
title: "does not recongize HD after fail ext 3 formating"
date: 2008-06-04
forum: Installation &amp; Upgrades
---

### Post by neuromancer2701 on 2008-06-04
I am trying to setup Xubuntu on my friends old laptop(HP pavilion ze1230).  Installation went pretty well until it started formating the HD, I just used the automatic feature instead of doing it manually.

It started with an ext3 partition(could have been the swap not sure) got to 5% and hung there until it failed.  Now if I try to install it again it does not recognize the HD at all, neither does fdisk(DOS).

I tried resetting the MBR with the dd command but I don't know if that did anything, fdisk(DOS) or cfdisk still did not recognize.
dd if=/dev/zero of=/dev/hda bs=256 count=1

Anyone ran into this problem? 

Thanks

---

### Post by wpshooter on 2008-06-04
Does this computer currently have any other valid O/Ss installed on it ?

---

### Post by neuromancer2701 on 2008-06-04
He tried to install Kubuntu on it, not sure how far he got, the laptop had XP on it before that.

---

### Post by wpshooter on 2008-06-04
If it were me I would get [www.killdisk.com](www.killdisk.com) and WIPE the hard drive completely clean AFTER I have saved anything from it that I might want to keep.

And then I would try to install Xubuntu and I would use the manual partitioning and not automatic.

I would partition as:

/ = root - 15gb if that much available
/home = home - balance of drive space after root & swap
/swap = swap - 2 times the amount of physical memory - for storage if physical memory become to low.

Good luck.

---

### Post by neuromancer2701 on 2008-06-05
Thanks for the tips

KillDisk worked great and Xubuntu recongized the HD and I was able to partition it, but it has been stuck @ 15% for the last 10+hrs.(@ detecting file systems)

I think the hard drive might be bad, I don't know what else would be causing all these problems.(I have not seen the HD led blink since it got to 15%)

Side Note: I used the swap type partition, not just an ext3 partition labeled /swap.


Thanks for the help again.


Edit: I restarted the install and changed the swap to /swap(ext3)  installation got passed all the partitioning started installing the software.  Everything looked good all of a sudden the screen when dark.
I rebooted now it just comes to the initfras(not sure about the spelling) prompt when I try to install again.

---

