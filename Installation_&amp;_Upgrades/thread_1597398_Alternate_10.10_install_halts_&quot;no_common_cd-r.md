---
title: "Alternate 10.10 install halts: &quot;no common cd-rom was detected&quot;"
date: 2010-10-15
forum: Installation &amp; Upgrades
---

### Post by c00kiemonster on 2010-10-15
I am attempting an alternate install of 10.10 from a USB stick. Everything seems to be going fine, I select location and keyboard, but after that the installation complains that it can't find any cd-rom. It then checks other removable media for drivers, but that doesn't work either and the installation halts.

The system I am installing it on is a asus at3iont motherboard, and I don't have a cd-rom drive connected (hence the USB install).

I have tried both "Universal USB Installer" and UNetbootin as [this post]("https://help.ubuntu.com/community/Installation/FromUSBStick") suggests, but without any success. I also tried the "cdrom-detect/try-usb=true" thing that a lot of google results suggest, but that too is a dud for me.

As far as I can tell from the Google results it seems like it's an old bug from 2008 or something. I can't tell whether it has been fixed though. There are a few posts here and there on the forum about the same problem, but there is no definite answer it seems.

I would **really** appreciate help on this. I have eyed ubuntu for a long time, and I finally went out and bought hardware for a ubuntu media center. It really sucks that I can't even get the installation started. I could go off on an ironic tangent here with snide remarks about the '90s and its nowadays obsolete cd-rom technology. But I won't. I just want ubuntu up and running. Any help is greatly appreciated.

---

### Post by mörgæs on 2010-10-15
Hi, welcome to the forum.

As a first test: Can you install 10.04 on the machine?

---

### Post by c00kiemonster on 2010-10-15
I just installed 10.10 with the regular iso. It worked fine, no problems there.

However I am setting up SW RAID on my system disk so I need the alternate iso to work too.

I am trying now to see whether I have better luck with 10.04.1 alternate instead.

---

### Post by c00kiemonster on 2010-10-16
An update on the progress:

I tried to create a USB stick with usb-creator-gtk in the terminal. The 10.10 alternate iso didn't work (all I got was segmentation faults). The 10.04.1 alternate iso worked ok, I can boot from it and there is no cdrom issue at all.

So, to conclude, it seems like the 10.10 alternate iso is jinxed with USB installs... Will run 10.04.1 for now.

---

### Post by Dr. Cox on 2010-10-16
neither 10.10 nor 10.04.1 work for me as alternate install cd via usb.... always the complaint about no cd-rom drive to be found (yes, it's a netbook and has no cd drive) but why does that matter?

any ideas?

cheers,

dr.cox

---

### Post by c00kiemonster on 2010-10-16
To be more elaborate, I tried three different usb stick creators:

**Universal USB Installer [win]**
Successfully made a 10.10 alternate USB stick, but it had the cdrom issue.

**Unetbootin [win]**
Successfully made a 10.10 alternate USB stick, but it had the cdrom issue.
Successfully made a 10.04 regular USB stick, with a successful installation too.

**Startup Disk Creator (usb-creator-gtk) [ubuntu]**
Could not make a 10.10 alternate USB stick, got Segmentation Fault instead.
Successfully made a 10.04.1 alternate USB stick, with a successful installation too.

A bit long-winded, but I first installed a plain vanilla 10.04 (no raid), where I could make the 10.04.1 alternate USB stick. 

N.B., the 10.04.1 alternate USB stick that Startup Disk Creator had a slight hick-up with some unrecognized tag. But simply typing 'help' and hitting enter, and then hitting enter in the help menu booted the installation process just fine.

So all in all,  I finally got the raid setup ok, but running 10.04.1 instead of 10.10. Wouldn't hurt if it would have been easier though, I wasted a good few hours on this...

---

### Post by thrvers on 2010-10-18
'
you can use this tips :D it works for me [create using Startup Disk Creator from linuxmint 9 {same as ubuntu 10.04}]

_[[SOLVED] ubuntu alternate 10.10 "no cdrom detected"](http://ubuntuforums.org/showthread.php?t=1500654)_ and i combine with _[edit syslinux.cfg](http://ubuntu-virginia.ubuntuforums.org/showpost.php?p=9702639&postcount=11)_

:guitar:

---

