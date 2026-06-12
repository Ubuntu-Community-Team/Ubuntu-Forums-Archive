---
title: "GNOME failsafe works, GNOME doesn't - 10.04 upgrade"
date: 2010-05-27
forum: Installation &amp; Upgrades
---

### Post by sandpvrr on 2010-05-27
Hello All,
      Older machine here that I upgraded to 10.04 after a clean install of 9.10 some months ago. When booting into GNOME, the desktop image flashes on the screen and the second the bars on top and bottom try to appear the system boots out of the desktop and returns to the log on screen. I assume this is a crash of Xserver, but just guessing. Per another page I ran: lspci | grep VGA
and returned: 
01:00.0 VGA compatible controller: VIA Technologies, Inc. KM400/KN400/P4M800 [S3 UniChrome] (rev 01)

I know - old machine :-)
      Typing this from failsafe mode, would be great to hear from someone as to what I can do to get this working in normal mode again.
      Thanks!
       -Joey

---

### Post by sandpvrr on 2010-05-29
Still haven't heard anything - any ideas regarding this VIA Chipset crashing GNOME? 
          Thanks!
         -Joey

---

### Post by davidwall on 2011-12-06
I had the same problem, with the same output from lspci | grep VGA.  My .xsession-errors file included:
[INDENT]Initializing nautilus-gdu extension
/usr/bin/compiz (core) - Fatal: Support for non power of two textures missing
/usr/bin/compiz (core) - Error: Failed to manage screen: 0
/usr/bin/compiz (core) - Fatal: No manageable screens found on display :0.0
gnome-session: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.0.
[/INDENT]and I saw this text in [http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=428974](http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=428974) which ended with
[INDENT]Looks like your graphic driver does not like non-power-of-two textures,
while compiz requires this feature. It's unlikely to get fixed soon
unfortunately.[/INDENT]I found instructions for removing compiz from ubuntu here:  [http://m.jguk.org/2009/03/remove-compiz-from-ubuntu.html](http://m.jguk.org/2009/03/remove-compiz-from-ubuntu.html)
[INDENT]Right click on the desktop, select "Change Desktop Background".
Click "Visual Effects", click the "none" option.

Then issue these commands to remove the Compiz packages:

# apt-get --purge remove compiz compiz-core

^ It doesn't tell you, but compiz is actually still running, so you will need to reboot to benefit.
[/INDENT]I did this, and was able to log out and back in a couple of times in normal non-failsafe gnome.

Don't know what else I might have broken by doing that :) but for the moment I'm a happy camper.  If you see the same thing in .xsession-errors (or .xsession-errors.old), you might have the same luck.

-David

---

