---
title: "Karmic - failed update to LiveUSB"
date: 2010-01-07
forum: Installation &amp; Upgrades
---

### Post by hyfforddwr on 2010-01-07
I created a LiveUSB and that worked. On about the 3rd use I attempted to update packages - about 174 came up I think (I saw that number on another post which reminded me, hence the precision). Two or three dialogues came up, unfortunately unintelligible to me, a Ubuntu novice. Both concerned grub2. The first I just forwarded on and the update trundled on. The 2nd asked me something like whether I wanted grub to update sda or sdb. I checked neither (against the pop-up help advice). The update completed but when I eventually went to reboot from the USB I got a repeating fatal message: something like "Could not load /lib/modules/2.6.31-17-generic/.dep". I had to switch off. It did reboot successfully from a LiveCD.

Any suggestions how I may (easily please) get the LiveUSB working again? Or do I just have to start from scratch again?

---

### Post by efflandt on 2010-01-07
If you use the USB Startup Disk Creator to boot live/install iso from USB with persistent data, you can add packages or activate drivers.  But it is not a good idea to update the system, because the boot kernel and certain other things are booted from the iso before the persistent data is mounted, that will not exist during initial boot.  So things like kernel upgrades will not work and there is no grub.

You can do a regular installation to USB flash or hard drive, although that takes more space, 4 GB will work, but 8 GB or more is recommended.  But at the summary screen just before the installation, pay attention to the **Advanced** button to put grub on the USB device.

---

### Post by hyfforddwr on 2010-01-08
OK, thanks. Lesson learnt.

---

