---
title: "cannot install ubuntu on new hd"
date: 2012-03-16
forum: Installation &amp; Upgrades
---

### Post by timberwolf2346 on 2012-03-16
Hi people, I am a newbie. I installed a new hd in an old HP and cannot get past the bios setup screen. The new hd is recognized but nothing happens except either disc boot failure or blinking curser. I have reset the bios several times but the same thing happens. I may need drivers?  The old wxp is gone and I want to install ubuntu for cost as well as security. I am the type to beat my head against the wall so I will try anything a thousand times. I hope this doesn't sound like babble to you.  I have downloaded 11.10 both to a lexar usb stick and to a dvd+rw. I am sure the data came correctly, I am not sure I have all the os install steps that I need. I will ask this question first. If there is a set procedure to install 11.10 ,which I am sure there is, I need to have that info.
hd=wd5000aads-00s9b0,  mb=ms7184 (AmethystM), bios=PHEONIX AWARD v6.00pg, processor = AMD athlon 64x2 3800+ 2.0GHZ.

---

### Post by darkod on 2012-03-16
The blinking cursor might mean video issue. Look at this discussion (not to retype everything now):
[http://ubuntuforums.org/showthread.php?t=1941837](http://ubuntuforums.org/showthread.php?t=1941837)

You need to do the same, hit Esc as soon as it starts booting the cd, activate the nomodeset parameter and see if that brings you to working live mode.

---

### Post by Helen McCall on 2012-03-16
Doesn't look like it is trying to boot from the CD.

Go into your bios settings and check the boot priorities. Make sure that it has CD and USB booting before trying to boot the hd.

Also check that you connected the CD/DVD drive properly.

And when writing the CD/DVD always do a MDSUMS test on the image before writing, and do a full track test after writing.

I hope that helps.

---

