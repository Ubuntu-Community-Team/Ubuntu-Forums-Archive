---
title: "randy"
date: 2008-03-03
forum: Installation &amp; Upgrades
---

### Post by Randy Matheson on 2008-03-03
hi!  I'm a happy gutsy gibbon user for 6 months now! However, I've hit a roadblock when I upgraded my video card from an ATI Radeon 128 meg card to a Radeon X1600 Pro.  First I hoped it would autodetect and accept it, but it didn't.  Then I decided to do a fresh install. This went well until I accepted the option to install a restricted driver. Upon reboot, I was unable to get past the first ubuntu screen at the beginning of the loader. 

 From there I went to the forum and was given the instructions to try 'sudo dpkg-reconfigure-phigh xserver-xorg'.  this brought me to a dialogue box of choices for manufacturers. I scrolled up to ATI and pressed enter, the OS loaded to the desktop, but it didn't detect my video and it gave me the options of 2 very low resolutions (800x600 and one lower).  

The next instruction from the forum was the command 'sudo dpkg-reconfigure xserver-xorg' which brought me to a process that I don' t quite understand.

I'm in love with gutsy gibbon! I don't want to go to another distro!

can you help me through this mess?

thanks

RandyM

obtw - how do you thank the ones who help you ... is there a special button or somthing?

---

### Post by dstew on 2008-03-03
> The next instruction from the forum was the command 'sudo dpkg-reconfigure xserver-xorg' which brought me to a process that I don' t quite understand.At this point, that is your only way out. I would recommend doing that, and using the vesa driver just to get your display back.

After that, you can try to install the driver again. [Here]("http://packages.ubuntu.com/gutsy/xserver-xorg-video-radeonhd") is a gutsy package that may work for you.

---

