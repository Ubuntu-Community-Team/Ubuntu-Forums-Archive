---
title: "PC freezes while playing video"
date: 2014-03-23
forum: Installation &amp; Upgrades
---

### Post by bofh19612 on 2014-03-23
I've installed 13.10 on an old HP dc7100, which uses the Intel 915G x86/MMX/SSE2 graphics chipset and driver.  When I play a video the screen freezes after a couple of minutes and the pc doesn't respond to the mouse or keyboard.  It doesn't seem to make any difference if I use another video player or a different video file type.  For a few seconds after the freeze the audio sounds like a skipping record before it too ceases.  Any ideas?  Is there anything in the hardware setup I need to change for Linux?  I did notice that there was a message from the bios about having to make changes for Unix when I swapped the hard disk.  Obviously it didn't say what changes... that would be too helpful.

---

### Post by overdrank on 2014-03-23
> **bofh19612 said:**
> I've installed 13.10 on an old HP dc7100, which uses the Intel 915G x86/MMX/SSE2 graphics chipset and driver.  When I play a video the screen freezes after a couple of minutes and the pc doesn't respond to the mouse or keyboard.  It doesn't seem to make any difference if I use another video player or a different video file type.  For a few seconds after the freeze the audio sounds like a skipping record before it too ceases.  Any ideas?  Is there anything in the hardware setup I need to change for Linux?  I did notice that there was a message from the bios about having to make changes for Unix when I swapped the hard disk.  Obviously it didn't say what changes... that would be too helpful.

Hi and welcome. Could it possible the system is limited in ram to share with the onboard graphics. How much ram does the system have?

---

### Post by bofh19612 on 2014-03-24
2.5 gb.

---

### Post by tgalati4 on 2014-03-24
Look through the log files; open a terminal:

```
less /var/log/Xorg.0.log
```

Spacebar or backspace to navigate.  "q" to quit.

Post only errors, not the entire log file.

---

### Post by frank18 on 2014-03-24
> **bofh19612 said:**
> 2.5 gb.






That's a P4 and think you are better off with Xubuntu 13.04  or 14.04beta, i have a dell  P4 and it doesn't run ubuntu very well,but i installed Xubuntu 13.10 and ir runs fine and i decided to move to xubuntu 14.04 and it's been outstanding no buggs nothing. 

[http://www.engadget.com/products/hp/compaq/dc7100/specs/](http://www.engadget.com/products/hp/compaq/dc7100/specs/)

---

### Post by mörgæs on 2014-03-24
If you want to upgrade BIOS here's some [advice]("http://ubuntuforums.org/showthread.php?t=361236&page=86&p=12775075&viewfull=1#post12775075") for a 7700. Might come in handy for a 7100 as well.

Agree that Xubuntu 13.10 would be a good candidate.

---

### Post by bofh19612 on 2014-03-25
log file as requested...  I found these errors near the start.  I hope it's the right bit.

[    19.384] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    19.385] (==) No Layout section.  Using the first Screen section.
[    19.385] (==) No screen section available. Using defaults.
[    19.385] (**) |-->Screen "Default Screen Section" (0)
[    19.385] (**) |   |-->Monitor "<default monitor>"
[    19.385] (==) No monitor specified for screen "Default Screen Section".
        Using a default monitor configuration.
[    19.385] (==) Automatically adding devices
[    19.385] (==) Automatically enabling devices
[    19.385] (==) Automatically adding GPU devices
[    19.385] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    19.385]    Entry deleted from font path.
[    19.386] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[    19.386]    Entry deleted from font path.
[    19.386] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[    19.386]    Entry deleted from font path.
[    19.386] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[    19.386]    Entry deleted from font path.
[    19.386] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[    19.386]    Entry deleted from font path.
[    19.386] (==) FontPath set to:
        /usr/share/fonts/X11/misc,

---

### Post by bofh19612 on 2014-03-25
Er... I prefer to use Gnome.  This freeze happens under Gnome, Gnome Classic or Unity though.

---

### Post by mörgæs on 2014-03-26
But you should try L/Xubuntu 13.10 anyway as a means of diagnosing the problem. It is not about choosing desktop environment now.

---

### Post by bofh19612 on 2014-03-26
I'm just trying to find a cdr to write the iso image to.  How does a file of 850MB tell me I need a CD when I've put a dvd in the drive?  Incidentally, the video crashes even from the Live dvd.

---

### Post by bofh19612 on 2014-03-27
Booted from a usb stick and installed Xubuntu 13.10.  Haven't installed all the patches yet but videos appear to play fine in Parole.

---

### Post by mörgæs on 2014-03-28
Good. If it solves the problem please mark the thread so.

---

### Post by bofh19612 on 2014-04-01
Crazy thing... it did solve the problem.  Despite the fact that the real problem was that the heatsink had come away from the graphics processor because the retaining clip actually pulls it off if one end comes away from the motherboard.  I put the hoop back into the motherboard with araldite, waited 36 hours, put a bit of thermal paste on and reassembled.  Seems to be working fine now.  Famous last words.  Best regards, Mark

---

### Post by mörgæs on 2014-04-01
'Solved' is under 'thread tools'.

---

