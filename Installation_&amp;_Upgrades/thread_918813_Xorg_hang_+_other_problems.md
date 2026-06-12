---
title: "Xorg hang + other problems"
date: 2008-09-13
forum: Installation &amp; Upgrades
---

### Post by dfrandin on 2008-09-13
I'm trying to do a clean install of 8.04 to a Dell GX620 (P4D/2.8Ghz/4GB ram) and am seeing several problems during install, the worst problem is that after the install is completed, system reboots for first time, I get the normal Ubuntu splashscreen/progressbar, then the screen goes black, I get the spinning wheel mouse pointer, the mouse pointer can be moved around the screen, but the wheel is not animated, and the system is locked up tight.. Cannot restart Xorg, and the only fix is to cycle system power..
I have a 512MB Nvidia GeForce8400GS installed. The other problem is, when booting from the install DVD, the initial install menu comes up, but the installed USB keyboard will not talk to this menu. I've waited up to 10 min to see if it was a slow detection issue... Never sees it.. Fortuantly I have one of the Dell PS2/mouse/keyboard adapter plates, and temporarily put an old PS2 keyboard on the system, and am able to install succesfully. I've seen the same problem on 7.10 also... Seems like a bug in the installer perhaps??  I tried installing 8.04 back when it first came out, and ran into these issues, and finding no resolution, put the project on the backburner.. Now I really need to get this system with the program on Ubuntu.... Any ideas??

Dave

---

### Post by dfrandin on 2008-10-19
BUMP?? Anybody have any ideas???

---

### Post by overdrank on 2008-10-19
> **dfrandin said:**
> BUMP?? Anybody have any ideas???

Hi and have you checked the cd for errors and also the checksum of the iso?
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)
Have you tried editing the kernel line from the grub by pressing the esp key at the grub line, this will allow you to edit  the kernel line by pressing e and you can remove the quiet splash and noapic. If you have it installed.

---

### Post by dfrandin on 2008-10-19
> **overdrank said:**
> Hi and have you checked the cd for errors and also the checksum of the iso?
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)
Have you tried editing the kernel line from the grub by pressing the esp key at the grub line, this will allow you to edit  the kernel line by pressing e and you can remove the quiet splash and noapic. If you have it installed.

Thanks for the reply.. Yes I did check the DVD, and the checksum both are fine.. In fact the second time I tried to install I used a friends DVD that was a pressed one from Canoniacal. I brought the system up in single, and tried running the "fix xorg" selection.. No joy.. X seems to start, I do get the hourglass spinner, but it doesnt spin and the system is totally locked.. takes a pwr cycle to recover.. Some additional testing since I posted the original post.. I got a copy of Fedora9 and tried installing it.. Same xorg problems.. Yet the system/video card works flawless under Windows. I'd think if the system had such a problem to keep xorg from running, I'd be seeing issues in Windows... Guess not..

---

