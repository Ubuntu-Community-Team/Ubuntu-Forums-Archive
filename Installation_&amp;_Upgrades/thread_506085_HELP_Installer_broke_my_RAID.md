---
title: "HELP: Installer broke my RAID"
date: 2007-07-21
forum: Installation &amp; Upgrades
---

### Post by ibender on 2007-07-21
I have a Gigabyte GA-965p-DS3 motherboard, and I had 2 SATA drives configured in a RAID 0  via its built in RAID controller. I also have a 250 GB IDE drive, onto which I intended to install Ubuntu. I went through the install procedure, being very careful that the install would only touch the 250 GB drive (which was recognized as scsi3). No screen in the installation said anything about the other drives.

I got to the end of the install procedure, and then a message said somethig abount installing a bootloader, and the access light for one of the RAID drives came on (they all have separate access lights). When I went to reboot, the BIOS screen said the RAID was incomplete. It looks like the Ubuntu installer wrote something onto one of the RAID drives that screwed it up.

Can anyone help me recover the RAID? The entire drive probably hasn't been wiped. It's probably just a boot sector that needs fixing or something.

UPDATE:
I found this thread:
[http://ubuntuforums.org/showthread.php?t=432346](http://ubuntuforums.org/showthread.php?t=432346).

This is the exact thing that happened to me. The sole purpose of this post is now to express how pissed off I am, since I now have a solution. I will now VERY CAREFULLY attempt to implement the solution.

Whoever is responsible for this bug is a really shoddy programmer.

In the future, when installing ANY OS, I will physically disconnect the power to the drives I don't want to be affected.

Lesson learned the excruciatingly hard way.

---

