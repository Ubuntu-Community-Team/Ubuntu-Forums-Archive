---
title: "Basic re-install question (partition and bootloader)"
date: 2010-04-15
forum: Installation &amp; Upgrades
---

### Post by Lord Stig on 2010-04-15
Hi.
Probably a very basic question, but if I don't ask and just assume then I may become unstuck later, and I'm messing with someone else's computer and their partitions!

I installed Mint 8 on my sister's laptop (after her existing Vista, and I did so on a separate partition created during the normal setup process in Gparted) and she now wants to try out another distro and take off Mint, so how would I go about this?
Would I boot from the distro's live CD, determine the correct partition, (I'm thinking of Gparted here) and then... what?
1) Would I have to mark the partition to be deleted, delete it, then ask it to install on a similar-sized partition? 
2) Or would I not delete it, just mark to format it as ext4 or some other file system and it would then just install the OS of that live CD over the existing partition? 
3)What about the swap partition - does that need any changes at all?
4) Will Grub/Grub2 et al normally be updated to reflect the replaced OS?

Am I thinking about this in entirely the wrong way?

Many thanks in advance.

N.B. 6) I may do this on my own desktop machine in the future: I may want to consolidate all my existing partitions into one easy to manage massive partition. Is this also easy to do?
7) How can I determine which OSs are on which partitions?

---

### Post by mikewhatever on 2010-04-15
> **Lord Stig said:**
> ...
Would I boot from the distro's live CD, determine the correct partition, (I'm thinking of Gparted here) and then... what?
1) Would I have to mark the partition to be deleted, delete it, then ask it to install on a similar-sized partition? 
2) Or would I not delete it, just mark to format it as ext4 or some other file system and it would then just install the OS of that live CD over the existing partition? 

At the partitioning stage, you have to manually specify the root(system) partition, by selecting '/' as a mount point.

> 
3)What about the swap partition - does that need any changes at all?
Ubuntu autodetects swap and uses it as such, I don't know about other distros.

> 
4) Will Grub/Grub2 et al normally be updated to reflect the replaced OS?


Grub should get reinstalled.

> 
7) How can I determine which OSs are on which partitions?

Use the following commands from a terminal:

df -h

sudo fdisk -l

---

### Post by oldfred on 2010-04-15
With Ubuntu on the last partition screen just above the install button is an advanced button. The advanced button will let you select where to install or not install grub. With one drive you just want to let it install to sda, but if you have more than one you  need to check.

To help keep track of partitions I like to use the label to say what each partition is. You can set labels with gparted, disk utility or command line.

fred@fred-desktop:~$ sudo ls -l /dev/disk/by-label
total 0
lrwxrwxrwx 1 root root 10 2010-04-13 14:27 backup -> ../../sda2
lrwxrwxrwx 1 root root 10 2010-04-13 14:27 BETA -> ../../sdc7
lrwxrwxrwx 1 root root 10 2010-04-13 14:27 Data -> ../../sdc6
lrwxrwxrwx 1 root root 10 2010-04-13 14:27 grub -> ../../sdc1
lrwxrwxrwx 1 root root 10 2010-04-13 19:27 MC4GB -> ../../sdd1
lrwxrwxrwx 1 root root 10 2010-04-13 14:27 newhome -> ../../sdc9
lrwxrwxrwx 1 root root 10 2010-04-13 14:27 OLDG -> ../../sdc8
lrwxrwxrwx 1 root root 10 2010-04-13 14:27 SHARE -> ../../sda4
lrwxrwxrwx 1 root root 10 2010-04-13 14:27 Shared -> ../../sdc2
lrwxrwxrwx 1 root root 11 2010-04-13 14:27 Test -> ../../sdc11
lrwxrwxrwx 1 root root 10 2010-04-13 14:27 ubuntu32 -> ../../sdb1
lrwxrwxrwx 1 root root 10 2010-04-13 14:27 ubuntu64 -> ../../sdc5
lrwxrwxrwx 1 root root 10 2010-04-13 14:27 WinXP -> ../../sda1

---

### Post by bcschmerker on 2010-04-15
Unlike Microsoft® Windows and Apple® MacOS®, LinUX has been designed from the outset for multiple hard drives, as was its ancestor Bell Laboratories® UnIX.  I am currently planning hardware for a major Dist-Upgrade on my hybrid Everex® mid-tower (orig. a TC2502 with an all-VIA chipset, now running all-AMD hardware), with up to four SATA hard drives for a clean install of the in-beta (as of 15 April 2010) Ubuntu® 10.04 or 10.05 Lucid Lynx to supersede 8.04.4 Hardy Heron (in my specific case, 8.04.4 is split between two PATA drives with a smallish drive for /home).

As an example, assuming GRUB 2 remains stable as of Lucid's official release to market, I plan on ten total partitions across the four drives.  The Boot (/boot), Root (/; holds /bin, /sbin, /etc, /lib), Root-User (/root) and Swap partitions will go onto /dev/sda; the User-Programs (/usr) and Option-Programs (/opt) partitions, onto /dev/sdb; the Variables (/var) and Temporary-Files (/tmp) partitions, onto /dev/sdc; and the Home (/home, /vhome), onto /dev/sdd.  The Gigabyte® MA78GM-S2HP mobo that I'm running has a fifth SATA port that will be freed, as I'm switching back to a PATA DVD drive for compatibility with the Creative Laboratories® SB0350 that I retrofitted in late 2009 (it is currently occupied with a SATA optical drive, as the MA78GM-S2HP has only one PATA port).  GRUB 2 will be in /boot, along with the appropriate versions of LinUX Kernel files initrd.img and vmlinuz; Modules will be in the root partition subdirectory /lib/modules.

---

