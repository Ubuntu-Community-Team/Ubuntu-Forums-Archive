---
title: "Ubuntu 14.04 LTS install"
date: 2014-10-21
forum: Installation &amp; Upgrades
---

### Post by ngant on 2014-10-21
looks like Ubuntu 14.04 LTS has proven itself again.  At least in the laptop's wireless hardware dept. After installing other Linux OS, some Ubuntu-based and others not, the only one that worked automatically on my laptop with my built-in wireless chipset was this version of Ubuntu.  Linux Mint, Zorin, Pinguy and of course Windoze XP simply failed to the task, even after searching and installing the Broadcom driver.
Yes, I love Mint with it's pretty awesome artwork backgrounds.  Zorin and Pinguy has their own positive qualities.  They all did wired ethernet great, although re-installing Windoze XP drivers were the biggest bottleneck in a standard install.  But when the bottom line is wireless access, you have to give credit where it is due.

For that reason I will have to stick with current and future versions of Ubuntu.

One note:  I did a back up of original Ubuntu before wiping out hard drive, and when I restored data to a fresh Ubuntu install, everything seemed normal except that I kept getting kicked off my wireless connection, looping endlessly thru password entry.  I suspected that the built-in Broadcom wireless chipset was going bad, but it resurrected itself when I did a brand new install of Ubuntu and avoided restoring previous data. 
I did not have a wireless card in my laptop, but I am ordering one to facilitate fresh installs of other Linux OSs.

---

### Post by irv on 2014-10-21
Broadcom cards started giving me problems back in version 11.04 but I found a work around  (See post 25 of this thread) [THREAD,]("http://ubuntuforums.org/showthread.php?t=1742147&page=3")  To find the card you have type this in a terminal  and look for your wireless card in the output. 
```
sudo lshw -C network
```

Dell used Broadcom cards in some of there older laptops. I still have three of the 1521 with Ubuntu on them.

---

