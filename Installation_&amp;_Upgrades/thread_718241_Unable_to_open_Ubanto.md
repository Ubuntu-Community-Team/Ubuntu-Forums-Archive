---
title: "Unable to open Ubanto"
date: 2008-03-07
forum: Installation &amp; Upgrades
---

### Post by Gawler on 2008-03-07
Hi, I'm having problems booting Ubantu.
I loaded Ubantu and had Grub installed to the MBR (I would have preferred it in the Linux partition but was not given a choice). After installation the machine booted OK and I was able to access Win98. On the next boot and everytime afterwards I got a error 17. Particularly frustrating as I couldn't access the net from the live Ubanto disk. Not being able to resolve the error 17 problem I reinstalled Windows and Boot Magic.
As predicted the Linux option on Boot Magic failed to load Ubantu so I have just followed instuctions and loaded Grub to (hd0,5). I presume this is the correct partition as Ubantu is on hda6. Installation went OK as per messages.   Boot Magic on the MBR should then open Grub and hence Ubantu, according to posted messages.
Unfortunately Ubanto still doesn't boot from Boot Magic. So have I put Grub in the wrong place or is the error 17 still the problem? I notice that Boot Magic lists Linux as Primary Partition 4, Partition Magic has it as the 6th listed (logical) partition, and the partition table in Ubantu has Linux as ext3 hda6 while hda4 is an almost empty ext2 Linux partition.
I've installed Grub on to a floppy.  This also gives an error 17 when Linux is selected.
Any ideas? This is my first attempt at Linux so please don't assume I have prior knowledge.
Thanks

---

