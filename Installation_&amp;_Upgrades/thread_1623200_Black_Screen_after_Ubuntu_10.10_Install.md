---
title: "Black Screen after Ubuntu 10.10 Install"
date: 2010-11-16
forum: Installation &amp; Upgrades
---

### Post by Duir on 2010-11-16
I have tried, unsuccesfully, to install Ubuntu.

The install process itself seems to work just fine but once it comes time to actually load the OS it stops at a black screen.

I first tried a clean install with it being the only OS and then again from inside Windows after reinstalling it.

It wasn't until dual-booting that I actually noticed Grub and was able to try some of the troubleshooting methods I had found through searching (basically tried removing SPLASH and tried removing QUIET and SPLASH and adding XFORCEVESA) but it didn't make a difference.

One of the troubleshooting suggestions mentioned changing the resolution as it might be trying to use one that's incompatible with the card but I don't how I would edit the xorg.conf file they mention when the farthest I can get into Ubuntu is Grub.

I also tried booting into the recovery option but same result.


Specs for the machine I'm trying to install on are as follows:

Motherboard: Intel 875PBZ
CPU: Intel P4 3.0GHz
GPU: ATI 4650HD
Audio: SB Audigy 2ZS
HDD: WD 120GB (IDE)
OS: Windows XP (SP3) / Ubuntu 10.10

---

### Post by dino99 on 2010-11-16
dont use xforcevesa (scary)

instead try with nomodeset or with video=vesa if nothing else works

---

### Post by Duir on 2010-11-16
> **dino99 said:**
> dont use xforcevesa (scary)

instead try with nomodeset or with video=vesa if nothing else works

Awesome, thanks.

Finally got into the OS using nomodeset.


Do I need to edit Grub now so it does that without my having to it every time or is something that can be fixed by installing the so-called restricted version of my GPU drivers?

I guess I want to be sure I'm not disabling something I might want/need later or might be able to actually fix now that I can get into the OS.


EDIT:
Activated the fglrx driver and am able to load without problems and without having to edit Grub.

---

### Post by infektd on 2010-11-16
where do you input video=vesa? the same place you put nomodset? When ive used nomodset it boots verbose and comes up with a I for text input but it doesn't blink (GPU freeze?) any help is appreciated

---

