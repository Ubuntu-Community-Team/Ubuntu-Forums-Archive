---
title: "My install experience"
date: 2008-11-29
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by mencargo on 2008-11-29
Hi there, I was thinking about how can I contribute to Ubuntu, so I 
thought testing and sharing my experience... until I can program better. =P

So I will tell my story, hope it helps.

I was using Ubuntu 8.04 and then 8.10, both had video playback problems when I was using an "Appearance" "Visual Effect" level different than "None". Video would flicker constantly. I didn't care about the visual effects, I started using "None" when I found that was my problem.

I was using ATi restricted drivers on my Radeon x1950 Pro.

I also had mount issues with an external USB hard drive, and with an internal partition, both NTFS. I had to force the mount for both, and sometimes the external drive was mounted with an alternative mount folder.
Like "Folder_" instead of "Folder".

But the worst part, and the one that forced me to try Ubuntu 9.04, was that Firefox was REALLY slow and unresponsive, mostly when changing tabs and opening new links at new tabs. It was really horrible.

So I downloaded Alpha 1 and try it with VMware, then VirtualBox, then natively.

First try I used "Expert install" with graphics, it was going great until the part of "Select and Install software", or something like that.
It took forever, I thought it was downloading a lot of stuff from Internet because I selected automatic security updates. But after like 25 min it pops up an error about not able to install something and had to restart. Sorry, I don't remember it exactly, but it was at 6%.

During the Expert Install configuration something felt weird, it told me to select the kernel version from a list, and it was something like:
linux-generic
linux-image-generic
linux-image-2.6.27-generic

I was like.. What? So I selected 2.6.27.

After restart I tried the normal install, and it took like ... 2 hours to install, but finally it finished.
Then the update manager asked to download like 280Mb for upgrades, I accepted and it told me that it wasn't possible, but it could make a partial upgrade, restart and then continue, so I accepted.
It did an upgrade, asked me to restart, accepted but it didn't, so I restarted manually and the update manager tells me my system is up to date.

Anyway, my External Hard Drive was automatically mounted, Firefox is much more responsive, although chromium is much faster, but well, I can live with this.
Video flicker is gone even with visual effects, although I haven't install the ATi restricted drivers.

Well, everything seems better, boots a little faster and shuts down much faster.

My next test will be the 64bit version.

---

### Post by ktp on 2008-11-29
Video flicker is known issue with the ATI restricted drivers and compiz not playing well together.  The new open ATI drivers, which is what you are using most likely works better with compiz and video playback.  In some cases, I think open source is better/faster for my video card when I was using it when ATI restricted drivers did not support latest X during interpid.

---

### Post by dakkar9999 on 2008-11-29
You overcame quite a bit of problem!

I was wondering, what did you do to get rid of the flicker while using effects on desktop?  I have the ATI X1650 and I still have that problem.

---

### Post by ktp on 2008-11-29
Just uninstall the ati restricted drivers and install the open source ati driver.
[https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)

---

### Post by ktp on 2008-11-29
> **dakkar9999 said:**
> You overcame quite a bit of problem!

I was wondering, what did you do to get rid of the flicker while using effects on desktop?  I have the ATI X1650 and I still have that problem.

If you want to install the open source drivers see this:
[http://ubuntuforums.org/showpost.php?p=5795292&postcount=25](http://ubuntuforums.org/showpost.php?p=5795292&postcount=25)

---

### Post by mencargo on 2008-11-29
"I was wondering, what did you do to get rid of the flicker while using effects on desktop? I have the ATI X1650 and I still have that problem."

In fact I didn't do anything.
I just installed Ubuntu 9.04 Alpha 1, once installed and updated it told me about the restricted drivers from ATi, I didn't install them I just continue using the ones that came with it, and they work fine.
I'm now running with "Extra" Visual Effects, and it works smoothly.

And responding to "In some cases, I think open source is better/faster for my video card"...
I think it's in ALL cases, ATi and nVidia use the same chipset for Radeon/FireGL and GeForce/Quadro cards.

That's why in windows there's an application called RivaTunner to unlock their professional capabilities and use them as Quadro/FireGL cards, it consists in several driver tweaks.

Of course this potential is available with opensource, the problem is developing them, that is no piece of cake.

So far this drivers work fine, of course I can't play QuakeLive to compare it... =P

But I'll be testing the 64bit edition with games.

=)

Thanks for the replies, and 1 doubt, where should I propose specific tweaks/features for Ubuntu 9?

---

### Post by danf_1979 on 2008-11-29
Video flickering fix: use AccelMethod EXA in /etc/X11/xorg.conf.

```

Section "Device"
        Identifier      "Configured Video Device"
        Option          "AccelMethod"   "EXA"
        Driver  "fglrx"
EndSection

```

---

### Post by ktp on 2008-11-29
did not work for me...hum?

---

### Post by mencargo on 2008-11-29
> **ktp said:**
> did not work for me...hum?

I think fglrx driver's are the ones that ATi developes, the restricted ones.
So you should disable them:
"System" > "Administrator" > "Hardware Drivers"

And work with the open source drivers.

I'm running with them, and "extra" visual effects, no problems so far.

---

### Post by ktp on 2008-11-29
> **mencargo said:**
> I think fglrx driver's are the ones that ATi developes, the restricted ones.
So you should disable them:
"System" > "Administrator" > "Hardware Drivers"

And work with the open source drivers.

I'm running with them, and "extra" visual effects, no problems so far.

I know that open source drivers work...I said it does but I was talking about following which says it works with fglrx drivers...but not for me.

> **danf_1979 said:**
> Video flickering fix: use AccelMethod EXA in /etc/X11/xorg.conf.

```

Section "Device"
        Identifier      "Configured Video Device"
        Option          "AccelMethod"   "EXA"
        Driver  "fglrx"
EndSection

```

---

### Post by mencargo on 2008-11-30
In that case, did you upgraded your Ubuntu 9.04 once installed?
During the 280Mb upgrade I had, several xorg files where downloaded, I suppose it' using the latest ati driver.

---

### Post by mencargo on 2008-12-02
More testing and doubts.

Hi there, I decided to try the 64 bit edition, but unfortunately for me it didn't work.
Seems that the Alpha 1 CD didn't burn ok, told me about corrupted files while installing, and I didn't thought it was the CD so I downloaded a daily release, that freezes at language selection.

Bad luck, but any way, I went back to 8.10 64bit, and while it's running ok, I have several issues.
I gave my /home it's own partition, and told 8.10 to use it, so it... well, saved all my configuration from 9.04, my firefox has the same plugins I installed in 9.04, it started with the same wallpaper I had, and have the same panel shortcuts, weird stuff... and now firefox does strange things...
It's not saving my history and the URL doesn't show.
I mean, I type ubuntuforums.org and press enter, and my URL stays like "ubuntuforums.org" even if I follow other links.

Another thing I noticed is that I removed my ATi Radeon x1950 Pro to test the onboard intel x3100, and it worked surprisingly great, started with "Extra" visual effects, possibly saved from 9.04, no video playback problems, and everything running smoothly with no restricted drivers, or so I'm told by ubuntu.

The other benefit from 64bit is that it shows my 4Gb of ram instead of 3.2Gb that showed 9.04 32bit.

---

