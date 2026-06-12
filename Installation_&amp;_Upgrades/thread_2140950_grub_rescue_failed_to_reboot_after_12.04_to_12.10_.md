---
title: "grub rescue: failed to reboot after 12.04 to 12.10 upgrade"
date: 2013-05-01
forum: Installation &amp; Upgrades
---

### Post by BcRich on 2013-05-01
Hi 
I was upgrading my system from 12.04 to 12.10, everything went along fine. I got to the section when I was told to reboot, so I clikced reboot and the system started to go down for reboot then just hung. I had to manually reset the computer and now when i try to boot i just get a grub rescue prompt.
booted with a 12.04 live cd installed boot repair tried the "recommended" option, no dice.
so here's the link to my log file from boot repair
[http://paste.ubuntu.com/5622219/](http://paste.ubuntu.com/5622219/)
Any suggestions?

---

### Post by fantab on 2013-05-01
You can 't use 12.04 Live cd to repair 12.10. You should download '[Boot Repair Disc]("http://sourceforge.net/projects/boot-repair-cd/files/")", burn it on CD/USB and fix your boot. If you have UEFI. LVM or RAID then use [Linux-Secure-Remix]("http://sourceforge.net/p/linux-secure/wiki/Home/").
OR Download 12.10 and reinstall.

---

### Post by BcRich on 2013-05-04
Hi fantab,
I managed to fix the problem with a 12.10 live cd and boot-repair. however my grub is now a mess (no pun intended). It seems as though my operating system list at system startup has reverted to the old boot loader screen, which amounts to about 12 choices in the menu (incl the recovery options for 9.10 and 10.10 which are still on this machine). basically do you know of a way of cleaning up the boot loader menu or reverting to my previously installed menu which only had about 4 choices i.e. 9.10, 10.10 etc and a single recovery option. Currently, there are spans of different kernels listed to boot into. Perhaps, uninstalling the kernels i don't use is a better option? Thanks for your help, it's very much appreciated :)

---

### Post by Bucky Ball on 2013-05-04
I use Grub Customizer. It cleans things up and more.

[http://ubuntuforums.org/showthread.php?p=10340183](http://ubuntuforums.org/showthread.php?p=10340183)

---

### Post by BcRich on 2013-05-04
Thanks for the link Bucky Ball, that's what I've been using too but didn't really know how to use it properly so the instructions will defs come in handy :)

---

