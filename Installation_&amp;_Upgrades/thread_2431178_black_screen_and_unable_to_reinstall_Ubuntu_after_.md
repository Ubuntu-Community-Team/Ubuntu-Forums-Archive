---
title: "black screen and unable to reinstall Ubuntu after update"
date: 2019-11-12
forum: Installation &amp; Upgrades
---

### Post by stacey-bean on 2019-11-12
Hi, total novice here. 
I ran an OS update for Ubuntu last week and after rebooting the machine I got an empty black screen. Tried running with nomodeset but it didn't make any difference. I also tried the command "sudo apt update && sudo apt upgrade --fix-missing" which didn't work either. 

I'm now trying to reinstall Ubuntu from a USB, but after selecting "install Ubuntu" I get a loading screen for about thirty seconds and then the machine shuts off. When I checked the disc for errors it says "no errors found." 

UPDATE: I have managed to get an OS running off the USB, but the system is apparently not detecting my laptop's hard drive. I suspect that this is what's been causing the boot to black screen.
I don't understand how a regular system update could render my hard drive inaccessible, or what to do about it. Can someone please help?

---

### Post by mörgæs on 2019-11-13
First we need to know more of the hardware. From a live boot please copy ```
sudo lshw -sanitize > lshw.txt
``` and paste it into the command line, run it and post lshw.txt in CODE tags.

---

