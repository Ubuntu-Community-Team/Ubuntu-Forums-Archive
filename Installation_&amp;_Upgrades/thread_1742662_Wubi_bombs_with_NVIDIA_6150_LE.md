---
title: "Wubi bombs with NVIDIA 6150 LE"
date: 2011-04-29
forum: Installation &amp; Upgrades
---

### Post by Zepp Jamieson on 2011-04-29
I'm on an AMD Athlon 64X2 (3800) running an NVIDIA 6150 LE video card.  I was aware of the problems with 10.04 and 10.11, and hoped Narwhal would address them.

Instead, I can't even load the Demo from the Live CD.  64 bit snow crashes the screen, leaving nothing but blue and white bands, and 32 bit just has a dark screen and cycles endlessly.

What's available to address this?:confused:

---

### Post by dino99 on 2011-04-29
sadly this bug is not fixed:

[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-nouveau/+bug/712280](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-nouveau/+bug/712280)

the solution is to use "nouveau" only: deinstall nvidia-current

---

### Post by whokilledsanta on 2011-05-17
Hi, I'm new to ubuntu (and new to Linux - I came from Windows7) and I have a very similar problem with my Nvidia 6150LE graphics card. I can run ubuntu, but I can't use desktop animation (there is no option for it in display/desktop properties). When I got to 'Additional Drivers' it says that the proprietary recommended driver is 'installed but not in use'. I do have the Nvidia Server application available in settings.
 
The only reason I have changed to ubuntu from Windows7 is because I liked the workspace cube features that some of my friends have on their ubuntu systems. I can't use this feature because of these graphics card driver issues that are still unresolved.
 
It is very frustrating and I am considering going back to Windows so that I can play movies full screen and use the graphics card to its potential... Before I do go back to Windows7, I was wondering if somebody might have some advice as to an alternative? Would Linux Mint or Fedora support the card? Is it related to Compiz? Is there an alternative to Compiz that will work on ubuntu? Is it Beryl? I tried to uninstall Compiz and it resulted in me having a blank ubuntu home screen with no menus - so I couldn't figure out how to reinstall Compiz or install Beryl - I had to reinstall ubuntu but it still does not use the driver.

---

