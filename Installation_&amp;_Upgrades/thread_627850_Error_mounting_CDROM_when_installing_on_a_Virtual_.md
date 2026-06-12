---
title: "Error mounting CDROM when installing on a Virtual Server 2007 virtual machine"
date: 2007-11-30
forum: Installation &amp; Upgrades
---

### Post by cmenning on 2007-11-30
I am trying to install Ubuntu Server 7.10 on a MS Virtual Server 2007 virtual machine.  Unfortunately, after choosing the keyboard layout, I get an error message that reads:

Your installation CD-ROM couldn't be mounted.  This probably means that the CD-ROM was not in the drive.  If so you can insert it and try again.  Try again to mount the CD-ROM?

Saying yes hangs the installer for about 5 minutes, then the error message appears again.  I've used the option to check the image for errors, and it does the same thing.

Checking the dmesg output, the CD-ROM is properly being seen and is assigned /dev/scd0.  Manually trying to mount the CD using 'mount /dev/scd0 /cdrom' gives the message 'mount: /dev/scd0 is write-protected, mounting read-only' and then it just sits there for a long time and appears to hang that console.  I'm not able to kill the mount process from another console.

Has anyone else seen this strange behavior?  It's booting off the CD, but then can't mount it for the installation...  Any ideas?

Thanks ahead of time for any help that can be provided!!!

Craig

---

### Post by aktxyz on 2007-12-01
Sorry, no answer here, but I have the exact same problem.  I tried with a physical CD as well (not just the ISO image), still fails.  I am really stuck here.  Works fine in Virtual PC 2007, just not Virtual Server 2005 R2 S1.

---

### Post by jowie on 2008-01-13
> **aktxyz said:**
> Sorry, no answer here, but I have the exact same problem.  I tried with a physical CD as well (not just the ISO image), still fails.  I am really stuck here.  Works fine in Virtual PC 2007, just not Virtual Server 2005 R2 S1.

Same here. No clue how to fix it. I want to try out Ubuntu Server in a VM session on my Windows server before commiting my hardware over to Ubuntu non-virtually.

---

### Post by peteNorris on 2008-01-30
First post here, and never used Linux before... however I'm not sure your problems have anything to do with it...
Are you installing remotely? eg... If I connect to a remote machine (eg. VM1) and installing Ubuntu onto a Virtual Server living on VM1 then I too get this error. 
I sucessfully installed being local on the VM1 (ie... attach the keyboard, Screen and mouse).

Hope this helps (if you havent already solved it).

Pete.

---

