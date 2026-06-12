---
title: "How do I boot from a CD? PowerBook G4"
date: 2007-05-21
forum: Installation &amp; Upgrades
---

### Post by transkinetic on 2007-05-21
I am trying to install Ubuntu Dapper on my girlfreinds PowerBook G4. I cannot figure out how to get it to boot from the CD. System Preferences only lets choose the hard drive or network boot. I have no idea how to acces the bios on a mac.

Any ideas?

thanks,

-spivey

---

### Post by vikramsharma on 2007-05-21
Assuming that you are trying to boot from the ppc edition of Ubuntu.  Press and hold the alt (Option key on the mac) key (next to the apple key).  You would see a grey screen with a hard drive icon and a cd icon use the the mouse to choose the CD icon and click on the arrow.  You should be able to boot into Ubuntu after that.  I this helps, in case you have any doubts don't hesitate to ask.

---

### Post by transkinetic on 2007-05-21
it worked, thank you
I want to install Feisty Fawn on it but I can't find any downloads for ppc.
EDIT:
community platform...I seee.

[http://ubuntuforums.org/showthread.php?t=427714](http://ubuntuforums.org/showthread.php?t=427714)

---

### Post by vikramsharma on 2007-05-21
> **transkinetic said:**
> it worked, thank you
I want to install Feisty Fawn on it but I can't find any downloads for ppc.

Glad to help you out, the link to download the PowerPC link in [here]("http://cdimage.ubuntu.com/ports/releases/feisty/release/ubuntu-7.04-desktop-powerpc.iso").  Btw what kind of ppc do you have, I have a PowerMac G5 1.6 Ghz.

---

### Post by transkinetic on 2007-05-21
I have  no idea what sort of mac this is. How do I find out? It says powerbook G4 on it.
The Feisty install went great. Everything works except for wireless.

---

### Post by charlie763 on 2007-06-25
To enable my AirportExtreme wireless card on my 12" Al PowerBook in feisty fawn I did the the following:
```
sudo apt-get install bcm43xx-fwcutter
```
The program will then ask you for permission of download and install the firmware. Select YES. You may have to enable the universe or maybe even the multiverse repositories to do this.

I just tested the daily-live PPC build for gutsy on 20070625. I did a fresh install with that daily build and then did a
```
sudo apt-get update; sudo apt-get dist-upgrade
```
to ensure I had the latest packages. The Restricted Manager now has an entry for the broadcom chipser drivers. The Tribe-2 milestone in the gutsy release cycle should have support for it. Tribe-2 comes out on Thursday 20070628. It's development software, so be careful. Simple support is on the way. Keep your hopes up.

The current daily-live PPC build can be found at [http://cdimage.ubuntu.com/ports/daily-live/current/](http://cdimage.ubuntu.com/ports/daily-live/current/)

-Charles Edward Pax

---

