---
title: "[SOLVED] Can't log in"
date: 2007-09-28
forum: Installation &amp; Upgrades
---

### Post by Niniel on 2007-09-28
Hello,

Since the live CD was running nicely on my computer [HP Pavilion z5000 notebook, 2.4 GHz P4, 512 MB RAM, 4 GB partition for Ubuntu, 1 GB swap partition] I decided to go ahead and install it on the hd next to my Windoze. All seems to have gone well -  no error messages during installation, boot menu works, system starts ok... until I get to the login screen. I put in my username and password, and that's the end of it. The system just hangs. No messages, either. Sometimes I get a grey rectangle in the upper left corner where the cursor changes to an I-beam in certain areas, but that's it. I tried loading other sessions, but get the same result. Except when I run "failsafe terminal", then I am graced with a terminal window in the lower right corner of the screen (which doesn't do *me* a lot of good :) ). 

What I am wondering now is what could have caused this, and what would be the best way of dealing with it? Delete installation and re-install? 
Could the fact that I burnt the ISO to a CD/RW have anything to do with it? As I said, I didn't get any errors during installation, but I'm having problems that are most likely due to the RW with another installation, so maybe something got corrupted...
Or is my partitioning to blame? Hda1 (ntfs), hda2 (ext3) and hda3 (swap) are all primary partitions.

Very odd. :)

---

### Post by pbcartwright on 2007-09-28
if you boot Ubuntu and do this:
CTRL-ALT-F1
do you get to a text-style login prompt ? If so, then you have a video driver issue. Do you have NVidia card or ATI ?? they take special drivers that don't always install right. If NVIDIA, go to nvidia.com and download the latest driver & follow the install instructions.

---

### Post by dgtldaydrmr on 2007-09-28
sounds like an issue i once had.
See if this old post/replies help

[http://ubuntuforums.org/showthread.php?t=549213](http://ubuntuforums.org/showthread.php?t=549213)

---

### Post by Niniel on 2007-09-28
> **pbcartwright said:**
> if you boot Ubuntu and do this:
CTRL-ALT-F1
do you get to a text-style login prompt ? If so, then you have a video driver issue. Do you have NVidia card or ATI ?? they take special drivers that don't always install right. If NVIDIA, go to nvidia.com and download the latest driver & follow the install instructions.

I have an ATI mobility 9600, I believe. 
How can the video be at fault though when the live CD worked flawlessly? And I do get the graphical login prompt.

---

### Post by Pumalite on 2007-09-28
Do you get a command line with Ctrl+Alt+F1?

---

### Post by Niniel on 2007-09-28
> **dgtldaydrmr said:**
> sounds like an issue i once had.
See if this old post/replies help

[http://ubuntuforums.org/showthread.php?t=549213](http://ubuntuforums.org/showthread.php?t=549213)

Thank you.
It does not quite sound like my problem since I do get the graphical login screen, but I'll see if your solution helps. Would be cool if it did.

---

### Post by Niniel on 2007-09-28
> **Pumalite said:**
> Do you get a command line with Ctrl+Alt+F1?

Haven't tried it yet, and can't do it now, but I'll attempt to do this tonight.

---

