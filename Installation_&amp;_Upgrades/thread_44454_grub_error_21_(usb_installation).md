---
title: "grub error 21 (usb installation)"
date: 2005-06-26
forum: Installation &amp; Upgrades
---

### Post by snigel1 on 2005-06-26
hello. i have a worklaptop with win xp on it, which i had to keep for several reasons.
so i decided to install ubuntu to a usb hard drive.

installation proceeded with no problem and my computer is usb-bootable.

but when i boot i get grub error 21, leaving me with no options. cant neither get to xp or ubuntu.

someone told me its because the real grub-stuff is on the usb drive and i need to  do some fixes with my partitions on hda by logging in with knoppix live cd. now im in knoppix but i dont know what to do!


Heeelp! :)

---

### Post by unquenchablefire on 2007-10-19
I'm having the exact same problem. I'll let you know if i find a solution before anyone else.

---

### Post by ErnobmaS on 2007-10-19
Same problem here--but no USB key. Just a normal install of Gutsy and get:

> GRUB Loading stage1.5

GRUB loading, please wait...
Error 21

---

### Post by unquenchablefire on 2007-10-19
I got my computer working again. I haven't tried to get Ubuntu running, but at least i got my computer booting unassisted and running XP. I tried a few different things, but this is what ultimately worked: a [SuperGrub]("http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html") disk. I'm sure you could get a floppy working if you had one, or a USB key if you had the time, but a good ol' CD is what resurrected my machine. I think I may try and get Ubuntu working this weekend by adding a small Linux partition to my internal harddrive - enough to hold Grub and not much else, and run from there. This SuperGrub disk really does work wonders.

---

### Post by FiReSTaRT on 2007-10-20
For those of us trying to get around this problem, there's always booting from the XP CD, running the repair console and doing FIXMBR and FIXBOOT. 

Is there a way to install 7.10 without GRUB buggin' like this?

---

### Post by ErnobmaS on 2007-11-18
Well, the way I got around error 21 was to go into the BIOS--I was trying to install Ubuntu on a hard drive that wasn't even being recognized. Once I switched that on in the BIOS, there were no more problems.

---

