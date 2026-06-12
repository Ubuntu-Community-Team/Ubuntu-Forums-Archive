---
title: "White screen after installing Nvidia restricted driver as prompted"
date: 2010-01-06
forum: Installation &amp; Upgrades
---

### Post by PureChance on 2010-01-06
OK, brand new, first post :-) I didn't find any thread details basic rules, so I just tried to be as descriptive as I could in the topic title without going over board and avoided cross-posting. So I guess I'll open with the specifics of my problem, and then list my system details. Sorry for all the unnecessary information, but I thought more would be better than less, and I didn't know what was pertinent.

I've had Ubuntu installed on my desktop for a month now, and its all worked like a charm, so I'm thrilled. I then decided to install it on my old laptop as well to see if I could breath a bit more life into it, and to get used to working Ubuntu a bit more. The laptop had 18.6GB partitioned to C:// drive or windows XP, and an empty 18.6GB D:// drive, so I deleted the D:// drive in XP using the Microsoft disk utilities tool, all well and good. I then did a clean install of Ubuntu-9.10-desktop with an Ubuntu CD into the largest continuous free space, and it set it up nicely. When I first booted it up there were a ton of updates to install, as there had been on the desktop first time, which I dutifully installed. As on the desktop a little notice popped up telling me to install the NVidia Proprietary driver for the NVidia card (specifically "NVIDIA accelerated graphics driver (version 96)[Recommended]"), as it had when I installed it on the desktop, so I chose to install that and then restarted the computer. 

On restarting GRUB2 loaded, and it booted Ubuntu. I then saw the little white logo on the black screen for a couple of seconds, and then the screen goes completely white, with some pixels left behind fading to white slightly slower. First time through I held down the power button to force shut down, and on restart exactly the same thing happened. This time I held down alt+sysrq and went through the R, E, I, S, U, B sequence, however as opposed to usual I didn't get a black terminal-like screen after hitting any of the buttons, although it did reboot on B. It did boot correctly in recovery mode, however I was at a loss what to do here. Incidentally, the same problem occurred when I booted to previous version of the kernel as well.

Then I decided that as I didn't have any data to lose, and it was still early in the day, I'd do a clean re-install. This time I chose to ignore the updates, and just install the NVidia driver as prompted to check that it was the driver causing the trouble. Having installed the driver and restarted I got exactly the same problem as before - definitely this pesky NVidia driver, not any of the updates.

So here I am at clean install 3, having just got all the updates, but not having downloaded the NVidia driver as prompted, with little desire to go through yet more reinstalls. My questions are: 

1) Do I need to install this NVidia driver? The rest of the computer specifications are fairly paltry by modern standards, and I won't be doing anything graphics intensive on it (the most graphical program will probably be Battle for Wesnoth) and I I don't need to install it, not installing it seems to be the easiest way to solve the problem.

2) If I do need to install it how would I go around doing this without getting my charming white screen?

3) Is there a way of removing the driver from recovery mode that doesn't involve a clean install again? I have tried sudo apt-get purge nvidia-driver, which tells me there isn't any installed. I have tried sudo rm /etc/X11/xorg.conf which made no difference. I have tried dpkg-reconfigure xserver-xorg and this didn't help. I have tried a couple of other commands as well but I can't remember them, however I would probably recognise them if I saw them again.

Onto System information - pulled from listed specifications and SysInfo:

**General System Information**
**Release:**Ubuntu 9.10 (karmic)
**GNOME:** 2.28.1 (Ubuntu 2009-11-03)
**Kernel:** 2.6.31-17-generic

**Hardware**
**Computer:**Toshiba Satellite S5100-503
**CPU:** Intel(R) Pentium(R) 4 Mobile CPU 1.80GHz
**Graphics Card:** nVidia Corporation NV17[GeForce4 440 Go]

Thanks

---

### Post by PureChance on 2010-01-22
Not sure about the regulations regarding bumping of threads, but I figure that 2 weeks is sufficient in between bumps. If anyone has any help on any aspects of this problem that would be great.

Also, I'm not sure if this would be more suited the the laptops/hardware section of the forum, if so, would a mod mind moving it there for me?

Many Thanks,
PureChance

---

