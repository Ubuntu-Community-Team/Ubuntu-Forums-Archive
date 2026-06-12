---
title: "Bad crash in Gusty 7.10"
date: 2007-10-19
forum: Installation &amp; Upgrades
---

### Post by haphappy on 2007-10-19
I just upgraded my laptop from 7.04 to 7.10 by downloading the alternate install CD, mounted the iso, ran the upgrade script.

All went pretty well, it kept trying to start another session of X for some reason, but still made it through the entire install, rebooted.

So I login through GDM, get the familiar start up sound, loads top and bottom menu bars. Starts to load icons, and then *Bam* shuts off.  I power up again. It starts up, I log in. It loads everything. Now I'm at the desktop, I click the icon to upgrade proprietary restricted drivers, *BAM* shuts off.  It halts HARD. Instant poweroff.  

How do I find out what is happening?

It ran 7.04 fine. It runs XP fine (as it is now).

---

### Post by Pumalite on 2007-10-19
Screensaver comes activated at boot. Check yours and 'inactivate' it. Let's see what happens.

---

### Post by haphappy on 2007-10-19
Any way to do that from cli? Like if I boot in recovery mode?

---

### Post by Pumalite on 2007-10-19
Mmmm...mine at least allow me to go to Systems>Preferences before it shut down.
Try: sudo killall screensaver
(nor sure it will work)

---

### Post by haphappy on 2007-10-19
I was able to go to system > preferences > screensaver, uncheck the box *BAM* shuts off before I could click "Close"


I have to boot back into XP every time I want to post results.. :(

---

### Post by haphappy on 2007-10-21
This problem still continues, I was going to try a fresh install, so I loaded up a fresh burn of the full 7.10 desktop.  It starts to load the live GDM, plays the start up sound, loads a bit longer, and then shuts off.

What is causing this? How do I find out which process is causing my computer to shut off so abruptly.

P.S. This is a Toshiba Satellite M35X-S109

---

### Post by Pumalite on 2007-10-21
I've seen several threads in which detection of hardware upon install derives in a shut down. You could try installing with Alternate CD. But beware of this too:
[http://ubuntuforums.org/showthread.php?t=583007](http://ubuntuforums.org/showthread.php?t=583007)

---

### Post by haphappy on 2007-10-21
I guess I'll try from alternate install, but I feel like the processes would not be so different, as I already tried upgrading from the alternate CD, and it crashed after the upgrade.

Is there a log or recovery file I can check to find out what it was trying to do just before it crashes?

---

### Post by haphappy on 2007-10-21
Still no joy, ran Memtest86 for a few hours while I was out,  found a bad address. I'm not sure what to do with it, or how to work around it.  I still do not think it is the source of the problem, as XP and Ubuntu 7.04 worked fine.

Thanks for that thread,  Pumalite.  Is there any way to see what it is trying to detect when it boots or tries to load the live cd?

---

### Post by haphappy on 2007-10-22
Any ideas?

---

### Post by emattic on 2007-10-25
I am having the same problem. Have you resolved it? What kind of laptop do you have?

---

