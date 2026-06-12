---
title: "Persistent installation on USB or External drive fails"
date: 2012-09-06
forum: Installation &amp; Upgrades
---

### Post by ultrabunter on 2012-09-06
Hi,
the persisent installation - where changes are written to the external device - of Ubuntu and other Linux distributions does not work for me. I tried serveral devices and sticks but during the boot process all systems get stuck. I used Universal-USB-Installer-1.9.0.9 and Linux Live USB Creator.

Any idea what might be wrong?

Thank you in advance

---

### Post by sudodus on 2012-09-06
Can you boot from a normal live USB drive (without persistence)?

If that is the case, I suggest that you describe how you did it (which version and flavour of Ubuntu!

And if Universal-USB-Installer won't work, try Unetbootin! It is in the repos:

```
sudo apt-get install unetbootin
```

See also this link which is now getting old. The present version of Unetbootin (in 12.04 LTS) can create the persistence directly 'Space used to preserve files across reboots (Ubuntu only)'
[[COLOR="Red"]_http://ubuntuforums.org/showthread.php?t=1885392_[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1885392")

---

### Post by ultrabunter on 2012-09-06
I tried various ubuntu versions and other linux distros. The live start with Unet Bootin works, only persistent installation fails. Maybe I have to change some other bios settings?

---

### Post by sudodus on 2012-09-06
> **ultrabunter said:**
> I tried various ubuntu versions and other linux distros. The live start with Unet Bootin works, only persistent installation fails. Maybe I have to change some other bios settings?
No I don't think there is a problem with the bios.

Try the manual method described in the link in my previous post! That shows what to do with the various files in order to make the unetbootin boot system recognize the casper-rw file or partition. (You can also have a casper-rw partition.)

---

### Post by ultrabunter on 2012-09-06
I'm sorry, I'm new to linux and I run winxp at the moment, so I can't do the manual install from linux to perform the necessary changes. Is there a tool which can do this automatically? I also have an external drive, maybe I could install it in there?

---

### Post by sudodus on 2012-09-06
> **ultrabunter said:**
> I'm sorry, I'm new to linux and I run winxp at the moment, so I can't do the manual install from linux to perform the necessary changes. Is there a tool which can do this automatically? I also have an external drive, maybe I could install it in there?

What I was thinking of was to do that work from a live session with Ubuntu or any of its flavours, Kubuntu, Lubuntu, Xubuntu.

The automatic tool is Unetbootin itself, and there are versions for Windows as well as for Ubuntu. I did the work described with old Ubuntu 10.04 'lucid' and the version of Unetbootin that comes with it.

And yes, you can install it to any USB drive, hard disk, flash pen-drive, flash card. It is no use to have persistence if you have less than 2 GB, I would recommend at least 4 GB.

A good alternative with a bigger drive, say 8 GB or more is to make a 'regular' installation of Ubuntu, but to the external (USB) drive instead of the internal drive. If you don't install any proprietary drivers (typically for graphics and wifi), it will be portable like a persistent live system.

In that case, it will be simpler if you disconnect the internal drive during the installation.

---

### Post by sudodus on 2012-09-06
I tested Unetbootin in Ubuntu 12.04 right now. I used the iso-file for Lubuntu 12.04 64-bit live. I demanded more space for persistence than available, to be sure that all space was used. This works up to 4 GB, which is the maximum file size in a FAT 32 file system.

It works :-)

Tips:

1. You must wait a while to let the system finish writing to the USB drive. If there is a LED, it is easy to see. Otherwise you can run the command ```
sync
``` in linux, and when it returns to prompt, the writing has finished. Or just wait for a minute or two.

It is important to wait when you make the drive, but also every time that you finish a persistent live session (at reboot as well as poweroff).

2. You must remember to increase the size of the 'space used to preserve files across reboots'. If it is zero, there will be no persistence.

---

### Post by C.S.Cameron on 2012-09-06
Following is a method of using persistent partitions:

Boot Live CD.
Plug in flash drive.
Start Partition Editor
Create 1 GB FAT32 partition, (on the left side of the bar). (size is optional)
Create a 1.5 GB ext3 partition to the right of this, labeled it "casper-rw". (ext2 and ext4 also work).
Create a partition in the remaining space and label it "home-rw". (optional, creates a separate home partition)
Close Partition Editor.
Un-mount and re-mount flash drive.
Start "Create a live usb startup disk", (usb-creator).
Select "Discard on shutdown".
Press "Make Startup Disk.
When usb-creator finishes, run "gksu nautilus"
Select disk / syslinux / text.cfg and add "persistent" as shown below:
append  noprompt cdrom-detect/try-usb=true persistent file=/cdrom/preseed/ubuntu.seed boot=casper initrd=/casper/initrd.gz quiet splash --
Shutdown, remove CD, reboot.
You are persistent.

---

### Post by ultrabunter on 2012-09-06
Thank you! The last option worked fine for me:popcorn:

---

