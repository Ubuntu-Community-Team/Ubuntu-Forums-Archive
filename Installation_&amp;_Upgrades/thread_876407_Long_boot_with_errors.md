---
title: "Long boot with errors"
date: 2008-07-31
forum: Installation &amp; Upgrades
---

### Post by Slaakker on 2008-07-31
Hello.  I am a new user to Linux.  I have installed Ubuntu on a separate drive in my computer and I am successfully dual booting XP and Linux.  The problem I am having is that it takes forever for Ubuntu to load as it scrolls many errors.  They look to be hard drive read errors but I am not familiar with Linux yet.  I could sure use some help.

I have attached my syslog.  If there is a different log that would help better diagnose the problem, please let me know and I will post it.

Thanks for the help!

Intel dual core 2.4gh
Nivdia 9600gt
4 gig ram
Asus p5w-dh deluxe Mobo

---

### Post by Pumalite on 2008-07-31
Edit menu.lst and remove 'quiet splash'
See where it lags.

---

### Post by Pumalite on 2008-07-31
[http://ubuntuforums.org/showthread.php?t=601485](http://ubuntuforums.org/showthread.php?t=601485)
[http://ubuntuforums.org/showthread.php?t=89491](http://ubuntuforums.org/showthread.php?t=89491)
[http://ubuntuforums.org/showthread.php?t=254263](http://ubuntuforums.org/showthread.php?t=254263)
[http://ubuntuforums.org/showthread.php?t=585635](http://ubuntuforums.org/showthread.php?t=585635)

---

### Post by Slaakker on 2008-08-01
> **Pumalite said:**
> Edit menu.lst and remove 'quiet splash'
See where it lags.

It looks like the quiet splash is off.  The error messages just scroll by.  One of the messages I get over and over is...

Jul 31 08:12:08 daddesktop
kernel: [ 79.102535] Buffer I/O error on device sdd, logical block 1


Any ideas?  I looked at all the links you posted but most of it looked like tweaking.  I think I have an issue with Ubuntu and my sata drive.

---

### Post by Pumalite on 2008-08-01
Is your drive working with Windows now? If not; check it with rescuecd:
[http://www.sysresccd.org/Download](http://www.sysresccd.org/Download)

---

### Post by pastalavista on 2008-08-01
If you installed from a live CD, the problem may be that  the usplash.conf file has the wrong screen resolution. It was like that for a while when I first installed Ubuntu from the 'gutsy' live CD.

```
sudo gedit /etc/usplash.conf
```

change the screen resolution values to whatever your monitor/graphics supports.

---

