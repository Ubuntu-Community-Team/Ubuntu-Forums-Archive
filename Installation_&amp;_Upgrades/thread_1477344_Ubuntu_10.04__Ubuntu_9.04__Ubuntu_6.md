---
title: "Ubuntu 10.04 / Ubuntu 9.04 / Ubuntu 6"
date: 2010-05-08
forum: Installation &amp; Upgrades
---

### Post by ashfame on 2010-05-08
I want to have Ubuntu badly as I want rock solid stable system with eye candy effects but the problem is I can't get it to run.

Attempt #1
I made a bootable usb of Ubuntu 10.04 using unetbootin, tried to boot from it and it will freeze while loading drivers. It stucks at the point where **system_call_fastpath** comes in the list.

Attempt #2
Two of my friends suggested to do it with a CD but I haven't tried it yet. To be sure that this ain't a USB problem, I installed Ubuntu within Win 7 and now it shows up in the OS boot list but when I select it, it will again froze at the same point **system_call_fastpath**.

Attempt #3
My friend advised me to install Ubuntu 9 and then upgrade. So I again created a bootable usb using unetbootin and it will freeze all of a sudden on boot screen (ubuntu logo with progressive bar at its bottom). At this point Caps lock & Scroll lock will start blinking.

I can recall that when I installed Ubuntu 6 on it for the first time, all was well but I stopped using it for no reason and after some time, it stopped working. It will hang on the boot screen too with blinking keyboard LEDs.

Doing some research on system_call_fastpath, I found that its some sort of a deadlock condition and I have no idea if thats a specific bug with my system configuration.

Any ideas? What should I do? I don't want XP or 7, I want Ubuntu :mad:

---

### Post by gary4gar on 2010-05-09
Care to share your Hardware config?
Anyways, general instructions 
Hi,
1) First verify if the install disc or image is not corrupted due to a bad download - [Go here]("https://help.ubuntu.com/community/HowToMD5SUM")
2) Select F4. Safe graphics mode may provide better results during LiveCD operation or also try Other boot options:
[https://help.ubuntu.com/community/BootParameters](https://help.ubuntu.com/community/BootParameters)
3) If it still does not work, then try another distro like Fedora or OpenSuse

---

### Post by ashfame on 2010-05-09
Hi Gary,

My configuration is Core2Duo 2.0 Ghz with Intel 965 motherboard.
I have ATI HD 4850 512MB graphics card with 2GB of DDR2 RAM.

I have installed the same to a laptop and its working fine, so the issue is with my desktop only.

I have tried with 64bit, will try with 32bit too. Also I read somewhere that this has to do with the file system, so I am gonna kill XP by deleting partition and then try booting with ubuntu.

Can you explain the boot parameters a bit?

---

### Post by SathyaBhat on 2010-05-09
At the bootsplash screen, just before you select Ubuntu, hit F6 and use one of the boot parameters mentioned in the link gary4gar mentioned.

---

