---
title: "Freezes on Install Boot"
date: 2012-05-14
forum: Installation &amp; Upgrades
---

### Post by Mc2992 on 2012-05-14
I am using an older Gateway Laptop running Windows XP and am attempting to boot from the CD.  I can not boot into live mode or install it freezes when the ubunto logo and four white dots are on the screen.  It cycles red to white maybe four or five times then freezes all red and nothing happens.  Can someone advise.  This is running a 2.4 Ghz Athlon64 3700+ Mobile PRoc with 1gb of ram.  I managed to install and boot ubunto in a VM inside of windows but I need to re format and replace windows but right now the only OS on disc I have is Ubuntu so I don't want to format and then not be able to boot it.  Any thoughts??  Can I try an older version could this be to new for this computer??


Thanks for any advice.  Im a bit of a noob to Linux.  

2992

___________________________________________________________________________________________________Update

So I messed with the installation options and now when it freezes on the splash screen with the dots it actually shows the error.  And it says something about can not find driver for wireless device or something.  Anyway to resolve this??  I am running the broadcom wireless card in my laptop and have heard that there is some bug with it.  Wondering if there is anything I can do.  Thanks.

---

### Post by wilee-nilee on 2012-05-14
It may not actually be freezing but needs a graphic driver. A virtual has its own drivers separate from the OS.

Take a look at this link on nomodeset.

[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

Your best way to really find out what is going on as far as the exact computer model and hardware is run this command to name the hardware.

```
lspci
```Then go on the web and search with the exact computer model and Ubuntu and or the release number, you're trying, and confirm your hardware as well in this process. If that computer will not work or any of the hardware I suspect you will find it there.

---

