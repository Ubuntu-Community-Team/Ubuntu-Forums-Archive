---
title: "Grub and Multiboot USB Devices"
date: 2011-05-19
forum: Installation &amp; Upgrades
---

### Post by Ritzbitts on 2011-05-19
So I've been a Linux user for a few years now, and lately I've been teaching myself about network and general security. I want to install Ubuntu 11.04 and Back|Track 5 on a bootable USB flashdrive (BT5 is based on Ubuntu/Kubuntu).

This is the first time I've set up a dual boot on a USB, but not the first time I've worked with a bootable USB or Grub.

My device is configured as such:

4.5 gig extended partition containing:
-2.5 gig ext3 logical partition for Back|Track 5
-2 gig ext 3 logical partition for Ubuntu 11.04
2 gig Linux Swap
30 Meg Fat32 for Grub
And the remaining 1.5 or so gigs is an Ext3 partition for shared data.

So, I've been having trouble installing grub on the 30 meg partition (I know Grub can fit on a much smaller partition). I've tried several approaches, and in the process upgraded my workstation to Grub 2. I have had mixed results and know I'm missing something (maybe even something obvious) along the way. I've searched extensively on the topic but haven't seen more than a few pages dedicated to what I want to do.

I'd like to ask some users how they would approach this task, and how they would install the bootloader.

Thanks!

---

