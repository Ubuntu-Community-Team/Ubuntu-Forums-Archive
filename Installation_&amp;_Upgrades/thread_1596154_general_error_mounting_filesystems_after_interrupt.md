---
title: "general error mounting filesystems after interrupted upgrade from 10.04 to 10.10"
date: 2010-10-13
forum: Installation &amp; Upgrades
---

### Post by gaberlunzie on 2010-10-13
Originally posted in Launchpad yesterday [Question #129083]:
> System froze in mid-upgrade from 10.04 to 10.10  and now fails to boot, giving a 'general error mounting filesystems'  message when loading [in either normal or recovery mode.] However, the boot menu remains accessible with the  F8 key and is functional.

 While in the 10.10 Live CD, using the chroot method in the [grub2 help]("https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202") proved unsuccessful and returned this [pastebinned result]("http://pastebin.com/S5PBEpG9").

The system is 10.04 64-bit running an nvidia card and sporadically  froze with increasing frequency. No resolution to the freezing could be  found online, which seemed associated with any of nvidia, usb, flash or  even firefox.

 Can someone suggest an alternative to restore to bootable condition  and resume upgrade without having to reinstall and wipe the drive?I also followed the copy alternative to the chroot method in the grub2 help and still get the same core dump for chroot and device not found error for upgrade-grub as posted in pastebin. I'm still running off of the 64-bit 10.10 Live CD.

Skimming other "general error mounting filesystems" topics in this section, I realise I may have to bite the bullet and cut my losses, since those other users seemed to settle for a reinstall. Any final advice out there I can try out? :(

---

### Post by gaberlunzie on 2010-10-14
OK, I did the (apparent) inevitable and reinstalled afresh overnight, based on similar user experiences in this section regarding the general error mounting filesystems. Dreading any event of freeze-ups like previously.

Just want to say Maverick is impressively slick and fast! Now to slog through reinstalling and configuring all those apps! *sigh*

---

### Post by mörgæs on 2010-10-14
Good, please mark the thread 'solved'.

If only more people would reinstall when problems appear...

---

