---
title: "Can't pick a res higher than 1360 x 768 with LG Flatron E2350V + Intel P35 Chipset"
date: 2011-04-15
forum: Installation &amp; Upgrades
---

### Post by somesoma on 2011-04-15
Hey there

I just recently installed Ubuntu 10.10 and I am new to Linux in general. While I'm all in all very happy (and surprised) with the user friendliness and overall fantastic desktop environment, I do have one problem that's bugging me:

I have an LG Flatron E2350V widescreen monitor that should enable me to pick resolutions higher than 1360x768. Both 1600x900 and 1920x1080 work flawlessly when I boot windows.

Going to System>Preferences>Monitors gives me this:

[IMG]http://i.imgur.com/WQ3Zy.png[/IMG]

Clicking "Detect monitors" does nothing at all.

As for my GFX card, it is part of the Intel P35 Chipset, so it's a mediocre onboard gfx chip. I'm guessing that's the problem instead of my monitor?

**lspci | grep VGA:**
00:02.0 VGA compatible controller: Intel Corporation 82G33/G31 Express Integrated Graphics Controller (rev 10)

**xrandr**:
Screen 0: minimum 320 x 200, current 1360 x 768, maximum 4096 x 4096
VGA1 connected 1360x768+0+0 (normal left inverted right x axis y axis) 0mm x 0mm
1360x768       59.8* 
1024x768       60.0  
800x600        60.3     56.2  
848x480        60.0  
640x480        59.9     59.9

**grep -i intel /var/log/Xorg.0.log:**
[http://pastebin.com/raw.php?i=LFa4d1Ln](http://pastebin.com/raw.php?i=LFa4d1Ln)

Any ideas what I can do? Any help would be much appreciated. :)

---

