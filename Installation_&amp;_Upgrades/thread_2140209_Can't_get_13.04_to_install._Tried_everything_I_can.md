---
title: "Can't get 13.04 to install. Tried everything I can think of"
date: 2013-04-29
forum: Installation &amp; Upgrades
---

### Post by CoolBreeze47 on 2013-04-29
Hi everyone.

First of all...

My PC: Inspiron 2200 laptop
Graphics card: integrated Intel chip
Trying to install: Ubuntu 13.04

I have been using 12.10 since it was first released and have experienced no issues with it whatsoever. However, I was unable to install 13.04. Once I got past the screen that asked if I would like to download updates while installing and download restricted drivers (ie; the boxes that can be ticked), it would cook for a few minutes and then a black screen with "modprobe tainted" and a lot of hexidecimal addresses would appear.

So, I tried it with both of these boxes un-ticked and it installed just fine but since I didin't tick the boxes, no drivers were installed and so the computer was very slow and the graphics were completely screwed up (weird colors, quad screens, dock/menu missing, etc).

Next, I tried to install with "nomodeset" selected and it would go so far and then stop at "configuring bcmwl-kernel-source" so I figured it was my Broadcom wireless modem. So, I tried once again but this time I blacklisted it in the kernel parameters just like I had to do in 12.04 (ie; b43.blacklist=yes) and it got half-way through the install and yet again, stopped at "configuring bcmwl-kernel-source".

I'm not sure what to do at this point. I've tried everything I can think of. I even tried a fresh install of 12.10 and then upgraded that to 13.04 and got all kind of weird graphics stuff again.

I even tried installing 13.04 on a much newer PC with an Nvidia card and had pretty much the same issues even though I could see that the nouveau drivers were installed and worked just fine when I was using 12.10. A friend of mine also installed 13.04 on his PC and had issues. I'd love to stick with 12.10 but I have to think about it's end-of-life and I really don't want to use the LTS version. A new PC, new graphics card, etc are not possible and I've never had any issues with my current graphics card on this PC with any of the other versions of Ubuntu. What are my options and is there anything you folks can suggest?.

Thanks so much for your time and assistance. It is really appreciated.

---

### Post by grahammechanical on 2013-04-29
Back in the days of 12.04 if a machine lacked the specification to run Ubuntu 3D then Unity 2D was installed. With 13.04 we get something called llvmpipe. It is an attempt to give a standard Unity experience even on low specification machines.

[http://www.mesa3d.org/llvmpipe.html](http://www.mesa3d.org/llvmpipe.html)

By using nomodeset we load with llvmpipe. By using Recovery Mode>Resume we get llvmpipe. We used to get Nouveau open source driver but now we get llvmpipe. This is my guess as to why we get these slow graphics and other stuff when we load 13.04 without a video driver.

It is possible to install both the restricted extras and a video driver after installation. That is my standard practice because proprietary video drivers get installed with third party software and I have experienced issues with proprietary video drivers.

Upgrades often require the re-installation of video drivers. With an upgrade we get later Linux kernels and they require the appropriate later video drivers. If you open System Settings>Software & Updates you will see that the Additional Drivers tab will offer several video drivers. You will need to experiment. The last time I tried this with 13.04 and my Nvidia GT 220 I gave up trying after the top three Nvidia drivers broke the desktop in some way.

So, if you get to a desktop without the top panel or the laucher, then right click the desktop and select Change Desktop Background and that will open System Settings and get you back to software & Updates and the Additional Drivers tab.

Regards.

---

### Post by CoolBreeze47 on 2013-04-30
I just wanted to pop in and thank you for your very detailed and helpful response. I followed your suggestion for the Nvidia card and everything is working perfectly now on the second computer. The only problem now is getting 13.04 installed on the Inspiron 2200 (my main computer) with an Intel graphics card. Unlike with Nvidia, it doesn't look like there is a selection of drivers that can be installed from the menu you mentioned. In fact, there isn't anything at all listed. I thought Intel drivers were just installed automatically (which is what usually happens). Anyone have any suggestions on how to get this to work (per my original post)?. Thanks again for your help!.

---

