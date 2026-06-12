---
title: "Ubuntu Server on Compact Flash Weird GRUB ERROR"
date: 2007-08-17
forum: Installation &amp; Upgrades
---

### Post by igutekunst on 2007-08-17
I have build a small embedded system for running mpd, and playing music through a network.

I installed Ubuntu 7.04 Alternate x86 onto a on Gig Compact Flash card in an IDE adapter.

The install went fine, and I booted into my new Linux distribution. I updated th system, and install openssh-sever, and a few other packages. 

For some reason (I can't quite remember) I needed to restart the computer.I immediately displayed the following error

GRUB loading Stage1.5 Read Error

So I booted into a live cd, looked at /boot/grub/menu.lst  added a menu timeout (which should affect the error.)

Needless to say, when I rebooted, the GRUB menu came up fine, and I was able to boot into Ubuntu. 
:confused:

About an hour later, I rebooted my system again, and got the same GRUB error.

Once again, I booted into the live cd, but this time, I added another boot entry. 

Restart.

Works fine.

Well,  I did this about three or four times, each time, simply changing a tiny bit of the menu.lst file.

I came to the conclusion, that GRUB will fail unless it sees a change in the menu.lst.
Maybe GRUB cannot really see the root of the CF card, and only in the event of a change will reexamine the the partition table, or something like that. 

:confused:

I'm pretty sure that the actual problem has something to do with the compact flash card, and the age (very old) of my motherboard and BIOS. 



I am definitely not very knowledgeable in Linux, so keep that in mind if this is an obvious oversight.

---

