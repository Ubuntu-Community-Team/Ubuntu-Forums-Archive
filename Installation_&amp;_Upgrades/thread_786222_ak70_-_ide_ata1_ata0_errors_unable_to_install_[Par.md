---
title: "ak70 - ide ata1 ata0 errors unable to install [Partially Solved]"
date: 2008-05-07
forum: Installation &amp; Upgrades
---

### Post by tagra123 on 2008-05-07
This is mainly for my own reference but thought it might help others.

A friend gave me and old slot a computer to fix up with Ubuntu.


The computer has a dfi ak70 motherboard.

I was unable to install ubuntu using the minimal, alternate or live cd. A lot of ide errors and ata1 ata0 several messages -- basically unable to mount the Cdrom -- no device or module that worked.

So I put the hard drive into a bench computer I have to use whenever something won't work.

I installed Ubuntu onto the hard drive using this bench computer. Put the hard drive back into the old computer and booted. 

Problem same as CD unable to mount the hard drive or CDROM still IDE ata0 ata1 message all resulting in an inablilty to mount the drive. Big problems when you cannot mount the root filesystem. No mount = No usable computer.

Took the disk back out rebooted on the bench computer and applied the hack for bug #104581 -- The messages I was receiving were not the same but why not try.

[https://bugs.launchpad.net/ubuntu/+bug/104581/comments/25](https://bugs.launchpad.net/ubuntu/+bug/104581/comments/25)

Once booted

Edited /etc/initramfs-tools/modules, and added these lines:

piix
ide_generic
ide_cd
ide_disk

# blacklist bad driver
blacklist ata_piix

Save and then


sudo update-initramfs -u

Took the disk back out and put in the old machine.

Booted logged in and running. How about that.

Hope this helps someone.


A questions for gurus: Is there any way to do what was done directly on the live CD to get it to boot?

---

