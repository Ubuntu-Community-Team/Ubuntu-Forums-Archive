---
title: "Grub2 problems?"
date: 2009-11-14
forum: Installation &amp; Upgrades
---

### Post by Gitanes on 2009-11-14
I been playing around with a Windows XP/9.10 (alt. CD) dual boot in Virtualbox.  I install Windows (one partition), create 3 partitions for 9.10: /boot ext4 (boot flag on), encrypted swap, encrypted / ext4, all primary partitions.  The install, seemingly, goes fine.  At the "where to put Grub prompt", I select (hd0,1) since I intended to encrypt Windows with Truecrypt later and Grub needs to be installed in the /boot partition (hd0,1) because the TC bootloader will overwrite it in the MBR.  So Grub seemingly gets written to where I tell it but on restarting nothing loads.

So, I put in Supergrub CD and I can get to a Grub menu by selecting Windows and Ubuntu will load but Windows will not load from this Grub menu.  I attempt to repair the MBR of Windows with Supergrub but this does no good and ultimately I have to do a repair re-install of Windows to get it running.

I was able to install Grub to (hd0,1), after booting into Ubuntu, but it bitches and moans about being installed anywhere but the MBR.  I've got a similar (not 9.10 though) dual boot setup on my laptop and don't remember having any trouble installing Grub to a /boot partition.

Whatever is happening here in setup seems to be hosing the Windows partition enough that trying to fix the MBR with Supergrub won't recover the partition.

Nice to have Virtualbox so you can play with this stuff w/o doing real damage.

---

