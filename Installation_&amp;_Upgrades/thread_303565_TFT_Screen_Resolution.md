---
title: "TFT Screen Resolution"
date: 2006-11-20
forum: Installation &amp; Upgrades
---

### Post by tjb001 on 2006-11-20
I am a Linux novice and have installed and been playing around with Ubuntu for a few weeks now. Having been using MS operating systems for many years it is a breath of fresh air!

Ubuntu is all installed and working OK on an older "test PC" I keep for messing around on. It is an AMD Athlon XP3000+ with an Nvidia FX5700 graphics card and Dell FP1907 19" TFT monitor.

My problem is with the monitor resolution at 1280 x 1024. In Windows is looks great especially with true type fonts and the clear type effects enhancements. But in Ubuntu it is OK at 1024 x 768 60Hz but when you move to 1280 x 1024 60 or 70Hz the fonts become blurred and ghosting appears and it generally looks poor. Is there anything I can do to resolve this or is it just a Linux xOrg anomaly?

Any help or advice would be greatly appreciated.

Thanks,
Tim.

---

### Post by ajgreeny on 2006-11-20
Is 1280 x 1024 your screen's internal resolution or should it be higher or lower?  What about antialiasing?  Seems odd I must agree, but can't suggest any other things to look at.

---

### Post by tjb001 on 2006-11-21
1280 x 1024 @ 60Hx is my TFT's optimal resolution.

I have seen this issue before with different TFT's and versions of Linux so it must be just that this OS is not too good with TFT screens. I tried an old CRT and the reolution was fine and as expected. Maybe it's just that Linux is not very good with TFT screens!

---

### Post by ajgreeny on 2006-11-21
No problem with mine. It worked OK after I changed monitor 18 months ago, and has not let me down once since then.

---

### Post by tjb001 on 2006-11-22
Would you be kind enough to share your settings and instructions you used to get the TFT working with me?

Thanks.

---

### Post by dcstar on 2006-11-22
> **tjb001 said:**
> ......
My problem is with the monitor resolution at 1280 x 1024. In Windows is looks great especially with true type fonts and the clear type effects enhancements. But in Ubuntu it is OK at 1024 x 768 60Hz but when you move to 1280 x 1024 60 or 70Hz the fonts become blurred and ghosting appears and it generally looks poor. Is there anything I can do to resolve this or is it just a Linux xOrg anomaly?

Any help or advice would be greatly appreciated.

Thanks,
Tim.

One assumes that you are able to do an "Auto" adjust after changing the settings?

---

### Post by ajgreeny on 2006-11-22
Happy to let you know my settings, but which ones?  I use Kubuntu, and have changed all sorts of things from the defaults, eg desktop fonts, but there are no problems even with the defaults of the system.  My screen is a Difusion P176 (no, I'd never heard of it either, but it is terrific) with an internal res of 1280 x 1024, which is the same as the CRT I used before, and I didn't need to make any changes to anything to get the new TFT to work exactly as I wanted.  However I attach my xorg.conf for you to look at and see if it helps you sort your problem.

By the way, could it be a problem with your graphics driver?  I have an ATI Radeon 9200SE which runs the driver setup when I installed Ubuntu originally.  I have tried to add fglrx on another test partition installation of ubuntu that I use just to test things out, but had no luck at all so have stuck with the original on my work install.

Hope something in this post helps, but it all seems a bit strange to me.

---

