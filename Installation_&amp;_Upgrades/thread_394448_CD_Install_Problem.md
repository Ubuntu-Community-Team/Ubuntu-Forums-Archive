---
title: "CD Install Problem"
date: 2007-03-26
forum: Installation &amp; Upgrades
---

### Post by Krymore on 2007-03-26
Windows XP went to hell on my laptop, so I decided to install Ubuntu on it instead.  I downloaded the iso from [http://releases.ubuntu.com/edgy/ubuntu-6.10-desktop-i386.iso](http://releases.ubuntu.com/edgy/ubuntu-6.10-desktop-i386.iso), burned it to a CD-RW, changed the BIOS stuff to boot from the CD, yet my laptop just spins the disk around a few times before attempting to load windows and immediately blue screening me before rebooting the laptop and repeating the cycle.  I can't get Windows to load at all with the blue screen-reboot cycle and I don't know how else to get it to load the iso from the CD other than attempting to go back to my desktop and redownload the file and reburn it again.  Can anyone help me?

---

### Post by tommcd on 2007-03-27
How did you burn the disk? You need to use an iso burning tool, you can't just copy it to a CD.
[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)
Also, check the md5sum of the download, and burn the disk at a very slow speed.
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)
Also double check the BIOS to make sure you saved the changes when you set it to boot from the CDROM.
And welcome to the forums.

---

### Post by Krymore on 2007-03-27
Ah, thanks for that, I must have burned it wrong.  The .iso was appearing as the one file rather than all the directories and such.  I'll redownload and try again with burning software that doesn't suck so bad.

---

### Post by tommcd on 2007-03-28
If the md5sum checks out on the iso you downloaded you should be able to use that. Just burn it with the iso burning tool I linked to. Good luck.

---

### Post by Saur0n on 2007-03-28
I've noticed a few copies of the .iso are corrupt on the download mirrors list.  Utah for sure has a corrupt .iso :(

---

