---
title: "NVidia Resolution Workaround"
date: 2009-11-14
forum: Installation &amp; Upgrades
---

### Post by oldefoxx on 2009-11-14
I like NVidia myself, but the present a bit of a challenge with Ubuntu, at least since version 7.10. as this bug report shows:

[https://bugs.launchpad.net/ubuntu/+source/nvidia-settings/+bug/362704](https://bugs.launchpad.net/ubuntu/+source/nvidia-settings/+bug/362704)

Fact is. with version 8.04, I had to find the right NVidia driver myself, install it, then after getting the NVidia toolbox up to set the desired resoluton, face the fact that my settings would not take in /etc/X11/xorg.conf because for some silly reason, it said it could not write to /etc/X11/xorg.conf.backup, even though there was no existing file by that name.  Doing a cp from xorg,conf to xorg,conf,backup did not help either.  I finally just had to edit the xorg.conf file manually and dicker with it until I got the setting I wanted to take during bootups.

Guess what?  Ubuntu 9.10 shows the same problem, so I wanted to work around it.  And this is what I've learned so far.

If you first go under System/Administration/Software Sources, you have a chance to turn on things like 3rd party sources.  This would mean that the Update Manager would now be free to probe for some of the restricted (not supported by Ubuntu directly) software, and then I could get the NVidia drivers via the Update Manager.  That saved a tussle with getting them myself from the NVidia website.

With the install of the NVidia driver, and going through System/Preferences/Display, you now get Ubuntu wanting to know if you want to use the provided toolbox instead.  Of course you do, but then after moving the resolution setting from Auto (highest setting possible) to what you want and applying it, you find you can't save it.  Did I have to edit the /etc/xorg.conf file again myself?

Actually, no.  The bug report above gave me a clue about what might be happening, so I returned to /System/Preferences/Display and this time said "no" to using the toolbox for NVidia.  Then I picked the resolution I wanted, applied it, told it to keep it, went through System/Preferences/Display again, elected to use the toolbox with a "Yes", and found that the NVidia driver was already set now to the same setting.  And it kept on the next reboot.  I figured this might be a help to some others.

Workarounds aren't a cure, but they are good to have when they work.

---

### Post by Arup on 2009-11-14
You have to do a gksudo nvidia-settings and then select your resolution and save to X, I do it like that for my 21" SONY CRT and it works out everytime with every Ubuntu distro.

---

### Post by monton on 2009-11-14
That worked for me too. Set the refresh rate in Ubuntu and saved it. Now when I go to the nvidia panel it has the correct refresh rate.

Thanks for the tip

BTW I didn't think it would work because it changed on me before. I think it was because I went to nvidia after setting up under Display and made changes. I think it caused the refresh rate to revert after reboot. Anyway, works now.... and that is what counts!
Thanks
M

---

