---
title: "boot liveCD iso on Hard Drive, content on 2nd partition"
date: 2012-09-04
forum: Installation &amp; Upgrades
---

### Post by davea0511 on 2012-09-04
Linux n00b here.

I'd like to run Ubuntu in the same way I used to use knoppix ... essentially I created a liveCD with all my defaults, then put the iso on my hard drive and booted from it in a way that the liveCD ran 100% in memory.  It took a while to boot, but it was fast and the most robust system in the world because I never touched the original OS other than to pull it out an into memory.

I also kept my content on another partition of the drive... it was writable.  The ISO partition was not writable.

It was great as an unattended kiosk ... ultra-reliable... never bogged down (everything was in memory ... booted original image every time) ... super secure.  I used it for a kiosk.

I'm sure there's a guide somewhere how to do that with ubuntu but I've searched and searched but I guess I just don't have the right terminology to find it.  Any ideas?

---

### Post by davea0511 on 2012-09-04
I found this ... will give it a shot:
[http://askubuntu.com/questions/121212/using-a-bootable-live-cd-disk-image-mounted-on-the-hard-drive]("http://askubuntu.com/questions/121212/using-a-bootable-live-cd-disk-image-mounted-on-the-hard-drive")

Any other recommendations will be very much appreciated.

---

### Post by oldfred on 2012-09-04
This is the same as your link to askUbuntu. Has a bit more info. I have only been able to boot Desktop, not any of the other versions.

This will boot an ISO from a hard drive.
ISO Booting with Grub 2 from Hard drive - drs305
[https://help.ubuntu.com/community/Grub2/ISOBoot](https://help.ubuntu.com/community/Grub2/ISOBoot)
Examples - you may copy & edit for your path & ISO version
[https://help.ubuntu.com/community/Grub2/ISOBoot/Examples](https://help.ubuntu.com/community/Grub2/ISOBoot/Examples)
[http://ubuntuforums.org/showthread.php?t=1549847](http://ubuntuforums.org/showthread.php?t=1549847)
Boot ISO from harddrive. To install it would have to be different partition
[SOLVED] Using grub 2 to boot an iso off hard drive old examples
[http://ubuntuforums.org/showthread.php?t=1535864](http://ubuntuforums.org/showthread.php?t=1535864)

Pros & cons of persistent install over direct install to flashdrives - C.S.Cameron
[http://ubuntuforums.org/showthread.php?t=1655412](http://ubuntuforums.org/showthread.php?t=1655412)

USB installs with persistence:
With grub2 persistent C.S.Cameron 12.04
[http://ubuntuforums.org/showthread.php?t=2042965](http://ubuntuforums.org/showthread.php?t=2042965)
With grub2 persistent C.S.Cameron post#5 10.10:
[http://ubuntuforums.org/showthread.php?t=1643791](http://ubuntuforums.org/showthread.php?t=1643791)

---

### Post by davea0511 on 2012-09-05
Thanks oldFred!  That will definitely help!

---

