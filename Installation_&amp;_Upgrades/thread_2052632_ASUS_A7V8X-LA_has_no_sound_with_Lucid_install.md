---
title: "ASUS A7V8X-LA has no sound with Lucid install"
date: 2012-09-03
forum: Installation &amp; Upgrades
---

### Post by Omo on 2012-09-03
I have some socket A mainboards acquired for experiments in dual-booting 98 and Linux, and I have been using the ASUS A7V8X-LA (Kelut) with Hardy. Naturally, I tried to upgrade to Lucid, but two problems. No sound (onboard VIA 8237) and no 1280x800 monitor resolution (Acer X193W with 1440x900 native resolution - video card is PNY nVidia 6200)

Is there some way I can collect the various driver files that are working for me in Hardy, and copy them to CD or thumb drive, to use later on to 'correct' a flawed install of Lucid or Precise? Where to find them now, I don't know. How to make use of them later, I also don't know.

---

### Post by cortman on 2012-09-03
> **Omo said:**
> I have some socket A mainboards acquired for experiments in dual-booting 98 and Linux, and I have been using the ASUS A7V8X-LA (Kelut) with Hardy. Naturally, I tried to upgrade to Lucid, but two problems. No sound (onboard VIA 8237) and no 1280x800 monitor resolution (Acer X193W with 1440x900 native resolution - video card is PNY nVidia 6200)

Is there some way I can collect the various driver files that are working for me in Hardy, and copy them to CD or thumb drive, to use later on to 'correct' a flawed install of Lucid or Precise? Where to find them now, I don't know. How to make use of them later, I also don't know.

If you had sound/correct video resolution in Hardy, it's probably because of a different kernel. You can see what kernel your version of Hardy used and install that in Lucid.
But as Lucid is only supported for another 7 months, you're probably better off installing [XLU]buntu 12.04.

---

### Post by Omo on 2012-09-03
> **cortman said:**
> If you had sound/correct video resolution in Hardy, it's probably because of a different kernel. You can see what kernel your version of Hardy used and install that in Lucid.
But as Lucid is only supported for another 7 months, you're probably better off installing [XLU]buntu 12.04.Thank you for replying. I think my Hardy started with the Linux kernel 2.6.24, and has been upgraded to 2.6.32 by now. The sound and monitor resolution haven't been affected throughout the upgrades.

I'm somewhat burdened with "Windows-think" and am picturing replacing incorrect drivers with ones that work. Maybe Ubuntu doesn't work that way.

---

### Post by cortman on 2012-09-03
> **Omo said:**
> Thank you for replying. I think my Hardy started with the Linux kernel 2.6.24, and has been upgraded to 2.6.32 by now. The sound and monitor resolution haven't been affected throughout the upgrades.

I'm somewhat burdened with "Windows-think" and am picturing replacing incorrect drivers with ones that work. Maybe Ubuntu doesn't work that way.

Drivers for Linux are part of the kernel. Occasionally a hardware maker will make a proprietary driver for their hardware; this is not included in the kernel but must be installed manually.
If your hardware was working without proprietary drivers it should continue to do so.
Frankly my advice would be to just re-install a more modern version.

---

### Post by Omo on 2012-09-03
> **cortman said:**
> Drivers for Linux are part of the kernel. Occasionally a hardware maker will make a proprietary driver for their hardware; this is not included in the kernel but must be installed manually.
If your hardware was working without proprietary drivers it should continue to do so.
Frankly my advice would be to just re-install a more modern version.I did give a try of the Lubuntu 12.04 live CD, but it did not show well. I'll download and burn a Ubuntu 12.04 LTS CD and try it, but I anticipate more of the same. It doesn't trouble me if support for old hardware is left off newer Ubuntu builds, so long as there is a way to add it manually. I just wish it was as easy as placing the correct driver file in the appropriate folder.

---

### Post by cortman on 2012-09-03
> **Omo said:**
> I did give a try of the Lubuntu 12.04 live CD, but it did not show well. I'll download and burn a Ubuntu 12.04 LTS CD and try it, but I anticipate more of the same. It doesn't trouble me if support for old hardware is left off newer Ubuntu builds, so long as there is a way to add it manually. I just wish it was as easy as placing the correct driver file in the appropriate folder.

Typically, it's easier! It comes with Linux, the kernel.
For older hardware I would definitely recommend Lubuntu. Or for an even lighter (but in my opinion, superior) experience try Bodhi Linux or Crunchbang.

---

### Post by Omo on 2012-09-03
> **cortman said:**
> Typically, it's easier! It comes with Linux, the kernel.
For older hardware I would definitely recommend Lubuntu. Or for an even lighter (but in my opinion, superior) experience try Bodhi Linux or Crunchbang.just like the spaghetti sauce, "It's in there!" ?? ~ well, it appears that 12.04 LTS may do the trick, since the live CD got me the little bongo drums that I hear when the Hardy log-in screen appears

---

### Post by cortman on 2012-09-03
> **Omo said:**
> just like the spaghetti sauce, "It's in there!" ?? ~ well, it appears that 12.04 LTS may do the trick, since the live CD got me the little bongo drums that I hear when the Hardy log-in screen appears

Great. :) My goal is not to answer all problems with a simple "reinstall!"; if you really wanted we could dig into the issue (and my knowledge would likely be outstripped fairly soon) but in the long run if all you want is a functioning system, a reinstall is your quickest, easiest, and most effective option.

---

### Post by Omo on 2012-09-04
> **cortman said:**
> Great. :) My goal is not to answer all problems with a simple "reinstall!"; if you really wanted we could dig into the issue (and my knowledge would likely be outstripped fairly soon) but in the long run if all you want is a functioning system, a reinstall is your quickest, easiest, and most effective option.Well, the news is good, bad, and curious. The curious is that I decided to try a live CD of the newest version of 10.04 LTS, just for grins, and it booted up in complete silence, but I poked around and saw the sound was muted, for some unknown reason. Go figure. Unmute, and I got sound.

So I'm now working with a fresh install of 10.04.4, and am adding the usual bits and pieces (GIMP, Flash, VLC, etc) but the one thing that seems to elude me is the monitor support that I got in Hardy. It must be that a 16x10 aspect ratio is for antiques, or something, because nothing I do can get me the 1280x800 display that worked for me in Hardy. I tried three different nVidia drivers, and no joy, and a dozen more would probably accomplish nothing, since the System/Preferences/Monitor pathway gets me a popup that states the nVidia proprietary driver isn't going to give me control over resolution settings. I can only adjust that through Ubuntu's controls, and they don't have 1280x800

---

### Post by cortman on 2012-09-04
> **Omo said:**
> Well, the news is good, bad, and curious. The curious is that I decided to try a live CD of the newest version of 10.04 LTS, just for grins, and it booted up in complete silence, but I poked around and saw the sound was muted, for some unknown reason. Go figure. Unmute, and I got sound.

So I'm now working with a fresh install of 10.04.4, and am adding the usual bits and pieces (GIMP, Flash, VLC, etc) but the one thing that seems to elude me is the monitor support that I got in Hardy. It must be that a 16x10 aspect ratio is for antiques, or something, because nothing I do can get me the 1280x800 display that worked for me in Hardy. I tried three different nVidia drivers, and no joy, and a dozen more would probably accomplish nothing, since the System/Preferences/Monitor pathway gets me a popup that states the nVidia proprietary driver isn't going to give me control over resolution settings. I can only adjust that through Ubuntu's controls, and they don't have 1280x800

Hm, have a look at [this thread]("http://ubuntuforums.org/showthread.php?t=1112186"), especially post #3. But don't make any changes persistent until you've confirmed they work. :)

---

### Post by Omo on 2012-09-04
> **cortman said:**
> Hm, have a look at [this thread]("http://ubuntuforums.org/showthread.php?t=1112186"), especially post #3. But don't make any changes persistent until you've confirmed they work. :)Thanks, I'll bookmark that, and see what I can {break} figure out

---

