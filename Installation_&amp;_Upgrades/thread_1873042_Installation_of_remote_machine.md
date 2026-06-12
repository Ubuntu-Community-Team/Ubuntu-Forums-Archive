---
title: "Installation of remote machine"
date: 2011-10-31
forum: Installation &amp; Upgrades
---

### Post by Skaperen on 2011-10-31
I want to install Ubuntu (likely server edition but possibly a desktop edition) on a remote machine.  The person who is physically at the remote machine is limited to booting a CD/DVD or USB memory stick, and cannot answer any interactive questions during the install.  So, obviously, I need a special image.  Is there a particular tool Ubuntu would have to construct such an image which would boot and then either install things according to a prescribed plan, or allow ssh access to let me do anything interactive in text mode?

FYI, I have done this already with Slackware.  I did it by pre-building an installation in a VM, installing also to a USB memory stick, and copying the VM install image to the memory stick (so now it has its own installed OS plus the image of the one installed in the VM).  The USB memory stick gets booted on the target machine, and enables ssh access.  I login via ssh and copy the image to the hard drive, and tweak the partition table to add a "remainder of the drive" partition.  Then I shut down and the person at the remote is instructed to remove the USB memory stick and reboot the machine.  This works.

I have tried the above with Ubuntu, but it has not worked.  There are too many things trying to second guess what I am doing and assuming the machine is broken, such as udev.  But maybe Ubuntu has another means to accomplish this.  I described the above so you could see the kind of thing I need to do and provide a specific suggestion if one is known.

---

