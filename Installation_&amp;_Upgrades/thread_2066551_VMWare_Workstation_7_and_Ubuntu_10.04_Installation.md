---
title: "VMWare Workstation 7 and Ubuntu 10.04 Installation problem"
date: 2012-10-04
forum: Installation &amp; Upgrades
---

### Post by ChrisLee13 on 2012-10-04
I'm attempting to install ubuntu 10.04 on VMWare 7 for school, and I'm running into some installation problems.

My computer:
HP Pavillion G6
AMD A6-4400M
AMD Radeon HD 7520G

I've attempted several things:

Installing ubuntu-10.04.4-desktop-i386.iso
----------------------------------------------------
doesn't install goes straight to terminal no gui install

ubuntu-10.04.4-desktop-amd64.iso
-----------------------------------------
same thing straight to terminal no gui install

ubuntu-10.04.4-alternate-i386.iso
-------------------------------------------
halfway thru install it says it cannot find a kernel

tried this:
When the final prompt "Installation complete" appears (i.e. the  one that appears just before it goes down for reboot), do the following:
[LIST=1]
[*]Press Alt+F3 to switch to a virtual console, then press Enter to activate it.
[*]Type "apt-install linux-image-generic"
[*]Wait for the prompt to re-appear (you can monitor progress by  pressing Alt+F4, but you must Alt+F3 to see whether it's actually  finished)
[*]When the installation of the kernel is complete, press Alt+F1 to  return to the installer, and press Enter with the Continue button  highlighted to reboot the system
[/LIST]
when system boots it goes to memtest86 and can only get to grub cmdline.

ubuntu-10.04.4-alternate-amd64.iso
-------------------------------------------------
installs without errors but still no gui, and only the terminal seems to work. Tried a bunch of stuff at the terminal and that didn't work.

ubuntu-12.04.1-desktop-i386.iso
-------------------------------------------------
Fails at - Load Fallback graphics devices

I'm completely new to Ubuntu and this is driving me insane, I think it's something with my graphics card but I'm not to sure. Any help would be greatly appreciated.

---

### Post by hatoon on 2013-04-08
Any updates on this? I have the same issue here... Were you able to fix it?

---

### Post by hatoon on 2013-04-09
This link was very useful to me.
[http://ubuntuforums.org/showthread.php?t=1743535](http://ubuntuforums.org/showthread.php?t=1743535)
It worked based on instructions there.

---

