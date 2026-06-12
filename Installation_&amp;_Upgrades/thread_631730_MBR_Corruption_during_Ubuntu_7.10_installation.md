---
title: "MBR Corruption during Ubuntu 7.10 installation"
date: 2007-12-04
forum: Installation &amp; Upgrades
---

### Post by travisj on 2007-12-04
Hi,

I was hoping someone could help explain what happened.  This isn't a big deal because I have full backups, and should even be able to fix the MBR without restoring.  But I'm not sure where I went wrong or if something deeper is wrong.  I thought I told it not to modify the hard disk MBR

I had Windows XP SP2 installed on a 250GB HD and only 20GB used.  Scandisk'd and defragged multiple times, and then booted to run GParted. I shrunk the first partition so that 20GB was available at the end of the drive.

Then, I began installing ubuntu.  In the partitioning page of installation, I chose to use the guided "largest contiguous free space" option.  At the end, I chose to install the MBR to a pre-prepared USB drive, rather than the hard disk!

After the install, I rebooted without the USB drive to see if everything was still OK with the windows installation. I get a Cannot Load Operating System message.  When I check via the Ubuntu Live CD, my original windows partition is still there with all of its data.

So how did the MBR become corrupted?

---

### Post by gazj on 2007-12-04
well i'm not sure i haven't had much expirience with booting with usb sticks etc

but to restore the orignal windows mbr on your hard disc, insert you xp cd and select recovery console (it somewhere in the first few installation screens)

then run the following 2 commands

fixmbr

fixboot

this will definitely (he sais) get windows booting again, although i'm not sure you will be able to boot ubuntu when you reinsert you usb stick.

In future i would just put ubuntu's mbr (grub boot loader) on your hard disc, you can always restore the window mbr later with the above commands if you ever remove ubuntu

---

### Post by Pumalite on 2007-12-04
To install to USB, disconnect your internal drive. That way you can be sure that Grub will not install itself in them and only in the USB drive.
[http://ubuntuforums.org/showthread.php?t=598961&highlight=boot+from+external+drive](http://ubuntuforums.org/showthread.php?t=598961&highlight=boot+from+external+drive)
[http://ubuntuforums.org/showthread.php?t=598787&highlight=boot+from+external+drive](http://ubuntuforums.org/showthread.php?t=598787&highlight=boot+from+external+drive)
[http://ubuntuforums.org/showthread.php?t=598961](http://ubuntuforums.org/showthread.php?t=598961)
[http://www.ubuntuswitch.com/2006/08/01/installing-ubuntu-on-an-external-usb-hard-drive/](http://www.ubuntuswitch.com/2006/08/01/installing-ubuntu-on-an-external-usb-hard-drive/)
[http://ubuntuforums.org/showthread.php?t=614913](http://ubuntuforums.org/showthread.php?t=614913)
[http://ubuntuforums.org/showthread.php?t=614863](http://ubuntuforums.org/showthread.php?t=614863)

---

