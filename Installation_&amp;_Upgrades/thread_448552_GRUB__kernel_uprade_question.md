---
title: "GRUB / kernel uprade question"
date: 2007-05-19
forum: Installation &amp; Upgrades
---

### Post by maybeway36 on 2007-05-19
I have a computer dual-booting FreeDOS with Ubuntu 7.04.
My GRUB menu looks something like this:

Ubuntu, kernel 2.6.10-5-386
Ubuntu, kernel 2.6.10-5-386 (recovery mode)
Ubuntu, memtest86+
Other operating systems:
FreeDOS

If I make FreeDOS the default by making "default" be 4 in menu.lst, will FreeDOS still be the default when I upgrade the kernel? In other words, would the kernel upgrade system in Ubuntu change the menu.lst default when it adds the new kernel?

---

### Post by brundles on 2007-05-19
It'll depend where it adds the new kernel entries. Remember you determine the GRUB entry to boot by number rather than a label.

The automatic kernel patching from the software upgrade has caught me out before as I have a dual boot system which (very occasionally) gets booted to Windows. It gave me a bit of a scare when I hit the 'boot windows' button on the remote after a kernel upgrade and it came back with just a Linux boot prompt and nothing else!

I would check the menu.lst file and default boot option after the kernel is upgraded before you reboot to be sure it's going to come back the way you want.

---

### Post by micha_silver on 2007-06-01
> **maybeway36 said:**
> I have a computer dual-booting FreeDOS with Ubuntu 7.04.
My GRUB menu looks something like this:

Ubuntu, kernel 2.6.10-5-386
Ubuntu, kernel 2.6.10-5-386 (recovery mode)
Ubuntu, memtest86+
Other operating systems:
FreeDOS

If I make FreeDOS the default by making "default" be 4 in menu.lst, will FreeDOS still be the default when I upgrade the kernel? In other words, would the kernel upgrade system in Ubuntu change the menu.lst default when it adds the new kernel?

I tripped over that exact problem this week. I have WinXP and Feisty dual booting on my laptop. I had edited the menu.lst file to have the WinXP stanza as the first entry, and I left the default 0.
After the kernel upgrade, the first entry in the menu.lst was **deleted** and the new kernel stanza was put in its place. I had to manually re-enter the WInXP stanza in order to get back the dual booting. 
_Not a very friendly way to upgrade the kernel!_

I'm not sure what to do to avoid this problem in the future. I'll try putting the Windows entry as second in the list, and enter default 1. THen we'll see what happens at the next kernel upgrade...

Cheers,
Micha

---

