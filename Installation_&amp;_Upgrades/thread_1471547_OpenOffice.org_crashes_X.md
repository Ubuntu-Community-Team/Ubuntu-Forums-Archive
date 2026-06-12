---
title: "OpenOffice.org crashes X"
date: 2010-05-03
forum: Installation &amp; Upgrades
---

### Post by MeanEYE on 2010-05-03
This stopped being funny after first time it happened to me. First of all, it's really stupid to remove OpenOffice from the system and continue to brag about it. Installation is not as straight forward as one would think.

I did a clean install of Ubuntu Lucid 32bit. Now every time I try to start any tool from OpenOffice, my screen goes blank and system crashes. 

I tried removing, purging, clearing all the configuration stuff. I've even tried with different JREs and nothing helped. Am thinking it could be a problem with fonts cache or something similar as I can't really see why would OpenOffice crash X when Java runs just fine. And this is really strange, I did the same thing on my laptop, and everything works... No problems what so ever...

Anyone has any ideas or similar experiences to share?

---

### Post by MeanEYE on 2010-05-03
Now am even more sure that problem resides with fonts or something related with font rendering.

If I enable font smoothing with winetricks same thing happens.

Anyone?

I tried clearing font cache with fc-cache... :/ no result

---

### Post by MeanEYE on 2010-05-04
*Bump*

---

### Post by MeanEYE on 2010-05-04
Ok, am gonna continue writing here in case some poor soul runs into same problems as I do.

I've narrowed problem down to font rendering. If Ubuntu has font anti-aliasing turned on and you start any other non-gtk application which tries to render anti-aliased font system crashes.

After I turned font rendering off in System->Preferences->Appearance those programs (OpenOffice, IDLE and Wine) are working well without any glitches.

Edit: Turns out, only if I select SubPixel Smoothing X crashes :/

---

### Post by &#304;skender on 2010-05-25
I get exactly the same problem - if I enable subpixel smoothing in System->Preferences->Appearance then starting OpenOffice or BOUML causes the screen to go black, the monitor to repeatedly turn on and off and the system to crash. 

With subpixel smoothing off then everything's fine, except that the fonts look horrible.

---

### Post by MeanEYE on 2010-05-25
> **&#304 said:**
> I get exactly the same problem - if I enable subpixel smoothing in System->Preferences->Appearance then starting OpenOffice or BOUML causes the screen to go black, the monitor to repeatedly turn on and off and the system to crash. 

With subpixel smoothing off then everything's fine, except that the fonts look horrible.

Can you tell me which graphic card you have and what Ubuntu version is installed. The case with me is On-board nVidia 6150 on Ubuntu 32bit. It's really funny to note that I had the same problem after 2 clean installs.

---

### Post by ckop64 on 2010-05-25
Hi. Maybe posting the system specs would be helpful. I didn't have such errors while I was using Ubuntu. (Now I'm using Xubuntu btw.)

---

### Post by Hagar Delest on 2010-05-25
Have you tried with the Sun version? See [[Ubuntu] Installing OOo on Debian and Co.](http://user.services.openoffice.org/en/forum/viewtopic.php?f=16&t=68)

---

### Post by MeanEYE on 2010-05-25
> **Hagar de l'Est said:**
> Have you tried with the Sun version? See [[Ubuntu] Installing OOo on Debian and Co.](http://user.services.openoffice.org/en/forum/viewtopic.php?f=16&t=68)

Hi, thank you for your interest. Unfortunately problem is not with OpenOffice itself but rather with font smoothing that OO (Java) uses. My X crashed even when I tried running IDLE which has nothing to do with Java or OO.

---

### Post by &#304;skender on 2010-05-26
My graphics card is an nVidia GeForce Go 7400, and I have just upgraded from Ubuntu 9.10 to 10.04 (32 bit) - this issue did not occur in 9.10.

---

### Post by MeanEYE on 2010-05-30
Ok, I've found another reason. If you turn off compiz and enable sub-pixel smoothing. Everything works. So I think compiz is the one to blame.

---

### Post by MeanEYE on 2010-05-30
I need to work more on this... I'll let you know what I've found out!

Edit:
Well in the end... (until Compiz bug is fixed)... I decided to keep Compiz, turn off font smoothing in OpenOffice (in Options->View->System font smoothing) and to stop using IDLE.

If someone finds a solution... please post it!

---

### Post by Piraja on 2010-06-01
Thanks for this thread and for trying to narrow the problem down. I cannot be of much help, I'm afraid, but I can tell the following:

1. I'm using CrunchBang 9.04 (based on Ubuntu Jaunty) 32-bit on an HP 6735S laptop, with OpenOffice.org 1:3.0.1-9ubuntu3.2. WM: Openbox, neither Compiz nor any other compositing stuff (such as xcompmgr) in use.

2. OOo Writer makes X crash when I try to open a file from the file manager (PCManFM in my case) via the right-click menu ("Open with...")...

3. ... but the crash doesn't seem to occur if I open OOo e.g. from the applications menu or via the terminal and, only after that, open a file from within OOWriter.

4. This is a relatively recent problem. The kernel in question is as old as 2.6.28-18 and this does not occur on another machine (with #! 10 alpha based on Debian Squeeze). 

5. I will try turning off sub-pixel smoothing and see if I can reproduce the crash...

I don't know what other information I should give for hints.*

*) Oops, this part of hwinfo output of course:
> Hardware Class: graphics card
  Model: "ATI RS780M/RS780MN [Radeon HD 3200 Graphics]"
No restricted driver in use.

Hmm... By the way, I don't remember how to turn off font smoothing in Openbox...

---

### Post by &#304;skender on 2010-06-02
I don't seem to get the problem if I use version 173 of the nvidia restricted drivers (rather than the 'recommended' version) - with compiz and sub-pixel smoothing enabled, openoffice does not crash. If I revert to the recommended restricted driver then openoffice does crash.

---

### Post by MeanEYE on 2010-06-02
> **Piraja said:**
> Thanks for this thread and for trying to narrow the problem down. I cannot be of much help, I'm afraid, but I can tell the following:

1. I'm using CrunchBang 9.04 (based on Ubuntu Jaunty) 32-bit on an HP 6735S laptop, with OpenOffice.org 1:3.0.1-9ubuntu3.2. WM: Openbox, neither Compiz nor any other compositing stuff (such as xcompmgr) in use.

2. OOo Writer makes X crash when I try to open a file from the file manager (PCManFM in my case) via the right-click menu ("Open with...")...

3. ... but the crash doesn't seem to occur if I open OOo e.g. from the applications menu or via the terminal and, only after that, open a file from within OOWriter.

4. This is a relatively recent problem. The kernel in question is as old as 2.6.28-18 and this does not occur on another machine (with #! 10 alpha based on Debian Squeeze). 

5. I will try turning off sub-pixel smoothing and see if I can reproduce the crash...

I don't know what other information I should give for hints.*

*) Oops, this part of hwinfo output of course:

No restricted driver in use.

Hmm... By the way, I don't remember how to turn off font smoothing in Openbox...
I don't think you have same problem as we do. In my case X crashed the moment some fonts were displayed, meaning when open office main windows is displayed. In my case it's not even an X crash, my whole system stops responding. So debugging was a bit hard.

---

### Post by MeanEYE on 2010-06-02
> **&#304 said:**
> I don't seem to get the problem if I use version 173 of the nvidia restricted drivers (rather than the 'recommended' version) - with compiz and sub-pixel smoothing enabled, openoffice does not crash. If I revert to the recommended restricted driver then openoffice does crash.

Oh, I didn't think of that. I never thought that nVidia was to blame. At least we know how to handle the problem now. Although I've killed OpenOffice.

Edit: I tried using version 173 but there's a noticeable performance degradation. I get 40-60 frames less in compiz benchmark. I'd rather look at ugly office once a month than use a slow system 16h a day :)

---

