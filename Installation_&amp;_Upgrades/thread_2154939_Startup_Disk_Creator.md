---
title: "Startup Disk Creator"
date: 2013-06-16
forum: Installation &amp; Upgrades
---

### Post by asdrubale on 2013-06-16
Did anyone ever managed to make it work? I remember i tried to use it since Ubuntu 10 but i never got it to work; i tried with many different computers, and many different USB thumb drives, and i always have the same problem: after i erase a disk, it multiplies many times.
I don't understand if it's just horribly buggy or if i'm doing something wrong; right now, i have 4 different thumb drives i often use with no issues; if i try to use them, the bug in the screenshot i linked appear

[http://www.pasteall.org/pic/show.php?id=53617](http://www.pasteall.org/pic/show.php?id=53617)

Thanks for your help

---

### Post by sudodus on 2013-06-16
Yes I can make it work and I am actively debugging it right now for Lubuntu 13.04 and Saucy (13.10). See these links

[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

[URL="https://bugs.launchpad.net/ubuntu/+source/usb-creator/+bug/1165200/"]bug report (and comments #15 and #16) 
[/URL]

---

### Post by sudodus on 2013-06-16
I saw it was your first post. Welcome to the Ubuntu Forums :-)

Do you want to use the USB drive to install, or do you want persistence? If 'only' to install, you might try cloning it instead of using the Startup Disk Creator alias usb-creator-gtk or usb-creator-kde. Cloning has a high rate of success, provided you write to the intended target drive, and I have made a script to help you with that task.

The method and the script for **dd image of iso file to USB device safely** are described in the [Ubuntu Forums tutorial "Howto make USB boot drives"]("http://ubuntuforums.org/showthread.php?t=1958073")

Anyway, if you are not used to the command line interface alias terminal window, maybe you should install the KDE version of Startup Disk Creator because it works without issues for me also outside Kubuntu.

```
 usb-creator-kde
```

---

### Post by C.S.Cameron on 2013-06-16
I never seem to have a problem with Startup Disk Creator using it with each new release of Ubuntu since 8.04, (once past beta stage).
I don't have much luck using it with any distro's but Ubuntu.

---

### Post by TNFrank on 2013-06-16
I've managed to use it to make Live USB's to try out different types of Linux. Sometimes it works, sometimes it doesn't. When it doesn't then I use my fall back, UNetbootin and it generally works. Between those two you should be able to make up a Live USB that'll let you give an Op System a Try before you install it.

---

### Post by TiberiusT on 2013-06-18
Well I'm with the OP. I have completely given up with it and now exclusively use LiLi under Win7. I've always found it very ironic that to get an USB Linux install stick I have to use Windows. It does sometimes work in Ubuntu (I revisit it occassionally) but I'd honestly say that's abt 10pct of the time. Using same hardware (the PC dual boots) I've never ever had a single problem in LiLi. 

But hang on..... @sudodus - I had no idea I could just dd the ISO image - I rarely care abt persistence so I'll give your script a go bcos dd certainly needs some safety barriers around it. Thanks a lot. 

T


T

---

### Post by sudodus on 2013-06-18
@TiberiusT

You are welcome and good luck :-)

---

