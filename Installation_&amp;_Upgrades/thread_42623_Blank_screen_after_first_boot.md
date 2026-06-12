---
title: "Blank screen after first boot"
date: 2005-06-18
forum: Installation &amp; Upgrades
---

### Post by jrohde on 2005-06-18
Hi,

I'm having an annoying problem with Ubuntu (and Fedora Core 4) - the installation process is ok, and Gnome shows up ok after the installation is finished. But when I reboot, the screen goes blank (or rather black). I have reinstalled three times, and the result was the same.

These are my specs:

DELL Dimension 5000 with BIOS A04
nVidia GeForce 6800 (using DVI)
1 Gb RAM
DELL wireless keyboard and mouse.
2 x 250 Gb SATA drives
DELL 1905FP 19" Flat Panel monitor

As mentiones above, I also have a problem with Fedora Core 4. It shows a weird image immediately after booting the installer.

I have recently upgraded the BIOS to A04. Could that be the reason?

Any help appreciated!

Jakob

---

### Post by jrohde on 2005-06-19
Anybody?

Jakob

---

### Post by mingus on 2005-06-20
[QUOTE=jrohde]I'm having an annoying problem with Ubuntu (and Fedora Core 4) - the installation process is ok, and Gnome shows up ok after the installation is finished. But when I reboot, the screen goes blank (or rather black). I have reinstalled three times, and the result was the same.[/QUOTE]

Confused a bit by the problem description . . . are you seeing gnome in the second completion stage of the installation, but then after the first post-install boot the screen goes black?  Do you see any text at all when you boot?

---

### Post by luca_linux on 2005-06-20
I had that problem about a year ago.
If I remember well, you are getting problems with the framebuffer.
Try passing "nofb" to your kernel at boot and see if it works.
Then let me know.

---

### Post by jrohde on 2005-06-20
[QUOTE=mingus]. . . are you seeing gnome in the second completion stage of the installation, but then after the first post-install boot the screen goes black?  Do you see any text at all when you boot?[/QUOTE]

Yes. The install process goes fine, and the initial start of X and Gnome is ok. But when I reboot, I only get a black screen (with no mouse pointer).

And yes, I see the boot / startup messages ok. And when I end up with a black screen, I can use the Alt+Fx text consoles.

Jakob

---

### Post by mingus on 2005-06-21
I did a forum, wiki, and a google search on your nvidia card and got quite a few hits.  The problem is that you need to install the proprietary nvidia driver.  I hesitate to point you to particular posts or howto's because I'm unfamiliar with the card and there appear to be different tweaks depending upon version, i.e., the driver needs to be installed and possibly add-ons depending on features desired.  This is not the same as the "nv" generic nvidia driver

You can just try a #dpkg-reconfigure xserver-xorg to see if it picks up the driver, but I'm doubtful.

---

### Post by jrohde on 2005-06-21
Hi,

I found out what was wrong: I have two LCD monitors attached to the pc: one 17" to the analog output and one 19" to the digital/DVI output.

Allthough the 17" monitor has been turned off all the time, it somehow interfered whith the hardware scan process. I unplugged the 17" before my last attempt to install Ubuntu, and everything went ok.

I would appreciate it, if anyone can explain exactly what happended and why.

Jakob

---

### Post by mingus on 2005-06-21
Have you *searched* the forums & googled the problem?

Here is one re 2 monitors, which itself refers to a fix on another webpage.  This may not help but there are many posts and webpages for this card.

[http://ubuntuforums.org/showthread.php?t=34392](http://ubuntuforums.org/showthread.php?t=34392)

---

