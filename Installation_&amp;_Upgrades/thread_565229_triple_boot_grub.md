---
title: "triple boot grub"
date: 2007-10-02
forum: Installation &amp; Upgrades
---

### Post by mwacky on 2007-10-02
I have a dual boot Ubuntu i386 Feisty/XP setup.  Want to install Gusty Beta AMD64 on the same PC, the partitions are set to handle the new install.  I know that the Grub will be set in the AMD64 install and easily detect the other OS's, but I want Feisty 32 bit to handle the grub for now.

Thanks in Advance.

---

### Post by rsambuca on 2007-10-02
When you install the 64 bit version, just have grub install itself to the new partition, not to the mbr.  This way, the Feisty grub will still be in control.  Then just add a chainloading entry to your Feisty menu.lst

title     Gutsy 64bit Beta
root     (hd0,2)
chainloader +1

You will have to change the (hd0,2) to correspond to your particular setup.

The benefit of this is that if Gutsy updates it's kernel and grub, you don't have to manually change anything, it should all be automatic.  The only downside is you hop from Feisty grub to Gutsy grub, but it isn't that big of a deal.

---

### Post by mwacky on 2007-10-03
Thanks for the tip, worked well.

The only problem now is the AMD64 version of Gusty kicks so much a**, I will probably want to wipe my install of Feisty and use the space to expand my Gusty partition.  Any advice on that?  Will gparted deal with that okay:

Current:
ext3 Gusty 4 GB
ext3 Feisty 15 GB

Then 2 gparted operations:
1. Wipe Feisty partition
2. Expand Gusty Partition with space from Feisty.

---

### Post by rsambuca on 2007-10-03
That should work.

---

