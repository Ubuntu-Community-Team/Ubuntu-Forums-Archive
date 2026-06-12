---
title: "Moar Dual Boot Issues"
date: 2008-01-20
forum: Installation &amp; Upgrades
---

### Post by Chest2Tank on 2008-01-20
Nifty search features, but I'm so new to this, I have no idea what I'm actually doing and what to look at.  I've googled and such, so posting is my last resort before seeking in-person help.  When I installed Ubuntu 7.1, it did not recognize Windows XP, like the literature said it would.  So, XP boots automatically.  

Both operating systems are there.  After I figured out that the installation didn't work as promised, I started poking around.  I have the appropriate partitions, but there is nothing on the FAT32 partition.  I started following [this tutorial.]("http://www.matthewjmiller.net/howtos/dual-boot-linux-and-windows/")  I got to the part about creating the boot file with the "dd" command, and it didn't do anything.

Here's what I figure I need to do:

1.) point "Boot.ini" to a linux booter
2.) create a linux booter (?)

I came from the DOS world, so I'm quite familiar with those functions.  I am not familiar with linux much.  How do I do this manually?  Step by step, if you please.  Thanks guys!

---

### Post by banewman on 2008-01-20
Boot from the live cd
open a terminal and type - sudo grub
then type - find /boot/grub/stage1
you should get an answer like (hd0,2) or similar
type - root(hd?,?) - the answer from above step
type - setup (hd0) - to set grub up on the first mbr
then type quit - and reboot and you should have the grub menu
:)

---

### Post by Chest2Tank on 2008-01-20
> **banewman said:**
> Boot from the live cd
open a terminal and type - sudo grub
then type - find /boot/grub/stage1
you should get an answer like (hd0,2) or similar
type - root(hd?,?) - the answer from above step
type - setup (hd0) - to set grub up on the first mbr
then type quit - and reboot and you should have the grub menu
:)

Awesome.  Will try it right now.  What happens when I get the grub menu?

---

### Post by banewman on 2008-01-20
It should have options for the ubuntu kernel, a rescue kernel and windows
:)

---

### Post by Chest2Tank on 2008-01-20
> **banewman said:**
> It should have options for the ubuntu kernel, a rescue kernel and windows
:)

Awesome thanks!  That was easy :)  Works perfectly!

---

### Post by banewman on 2008-01-20
If it's working now - great
can you mark the thread as solved please
:)

---

