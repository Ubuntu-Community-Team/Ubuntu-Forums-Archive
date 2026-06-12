---
title: "Workaround for XP installer blank screen"
date: 2008-01-12
forum: Installation &amp; Upgrades
---

### Post by imjustabill on 2008-01-12
I had a lot of problem trying to install Windows XP with on a separate partition, and have seen a lot of other people have the same problem. For some reason, when you try to install XP with Ubuntu already installed, you get stuck with a blank screen. The workaround I've seen is to completely erase the entire drive. I found a better way to do it.

Remember, messing with your MBR and installing windows could mess things up, so make sure you make a backup first!!!

I had a 20 gig partition that I wanted to install windows on, the rest of my drive was set up for Ubuntu. 
What I did was went into the BIOS and disabled the hard drive that I wanted to install windows on. For whatever reason, Windows would still detect the drive and install normally. When the windows installer goes to reboot, make sure you re-enable the drive so Windows can finish installing. After Windows installs, you'll need to [re-install grub]("http://ubuntuforums.org/showthread.php?t=224351")

---

