---
title: "Installation hangs :("
date: 2006-07-04
forum: Installation &amp; Upgrades
---

### Post by Regenerate on 2006-07-04
Hi, I'm a new Ubuntu user and I'm trying to install Ubuntu (dvd) or Kubuntu (cd). Both don't work however, both with the same problem:
When booting from the cd/dvd I tried the options to install (K)Ubuntu in OEM or textmode. Both result in a hang on an empty blue screen, after the point that the network is configured and the hardware is detected. 

I also tried starting Live Ubuntu from the disks but after starting, and the message "Decompressing Linux...done. Booting the kernel" the install hangs (I can still type text on the screen, but nothing happens).

I search through the documentation but cannot find a solution. Anybody with suggestions? See my signature for system specs. TIA!

---

### Post by Regenerate on 2006-07-04
Problem found, it's the sata2 driver that's missing in the 2.6.15 linux kernel (see [http://www.ubuntuforums.org/showthread.php?t=153384)](http://www.ubuntuforums.org/showthread.php?t=153384)). Can anyone tell me what version of the kernel edgy will have? And is there a way I can install a 2.6.16 linux kernel with dapper over it? TIA!

---

### Post by jsimmons on 2006-07-05
[QUOTE=Regenerate]Problem found, it's the sata2 driver that's missing in the 2.6.15 linux kernel (see [http://www.ubuntuforums.org/showthread.php?t=153384)](http://www.ubuntuforums.org/showthread.php?t=153384)). Can anyone tell me what version of the kernel edgy will have? And is there a way I can install a 2.6.16 linux kernel with dapper over it? TIA![/QUOTE]

Actually, the problem is that the SATA driver your motherboard needs isn't in the kernel.  You have several options:

0) Wait for Canonical to update the ISO with a patched kernel.  Of course, there are no guarantees they will do this, or if they do, when they'll get around to it.  I certainly wouldn't wait for Eft to be released.

1) Buy a new motherboard that has a SATA controller already supported by the 2.6.15 kernel.  If you're dual-booting Windows/Linux, this can be a pain because you'll have to reinstall Windows first, but at least you'll be good to go for Linux.  If you're using an amd64 CPU, the nForce boards appear to be fine.

2) Buy an add-on SATA card that is supported by the 2.6.15 kernel, connect your drives to that and disable the onboard SATA controller(s).

3) Remove/disconnect your SATA drives, install Ubuntu onto an IDE drive, patch the kernel (or update it through synaptic/aptituded/apt), and reconnect your SATA drives.

I am in the same boat you are.  I have a Asrock 939Dual-SATA2, and the SATA controller on that motherboard isn't supported by the 2.6.15 kernel.  I'm not dual booting, and my boot drive is an IDE drive, so I'm choosing optuion #3.  After four days of trying to install Drake, I finally disconnected my SATA drives and got it installed and booting.  This weekend, I'll disconnect my SATA drives again, boot into drake, update the kernel, and recompile it for i686.  Hopefully, that will go okay and I'll be able to reconnect my SATA drives again.

---

