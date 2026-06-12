---
title: "[SOLVED] Dual boot woes"
date: 2008-07-05
forum: Installation &amp; Upgrades
---

### Post by joemilx on 2008-07-05
I installed 8.04LT from the Live CD onto an existing Windows boot drive.  The install repartitioned the single 160GB drive into SDA1(102GB NTFS), SDA2 (45GB EXT3) and SDA3(2GB SWAP).

Everything looked OK with Ubuntu until I tried to reboot.  The system just sat with a blinking cursor on a black screen following the BIOS post.  After much experimentation, I found only one way to boot into Ubuntu or Windows.

I had to boot from the Live CD, then select "Boot from first drive".  There was approx. a 2 minute lag between the BIOS post and the Live CD menu being displayed.

Next, I selected "Boot from local disk".

After 45 seconds. the dual boot menu displayed and I could select either Ubuntu or Windows XP and proceed.

I have to specify pci=nomsi on the kernel line to get into Ubuntu.

Not sure what to do next.  Please advise.

ASUS A8V-VM mobo, Athlon 64 4000+, 4x512 DDR333 SDRAM, WDC 160GB SATA, Ubuntu 32 bit.

---

### Post by Herman on 2008-07-05
Either your BIOS isn't set to boot from your first hard disk or the bootstrap code area of the MBR in your first hard disk is empty or corrupted.
I would first check the BIOS and if there's no problem in there, try re-installing GRUB to MBR again.
You should be able to re-install GRUB to MBR with the Ubuntu Live CD.
[How to install Grub from a live Ubuntu cd.]("http://ubuntuforums.org/showthread.php?t=224351&highlight=re-install+grub").

---

### Post by joemilx on 2008-07-06
> **Herman said:**
> Either your BIOS isn't set to boot from your first hard disk or the bootstrap code area of the MBR in your first hard disk is empty or corrupted.
I would first check the BIOS and if there's no problem in there, try re-installing GRUB to MBR again.
You should be able to re-install GRUB to MBR with the Ubuntu Live CD.
[How to install Grub from a live Ubuntu cd.]("http://ubuntuforums.org/showthread.php?t=224351&highlight=re-install+grub").

Did what you suggested and no change.  However, your point about the bios got me thinking.  I removed a lot of hardware including an SIL680 RAID controller from the PC and Voila! I'm back in business.  Seems the RAID controller was confounding the boot process.  Thanks for the help.

---

