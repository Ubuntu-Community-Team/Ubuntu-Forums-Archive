---
title: "Various install issues"
date: 2006-04-10
forum: Installation &amp; Upgrades
---

### Post by Azio on 2006-04-10
This is my first time with Linux, so bear with me if I sound stupid.

Basically I installed Ubuntu to my USB hard drive per the instructions in [this thread]("http://www.ubuntuforums.org/showthread.php?t=80811"). I'm not sure if my problems are related to my using a USB drive so I decided to bring them here.

First off, near the end of the install process, it suddenly crapped out. Went to a grey screen with rapidly-scrolling black text, too fast to read.
[IMG]http://www3.telus.net/northlight/azio/images/linux/scroll.jpg[/IMG]

After a minute or two it finally stopped, and the aftermath can be seen below.
[IMG]http://www3.telus.net/northlight/azio/images/linux/panic.jpg[/IMG]

So I rebooted the machine, started Linux. It appears to boot okay, but it complains about something called Locale twice during the startup process:
[IMG]http://www3.telus.net/northlight/azio/images/linux/locale.jpg[/IMG]

Finally, X Server fails to start because it can't find any screens. This is the output:
[IMG]http://www3.telus.net/northlight/azio/images/linux/xserver.jpg[/IMG]

I have a hand-built machine with an AMD Athlon 64 3200+, 1GB (2x512) RAM, ATI All-In-Wonder X800XL, and a Creative Sound Blaster Audigy 2. The motherboard is DFI LanParty UT NF4 Ultra-D. The hard drive is a 40GB Hitachi Travelstar in an nGear USB Mobile enclosure. I'm running the latest AMD64 release.

---

### Post by Kapre on 2006-04-10
Azio - the install did not finish. Try to reinstall. Also did you d/l or is it from the mail. If its a d/l, check the MD5sum and maybe re-burn it again (at a slower speed - say 8X).

K

---

### Post by Azio on 2006-04-10
I'm re-downloading the image directly from FTP (as opposed to bittorrent which I did last) and I'll run it off a compactflash card because I'm out of CDRs.

---

### Post by taurus on 2006-04-11
From your last screenshot, you have a problem with GLX in /etc/X11/xorg.conf.  So, you may want to edit your /etc/X11/xorg.conf and comment that module out.  From a terminal, type
```

sudo nano /etc/X11/xorg.conf <-- what is capital x and number eleven, X11...

```
You can command out a line in /etc/X11/xorg.conf by placing a # in front of it!
```

#load          glx

```

---

### Post by Azio on 2006-04-12
Okay, I redownloaded the image via FTP, and tried to install from a compactflash card, and got the same errors. I redownloaded it again and used a CDR... and got the same errors. The grey screen thing happens when it's just about finished installing packages.

---

