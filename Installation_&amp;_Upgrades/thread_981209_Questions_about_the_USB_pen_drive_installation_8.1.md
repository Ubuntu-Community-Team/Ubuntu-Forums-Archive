---
title: "Questions about the USB pen drive installation 8.10"
date: 2008-11-13
forum: Installation &amp; Upgrades
---

### Post by witchbutter on 2008-11-13
First, I ran the automatic Ubuntu USB stick installer from the 8.10 CD and it works and boots into essentially an installer CD from the USB stick rather than a physical CD.  There was no issue with doing that.

This is great for someone trying to get an Ubuntu installed on a machine with no CD drive, but what I was looking for when searching and reading about the installer is something that creates a LiveCD for Ubuntu on which I can put various tools for diagnosis of problems and data recovery.  I've never tried to do this before, and it seems there are plenty of how-tos on the web to get an installer iso to become bootable, but not much on what to do after that. If someone could point me to other resources or give some advice that would be helpful:

1) It is really cheap now to get a USB drive with greater than 8GB of space on it, so why would you use this script installer rather than simply doing an ubuntu install onto the pen drive, and then modify applications?  Is the Live CD any more compatible than having a kernel with all possible modules built on a full install?

2)Why does everyone think it's great to have the usb stick formatted FAT16?  I would need to try and get into Intel based Macs whose resource forks will be lost if you copy a file from that computer to the stick in that case.

3) On the Ubuntu Live CD, what part of the stick will be "persistent" after a reboot?  Only /home?

---

### Post by psusi on 2008-11-13
I think the advantage of it working like the livecd is that it does automatic hardware detection every time you boot up so X won't crash trying to load the wrong driver when you plug it into a different machine.

The reason they come formatted as fat (  my 4 gb one is fat32 ) is because most people use Windows and that's what it uses.  If you want to there is no reason you can't format it with a different filesystem.

Finally everything becomes persistent provided you chose the option to reserve space to hold changes when you set up the stick with the installer.

---

### Post by C.S.Cameron on 2008-11-13
The advantages with a full install is that you can upgrade the kernel and use switchconf to select from various xorg.conf files when booting multiple machines, (duel monitors, wide screen TV's, etc) and boots are often faster once the flash drive gets loaded with lots of programs and drivers.
The advantage with a persistent install is ease of initial setup and it is more compact.
I set up my persistent install as follows and it does almost everything a full install does:

Booted Live CD.
Plugged in flash drive.
Started Partition Editor
Created 1 GB FAT32 partition, (on the left side of the bar).
Created a 1.5 GB ext3 partition to the right of this, labeled it "casper-rw".
Created a partition in the remaining space and labeled it "home-rw", (these can also formatted in reiserfs for a little extra speed).
Closed Partition Editor.
Un-mounted and re-mounted flash drive.
Started "Create a live usb startup disk", (usb-creator).
Selected minimum Stored in reserved extra space, you can leave more if you want to add a folder that windows can see.
Pressed "Make Startup Disk.
When usb-creator finished, ran "gksu nautilus"
Selected disk and deleted casper-rw file.
Shutdown, removed CD.
Rebooted, changes were persistent.

---

