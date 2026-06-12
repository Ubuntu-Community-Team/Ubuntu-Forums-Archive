---
title: "Ion3 fonts gone"
date: 2006-11-27
forum: Installation &amp; Upgrades
---

### Post by davor on 2006-11-27
After I upgraded to the latest version of Ubuntu, a few weeks ago, it broke my ion3-setup (windowmanager). All of a sudden, all of my fonts disappeared.

I tried removing my .ion3 folder, and reset to the standard configuration, but that didn't really help. Do you guys have any idea what I can do to fix this issue?

Thanks!

PS My problem doesn't seem to be isolated. This guy seems to have the same one. [http://lhealy.livejournal.com/](http://lhealy.livejournal.com/)

---

### Post by No Whammies on 2006-11-27
Try re-installing your fonts with Automatix.  When I upgraded to Edgy, my fonts looked funny, so I ran Automatix2 and just installed/reinstalled several files, including fonts.  Worked for me.

---

### Post by davor on 2006-11-29
That didn't really help. I had a look in .xsession-errors and it seems to complain about beeing "Unable to load any usable ISO8859 font"

---

### Post by davor on 2006-11-29
This is my entire .xsession-errors-file:

/etc/gdm/PreSession/Default: Registering your session with wtmp and utmp
/etc/gdm/PreSession/Default: running: /usr/X11R6/bin/sessreg -a -w /var/log/wtmp -u /var/run/utmp -x "/var/lib/gdm/:0.Xservers" -h "" -l ":0" "davor"
/etc/gdm/Xsession: Beginning session setup...
>> Could not load font "-*-helvetica-medium-r-normal-*-12-*-*-*-*-*-*-*", trying "fixed"
>> Failed to load fallback font.
>> Stack trace:
   0 [C]: in 'defstyle'
   1 /etc/X11/ion3/look.lua:49
     [Skipping unnamed C functions.]
>> Could not load font "-*-helvetica-medium-r-normal-*-17-*-*-*-*-*-*-*", trying "fixed"
>> Failed to load fallback font.
>> Stack trace:
   0 [C]: in 'defstyle'
   1 /etc/X11/ion3/look.lua:78
     [Skipping unnamed C functions.]
>> Could not load font "-misc-fixed-medium-r-*-*-13-*-*-*-*-60-*-*", trying "fixed"
>> Failed to load fallback font.
>> Stack trace:
   0 [C]: in 'defstyle'
   1 /etc/X11/ion3/lookcommon_clean.lua:3
     [Skipping unnamed C functions.]
   4 [C]: in 'dopath'
   5 /etc/X11/ion3/look.lua:106
     [Skipping unnamed C functions.]
Warning: Unable to load any usable ISO8859 font
Segmentation fault

---

### Post by davidakachaos on 2006-12-19
I have the same problem. Whoes fault is it? ion3 or Edgy? I don't want to downgrade to dapper again :( Does anyone have a solution?

---

### Post by nille on 2006-12-25
I have the same problem, and, unfortunately, I have no solution (at least not a nice one..), but I have some more information on the matter. Let's start with a (very) temporary and ugly "solution":

Let's assume you're using look_cleanviolet.lua (I think that's the standard look). Then go to your /etc/X11/ion3/ directory, open up look_cleanviolet.lua and change all helvetica-...12/17-rows into helvetica-...14 (don't know why 14 works and 12/17 not). Preferrably save as something else (i.e. look_tmplook.lua). Change into that look, and at least some fonts will show up (well, at least it works for me, so don't blame me if it doesn't work :p ).

Well, however, the problem is not ubuntu-specific, cause I've heard that someone using Gentoo had the same problem. From the #ion -irc the answer was something about braindamaged distros, and something about bringing a cluebat to the ubuntu headquarters.. ](*,) . Hopefully someone will find a solution to this, but I've got some ideas to test from your posts, I will be back if I find any (nice, and actually working) solution..

Marry Christmas (if you're celebrating that one :p )

---

### Post by nille on 2006-12-27
I've found a solution, I hope (well, for me it worked). Check out:
[http://www.ubuntuforums.org/showthread.php?t=270412]("http://www.ubuntuforums.org/showthread.php?t=270412")

The solution for me was just to change X11/fonts to fonts/X11 in xorg.conf .

---

