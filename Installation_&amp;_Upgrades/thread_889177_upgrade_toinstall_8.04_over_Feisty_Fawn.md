---
title: "upgrade to/install 8.04 over Feisty Fawn"
date: 2008-08-13
forum: Installation &amp; Upgrades
---

### Post by cearlp on 2008-08-13
I upgraded my version of Feisty Fawn with all the upgrades that were automatically listed when I started Ubuntu. Then I tried to upgrade to 8.04 but near the end of the process (about 20 minutes remaining) I returned to a blank screen and the computer was hung. Restarting the computer got as far as displaying the versions of Ubuntu that were available. After selecting the version I have always used the computer was hung. I then downloaded 8.04.1-desktop-i386.iso but would like to know what I do to install this file.

---

### Post by mvdberg112 on 2008-08-13
You have already the ISO file. That is in fact a CD-ROM image, isn't it?

This command puts the complete ISO file on the CD (in a text terminal): ```
dd if=/dev/cdrom of=/tmp/cdimg1.iso
```Where '/tmp/cdimg1.iso' is the full path to your iso file. Your iso file has probably a different name and sits in a different location, so fill that in. /dev/cdrom is your cdrom device. On your system, your device might have a different name. If you want to know which name, do as follows:
-Put in a CD, perhaps of the previous linux version
-do in the terminal: cat /etc/fstab
There should be a line in there that mounts your CD-ROM. The string that starts with /dev/ is your CDROM device. That device name needs to be used for the 'if=' option in 'dd'.
Hope this helps. If not, tell what you exactly did and what you saw.

---

### Post by cearlp on 2008-08-13
Okay, thanks for the info. I just have to copy the .iso file to a CD, right? and then use it as the install medium. 
My problem with your instructions is that I can't get my original Ubuntu to boot. I only have Windows XP running now. I'll try to burn the CD with it and then use it for the install CD.

---

