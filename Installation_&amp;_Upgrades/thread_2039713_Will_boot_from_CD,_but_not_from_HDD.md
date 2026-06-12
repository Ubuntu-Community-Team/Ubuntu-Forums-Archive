---
title: "Will boot from CD, but not from HDD"
date: 2012-08-09
forum: Installation &amp; Upgrades
---

### Post by bonbonblu on 2012-08-09
I searched a few similarly titled threads, but nothing seemed to match my comp's symptoms.

I just assembled the computer I'm typing on, and I'm doing that through the "try ubuntu" live cd.  The installation went fine, no messy partitions, no hardware failure, drivers for the lan and video card work fine on the cd, but when I try to boot from the hard drive I get a sputtering screen (orange and black).  I checked the hard drive (742 GB File System) and it looks like a normal layout, home directory and everything.

I hope this is the right forum; responses will be greatly appreciated.

(Btw I tried both the 64 and 32 bit .iso)

---

### Post by FatFrog on 2012-08-09
Can you switch to a TTY when this happens? If so, try running a 'unity --reset" from tty1 and see if that lets you log in...


(Switching between TTYs is easy: CTRL+ALT+'F1-F6' and I think CTRL+ALT+F7 will get you back to the GUI...)

---

### Post by bonbonblu on 2012-08-09
Do you mean switch the TTY and restart unity while I'm on the live cd, or when I'm on the hard drive?  I tried from the live cd and it didn't let me log in.

---

### Post by oldfred on 2012-08-09
What video card/chip?

With nVidia I have to use nomodeset.

How to set NOMODESET and other kernel boot options in grub2 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

---

### Post by FatFrog on 2012-08-09
was referring to booting from the HDD...
Basically, when you see the screen flicker, press CTRL+ALT+F1 and then run 'unity --reset' at the prompt after logging in with your UN and PW...

---

### Post by bonbonblu on 2012-08-09
> **oldfred said:**
> What video card/chip?

With nVidia I have to use nomodeset.

How to set NOMODESET and other kernel boot options in grub2 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

It's actually an AMD, but I'll try that.

---

### Post by bonbonblu on 2012-08-09
> **FatFrog said:**
> was referring to booting from the HDD...
Basically, when you see the screen flicker, press CTRL+ALT+F1 and then run 'unity --reset' at the prompt after logging in with your UN and PW...

I should have figured =] I'll try that but I can't for about an hour (I'm typing from my phone)

---

### Post by bonbonblu on 2012-08-09
> **bonbonblu said:**
> I should have figured =] I'll try that but I can't for about an hour (I'm typing from my phone)

When I 'ctrl-alt-f1' it stops the sputtering screen, but it doesn't bring up a terminal prompt.  When I change back to f7 the screen flashes (black and white)

---

### Post by bonbonblu on 2012-08-09
> **oldfred said:**
> What video card/chip?

With nVidia I have to use nomodeset.

How to set NOMODESET and other kernel boot options in grub2 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

I tried reinstalling using nomodeset, and the the stuttering is now localized to the top of the screen (the rest is black).  If I move the mouse over the stuttering part I can see the cursor.  Ctrl-alt-f1 doesn't show anything on screen, but it still stops the stutter.

---

### Post by oldfred on 2012-08-09
Natty or later Video issues. MAFoElffen
[http://ubuntuforums.org/showthread.php?t=1743535](http://ubuntuforums.org/showthread.php?t=1743535)

Some other settings, some have to use generic at first:
[http://ubuntu-tutorials.com/2010/05/06/ubuntu-10-04-lucid-blank-screen-at-startup-workaround/](http://ubuntu-tutorials.com/2010/05/06/ubuntu-10-04-lucid-blank-screen-at-startup-workaround/)
* Older Intel video card: i915.modeset=1 or i915.modeset=0
* nVidia: nomodeset
* Generic: xforcevesa or nouveau.modeset=0
* Radeon: radeon.modeset=0

---

