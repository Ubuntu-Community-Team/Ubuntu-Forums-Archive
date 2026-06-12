---
title: "Mac won't boot to disc."
date: 2010-03-25
forum: Installation &amp; Upgrades
---

### Post by chonald on 2010-03-25
I'm trying to install Ubuntu on an old iMac that is running Mac OS X 10.2.8.

I've tried holding down "c", holding down "option", and nothing works.

Would anyone know any tips on how to get Ubuntu to run on this computer?  I happened to find it next to a dumpster... it works!  It's just very old and has little memory.

What do you think?

---

### Post by zvacet on 2010-03-25
If it is old then probably it´s PPC so you will need to download iso for that architecture.You can find it [here.]("https://wiki.ubuntu.com/PowerPCDownloads")You will find more info about installing Ubuntu on Mac [here.]("http://ubuntuforums.org/forumdisplay.php?f=328")

---

### Post by chonald on 2010-03-25
Okay.  I'll look around.

I did just download the PowerPC version of 9.10... but it is over 700MB, it won't fit on a CD-R.  The iMac doesn't have a DVD-ROM.  Hmmm... 

Is there anyway I can somehow put the disc image on the iMac's desktop and install from there?

---

### Post by chonald on 2010-03-25
This just seems like a lost cause.

I hold "option" down, and get to a different screen.  But this screen asks for some sort of password.  I don't know the password.

---

### Post by Wiebelhaus on 2010-03-25
> **zvacet said:**
> If it is old then probably it´s PPC so you will need to download iso for that architecture.You can find it [here.]("https://wiki.ubuntu.com/PowerPCDownloads")You will find more info about installing Ubuntu on Mac [here.]("http://ubuntuforums.org/forumdisplay.php?f=328")

Just to reiterate this good advice.

---

### Post by chonald on 2010-03-25
If I were trying to boot from a burned disc image that was the wrong format (not ppc) the computer wouldn't even attempt to boot from this disc?

I did download a ppc friendly 9.10, but the file is too large for a CD-R.

This point makes me stuck.

I also tried the Yaboo commands, but the terminal doesn't recognize them.

---

### Post by zvacet on 2010-03-26
Download ubuntu-9.10-alternate-powerpc.iso from [here.]("http://cdimage.ubuntu.com/ports/releases/9.10/release/")You will also find MD5SUMS on that page.

---

### Post by chonald on 2010-03-27
zvacet, thank you.

i was finally able to get the computer to boot from disc.  there was a firmware password that i didn't know, this was keeping me from booting from cd.  i reset the firmware by taking out the ram and booting up holding down "control-alt-o-r" (i believe this is what i used).  i then boot up after this pram reset by holding "option".  this allowed me to select the disk to boot from.

i got an install started, but it was stuck at 6% for a while on software installation.  i'm going to download this 9.10 version you linked above, and see how that goes.

appreciate the help.

---

