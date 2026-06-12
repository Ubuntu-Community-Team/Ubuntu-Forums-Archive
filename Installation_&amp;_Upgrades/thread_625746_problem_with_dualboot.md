---
title: "problem with dualboot"
date: 2007-11-28
forum: Installation &amp; Upgrades
---

### Post by amimaya on 2007-11-28
I use Acronis Disk director and  installed xp, win2k, RedHat and now I want to install Ubuntu
all of each on different partitions, and another partition for swot 

when I install Ubuntu it some how sees all of my hd and not only the partition that I defined for it with the Acronis (and all the rest of the partitions are hidden) 
if I want to make a new partition I get a msg that all the files on the hd will be erased 

:confused:

How can I install it then?

---

### Post by bernied on 2007-11-28
Have you tried leaving empty space with your acronis tool, rather than creating a partition for ubuntu? See if  the ubuntu installer can find the empty (unpartitioned) space, rather than trying to find a partition defined by a foreign partitioning tool.

---

### Post by amimaya on 2007-11-29
The Ubuntu finds all of the 80g HD not only the unallocated 
xp- 5 g
win2k -6g
redhat- 7-g
swot- 1.5g
ubuntu- 6.5g
and the rest is unallocated
the Ubuntu some how sees all of the HD

---

### Post by bernied on 2007-11-29
The installer should give you the option to either use the whole disk, or to set up your partitions manually.

So, to clarify, are you unable to select manual partitioning of the disk? Or, when you do, are there no partitions shown at all?
If this is the case then it would seem that the the partition table that is created by the Acronis software is not recognised by the ubuntu system. Weird.

Can you open a terminal within the live-cd environment?
See what you get from this command:
```
sudo fdisk -l
```
Does it show any partitions?

---

### Post by amimaya on 2007-12-02
Yes, It shows...
>    Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         637     5116671   17  Hidden HPFS/NTFS
/dev/sda2   *         638        1290     5245222+  17  Hidden HPFS/NTFS
/dev/sda3            1291        3472    17526915    5  Extended
/dev/sda4            2362        2492     1052257+  82  Linux swap / Solaris
/dev/sda5            1291        2361     8602776   bb  Boot Wizard hidden
/dev/sda6            2493        3472     7871818+  83  Linux

but when I want to install it- it dosent see the partittions
pic is attached:

---

### Post by PmDematagoda on 2007-12-02
Why are you using the OEM install method? That maybe the problem you are having, try using the normal installation method.

---

### Post by amimaya on 2007-12-02
did that, same result

---

### Post by Pumalite on 2007-12-02
Get Gparted Live CD and boot from it. See if it detects your partitions and you'll be able to change them, resize them, etc

---

### Post by amimaya on 2007-12-02
i'm using the Acronis disc director and Os selector, as i said i managed to have 3 different OS- win xp, win 2k and redhat

Any other ideas what to do? How come the Ubuntu sees my partitions but chooses to ignore them while installing?

---

### Post by Pumalite on 2007-12-02
Use Gparted Live CD (drives unmounted)

---

### Post by bernied on 2007-12-02
> **amimaya said:**
> i'm using the Acronis disc director and Os selector, as i said i managed to have 3 different OS- win xp, win 2k and redhat

Any other ideas what to do? How come the Ubuntu sees my partitions but chooses to ignore them while installing?
My best idea on this is that the installer is NOT using fdisk to detect partitions, so while you can see the partitions with fdisk, the installer cannot see them - perhaps it uses parted (partition editor), which is the base for gparted (as mentioned by Pumalite). 

This doesn't solve your problem though, I'm sorry.

---

