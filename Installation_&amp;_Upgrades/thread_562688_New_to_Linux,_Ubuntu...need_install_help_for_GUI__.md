---
title: "New to Linux, Ubuntu...need install help for GUI / video card probs"
date: 2007-09-29
forum: Installation &amp; Upgrades
---

### Post by XMarceloX on 2007-09-29
I installed Ubuntu desktop on my GF's IBM/Lenova, and it just worked FLAWLESSLY.  Installed easier than XP, found everything...just WORKED.

Enthusiatic, and troubled with my web server's Windows issues (never ending), I decided to go with Ubuntu Server, based on my pleasant, though exceedingly brief exposure to the Desktop Client ( I really just installed it, and handed it to my GF...didn't "play" with it at all).

Cut to my problems:  Ubuntu server apparently does not install a GUI...AT ALL

OK, so I set about reading stuff on here.  I educate myself (I always do this first, rather than just cry for help like a clueless boob).

I've since done the apt-install for these packages:

$ sudo apt-get install xserver-xorg x11-common
$ sudo apt-get install xfonts-base
$ sudo apt-get install gdm

Originally,  my server had an ATI 128 Rage Pro, but my research on its compatibility lead me to purchase an NVIDIA GeForce 2, since the hardware compatibility list seemed to indicate that this card worked OK with Ubuntu (the ATI wasn't working with the GUI).

I've run dpkg-reconfigure xerver-xorg
I've tried the VESA driver
I tried adding:

Section "Extensions"
Option "Composite" "Disable"
EndSection

...to the xorg.conf file.

I've tried running turning off the frame buffer...NOTHING

At least because I manually installed GNOME, and the fonts, the GUI comes up, but after logon, and loading the initial screen, I choose what looks like the desktop (rightmost of two icons at the bottom of logo/splashscreen), and the logo disappears...but no desktop is forthcoming.  It just hangs solid with just a brown screen, and a mouse pointer...same as it did with the fricken ATI card.

Now I'm getting pissed, because I've just popped for a new graphics card, and it's the same s*** as before.

HELP!!!!!

I don't wanna go back to Windows.  Someone please save me from the evil Bill Gates empire of forever broken software!!

---

### Post by XMarceloX on 2007-09-29
Ohhh...and I also get an error about the Human theme not being installed as soon as the GUI starts to load.  I've searched, but can't find info on how to install this "theme" to end this carping error mssg.

---

### Post by XMarceloX on 2007-09-29
I also looked at the output when the screen fails to load at all (using various resolutions and drivers), and there are numerous font/path errors.

Why so many goof-ups with the install routine on this product???  Stuff doesn't go in right, needs to be hacked in manually...I'm starting to get bummed out.

Somebody please help me...

---

### Post by XMarceloX on 2007-09-29
Bueller?

---

### Post by XMarceloX on 2007-09-30
Great forum...thanks guys!

:rolleyes:

---

### Post by muguwmp67 on 2007-09-30
If you want to install the gnome gui after a server install use:

sudo apt-get install ubuntu-desktop

---

### Post by XMarceloX on 2007-09-30
Thanks, will try that.  Open to all other suggestions still.  Thanks again.

---

### Post by XMarceloX on 2007-09-30
Worked!  Thanks.  Probably coulda saved the $50 I blew on a new graphics card, had I tried this first.  No instructions anywhere said to try loading a desktop in this manner.  No posts anywhere I could find on this forum, either.

Thanks again, muguwmp

---

