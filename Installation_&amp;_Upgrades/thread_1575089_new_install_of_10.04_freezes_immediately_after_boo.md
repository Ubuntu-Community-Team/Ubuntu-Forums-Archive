---
title: "new install of 10.04 freezes immediately after boot"
date: 2010-09-15
forum: Installation &amp; Upgrades
---

### Post by justflints on 2010-09-15
After doing a clean install of 10.04, it freezes after booting.  I see the 'dots' screen, then the desktop is rendered; the mouse still moves, but suddenly it freezes and it's all over. This is a PC that has several versions of ubuntu over the years, no problems. Any one got any briaght ideas?

---

### Post by justflints on 2010-09-15
...should i be considering an earlier version of ubuntu, or is there another installation process I should consider? Or maybe buy a mac?):P

---

### Post by Rubi1200 on 2010-09-15
> **justflints said:**
> ...should i be considering an earlier version of ubuntu, or is there another installation process I should consider? Or maybe buy a mac?):P

> Or maybe buy a mac?
Not a good idea :lolflag:

What graphics card do you have installed?

---

### Post by justflints on 2010-09-15
It's an ATI Radeon 9200

---

### Post by justflints on 2010-09-15
ubuntu@ubuntu:~$ lspci
00:00.0 Host bridge: Silicon Integrated Systems [SiS] 645xx (rev 51)
00:01.0 PCI bridge: Silicon Integrated Systems [SiS] SiS AGP Port (virtual PCI-to-PCI bridge)
00:02.0 ISA bridge: Silicon Integrated Systems [SiS] SiS964 [MuTIOL Media IO] (rev 36)
00:02.5 IDE interface: Silicon Integrated Systems [SiS] 5513 [IDE] (rev 01)
00:02.7 Multimedia audio controller: Silicon Integrated Systems [SiS] AC'97 Sound Controller (rev a0)
00:03.0 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f)
00:03.1 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f)
00:03.2 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f)
00:03.3 USB Controller: Silicon Integrated Systems [SiS] USB 2.0 Controller
00:04.0 Ethernet controller: Silicon Integrated Systems [SiS] SiS900 PCI Fast Ethernet (rev 90)
00:05.0 RAID bus controller: Silicon Integrated Systems [SiS] RAID bus controller 180 SATA/PATA  [SiS] (rev 01)
01:00.0 VGA compatible controller: ATI Technologies Inc RV280 [Radeon 9200 PRO] (rev 01)
01:00.1 Display controller: ATI Technologies Inc RV280 [Radeon 9200 PRO] (Secondary) (rev 01)
ubuntu@ubuntu:~

---

### Post by buggyruss on 2010-09-15
I have an ancient PIII with Radeon 7000 et al; Xubuntu 8.04 works fine, Lubuntu and Ubuntu 10.04 broke (freeze on browser start if network is enabled). Updating Xubuntu 8.04 to 8.04.4 worked fine. Installing Ubuntu 8.04.4 direct from an ISO disk broke.

I decided to stick with Xubuntu 8.04.4 and simply have removed all processes that I don't need to make this machine work fast enough to do what I want it to do (surf, develop some minimal software). I got rid of all powersaving (except gnome-power-manager which I cannot find HOW to disable under XFCE), bluetooth, NetworkManager, dhcdbd (or whatever that ill-named daemon is called), etc. - a bunch of superfluous running processes that were useless with a system that has no powersaving ability and is on a smal hardwired home LAN behind a router to the world. I surf (with Firefox) now with a speed I can easily live with, can run certain graphics quite satisfactorily fast, listen to streaming audio if I want, etc.

Good enuf as a second machine!

[main machine is quad-core rocket XP; I use this PIII machine as my backup when the kid wants to do her own surfing...she NEEDS speed)

---

### Post by justflints on 2010-09-16
Thanks buggyruss.  Are you saying that you reckon that I should just revert to ubuntu 8.04? - or that I can remove a few spurious processes and make it work with 10.04?
By the way, it freezes as soon as it boots, I don't get a chance to start firefox or anything else.  Also, it does work in tryout mode, booting from a memory stick - I don't know if that's significant.

---

### Post by Rubi1200 on 2010-09-16
Have you tried 9.10?
Maybe that will work with your hardware?

---

### Post by justflints on 2010-09-16
No, not yet.  I naively thought that since the tryout worked (running from a memory stick), then the full install would work.

---

### Post by buggyruss on 2010-09-16
Yeah, based off your second post I was suggesting (albeit not real obviously, huh?) that an "older" version of (X)Ubuntu might be the ticket for you as it was for me. Depending on your needs it easily could be sufficient (it's more than sufficient for my needs).

And with a minimal amount of twiddling real performance increases can be achieved as well (though, based off others's posts elsewhere, Ubuntu is getting slower, not faster, over new versions).

=========

I should note here that I tried to install Lubuntu 10.04 with a new ethernet card (Intel Pro 1000 series). That system broke horribly during boot, gave a stack trace, then dropped off into a text terminal (no windowing system at all). The ethernet connection worked (!) but X wouldn't come up with minimal attempts to get it there. With the old no-name card the whole 10.04 system came up but crashed if a browser was invoked while the ethernet was up (ifup eth0). So I downloaded ISO files for everything from 8.04.4 to 10.04 and began burning them and trying them out one at a time!

I'm a Happy HighSpeed Networking Camper with Xubuntu 8.04.4, even on this old 600MHz PIII. It'll probably be the last OS I install on this machine (my main machine (that the kid is using right now) is a quad core (XP) rocket that'll become my "main" Linux box sooner or later - at that time this machine will bacome a mini-web-server or something for test purposes).

EDIT - added as an irrelevant aside...I "grew up" with UNIX on a PDP 11/45 in the mid-70s (grad school computer science). My current "old" PIII runs rings around that PDP - I've become ridiculously spoiled over the decades. I have here in my house SCO Unix on 5.25" floppies and early Redhat currently installed on a 200MHz Pentium box (though it's sitting un-turned-on in a hallway). Both systems, though, were sufficent for my needs at the time - mostly mini-development.

---

### Post by davidmohammed on 2010-09-16
> **justflints said:**
> After doing a clean install of 10.04, it freezes after booting.  I see the 'dots' screen, then the desktop is rendered; the mouse still moves, but suddenly it freezes and it's all over. This is a PC that has several versions of ubuntu over the years, no problems. Any one got any briaght ideas?

when booting press shift to display your grub.  Then press e to edit.  Find the line with quiet splash.  Add

nomodeset before quiet splash

i.e.

... nomodeset quiet splash --

then boot.

If this doesnt work, remove the text quiet splash and boot.  In a reply, describe the text outputted on the screen where the PC appears to hang.

---

### Post by justflints on 2010-09-17
Thanks buggyruss. davidmohammed, I haven't tried your suggestions, but thanks anyway, I decided that discretion was the better part of valour and installed 9.10, which - touch wood - works ok. Like buggyruss, this may be the last OS I install on this old pc (but it still works pretty well with the right version!).  Now I've just got to get all those bits that make it do useful stuff like play mp3s....

---

