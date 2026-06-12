---
title: "Installing Vista/Ubuntu on seperate drives"
date: 2007-03-08
forum: Installation &amp; Upgrades
---

### Post by brianv2.0 on 2007-03-08
HI everyone,
This is my first post here and my first real experience with Linux. I just upgraded my computer with some new hardware and I'm starting fresh with a new Vista install which  I setup a Raid for. I have a bunch of IDE drives that I'm going to be using for storage but I figured I could use part of one for Linux. I've already installed Vista but I wanted to dual boot with Ubuntu. Do I have to start over with my installs or can I forge ahead with installing Ubuntu?

Also as a side note, when I try to run the Ubuntu LiveCD I get past the loading screen, it makes a kind of jungle sounding start up jungle and the my screen stays blank. I've looked around and I think it maybe my resolution or video card, but I'm not totally sure what to do about it. I'm also going to try the alternate install CD tonight. any ideas?
Thanks!

My Setup:
Asus P5W DH Deluxe
Core 2 E6300
Radeon X1300
OCZ 1GB PC6400
Mad Dog 550W PSU

---

### Post by confused57 on 2007-03-08
> **brianv2.0 said:**
> HI everyone,
This is my first post here and my first real experience with Linux. I just upgraded my computer with some new hardware and I'm starting fresh with a new Vista install which  I setup a Raid for. I have a bunch of IDE drives that I'm going to be using for storage but I figured I could use part of one for Linux. I've already installed Vista but I wanted to dual boot with Ubuntu. Do I have to start over with my installs or can I forge ahead with installing Ubuntu?

Also as a side note, when I try to run the Ubuntu LiveCD I get past the loading screen, it makes a kind of jungle sounding start up jungle and the my screen stays blank. I've looked around and I think it maybe my resolution or video card, but I'm not totally sure what to do about it. I'm also going to try the alternate install CD tonight. any ideas?
Thanks!

My Setup:
Asus P5W DH Deluxe
Core 2 E6300
Radeon X1300
OCZ 1GB PC6400
Mad Dog 550W PSU

You'll have the same problems after installing with the alternate cd that you're seeing using the live cd...I'd suggest you try to get the live cd working first, it's probably your video card, ATI graphics cards can be difficult to get working.  Here's one of many threads for configuring ATI cards:
[http://www.ubuntuforums.org/showthread.php?t=190133](http://www.ubuntuforums.org/showthread.php?t=190133)
I'll try to find some more, you should be able to find several that may help, maybe even one with your specific card.

As far dualbooting on a separate hard drive, you might want to set your IDE drive you're going to install Ubuntu on as the first hard drive in your bios hard drive boot order...then use grub to boot Vista, rather than installing grub to your Vista drive's mbr.  I'd recommend getting the live cd to working first.

Other Links:
[http://www.ubuntuforums.org/showthread.php?t=294882&page=2](http://www.ubuntuforums.org/showthread.php?t=294882&page=2)
[http://www.ubuntuforums.org/search.php?searchid=15876146](http://www.ubuntuforums.org/search.php?searchid=15876146)

---

