---
title: "Can't Boot Live CD"
date: 2006-12-24
forum: Installation &amp; Upgrades
---

### Post by matthewkris on 2006-12-24
I'm trying to load up Ubuntu on a system I whipped together using orphan parts.

Specs:
Pentium III 1.3ghz
512 megs Ram
8 gig HD freshly formated to FAT32
Radion 9200

The disc boots to the menu just fine.  I have checked the CD for defects and also checked the memory.  I have also tried to start using safe graphics mode.

Boot up hangs just after:

Activating Swap [ok]
Checking File System [ok]

Then the system fonts change and the screen goes blank.  I hear cdrom activity but have let it sit for 30+ mins and nothing.

Any ideas?

---

### Post by taurus on 2006-12-24
Sounds like the desktop CD/LiveCD is having a small problem with your graphic card.  Therefore, I highly recommend you download and use the alternate CD to install it on your machine then...

[http://www.gtlib.gatech.edu/pub/ubuntu-releases/edgy/](http://www.gtlib.gatech.edu/pub/ubuntu-releases/edgy/)

---

### Post by matthewkris on 2006-12-30
I switched back to my onboard vid card and the system installed flawlessly.

I would now like to try to get the other card working.  What suggested steps would you recommend for me trying to install this card?

Any help would be greatly appreciated as I plan on using this as my primary desktop as to learn Linux.

Thank you.

---

### Post by taurus on 2006-12-30
First, go into your BIOS and turn off the onboard graphic card.  Then, make sure the monitor is connected to your video card.  Then, boot into recovery mode from the GRUB menu and at the prompt, reconfigure your X again...

```
dpkg-reconfigure xserver-xorg
startx
```

(If you don't know the answer to a question, just hit the return for the default value.  Use **vesa** for the driver of your video card for now.  You can install the right driver later on when you have X up and running!)

---

### Post by mykalreborn on 2006-12-30
download this file:[http://ubuntuforums.com/attachment.php?attachmentid=19059&d=1162940899](http://ubuntuforums.com/attachment.php?attachmentid=19059&d=1162940899) and then type ```
sudo ./ati-install.sh
```. hope you have a good internet connection though, because it takes quite a while to donwload the driver. 
this will give you 3d acceleration for sure, but if it still doesn't boot reconfigure the xserver and check "dri". 
check this thread:[http://ubuntuforums.com/showthread.php?t=287315](http://ubuntuforums.com/showthread.php?t=287315)

---

