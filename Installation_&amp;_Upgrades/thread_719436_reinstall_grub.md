---
title: "reinstall grub"
date: 2008-03-09
forum: Installation &amp; Upgrades
---

### Post by gos1 on 2008-03-09
Hi 
 
    I have to re-install the grub and cannot find the right command . 
 
    I have a laptop with one partitioned harddisk with only Kubuntu . And I cannot boot right now . I want to install the grub or anything that can help me to boot again . But cannot . 
 
   In one of the posts I have seen some one having the same trouble as me . And tried his solution you can find it here 
 
    [http://ubuntuforums.org/archive/index.php/t-607034.html](http://ubuntuforums.org/archive/index.php/t-607034.html)

 And when I deleted the files in /boot/grub I could not run the command again / Does anyone knows how can I boot my lap top again . I dont want to format , install all the updates and software for days and hope the system not to crash again

---

### Post by forestpixie on 2008-03-09
you can use your livecd, if you have one 

[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

or download, burn as iso and boot with supergrub
[http://supergrub.forjamari.linex.org/](http://supergrub.forjamari.linex.org/)

---

### Post by gos1 on 2008-03-09
Well because I deleted all the files in the /boot/grub directory I cannot run the find /boot/grub/stage1 command it does not give any answer except from file not found . I Take a backup of the menu.lst file is it going to help

---

### Post by forestpixie on 2008-03-09
if you've got a good backup then copy it across - if you can't get into recovery mode you'll have to do it in the livecd

If that's the case you will need to navigate to the correct /boot/grub - obviously the one that you can get to easily when in the livecd is not the one you boot with.

If you don't get anywhere with that then use supergrub

---

### Post by gos1 on 2008-03-09
i installed the supergrub in my usb drive but now getting missing operating system error . Do I have to do anything more than untaring the files _

---

### Post by gos1 on 2008-03-09
I created the super grub cd version and still cannot do anything because I previously deleted all the files  in /boot/grub is there a way to restore them or find a standard version of the files to put in the same directory

---

### Post by forestpixie on 2008-03-09
how did you actually delete them - if you used sudo rm I would guess that they're never gonna come back

I've found one other thread similar - but you're not gonna like the suggestion :(

You could wait and see if Herman turns up - he/she always seems to appear when grub is involved, but I'd be expecting to have to reinstall

Edit I don't suppose that [Herman]("http://ubuntuforums.org/member.php?u=44990") would mind a pm -

---

### Post by gos1 on 2008-03-09
I worked so hard to make the settings and downloaded really big amount of data for programs etc . The thing I need is to reinstall grub or is it possible for me to install lilo instead . Will that fix the problem . I mean installing lilo and use lilo as the default boot manager ? How can I do that ?

---

### Post by Pumalite on 2008-03-09
Reinstalling Grub will not reinstitute your deleted files.

---

