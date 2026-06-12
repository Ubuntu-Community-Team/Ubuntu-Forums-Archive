---
title: "Installing Ubuntu for the first time"
date: 2007-10-20
forum: Installation &amp; Upgrades
---

### Post by blackterror on 2007-10-20
Hello all,

I've just downloaded the newest version of Ubuntu and I'm trying to setup a dual boot of WinXP on my laptop and Ubuntu. After burning the ISO, I've modified my boot sequence and ran from CD. I get the Dos like messages followed by the OK messages. Once the installer loads, I hear the sound play, but my display doesn't show correctly. I get a series of brown horizontal lines all over the screen. Is there any documentation that might help me. My first thought is a graphics card support issue. I have a HP laptop AMD 3200, 1 GB ram with an unallocated 40Gb hd space on an 80gb drive. Any help is appreciated to this complete noob to Linux/Ubuntu. Thanks!


Terror.

---

### Post by Offoffoff on 2007-10-20
Try to Safe Mode install. This may help You. Dual boot? Are You ready for that?

---

### Post by rex_the_first on 2007-10-20
So you changed your boot sequence so CD was before HDDs.  Can you get to the CD-Check part of the installation or are there errors before that?  The first screen that loads should be able to do so an any graphics card.

---

### Post by blackterror on 2007-10-20
thanks for the help. these things are so obvious after you've got them figured out. i went in via graphics safe mode and installed. Went fine. Had a heck of a time with my wireless card driver but finally got that running. Now am having issues with the graphics card still. Ive been reading through countless threads on the nvidia drivers setup. Downloaded the correct legacy driver (GeForce 440) and installed using the correct sudo commands after shutting down the X server. The install goes great except when I restart, I get a message saying Ubuntu is loaded in graphics safe mode because the hardware could not be detected and you need to manually configure. I choose the correct nvidia driver from the list, but it doesnt help once Ubuntu gdm loads correctly. My only option to have 1280x800 support is to disable the nvidia-glx package, but it tells me I won't be able to run any graphics package or desktop effects. When it is enabled, it boots me back to 800x600 with no graphics accelleration support...sigh.:confused:

---

