---
title: "Unable to install because of Screen Resolution"
date: 2007-05-21
forum: Installation &amp; Upgrades
---

### Post by kernel89 on 2007-05-21
I can't seem to install anything, for I am a newbie and I do not know the concept of the installation. And to top it all off, I have a 800x600 Resolution that I can't increase because it's the maximum, and that causes me to miss the lower part of the installing window, and I can't seem to resize that window either....Very irritating, I can't seem to proceed with this little annoyance....Is there a way to reduce the color quality and make the resolution a little bigger so I can't view the installation window and proceed to my installation?

BTW. I'm installing Ubuntu 7.04 i386

Thanks in advance

---

### Post by kernel89 on 2007-05-21
Never mind my issue, I simply went on safe graphics mode in the booting screen, and the resolution was fine.

Thanks anyways.

---

### Post by stereo3D on 2007-05-21
I had the same problem. Of course the installation GUI was designed for 1024x768 yet the OS defaults to 800x600 on install before the video driver is setup. Duh! Then since you don't know the OS you can't navigate through the GUI. I eventually discovered that you can grab and move the dialog boxes, the secret (IIRC) is, Alt-RMB (Alt key plus right mouse button). That is from memory, but some combination, perhaps Alt-CMB. Once you are able to move the dialog box you will find a "next" or "forward" button. 

Best;)

---

### Post by Wherdgo on 2007-05-31
> **stereo3D said:**
> I had the same problem. Of course the installation GUI was designed for 1024x768 yet the OS defaults to 800x600 on install before the video driver is setup. Duh! Then since you don't know the OS you can't navigate through the GUI. I eventually discovered that you can grab and move the dialog boxes, the secret (IIRC) is, Alt-RMB (Alt key plus right mouse button). That is from memory, but some combination, perhaps Alt-CMB. Once you are able to move the dialog box you will find a "next" or "forward" button. 
Best;)

Yep, I had the same stupid resolution problem in [http://ubuntuforums.org/showthread.php?t=456835&highlight=resolution](http://ubuntuforums.org/showthread.php?t=456835&highlight=resolution)  I'll try your workaround, thanks for the tip.

---

### Post by Wherdgo on 2007-05-31
I tried setting the resolution before install, no joy.  I tried installing in safe mode, no joy.

However the Alt-LMB (Alt key plus Left mouse button) trick did work for me, and allow me to move the dialog boxes around enough to see and execute the correct buttons.  Note that for me, I had to use the left button, and not the right. 

Also, just an aside, this glaring gaffe doesn't seem too particularly smart of a design decision choice by the engineers.  I expected better from really smart people who'd like to make some market share inroads on M$.  Making it tough for the masses to install your product sure ain't the answer. 

If this was designed to have inflexible dialog boxes larger than the lowest common denominator resolution, then it's just plain stupid. There are mistakes, oversights, bugs, and stupidity. This one is in the latter if by design. At the VERY least Q/A should have caught this basic gem (at install?!?) setting up some older systems, eh?

---

### Post by Wherdgo on 2007-06-06
This is a known bug by the devs: [https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/38442](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/38442)

---

