---
title: "Video Config Issue - Gnome/Xorg"
date: 2007-12-20
forum: Installation &amp; Upgrades
---

### Post by OldManRiver on 2007-12-20
:):)

All,

I've been working off my installation bugs and keeping a running log of it all at:

[http://ubuntuforums.org/showthread.php?t=637969](http://ubuntuforums.org/showthread.php?t=637969)

Problem #2 in this is the one with my video.  You can see I've been at it on a fairly in-depth level and still have no resolution to my problem.

Thought maybe a need thread, addressing only that specific problem, might gen more interest, since not getting any responses on the original thread.

Thinking maybe everyone thought my problems were too complex, when grouped together.

Thanks in advance for all the help!

OMR

:):)

---

### Post by madking on 2007-12-20
make a backup of your x conf (sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_bu) and then try running the command

sudo dpkg-reconfigure xserver-xorg


with all the proper settings.
hope this helps. :)

---

### Post by OldManRiver on 2007-12-21
> **madking said:**
> make a backup of your x conf (sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_bu) and then try running the command

sudo dpkg-reconfigure xserver-xorg

with all the proper settings.
hope this helps. :)

:):)
Sorry tried all that, even wrote a script, to switch configs, but nothing is resolving this.

Problem is with the monitor.  I've emailed the mfg. (6 weeks ago and again today) but no response.  I know this one bends the curve, but need step-by-step manual help as the:

sudo dpkg-reconfigure xserver-xorg

command just makes things worse.  It even overwrites my source files for the config, so had to write >>restore<< and >>setup<< sections in my script to get all the files setup initially and restored right after the >>dpkg-reconfigure<<.  Have tried that command with and w/o the -phigh option, neither produces anything workable.

Thanks much for the response.  Hope maybe this gives you more to munch on!  LOL!

OMR

:):)

---

