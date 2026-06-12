---
title: "Stuck at boot on Ubuntu 14.04 Trusty"
date: 2015-03-11
forum: Installation &amp; Upgrades
---

### Post by prester2 on 2015-03-11
I have successfully installed Ubuntu (x64) but I can't seem to boot it properly. Also,I booted it in a Live CD session but I can't connect through Wi-Fi. Here are some screenshots and all of them gave an [ OK ]:
[IMG]http://i62.tinypic.com/2m6v503.jpg[/IMG]
[IMG]http://i59.tinypic.com/2vmyis9.jpg[/IMG]
The second screenshot happened after I disabled Network Boot in the BIOS although when I enabled it again the same boot session happens. I have tried holding up arrow key but it only blinks the booting screen. I'm using a laptop that is pre-installed with Windows 8.1 and installed Ubuntu through Legacy. I created the partitions I used for Ubuntu in Windows.

---

### Post by Mike_Ohlhausen on 2015-03-12
Try creating the file systems with the Ubuntu installer. Leave empty space where you want it from Windows. I never had a lot of good things happen creating filesystems from the other OS, either from Win to Lin or the other way around...

---

### Post by prester2 on 2015-03-13
> **Mike_Ohlhausen said:**
> Try creating the file systems with the Ubuntu installer. Leave empty space where you want it from Windows. I never had a lot of good things happen creating filesystems from the other OS, either from Win to Lin or the other way around...

Tried this and got the same stuck up situation. Also, when the installation finishes and restarts it opens the DVD drive and gets stuck there forever. I had to force restart after installation just to proceed on the situation I mentioned in my first post. It also happens when I am just restarting the PC from the live session. I'm new to Ubuntu so I guess the problem is on the hardware.

edit: I'll download other Linux's to see if the situation is similar.

---

### Post by Bucky Ball on 2015-03-13
Welcome. Are you choosing the install with third-party software option? Perhaps try it without if so.

---

### Post by prester2 on 2015-03-13
> **Bucky Ball said:**
> Welcome. Are you choosing the install with third-party software option? Perhaps try it without if so.
Never tried it so I'll do this once I had a rest. I may as well try to install the 32-bit version, thinking that it could be some compatibility issues.

---

### Post by Bucky Ball on 2015-03-13
I wouldn't install the 32bit if you have a 64bit system. I would delete the partitions you created in Windows (do this from a Live session if you need to) and install Ubuntu in EFI. If it was preinstalled with Win8, you have to install Ubuntu in EFI.

It is a waste of time creating partitions for Ubuntu with Windows. Ubuntu uses EXT* partitions and Windows can't read/write/recognise them as anything useable or create them. You haven't tried the previous suggestion along these lines that you try without creating partitions with Win, so ...

Remove the partitions you created with Windows which are now probably EXT* partitions;
Install Ubuntu 64bit in EFI mode;
Choose 'Something Else' when you get to the partitioning section of the install and create the partitions/mountpoints manually.

If you need help with any of this, ask. ;)

Your problem is probably that you have installed in legacy when Win is in EFI. 32bit install won't make any difference to that, it is not the issue here. 

You can also try[ Boot Repair]("https://help.ubuntu.com/community/Boot-Repair") which I believe can change things to an EFI install, but never tried that. Here's [more info]("http://ubuntuforums.org/showthread.php?t=1769482") re. Boot Repair.

---

