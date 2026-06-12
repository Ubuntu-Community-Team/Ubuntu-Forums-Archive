---
title: "Installation/Dual boot/dual monitors questions"
date: 2005-04-10
forum: Installation &amp; Upgrades
---

### Post by DanthemaninVA1 on 2005-04-10
I recently tried the LiveCD of the Hoary Hedgehog release, and I'm desperate to actually be able to install it.  The optimal solution would be a second hard drive; the primary hard drive would be windows, and the secondary would be Ubuntu.  I was wondering what the best way would be to be able to put to either on startup, while changing my windows installation as little as possible.  

I also have a question regarding dual monitors.  I use an Nvidia GeForce FX 5200, which has two monitor ports on it, so I use two monitors.  I'd like to know the easiest way to extend my desktop across both monitors intelligently, i.e. maximizing windows maximizes to one monitor.

Thanks in advance for all your help.

---

### Post by nad on 2005-04-11
An installation of Ubuntu will not modify your windows partition(s) in any way, unless of course you request it. It will ask to install a bootloader called grub into the master boot record of the active hard drive. As several posts here have noted, there may be problems with XP after doing this. I have not researched the problems as I have little experience with XP and do not care to know more. You can install grub into the /boot partition of your linux installation in which case you will have to handle the initiation of your other operating system(s) yourself. I thought that this bit of information would be useful as you do not mention what OS version you are using now.

Regarding dual monitors; For what OS would you like information?

Dan M

---

### Post by DanthemaninVA1 on 2005-04-11
I'm currently using Windows XP.  I have the dual monitors working fine under Windows, but I'm wondering if there's anything special I need to do to make them work properly under Ubuntu.  When I tried the LiveCD, the primary monitor worked fine; the secondary had random colors all over it; I just turned it off because I couldn't do anything on it, anyway.

---

### Post by nad on 2005-04-11
There will be some housekeeping to do. For starters, the open source nVidia driver will not presently initialize a second video card. Whether it will initialize a second separately addressable port on a single card, I have not tested. There is obviously no support for this with the liveCD. The manufacturers' driver has no problem and is available as a package for ubuntu. This will have to be installed.

Other than that and some configuring, there shouldn't be any other issues. You may want to research these forums for your particulars. Chances are somebody has done this already.

Dan M

---

### Post by DanthemaninVA1 on 2005-04-11
Thanks for all the help.  Hopefully in a week or so when I get my new hard drive in the mail, I'll be able to let you know how it went.

---

