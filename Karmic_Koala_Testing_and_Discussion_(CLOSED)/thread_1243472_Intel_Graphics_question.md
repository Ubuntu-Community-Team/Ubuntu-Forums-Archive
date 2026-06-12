---
title: "Intel Graphics question"
date: 2009-08-18
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by zoomy942 on 2009-08-18
First off, 9.10 Alpha 4 is blazing fast.  WOW.

something i noticed instantly was my Intel graphics were enabled with compiz by default, instead of blacklisted like in 9.04.  That said, is there a way to install this newer intel graphics on my 9.04?  the other features of 9.10 are great, but i cant install an alpha on my production machine.

im asking becaue i know there are drivers, and the kernel, and i didnt know what to install to take advantage of how much faster this is.

---

### Post by FFuser on 2009-08-18
> **zoomy942 said:**
> First off, 9.10 Alpha 4 is blazing fast.  WOW.

something i noticed instantly was my Intel graphics were enabled with compiz by default, instead of blacklisted like in 9.04.  That said, is there a way to install this newer intel graphics on my 9.04?  the other features of 9.10 are great, but i cant install an alpha on my production machine.

im asking becaue i know there are drivers, and the kernel, and i didnt know what to install to take advantage of how much faster this is.

It is possible to install newer X drivers in 9.04, and that is what I did before installing karmic.

But next to newer drivers you need to install a newer kernel, newer mesa, newer Xorg from a ppa. (which can cause trouble too)

After I've upgraded to karmic my system feels generally more stable (But I had a lot of others ppa installed (pulseaudio, new gdm, ...) next to the Xorg ones)

I think you have 3 options:
* Wait until october when 9.10 will be released
* Install 9.10 alfa next to your 9.04 on your production machine (with a shared /home if possible) and whenever 9.10 breaks you can still boot into 9.04.
* Just Install the xorg-updates ppa

The first one is the least satisfactory, the last one can make your stable system unstable, the middle one has all benefits you need but may not be possible (not enough HD for example, or when you don't have a seperate /home)

---

### Post by zoomy942 on 2009-08-18
> **FFuser said:**
> It is possible to install newer X drivers in 9.04, and that is what I did before installing karmic.

But next to newer drivers you need to install a newer kernel, newer mesa, newer Xorg from a ppa. (which can cause trouble too)

After I've upgraded to karmic my system feels generally more stable (But I had a lot of others ppa installed (pulseaudio, new gdm, ...) next to the Xorg ones)

I think you have 3 options:
* Wait until october when 9.10 will be released
* Install 9.10 alfa next to your 9.04 on your production machine (with a shared /home if possible) and whenever 9.10 breaks you can still boot into 9.04.
* Just Install the xorg-updates ppa

The first one is the least satisfactory, the last one can make your stable system unstable, the middle one has all benefits you need but may not be possible (not enough HD for example, or when you don't have a seperate /home)


i just might do option 2.  i know when i install 9.10, i get the GRUB 2 stuff, will that make my ubuntu 9.04 mad?  and do i need to resize my partition of 9.04 prior to starting this?

---

### Post by FFuser on 2009-08-18
> **zoomy942 said:**
> i just might do option 2.  i know when i install 9.10, i get the GRUB 2 stuff, will that make my ubuntu 9.04 mad?  and do i need to resize my partition of 9.04 prior to starting this?

You have to use a free partition, of you don't have that you have to resize your 9.04 partition.

Grub 2 should not be a big problem, except if it does not work for some reason on your hardware ;)

If it does not work you should still be able to use a 9.04 (or older) live CD to restore the old grub without any data loss.

If you don't feel very confident resizing partitions and using the live CD to restore your Grub you better don't go into all the trouble and just wait a few months...

---

### Post by andrewabc on 2009-08-18
According to your signature you have
Intel 4965
Exactly what version of intel graphics is that? g965? GMA x3100 ? EDIT: I'm guessing that means wireless card. So what exactly is your chipset/video hardware?

Which one listed from
[http://en.wikipedia.org/wiki/Intel_GMA](http://en.wikipedia.org/wiki/Intel_GMA)

As far as I know 965 series has not been blacklisted in more than a year.
Only 945 chipset (GMA 950) series and below are blacklisted as far as I know. I don't think many people got the GMA 3000/3100 (most got x3000/x3100)

When you say jaunty alpha is "blazing fast" are you running it from cd? virtualbox? If running from cd, try running from usb stick as it will run much faster :) Will run as fast as if you had it installed (no cd-rom lag)

Did you upgrade to 9.04 from 8.10 etc? That could be why it was blacklisted still (depends on what card you have).

---

### Post by zoomy942 on 2009-08-18
> **andrewabc said:**
> According to your signature you have
Intel 4965
Exactly what version of intel graphics is that? g965? GMA x3100 ? EDIT: I'm guessing that means wireless card. So what exactly is your chipset/video hardware?

Which one listed from
[http://en.wikipedia.org/wiki/Intel_GMA](http://en.wikipedia.org/wiki/Intel_GMA)

As far as I know 965 series has not been blacklisted in more than a year.
Only 945 chipset (GMA 950) series and below are blacklisted as far as I know. I don't think many people got the GMA 3000/3100 (most got x3000/x3100)

When you say jaunty alpha is "blazing fast" are you running it from cd? virtualbox? If running from cd, try running from usb stick as it will run much faster :) Will run as fast as if you had it installed (no cd-rom lag)

Did you upgrade to 9.04 from 8.10 etc? That could be why it was blacklisted still (depends on what card you have).

all excellent questions.  i have the GMA 3100/965.  mine will work, but when i install jaunty, it was blacklisted automatically, which is removed easily enough.

in reading over my post, i realized i came off sounding like a rookie.  lol.  im not.  i love ubuntu, have for a while, but when running 9.10 off my thumbdrive, the graphics were smoother than i have ever seen, and app loading/firefox browsing was blazing.  thats the first time since my jump to 8.10 that i saw a noticeable difference.

im curious in trying 9.10 on a space on my HD for 2 reasons - the changes to power management and the intel drivers.  those are both key for me since im mobile alot.

---

### Post by andrewabc on 2009-08-19
Do you mean x3100?
GMA 3100 does not use 965 chipset according to wiki page.

I find it odd that your video card was blacklisted as I have g965 x3000 in desktop tower and it was last blacklisted in 7.10 release. Although compiz only became usable in 8.10. And compiz only became "fast" usable in 9.04. I can now run video fullscreen in a workspace with no stuttering and do compiz stuff and it works flawlessly. Firefox scrolling no longer lags.

Although they say intel drivers were broke in 9.04 which caused slowdowns for lots of people. I didn't notice the slowdown. Maybe you were one of those affected, and they stated they fixed the problem in 9.10. I think comiz runs faster for me in 9.10, but that could be because of all the crap I have installed.

When testing alpha 4 off of usb it crashed a bunch when showing it off on a friends computer. But still useable.

If you need/want compiz and it works great on alpha 4 compared to 9.04, then you could install to a separate partition. At least this way you can always be testing 9.10 to make sure everything works when released.

---

### Post by zoomy942 on 2009-08-19
> **andrewabc said:**
> Do you mean x3100?
GMA 3100 does not use 965 chipset according to wiki page.

I find it odd that your video card was blacklisted as I have g965 x3000 in desktop tower and it was last blacklisted in 7.10 release. Although compiz only became usable in 8.10. And compiz only became "fast" usable in 9.04. I can now run video fullscreen in a workspace with no stuttering and do compiz stuff and it works flawlessly. Firefox scrolling no longer lags.

Although they say intel drivers were broke in 9.04 which caused slowdowns for lots of people. I didn't notice the slowdown. Maybe you were one of those affected, and they stated they fixed the problem in 9.10. I think comiz runs faster for me in 9.10, but that could be because of all the crap I have installed.

When testing alpha 4 off of usb it crashed a bunch when showing it off on a friends computer. But still useable.

If you need/want compiz and it works great on alpha 4 compared to 9.04, then you could install to a separate partition. At least this way you can always be testing 9.10 to make sure everything works when released.


understood.  yes i was one of those affected by the slowdowns and constant flickers anytime it was doing something 3D.  it was horrible.  i installed 9.10 on a seperate parition and it's a night and day difference.  compiz is faster, everything is smoother and nothing is flickering anymore.  wow.

---

### Post by andrewabc on 2009-08-19
> **zoomy942 said:**
> understood.  yes i was one of those affected by the slowdowns and constant flickers anytime it was doing something 3D.  it was horrible.  i installed 9.10 on a seperate parition and it's a night and day difference.  compiz is faster, everything is smoother and nothing is flickering anymore.  wow.

Don't get your hopes up. during Hardy development compiz worked perfect for me and then an update at some point slowed compiz down to an unusable state. I filed bugs and stuff, but wasn't fixed for me until 8.10 (and then improved more in 9.04).

So make sure to watch out for slowdowns after updates that could screw it up.

---

### Post by zoomy942 on 2009-08-19
understood.  good point.  It's great for now.  I wont use it as my primary - even though now standby mode and hibernate work on my tablet, and they never have :)

---

### Post by andrewabc on 2009-08-28
I'm fixing a computer now, it has intel g965 chipset (dunno which exact video card, it is onboard so x3100 probably).

With jaunty compiz is blacklisted (doesn't work). With karmic alpha 4 it is enabled by default and works ok.

Glad to see it working.

---

