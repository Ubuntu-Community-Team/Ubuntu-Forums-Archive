---
title: "Ubuntu 9.10 doesn't see my SATA drive"
date: 2010-02-20
forum: Installation &amp; Upgrades
---

### Post by bigyellow9999 on 2010-02-20
Hey guys. I have an Intel Desktop Board D975XBX2 motherboard with a Quad Core processor, 2 GB of RAM and a 500 GB Western Digital Sata drive. I don't know why, but this motherboard seems to be such that Ubuntu can't find the SATA drive.

I'll try not to give you the whole history, but I had a Gigabyte Motherboard and the exact same hardware and Ubuntu could recognize the board no problem. In fact, I installed Ubuntu on it that way. I've since got rid of that board and am using the Intel board. The bios sees the drive. What's even weirder, I can boot up from the drive (which I installed using the Gigabyte board). However, I have problems booting up. It says:

ALERT! /dev/disk/by-uuid/cb822b9c-a405-41f9-a384-5a92df6552b7 does not exist.

From what I've read, I should be able to go into /etc/fstab and modify the boot line to find the drive, but fstab doesn't even exist. So I want to just reinstall everything because, again, I just put Ubuntu on it using the Gigabyte Motherboard.

I tried setting the drive as IDE, SATA and AHCI. I've tried passing pci=nomsi as a boot option. Clearly, there's something about this motherboard that different that Linux is not able to pick up the Hard drive.

Since I can boot from the hard drive, it would seem to reason to me that the correct boot parameters are being passed during boot. Where are these boot parameters located and can I take them and pass them to the kernel line when attempting an install? Any help you guys can give would be greatly appreciated. Thanks in advance.

---

### Post by ChrisThompson on 2010-03-03
I'm having a complimentary problem.

Karmic ran (almost) fine on my desktop until my PATA drive died.  I say almost because it never detected my two SATA drives that house my Windows OS and filesystem, and I never bothered to make it.  (It was a mutual understanding.)

Now the PATA drive is dead and I have no choice.  Other install disks don't help, removing DMRAID doesn't help, booting as 'nolapic' does nothing, and GParted and Disk Utility have no idea the drives are even there.

Mobo=ASUS A8V-XE, SATA Controller (in BIOS) is IDE (changing SATA controllers=no change)

Any suggestions?

---

### Post by ChrisThompson on 2010-03-06
Have you tried adding "pci=nomsi" to the boot options?  I did and it finally detected them.

[Here's a link]("http://ubuntuforums.org/showthread.php?t=1421942") to my original thread where I give details on what I did.

Hope this helps!

--Chris

---

