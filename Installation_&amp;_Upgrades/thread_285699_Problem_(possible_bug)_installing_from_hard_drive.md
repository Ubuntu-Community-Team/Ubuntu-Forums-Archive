---
title: "Problem (possible bug?) installing from hard drive"
date: 2006-10-27
forum: Installation &amp; Upgrades
---

### Post by Ironfrost on 2006-10-27
Hi,

I'm having trouble installing Edgy on a laptop without a CD drive. To give you an idea of where I'm up to, I've managed to load the installer (by using Grub to load the files from [http://archive.ubuntu.com/ubuntu/dists/edgy/main/installer-i386/current/images/hd-media/](http://archive.ubuntu.com/ubuntu/dists/edgy/main/installer-i386/current/images/hd-media/) from the hard drive), but I can't seem to get it to find the rest of the data. I have copied both the ISO file and the contents of the Alternate Install CD to a new partition on the hard drive.

The installer gives me an error at the "Scan hard drives for an installer ISO image" stage. I know it's mounting the drive properly and looking through it, because I can see it flicking through the directories, but it is somehow missing the ISO file for some reason.

I guess that the component in question, which a google search tells me is iso-scan, is looking for a specific filename or location or something - but I don't know what. Can anyone help me with this?



It may be relevant that I can't seem to mount ISO files manually either. When I try to mount the ISO within the installer's shell, I get the error message:

 mount: Couldn't setup loop device

So it may be possible that iso-scan is finding the image but failing to mount it (?). Anyway, if people could help to tell me if I'm doing anything wrong, or if the problem is due to a bug I should report, that would be highly appreciated.

---

### Post by bzimage on 2006-10-27
yes, I met the same problem, we need help.

---

