---
title: "Can't get Xubuntu to start or install on old laptop"
date: 2008-11-08
forum: Installation &amp; Upgrades
---

### Post by Cyber Akuma on 2008-11-08
I have a very old laptop, its a Dell Latitude CPi D266XT.

It has a 200MHZ Pentium 2 CPU and 128 megs of what I assume is SDRAM, which is it's maximum limit.

Windows 2000 has been running PAINFULLY slow lately on it to the point of being unusable, so I decided to install a distro of Linux on it with hopes that it will run  little better, since I heard that many linux distros can run well on older hardware. Originally the system had Windows 98, but I forgot why, I needed to upgrade to Windows 2000 on it for something, so I can't go back to Win98 since im sure I will eventually bump into what forced me to upgrade last time.

However, I tried looking and most distros demanded 196 or 256 megs of ram as a minimum to work.

Finally I ran into Xubuntu which claimed to only need 128 megs to run live desktop or install and 64 megs to run after install.

However, I can't get the Xubuntu disk to work. If I try to live desktop, it takes about 15 minutes to load, then it just stays on a blank desktop with a firefox and help icon on the top left of the screen and the time on the top right, nothing else loads, no drop-down menus or anything. Nothing responds.

Trying the installer, a window appears with close/maximize/minimize buttons but thats it, nothing appears IN the window and nothing else loads. Nothing responds.

Anybody have any ideas what I can do to either get Xubuntu working or know of a better distro to use on such an old machine?

---

### Post by oilchangeguy on 2008-11-08
> **Cyber Akuma said:**
> I have a very old laptop, its a Dell Latitude CPi D266XT.

It has a 200MHZ Pentium 2 CPU and 128 megs of what I assume is SDRAM, which is it's maximum limit.

Windows 2000 has been running PAINFULLY slow lately on it to the point of being unusable, so I decided to install a distro of Linux on it with hopes that it will run  little better, since I heard that many linux distros can run well on older hardware. Originally the system had Windows 98, but I forgot why, I needed to upgrade to Windows 2000 on it for something, so I can't go back to Win98 since im sure I will eventually bump into what forced me to upgrade last time.

However, I tried looking and most distros demanded 196 or 256 megs of ram as a minimum to work.

Finally I ran into Xubuntu which claimed to only need 128 megs to run live desktop or install and 64 megs to run after install.

However, I can't get the Xubuntu disk to work. If I try to live desktop, it takes about 15 minutes to load, then it just stays on a blank desktop with a firefox and help icon on the top left of the screen and the time on the top right, nothing else loads, no drop-down menus or anything. Nothing responds.

Trying the installer, a window appears with close/maximize/minimize buttons but thats it, nothing appears IN the window and nothing else loads. Nothing responds.

Anybody have any ideas what I can do to either get Xubuntu working or know of a better distro to use on such an old machine?

while it may be true that some distros will run on less ram. you also have to think about the cpu speed. and 200mhz is not going to cut it. i'd suggest a fresh install of 98 if you have it. or damn small linux. but not any version of ubuntu.

---

### Post by Cyber Akuma on 2008-11-08
But the laptop actually exceeds the minimum requirements:

# 166 MHz processor
# 64 MB of system memory (RAM)
# At least 1.5 GB of disk space
# VGA graphics card 

It has a 200mhz cpu and 128 megs of ram, I forgot the HDD size but its over 10 gigs.

---

### Post by snowpine on 2008-11-08
You don't have enough ram to use the Xubuntu Live CD. You may be able to install using the Xubuntu Alternate CD, or a minimal command-line only install.

However, I would not recommend Xubuntu on that computer. Damn Small Linux, Puppy, or SliTaz would be better choices.

Good luck!

---

