---
title: "[SOLVED] Installation from Ubuntu to Beta of Gutsy"
date: 2007-09-28
forum: Installation &amp; Upgrades
---

### Post by lisati on 2007-09-28
I've been using Ubuntu 7.04 for a few months now and decided to upgrade to the beta of Gutsy.....The upgrade completed and now I've encountered a couple of challenges.....(Yes, I know it's Beta, so there might still be a couple of gremlins hiding there to test our troubleshooting skills)

1) allowing Grub to default to the first kernel in the list results in a blank screen with no obvious signs of disk activity, same result if I use the revoery mode and then use startx. Pressing the power button & then alt+S shuts the system down as expected
2) I can boot from the other kernal, but there seems to be something amiss with my wireless settings - I can get to my router's configuration page but not to internet (works perfectly with Windows....)

It's getting late so my troubleshooting skills aren't at their best...

The machine is a Toshiba Satellite from the A100 range, and had no major hassles with 7.04

I'll come tomorrow with more info as I do my research. In the mean time, suggestions would be welcome.
Thanks in advance.

Edit (several hours later): upgrade done by using the update-manager -d technique.

---

### Post by lisati on 2007-09-28
Progress report: I've tried sudo dpkg-reconfigure xserver-xorg as suggested [elsewhere]("http://ubuntuforums.org/showthread.php?t=562221") - no joy getting past the blank screen so far. I'm beginning to suspect that something's getting stuck somewhere, and will post results as they come in......

EDIT: one boot I did notice a message about "kernel.maps_protect is an unknown key" somewhere in proceedings. This, however, could be a red herring.

---

### Post by lisati on 2007-09-28
Hmmmm.....seems to be hanging somewhere between "Starting Gnome manager" and actually putting something on the screen. Various tinkerings with xorg and other stuff don't seem to help.


Boots ok from 2.6.20-15 kernel, but no sound and no Wifi (wired connection works)......but gets stuck when booting the 2.6.22-12 kernel

I think I'll go get myself an alternate CD to see if I can do some more troubleshooting from there...


Edit: Must be time for a break, my posting seems to be a bit disjointed and bordering on the incoherent and unhelpful.

---

### Post by Pumalite on 2007-09-28
[http://ubuntuforums.org/showthread.php?t=562424](http://ubuntuforums.org/showthread.php?t=562424)

---

### Post by lisati on 2007-09-29
Partial success at getting a display by tricking Xserver into thinking that I had a VGA monitor (aaargh) now to tinker with the settings and get internet working... (I'm using another machine at the moment)

EDIT: I'll look at coming back to Gutsy in a few weeks onces there's an "official release", I'm returning to Feisty in the meantime. BTW, I'd tried a fresh install as a dual boot (with WinXP)  from an "alternate" disk-Grub didn't seem to know about the XP partition.........

---

### Post by lisati on 2007-09-29
> **Pumalite said:**
> [http://ubuntuforums.org/showthread.php?t=562424](http://ubuntuforums.org/showthread.php?t=562424)

Jost spotted this.....thanks!

---

