---
title: "Installing from ash prompt?"
date: 2011-03-03
forum: Installation &amp; Upgrades
---

### Post by Ouroborus on 2011-03-03
I don't have a CD burner.  Please, don't tell me to burn a CD and do it that way.
That out of the way, the situation: I've got an old Gateway box, a pair of hard drives in it.  One is solely user data, the other was a  dual-boot system, Ubuntu and Windows XP.  Somehow, the Ubuntu side got messed up, and I can't figure how to fix it.  So, I figured I'd just reinstall it.  Picked up a 10.10 iso, downloaded a ramdisk image and a kernel, loaded them onto the linux partition, set up grub to boot to them.  Boots to the image fine, loads up, says it's searching hardware, and there's inevitably an error.  It either says it failed/errored searching hard disks  for the image, or that it can't load files from the cd-rom: "There was a problem reading data from the CD-ROM.. Failed to copy file from the CD-ROM".  I can, however, go into the shell and mount the install iso by hand, and it mounts fine.  MD5 matches, so it's not a corrupt file.  I've tried putting the image on both the ext3 and the fat32 partition as listed  below, neither makes the utility install correctly.  Is there something I can do, from the basic ash shell, to start the installer if I hand-mount the cd?  Or is there something else you can see I'm doing wrong with the set up for the whole thing?

Master drive partitions:
Windows XP partition, ntfs
Linux partition, ext3
swap partion
c partiton, fat3

---

