---
title: "grub won't respond to my keyboard"
date: 2012-09-22
forum: Installation &amp; Upgrades
---

### Post by jw1496 on 2012-09-22
I have just allowed my ubuntu 11.10 system to carry out updates without, I must admit, looking carefully to see what they were.  Update manager wanted a reboot but on restarting I saw an error message stating that the disc with /tmp was not present.  Not sure of the sequence of events after this - its been a bad day!  I rebooted with the on/off switch and entered the bios.  Everything seemed OK both hard drives were present and correct (OS is on an SSD, my documents are stored on a conventional hard drive).  Now if I try to reboot GRUB comes up but does not respond if I try to use the keyboard to select any option.  I have tried booting from two distro cds but neither of these will respond to the keyboard.  I have tried a second keyboard and I have tried plugging this via an adapter into the PS2 port.

Any suggestions?

---

### Post by jw1496 on 2012-09-22
A small update...
I tried boot-repair-disk ([http://sourceforge.net/projects/boot-repair-cd/files/](http://sourceforge.net/projects/boot-repair-cd/files/)) which I found through this forum.  Unfortunately since it does not automatically boot I am unable to start it because it requires keyboard input!

---

### Post by Bashing-om on 2012-09-22
Hello jw1496;

Let's proceed with baby steps to find our where we are at.

1. Can you boot the install cd => try ubuntu ...does keyboard respond ?
2. From your normal install can you boot into recovery mode ?

[INDENT]kind regards <==BDQ

[/INDENT]

---

### Post by jw1496 on 2012-09-22
Hi,

Thanks for your help.

I have just found a solution.  I don't know how or why but in the BIOS mouse and keyboard USB support was disabled.  (MB is a gigabyte GA-M61SME-S2 if anybody cares).  I enabled it and my keyboard was able to work in GRUB and then I was able to boot successfully.

So I think we can mark this solved.

---

