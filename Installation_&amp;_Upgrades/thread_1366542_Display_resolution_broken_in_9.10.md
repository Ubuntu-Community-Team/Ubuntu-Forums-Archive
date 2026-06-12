---
title: "Display resolution broken in 9.10"
date: 2009-12-28
forum: Installation &amp; Upgrades
---

### Post by bkline on 2009-12-28
I just upgraded a system with a 27-inch Hanns-G monitor from 9.04 to 9.10.  Because of problems I had with other systems using the upgrade process, I did the "upgrade" by backing up the user data, reformatting, and installing a fresh copy of 9.10.  At first everything appeared to have gone smoothly, but after a couple of days I noticed that I wasn't getting any sound from Firefox on a New York Times video.  After trying a couple of other things, I logged out and back in.  That solved the sound problem, but the video resolution, which had been working perfectly at 1920x1200, had dropped down to 1024x768, and the best it will do now is 1152x864.  I've tried using xrandr to add the 1920x1200 resolution (with the numbers supplied by cvt), but that results in the error message "xrandr: screen cannot be larger than 1360x864 (desired size 1920x1200)."  The nVidia driver installed is 185.18.36.  The card is nVidia GeForce G210.

Any idea how to make this work again?

---

### Post by bkline on 2009-12-30
> **bkline said:**
> Any idea how to make this work again?

I did some more combing through the forum archives, and I see that the more recent versions of Ubuntu have removed the displayconfig tools without replacing them with the equivalent functionality, so we're back to the "good" old days of editing the X configuration file by hand.  Got it working again by manually inserting a Monitor section with refresh rates, etc.  Seems like this part of Ubuntu is going in the wrong direction if we're hoping for broader acceptance in the non-technical community.

---

### Post by sohaila on 2010-01-07
I've just posted a request for help in another thread, but it looks like my problem may be more similar to yours. I get the same message from xrandr, though with different numbers. Do you mean xorg.conf (which seems to be missing from Karmic)? Can you please describe what you did to get it working?

---

### Post by grubdude on 2010-01-07
I am having a similar issue....

Installed 9.10 on this machine with Viewsonic VG930M Monitor 17", at first got great resolution...After reinstalling for another reason it will only display 800x600...I am also having this issue with Centos 5.4...

On the other hand works great with Windows 7 and Opensolaris--go figure..Any ideas how to fix it is very annoying...

---

### Post by bkline on 2010-01-07
> **sohaila said:**
> Do you mean xorg.conf (which seems to be missing from Karmic)?
Yes.  I'm running Karmic, and it wasn't missing on my system, but it was pretty well eviscerated, compared to what Ubuntu used to create.
> **sohaila said:**
> Can you please describe what you did to get it working?
I created a "Monitor" section:
```
Section "Monitor"
    Identifier     "Monitor0"
    Modeline       "1920x1200_60.00"  193.25  1920 2056 2256 2592  1200 1203 1209 1245 -hsync +vsync
    VendorName     "Unknown"
    ModelName      "CRT-0"
    HorizSync       24.0 - 80.0
    VertRefresh     56.0 - 75.0
    Option         "DPMS"
    Option         "PreferredMode" "1920x1200_60.00"
EndSection
```
and I added a "Display" subsection under the "Screen" section:
```
    SubSection     "Display"
        Depth       24
        Virtual     1920 1200
        Modes       "1920x1200"
    EndSubSection
```

---

### Post by bkline on 2010-01-07
> **grubdude said:**
> Any ideas how to fix it is very annoying...

See my response to Sohaila above.

---

### Post by bkline on 2010-01-07
I'm posting my complete xorg.conf, in case that helps anyone still floundering with this problem.  Oddly, I had to upload it as xorg.conf.txt, because this forum thinks "xorg.conf" is an invalid filename.  How silly is that?

---

### Post by grubdude on 2010-01-07
How would I adapt this to a monitor that does 1280x1024 maximum? Be gentle I am somewhat a newbie...can I apply the same to y centos 5.4 install?

---

### Post by bkline on 2010-01-07
> **grubdude said:**
> How would I adapt this to a monitor that does 1280x1024 maximum? Be gentle I am somewhat a newbie...can I apply the same to y centos 5.4 install?
What I did was to use [PowerStrip]("http://entechtaiwan.com/util/ps.shtm") booted into Windows (where the drivers knew about the monitor) and get the utility to give me the modeline information.  As I recall it was on a panel called "Advanced Timing" or something like that.  It'll give it to you (via the clipboard) in exactly the format needed by xorg.conf.  I'm off at a client site right now, so I don't have access to the machine, and this is off the top of my head.  As for CentOS, I've never used that distro, so you'll need someone else to help you there (and I'm no display expert myself, so I'm flailing around with Google as much as you are).  Good luck!

---

### Post by grubdude on 2010-01-07
Thanks and yes lots of flailing here too....not sure why both ubuntu and centos do this but opensolaris does not. You would think it would be even more fllakey than linux distros.:-)

---

### Post by bkline on 2010-01-07
> **grubdude said:**
> Thanks and yes lots of flailing here too....not sure why both ubuntu and centos do this but opensolaris does not. You would think it would be even more fllakey than linux distros.:-)

Well, it probably was while Ubuntu (et frères) were making progress in the area of user-friendly display support, and (I suspect) OpenSolaris was playing catch-up.  But now that Ubuntu seems to be moving backwards here it's much easier for other OS platforms to leapfrog past. :-)  I haven't worked on any flavor of Solaris for over ten years, though, so any comparisons I might make on where they stand now would be pure speculation.

---

### Post by sohaila on 2010-01-08
Thanks a lot for your help, and sorry I wasn't able to try your solution straight away (we've been a bit snowed in, and today was the best chance of getting the car dug out to go grocery shopping).

I had to modify the numbers to suit my laptop's display, and it looks like I probably made a mistake. I still get a 800x600 display, but 1024x768 is available in the Display Preferences drop down. But that doesn't change the screen resolution but does set a virtual screen size of 1024x768 which can be scrolled left/right and up/down in the 800x600 window.

Xorg.0.log may give some clues: it contains a message stating TRIDENT (0): Not using mode "1024x768_60.00" (hsync out of range)
followed by lots of messages starting "Not using" for various resolutions (including 1024x768 ) with reasons "hsync out of range" or "vrefresh out of range"

The modeline came from running cvt

My experience with Ubuntu started on 3 Jan 2010 so you can imagine I'm a little out of my depth here. Still, it feels like progress, and any other suggestions would be gratefully received. I've attached a copy of the xorg.conf file in case it helps.

I've just spotted in Xorg.0.log the line "TFT panel 1024x768 found", and hsync and vrefresh rates are also there.

---

### Post by bkline on 2010-01-08
#sohaila:

If you're able to dual boot into Windows, go back and read my reply to grubdude about using PowerStrip to find the numbers that work for your hardware.  Otherwise, you're going to need assistance from someone more knowledgeable about display hardware than me to track those numbers down (perhaps the manufacturer of the laptop?).

---

### Post by grubdude on 2010-01-09
Just seems like there must be something more elegant (read easier) to make this simpler for newbies....Very simple to accomplish under Centos.

---

### Post by bkline on 2010-01-09
> **grubdude said:**
> Just seems like there must be something more elegant (read easier) to make this simpler for newbies....Very simple to accomplish under Centos.

You mentioned earlier in this thread that you were having the same problem with CentOS.  I gather from this most recent comment that you found a solution.  Perhaps you could describe it here so that the folks coming up with a fix for the problem in Ubuntu can get some ideas about what works and what doesn't.

---

### Post by sohaila on 2010-01-10
I've managed to resolve my own problem from a post in another thread:
[http://ubuntuforums.org/showthread.php?t=763964&highlight=satellite+1800](http://ubuntuforums.org/showthread.php?t=763964&highlight=satellite+1800)
 - go to #63. I simply created a xorg.conf from the post and it worked on my laptop. So, highly recommended to anyone with a Tosh satellite laptop.

Thanks again to everyone who has helped.

---

