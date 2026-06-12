---
title: "where does the bootloader go on old hardware?"
date: 2016-02-17
forum: Installation &amp; Upgrades
---

### Post by sukelis on 2016-02-17
Simple version:

I'm doing a Something Else installation on an i386/Bios/MBR system.  The root, swap and /home partitions are all sorted.  But where does the bootloader go?  This is what's available:

  /dev/sda
  /dev/sda1 Windows Recovery Environment (loader) (NTFS)  (which XP sees as PQSERVICE)
  /dev/sda2 WinXP (NTFS)
  /dev/sda6 / root (ext4)

The rest are data partitions and I don't think eligible.

More details:

This is an Acer Aspire One AO-D150, running WinXP.  I'm setting up dual-boot (obviously) and trying to install lubuntu, since it's the most lightweight. I'm using the lubuntu-14.04.3-desktop-i386.iso on a USB, which boots fine.  I used a combination of Acronis Disk Director and Gparted to change the partitions.  I learned my install/dual-boot procedure following a guide for installing on an AMD/UEFI/GPT, which has an obvious boot partition.  I thought I could just adapt it to this older netbook, but when I got to the "where to put the bootloader" option, I realized that the answer wasn't as obvious on this system.  So I stopped the install. I did [quite] a bit of searching/reading before and after stopping.  But there isn't a really clear answer, and there are LOTS of disaster stories.

I think the sda1 that says loader, is the recovery loader not the boot loader (I know it's the recovery partition).  Therefore, the bootloader should go in... where?  I think /dev/sda - but I would love some confirmation before I shoot myself in the foot (or higher).

---

### Post by Bucky Ball on 2016-02-17
/dev/sda

---

### Post by sukelis on 2016-02-17
Thank you!  That's what I thought, but with a very low confidence level.  Worked a treat.  Grub came up with lubuntu as default, has both XP and the recovery loader in the menu.  Looks good!  Thank you again!

---

### Post by Bucky Ball on 2016-02-17
No problem at all and glad you got it going. If, say, you installed another Ubuntu on another partition, you would install that bootloader to its own partition (say sda5 for instance) then boot to the original install and:

```
sudo update-grub
```

That would pick up the new install on sda5 and add it to the boot list. Or, if you wanted the new install to 'take over' grub duties, naturally, you would install to sda, as here, boot the new install and 'sudo update-grub', if that is even necessary (and it probably wouldn't be in this second scenario).

Make sense?  

Good luck and enjoy. We live and learn and that's what it's all about round here (mostly!). :D

(PS: Have you check XP is booting ok? Don't boot the recovery, but the XP, obviously enough. ;))

---

