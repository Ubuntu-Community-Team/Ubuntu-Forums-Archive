---
title: "Installation of 11.4 - video problem.  ASUS."
date: 2011-05-15
forum: Installation &amp; Upgrades
---

### Post by youngryand on 2011-05-15
I am trying to install 11.4 over a Windows 7 installation.  The computer is an ASUS motherboard, ASUS graphics card and ASUS monitor.  The computer is four years old and the monitor is one.  The monitor native res is 1920 x 1020.  To be honest, I often have problems with the graphics driver crashing after a screensaver "reawakening" and it's actually my primary motivation to stop procrastinating the move to Ubuntu.  I also have intermittent other little issues with the graphics.  t is possible that I just have a fundamental hardware problem, but I don't think so because the graphics issues started happening with the upgrade from XP to 7.  Windows chooses a Generic PnP driver for the monitor and I've been unable to find any actualy manufacturer's driver for this monitor.  It's an ASUS VW246H.

Below is what I experience when I attempt to install Ubuntu 11.4 with a freshly burned boot CD from an .iso.  This should explain why I suspect it's a video card or monitor or related driver problem.

I let the installation CD boot:

**If I do nothing:**
Things seem to go well, Ubuntu 11.4 displays and progress lights blink.  Eventually the monitor switches resolutions (it seems) and the screen goes black except for a very large cursor (due to apparently relatively low res) that seems to be made up of random colored pixels.  Imagine a roughly 50px by 50px cursor with only about 5% of the pixels filled.  A random disparate splattering.  I can move the cursor using the mouse but am apparently unable to click any potentially "invisible" controls, etc...  No keys seem to help at this point--I have to reboot.

**If I hit Alt-F2 during the very beginning of installation:**
I am given an option of "Try Ubuntu," "Install Ubuntu," etc...  I have an option to change boot parameters below before selecting any given option.  I have tried running the install from the point w/ and w/out the fb=false boot parameter because I read that certain native resolutions will create a graphics problem related to "frame buffering" and to specify fb=false.  I'm not sure if I"m specifying the parameter correctly.  The end of the string ends with -- but I delete the -- and replace it with fb=false.  Nowhere have I been able to find documentation on how to syntactically enter boot parameters.

**Side note**
Using either of the above methods, sometimes (about 50% of the time) I receive a scrolling list of output that lists various tests and their results.  100% of the time I get this output, I see what I think is (it's very fast and hard to read before it disappears) "Graphics Fallback Driver [load?]         ...    [failure]"

Help please!  I consider myself pretty savvy and I work in IT / software, using Linux daily (command shell only) so I should be able to take instruction relatively well.  I initially thought I could figure this out myself, but I've spent at least a few hours on this already, and feel I could dwell on this small issue for quite a while to no avail.  I'm hoping someone has some direct experience with this problem and/or a solution that may cover this problem.

Thank You,
Ryan

---

### Post by MAFoElffen on 2011-05-15
> **youngryand said:**
> I am trying to install 11.4 over a Windows 7 installation.  The computer is an ASUS motherboard, ASUS graphics card and ASUS monitor.  The computer is four years old and the monitor is one.  The monitor native res is 1920 x 1020.  To be honest, I often have problems with the graphics driver crashing after a screensaver "reawakening" and it's actually my primary motivation to stop procrastinating the move to Ubuntu.  I also have intermittent other little issues with the graphics.  t is possible that I just have a fundamental hardware problem, but I don't think so because the graphics issues started happening with the upgrade from XP to 7.  Windows chooses a Generic PnP driver for the monitor and I've been unable to find any actualy manufacturer's driver for this monitor.  It's an ASUS VW246H.

Below is what I experience when I attempt to install Ubuntu 11.4 with a freshly burned boot CD from an .iso.  This should explain why I suspect it's a video card or monitor or related driver problem.

I let the installation CD boot:

**If I do nothing:**
Things seem to go well, Ubuntu 11.4 displays and progress lights blink.  Eventually the monitor switches resolutions (it seems) and the screen goes black except for a very large cursor (due to apparently relatively low res) that seems to be made up of random colored pixels.  Imagine a roughly 50px by 50px cursor with only about 5% of the pixels filled.  A random disparate splattering.  I can move the cursor using the mouse but am apparently unable to click any potentially "invisible" controls, etc...  No keys seem to help at this point--I have to reboot.

**If I hit Alt-F2 during the very beginning of installation:**
I am given an option of "Try Ubuntu," "Install Ubuntu," etc...  I have an option to change boot parameters below before selecting any given option.  I have tried running the install from the point w/ and w/out the fb=false boot parameter because I read that certain native resolutions will create a graphics problem related to "frame buffering" and to specify fb=false.  I'm not sure if I"m specifying the parameter correctly.  The end of the string ends with -- but I delete the -- and replace it with fb=false.  Nowhere have I been able to find documentation on how to syntactically enter boot parameters.

**Side note**
Using either of the above methods, sometimes (about 50% of the time) I receive a scrolling list of output that lists various tests and their results.  100% of the time I get this output, I see what I think is (it's very fast and hard to read before it disappears) "Graphics Fallback Driver [load?]         ...    [failure]"

Help please!  I consider myself pretty savvy and I work in IT / software, using Linux daily (command shell only) so I should be able to take instruction relatively well.  I initially thought I could figure this out myself, but I've spent at least a few hours on this already, and feel I could dwell on this small issue for quite a while to no avail.  I'm hoping someone has some direct experience with this problem and/or a solution that may cover this problem.

Thank You,
Ryan
First question is: What are you trying to accomplish?  I see you are trying to install Ubuntu, but can you successfully run Ubuntu from a LiveCD?

Successfully doing this would tell you a lot of things you will need to install Ubuntu, especially if you have non-standard graphics.

Please refer to this sticky
[http://ubuntuforums.org/showthread.php?t=1743535](http://ubuntuforums.org/showthread.php?t=1743535)
And follow the instructions in post 3 for instructions on booting up a LiveCD.  Being able to boot that LiveCD into a desktop or not... Will tell us where to direct you from there.

If you can boot it, download and install hwinfo, using
```

sudo apt-get install hwinfo

```Then from a terminal get and post the results of 
```

sudo hwinfo --framebuffer
sudo hwinfo --monitor

```Which will tell us the supported modes of your video card and monitor as it's seen by linux.

From that info or the failure to get that far, we could go from there.

---

### Post by youngryand on 2011-05-16
Thank you for the prompt and thorough reply.  I'm sorry I wasn't more clear.  I cannot boot from the CD into Live or install mode.  Results are exactly the same as far as I can tell.

I'll try some more experiments with boot parameters.  I also suspect I may get this to work if I can borrow someone else's monitor for the install period.  I often get the feeling this one is cursed.  It and Windows 7 both came to me around the same time.  It feels like one of them is to blame.

I welcome any advice and will try your suggestions.

Ryan


Small change:  Perhaps I misunderstood--it looks like there are some steps in the article you posted pertaining to the grub menu / rescue mode that I need to try first, and will (right now).

---

### Post by MAFoElffen on 2011-05-16
> **youngryand said:**
> Thank you for the prompt and thorough reply.  I'm sorry I wasn't more clear.  I cannot boot from the CD into Live or install mode.  Results are exactly the same as far as I can tell.

I'll try some more experiments with boot parameters.  I also suspect I may get this to work if I can borrow someone else's monitor for the install period.  I often get the feeling this one is cursed.  It and Windows 7 both came to me around the same time.  It feels like one of them is to blame.

I welcome any advice and will try your suggestions.

Ryan


Small change:  Perhaps I misunderstood--it looks like there are some steps in the article you posted pertaining to the grub menu / rescue mode that I need to try first, and will (right now).In post 3 of that is instructions on trying diffrent modes to boott a LiveCD.

---

### Post by youngryand on 2011-05-17
Thanks for all of your help.  The CD I had did not seem to have a way to break into the shell even using the instructions.  Therefore, I tried downloading the text-only/alternate installer and decided I should go with x64 this time since I can support it.

I somehow ended up with an .iso of the x64 bit graphical version instead and thought I was back again in the same boat-again, no way to break into the shell.  However, for some reason the x64 version worked beautifully the first time.  I've installed it on two of my drives (using it now), and am customizing.  Love it.  Never going back.  My laptop will be next.

Ryan

---

### Post by MAFoElffen on 2011-05-17
> **youngryand said:**
> Thanks for all of your help.  The CD I had did not seem to have a way to break into the shell even using the instructions.  Therefore, I tried downloading the text-only/alternate installer and decided I should go with x64 this time since I can support it.

I somehow ended up with an .iso of the x64 bit graphical version instead and thought I was back again in the same boat-again, no way to break into the shell.  However, for some reason the x64 version worked beautifully the first time.  I've installed it on two of my drives (using it now), and am customizing.  Love it.  Never going back.  My laptop will be next.

Ryan
Congrats!

Since you started this thread- If solved, please use the Forum Thread Tools to mark this thread as "solved"

---

