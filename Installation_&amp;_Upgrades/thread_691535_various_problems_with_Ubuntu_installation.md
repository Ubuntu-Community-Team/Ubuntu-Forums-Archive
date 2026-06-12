---
title: "various problems with Ubuntu installation"
date: 2008-02-08
forum: Installation &amp; Upgrades
---

### Post by phonkenstein on 2008-02-08
I'm having several different problems when I install Ubuntu.  First of all, a lot of the time both the live CD and the alternative CD won't detect the hard drive.  This happens with two different SATA drives both in 7.10 and 7.04.  The hard drives work well otherwise and are always detected in BIOS.  Resetting the CMOS battery usually fixes this.

Once I get the OS installed, I've been having problems with freezing.  This usually occurs when opening a program or clicking on a menu item.  It seems similar to a bug involving ATI cards, but it has the added symptom of preventing the machine from booting again.  It either hangs at the loading screen or restarts the computer.  The only solution I've found for this is reinstalling the OS. 

As I was typing this I installed the restricted ATI driver in my latest 7.04 install, and when I restarted the machine it makes it as far as "Starting Up ..." where it reboots.  

I've run memtest for 24 hours without any errors and checked every disk I've used for flaws, and I still can't get this to work out.  The machine works fine with Windows XP.

hardware is as follows

Abit IP35-E
Intel Core 2 Duo E4500
ATI Radeon x850xt  (pci-express)
2gb RAM

Edit:  I just went to boot into recovery mode, and noticed something I've never seen before.  It shows 4 options (including memtest).  Kernel 2.6.20-16 generic, 2.6.20-15 generic and their respective recovery modes.  Selecting 2.6.20-15 boots properly sometimes.

---

