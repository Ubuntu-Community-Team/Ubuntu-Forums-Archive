---
title: "Pease please help!"
date: 2007-12-19
forum: Installation &amp; Upgrades
---

### Post by manchu99 on 2007-12-19
I want to switch my desktop over to linux. BUt i have found that I can't boot or install any version of linux. Live cd's stall and hang at the point where it switches from verbose mode to the desktop. When i try to install with a text based installer, everythign installs, but when i go to restart into the new system, it too hang just short of loading the login screen.. it will show the splash screen but stop at login. I have tried ubuntu, kubuntu, xubuntu, puppy linux, DSL, and PClinuxOS. what do i do. it is an hp pavillion xt953. its 1ghz P3, 256 ram, 30 gig hard drive

---

### Post by manchu99 on 2007-12-19
I want to switch my desktop over to linux. BUt i have found that I can't boot or install any version of linux. Live cd's stall and hang at the point where it switches from verbose mode to the desktop. When i try to install with a text based installer, everythign installs, but when i go to restart into the new system, it too hang just short of loading the login screen.. it will show the splash screen but stop at login. I have tried ubuntu, kubuntu, xubuntu, puppy linux, DSL, and PClinuxOS. what do i do. it is an hp pavillion xt953. its 1ghz P3, 256 ram, 30 gig hard drive

---

### Post by rsambuca on 2007-12-19
You might try disabling the splash at boot to see where the errors are occuring.  Usually things like this are hardware problems, likely your video card.  What card are you using?

---

### Post by Lesouteneur on 2007-12-19
Your system is way too old. Was it like a windows 95? There are linux distros small enough but if youre thinking the mainstream distros, even Xubuntu, youre going to have to go even lighter than that. Check distrowatch, in the advanced search to help you find a light enough version.

---

### Post by reckless2k2 on 2007-12-19
Lesouteneur is on point to a certain degree. DSL should have worked just fine for you but it sounds like you might have a video ram issue and that's why a GUI won't start. there are a few parameters you can run at boot to fix this. you will not be able to use ubuntu or it's variants. 

i have run DSL and Vector on much lower specs than that without much issue. 

you might need to boot using "noacpi" or "vesa". each distro has a different code to use. try the boot help.

---

### Post by SyL on 2007-12-19
not user this HP box is supported [https://wiki.ubuntu.com/HardwareSupportMachinesDesktopsHp]("https://wiki.ubuntu.com/HardwareSupportMachinesDesktopsHp")

On such HP desktop the video card must be quite unusual ...

---

### Post by reckless2k2 on 2007-12-19
you are asking the same question in 2 places. please be kind.

---

### Post by hangfire on 2007-12-19
> **manchu99 said:**
> I want to switch my desktop over to linux. BUt i have found that I can't boot or install any version of linux. Live cd's stall and hang at the point where it switches from verbose mode to the desktop. When i try to install with a text based installer, everythign installs, but when i go to restart into the new system, it too hang just short of loading the login screen.. it will show the splash screen but stop at login. I have tried ubuntu, kubuntu, xubuntu, puppy linux, DSL, and PClinuxOS. what do i do. it is an hp pavillion xt953. its 1ghz P3, 256 ram, 30 gig hard drive

I've recently had similar problems that I narrowed down have having a Hitachi/Lucky/Goldstar GCC-4482B drive. It simply does not like later ISOLINUX formats, and will hang up anywhere between GRUB (the beginning) and the fifth install CD.

This was with multiple distro's on a dozen identical machines, all with this blased Cd/DVD drive. I found I could solve ALL my problems by switching to a NEC CD/DVD drive.

That being said, it sounds like you have a video card that autorecognizes incorrectly, or a common video mode that it or your monitor cannot handle. I would look at the Distro install instructions and look for options to limit force the VGA mode, limit the resolution to 800x600x60Hz.

Also, once booted to a blank screen, most Distro's will allow you to do Ctrl-Alt-F1 (F2, F3, etc). to go to a text console, log in, and fix your X problems (usually by editing /etc/X11/xorg.conf ).

If you can beg or borrow another video card, that would be a good test.

-HF

---

### Post by manchu99 on 2007-12-19
hey everyone! thanks for your help. I am posting this on a shinny new copy of ubuntu 7.10

the problem i was having was partly caused by windows. A while back, when i was using windows, i had no video output. not even the bios stuff at startup, and my monitor was not getting any signal. So i got an 11 year old video card out of the closet and had been using that. When i was trying to install all those linux os's they must not have liked that old card, i'm thinking it was because it had a top resolution of 800X600x16.. Out of desperation I plugged the monitor back into the on board video and poof, i had a signal. I have no idea why it stopped working before, but I am hoping it stays working. If it does, it is good bye windows for ever. it was a hardware issue. thanks again for your help!

---

