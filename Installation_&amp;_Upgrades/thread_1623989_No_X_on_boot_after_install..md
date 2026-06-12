---
title: "No X on boot after install."
date: 2010-11-17
forum: Installation &amp; Upgrades
---

### Post by rowanq on 2010-11-17
Hi All,
  Can anyone think of a reason that an Acer notebook would run the USB installer perfectly at native resolution, but then fail to start X on reboot?
 All attemps to run startx will only allow low graphics mode.

Thanks,
 Rowan

---

### Post by dino99 on 2010-11-17
check the driver activation: system admin additional driver

---

### Post by rowanq on 2010-11-17
Yeah, that was one of the first things I tried. I even reinstalled a few times, but each time I got the same result.

Rowan

---

### Post by vs8 on 2010-11-17
I'll never buy an Acer again. All Acer computers I've tried have some sort of problem with Linux.

My mother bought an Acer Aspire 5742z and I has exactly the same problem. I can only run it on low graphics mode. The audio card is not even recognised by Mavrick's kernel.

I installed Natty's latest version and everything worked out of the box during the live session, when I installed it X didn't start at all, not even in safe graphics mode.

I want to try linux 2.6.37 on this machine since it has all the drivers it needs to run. Is there an easy way (PPA) of installing this kernel on Maverick?

---

### Post by rowanq on 2010-11-17
> **vs8 said:**
> I'll never buy an Acer again. All Acer computers I've tried have some sort of problem with Linux.

My mother bought an Acer Aspire 5742z and I has exactly the same problem. I can only run it on low graphics mode. The audio card is not even recognised by Mavrick's kernel...

I want to try linux 2.6.37 on this machine since it has all the drivers it needs to run. Is there an easy way (PPA) of installing this kernel on Maverick?

This is the same model I have; Acer Aspire AS5742Z-4685. I have two other Acer machines, one netbook and  one other laptop and they work fine with Ubuntu, only very minor issues.

Maybe I should try out that new Linux Mint install rolling Debian. Its likely to have the latest kernel, thought I understand its not built for stability.

---

### Post by vs8 on 2010-11-17
Great Idea man! Let's see if it works! My mother really needs Ubuntu, it's were she started computing!

EDIT:
I have submitted a bug report, please mark "it affects me too".


Thank's in advance!

[https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/676805](https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/676805)

---

### Post by vs8 on 2010-11-18
It started working properly after an update. I used Ubuntu Tweak added some PPAs and some apps, updated the system and now everything works as usual.

---

### Post by rowanq on 2010-11-18
Really? So you ran an update in low graphics mode and everything sussed out? Are you getting audio as well?

---

### Post by rowanq on 2010-11-18
By the way, what ppa's did you install?

---

### Post by vs8 on 2010-11-19
I still can't believe it either!

I installed Ubuntu Tweak and installed all the PPAs I usually install.

emesene
UT testing
Xorg updates
Gnome3 Stack (Which is new in the list and maybe the one responsible for the fix)
Google Stable
Chromium Daily
Empathy
Gwiber daily
Mozilla Daily
Transmission
Elementary Nautilus

And some others I can't remember right now.

Suspend/resume started working and sound as well I was very impressed! I haven't tested hibernate because I never use it and already made my mom very happy when I gave her the computer with good ol' Ubuntu (she hates Windows 7).

---

### Post by wilee-nilee on 2010-11-19
Did you add this one?
[https://launchpad.net/~ubuntu-x-swat/+archive/x-updates](https://launchpad.net/~ubuntu-x-swat/+archive/x-updates)

---

### Post by vs8 on 2010-11-19
Yes, that one, the fresh X crack is not stable.

---

### Post by wilee-nilee on 2010-11-19
> **vs8 said:**
> Yes, that one, the fresh X crack is not stable.

You must have needed a graphic card driver that is in this ppa. To actually identify your card in the terminal.
```
lspci | grep VGA 
```

---

### Post by vs8 on 2010-11-19
> **wilee-nilee said:**
> You must have needed a graphic card driver that is in this ppa. To actually identify your card in the terminal.
```
lspci | grep VGA 
```

I've installed that PPA and Fresh X crack just to see what happens in two different installs and the problem insisted. I was re-installing the system for two days experimenting different options.

The video card always worked flawlessly in the live sessions, the sound device wasn't recognized and suspend/resume and hibernate didn't work either. 

The only different PPA I installed was the Gnome3 Stack. Other changes I made was Installing the system with BTRFS with EXT4 /boot partition instead of the standard EXT4 partition. What amazes me is the fact that now I have working sound, suspend/resume and 3d after adding these PPAs.

---

### Post by rowanq on 2010-11-19
So, I ended up going a different route. I installed kernel 2.6.37 from here:

[http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.37-rc2-maverick/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.37-rc2-maverick/)

Now I have full resolution and sound. Even the headphone jack works correctly. The only issue I still have is that I'm unable to adjust the screens brightness. Not a big issue, but it'd be nice to save a little battery power.

So I guess I'm calling this one a win. w00t!

---

### Post by vs8 on 2010-11-19
> **rowanq said:**
> So, I ended up going a different route. I installed kernel 2.6.37 from here:

[http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.37-rc2-maverick/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.37-rc2-maverick/)

Now I have full resolution and sound. Even the headphone jack works correctly. The only issue I still have is that I'm unable to adjust the screens brightness. Not a big issue, but it'd be nice to save a little battery power.

So I guess I'm calling this one a win. w00t!

Awesome! I can't control the backlight either.

Thank's for the kernel link I was looking for that!

---

### Post by rowanq on 2010-11-19
> **vs8 said:**
> Awesome! I can't control the backlight either.

Thank's for the kernel link I was looking for that!


No worries! Oddly enough, the function key that turns off the backlight works, but I have no control over brightness.

Is there a way to add that kernel ppa to the my repo list? I don't see any obvious way to do it.

---

### Post by vs8 on 2010-11-20
I don't think you can add it to your PPA list because it's for Natty.

I re-installed Maverick on my laptop today (no the Acer) and noticed boot speed improvements with this 2.6.37 kernel.

---

### Post by reb99 on 2010-11-20
Thanks rowanq and vs8 I installed 2.6.37 and my acer is working great now!!!:D

---

### Post by vs8 on 2010-11-21
> **reb99 said:**
> Thanks rowanq and vs8 I installed 2.6.37 and my acer is working great now!!!:D

I'm glad to hear that!

---

### Post by rowanq on 2010-11-21
> **reb99 said:**
> Thanks rowanq and vs8 I installed 2.6.37 and my acer is working great now!!!:D

Cool! My machine was down for a week. Glad to know others are finding this.

---

### Post by rowanq on 2010-11-25
Found a fix for the brightness control issue in this thread:

  [http://ubuntuforums.org/showthread.php?t=1617362](http://ubuntuforums.org/showthread.php?t=1617362)

---

### Post by vs8 on 2010-11-25
Thank you very much dude!!!!!

---

