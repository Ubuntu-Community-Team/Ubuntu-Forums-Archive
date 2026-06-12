---
title: "Ubuntu fails to load desktop/gnome (Frustrating)"
date: 2007-04-21
forum: Installation &amp; Upgrades
---

### Post by GButler on 2007-04-21
Wow, this has been a frustrating install. I'll admit, right from the get go, that I'm a Linux newb. I installed the OS onto my laptop so that I could use a better Hub running program than PtokaX called YnHub. My friend has been using Linux for years and recommended I use this distro, and even helped with the installation. We worked for a solid 6 hours on the thing, but it never panned out to a working circumstance.

The actual install of the OS (Feisty) seems to go fine. There was no hanging, there was no error messages, etc. Upon booting into the OS, though, it gets to the log-in screen, I put in the username and password, and then things go awry. The little splash screen that loads at Ubuntu's start comes up, the three little icons on the left begin to load, but they never load fully and remain watermarked for the remainder of the time that the splash screen is present. The little text reads Nautilus and never makes it to the restricted-manager text. (Sorry if this is confusing, but I'm trying to be as specific as possible). Then the splash screen, which appears to hang, disappears and the desktop tries to load. The wallpaper boots up, but the menus on the top and bottom of the screen either a) do not load at all, or b) do not have any buttons or text on them. The right-click function is also non-responsive. From here, the GUI is completely useless.

The Ctrl+Alt+F1 feature (I think it's called the terminal?) does not always work. Sometimes it will let me use the terminal (?), but sometimes it doesn't. If I try to Crtl+Alt+F7 out of the terminal, the area where the top menu bar is supposed to be goes black with little red crosses in it and has light blue squares interspersed into the mix randomly. Ctrl+Alt+Backspace DOES work, but any attempt to log back into the system takes me less far than the prior attempt in that, if attempted regardless of what session is chosen, the wallpaper does not load, nor any menu bar of any kind. 

If I boot into recovery mode, then the OS works fine...but I'd still like to be able to use the non-recovery mode...There is an error message which I assume is important: "Internal error - could not initiate HAL". I looked up information on HAL, and trying to remove it is warned against by the Ubuntu Synaptic Package Manager since it will also have to remove ubuntu-desktop. I assume the HAL refers to the hardware abstraction layer, and in my case it refers to an Atheros subject. Outside of that, I do not know what it means, or how to fix this error. The restricted drivers manager has the driver for HAL installed and enabled. 

To clarify: this isn't a dual-boot system. Only Ubuntu 7.04 is installed.

My system specs are: 
Mobile(R) Intel(R) Pentium 4 3.06GHz
1.4GB of RAM (I don't know the clock speed, sorry, and I don't know how to check that in Linux)
60GB HDD with 47.7 GB free
Linux Ubuntu 7.04 i386 version
ATI Mobility Radeon 9000 (I solved the problems relating to the out-dated drivers, so the OpenGL Desktop works fine)

The make of the laptop is a Toshiba Satellite
It has a 1280x900 resolution which appears to be fine on this desktop and not causing any trouble.

I don't know what other information I can provide, or what else I can do. Any help would be greatly appreciated, especially if it leads to the end of this problem. Is anyone else even experiencing this kind of an error?

---

### Post by GButler on 2007-04-21
Anyone? Any ideas?

---

### Post by GButler on 2007-04-22
Would reformatting using 6.10 and then upgrading maybe work?

---

### Post by rillip on 2007-04-22
Are you using the live CD to isntall?  If so, I'm guessing you didn't have these issues before, or you wouldn't have gone ahead.  I would recommend using the LiveCD of Dapper (6.06) and seeing how it boots before you give installing another try.  I've never seen an issue like this before, the only thing I can think of is a corrupt disk or install.

---

### Post by FishRCynic on 2007-04-22
see

[http://ubuntuforums.org/showthread.php?t=417819](http://ubuntuforums.org/showthread.php?t=417819)

i posted my answer there 
(hope it works for you)

---

