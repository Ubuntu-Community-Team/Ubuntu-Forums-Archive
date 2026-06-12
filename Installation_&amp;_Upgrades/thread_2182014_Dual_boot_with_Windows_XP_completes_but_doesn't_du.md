---
title: "Dual boot with Windows XP completes but doesn't dual boot"
date: 2013-10-19
forum: Installation &amp; Upgrades
---

### Post by GwDLpKy on 2013-10-19
I booted from a 12.10 32 bit Ubuntu DVD and chose the dual boot option. The process was straight forward. The system recognized that there was an Ubuntu OS already on the hard drive. I tried reinstalling and erasing and reinstalling with the same results. The install seemed to proceed correctly. At the end, I was told that I must restart the machine to complete the install, which I did. The DVD drive drawer opened, I removed the DVD, and closed the drawer. Nothing else happened: black screen, no mouse, no cursor, no error message, no anything. I forced the computer to shut down by holding the power button. When I started it again, it booted to Windows XP. There is no trace of Ubuntu except that the hard drive has lost about 5 Gigabites. I know Ubuntu is there because it is detected by Ubuntu when I try the entire process again.

I am a very new user who wants to use Ubuntu as much as I can. I have a new laptop that I have loaded Ubuntu in place of Windows 8 and I would like to have my older laptop Ubuntu bootable. Any ideas would be appreciated.

---

### Post by averos on 2013-10-19
If i understand your situation correctly, when you restart after installing Ubuntu you don't see GRUB screen that would let you decide which OS you want to boot into? Is that correct? When i installed, i saw an option on a screen that comes very early on during the installation which lets you configure where you want boot loader installed. In my case the boot loader was installed at the highest level of partition hierarchy, in fact the option already had the disk name selected. 

It would be interesting to find out where is your boat loader being installed.

---

### Post by fantab on 2013-10-20
After removing the DVD from tray and closing the tray back you are suppoesed to hit the Enter/Return key to continue.

Re-install ubuntu. These things happen.
Good Luck...

---

### Post by GwDLpKy on 2013-10-20
I saw no option regarding where the boot loader should be installed. How do I find out where my boot loader has been installed?

---

### Post by GwDLpKy on 2013-10-20
I'll try the install process again and hit the Enter key sooner then post the result. I hope it works. Thanks for the suggestion.

I tried it again with the same result. I'll try downloading a different file and try installing again.

---

### Post by martinr on 2013-11-09
Just make sure that you don't boot the installation CD with a UEFI boot sequence if your HD structures is MSDOS with MBR.
(See: [this thread]("http://ubuntuforums.org/showthread.php?p=12030957#post12030957"))

---

