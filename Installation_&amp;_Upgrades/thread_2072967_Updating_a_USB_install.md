---
title: "Updating a USB install"
date: 2012-10-18
forum: Installation &amp; Upgrades
---

### Post by eishethel on 2012-10-18
Is it possible to perform updates on a live USB version of ubuntu with or without having the persistant data store?

---

### Post by Cheesemill on 2012-10-18
Without persistence it's not possible.

With persistence you can update everything except the kernel.

---

### Post by C.S.Cameron on 2012-10-18
If you use Update Manager you will quickly fill your casper-rw file as it is maximum 4GB.
Once casper-rw is full, the drive will not boot.
You can make casper-rw and home-rw ext2, 3 or 4 partitions of any size, then if you don't mind using lots of space on the drive, updating is practical.
Using Computer-Janitor may help preserve casper-rw space.

---

### Post by efflandt on 2012-10-18
Basically for the bootable iso on USB you cannot update anything that happens during initial boot, not only the kernel, but you cannot install other video drivers, etc. or other things loaded from the fixed squashfs file system that runs before persistent data is mounted.  You can only install or update programs and things that happen after initial boot.

If you want to be able to update everything, do a regular install.  But 8 GB minimum is recommended for that.  For flash memory (other than SSD drives with TRIM) it may be best to use ext2 instead of a journal file system to minimize write cycles.  I have an old Celeron 300 Linux file and web server that still uses ext2 without any problems.  And I use ext2 to boot Ubuntu or Lubuntu from SDHC on my tablet PC.

---

### Post by kurt18947 on 2012-10-19
My experience parallels efflandt.  Updates eventually 'kill' a live USB install.  Formatting a USB drive to ext2  then doing a 'regular' install works okay.  The biggest downside is that booting off a USB drive seems pretty slow.  I wonder if the USB3 flash drives would be faster?  Flash drive capacities are getting large enough to provide space for the OS/apps and data.

If you're concerned about installing to the wrong drive, you can unplug the hard drive and boot from a live CD/DVD/USB and install to the ext2 formatted USB drive.  Can't mess up a drive that isn't plugged in.

---

