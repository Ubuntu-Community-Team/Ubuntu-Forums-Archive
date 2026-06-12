---
title: "I need some help with some grub , MBR switching hardrive questions"
date: 2008-07-13
forum: Installation &amp; Upgrades
---

### Post by CameronCalver on 2008-07-13
Hello i have 2 computers both have only 1 harddrive.
One of them is running Ubuntu the newest distro and the other has no os at all and will not run a cd from bootup it will not usb boot will not network boot and floppy disk drive doesnt work.
I was wondering if i take the hardrive out of it and take the hard drive out of the ubuntu box and put it on the same ide slot and install windows on it and then take it out and put it back in the original computer will windows boot? and if it does will the ubuntu one still boot or will it of wiped the grub off it?

---

### Post by Pumalite on 2008-07-13
Exchanging hard drives is always dicey. If you install Windows; you later have to reinstall Grub. I don't know how it is with Windows, but with Ubuntu, sometimes it works, sometimes it doesn't. Many times you have to at least reconfigure the xserver.

---

### Post by CameronCalver on 2008-07-13
mmmm ok i dont no how i am going to do this then

---

### Post by Rallg on 2008-07-13
Beginning with XP, Windows measures various properties of your computer to determine if the installation is "genuine." If you install Windows on a hard drive, then physically move the hard drive to a different computer, there is a good chance that Windows will say that it is an invalid copy.

Linux (in general) doesn't do that. You might be able to install Ubuntu on a hard drive, then move the drive to a different computer, where it will boot. For this to have the best chance of working, the hard drive will have to be otherwise clean (nothing on it but Ubuntu and related stuff, no other partitions unrelated to Ubuntu).

If your second computer is so un-bootable, it suggests that you have either (a) waaaay old equipment, or (b) a hardware problem.

---

