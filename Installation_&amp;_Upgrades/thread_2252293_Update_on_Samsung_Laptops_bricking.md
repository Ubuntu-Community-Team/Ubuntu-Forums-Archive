---
title: "Update on Samsung Laptops bricking"
date: 2014-11-10
forum: Installation &amp; Upgrades
---

### Post by mittleiderja on 2014-11-10
So I just got an upgrade from my company on my laptop, which means my old work laptop is now my personal property (!!!). It is a Samsung NP700Z5C-S04US, which brings up a lot of hits when googling Ubuntu on that specific laptop, for reasons that are kind of scary. It seems booting Ubuntu from a USB has caused these computers to brick in the past, so I'm a little scared of trying... although everything I can find on it is over a year old. Has anyone heard if this problem has been fixed? 


More info the computer...
NP700Z5C-S04US, bought originally with Windows 7 (in November, '12) but came with a free upgrade to 8, because I got it about a month before 8 was released. I just recently upgraded to 8.1, and over the weekend (since it became my personal property) I did a complete wipe and fresh install of 8.1. I would like to dual boot with Ubuntu 14.04 and already have 150GB of hard drive space partitioned off for this purpose. 


So basically I'm just asking if anyone has updated info or some tricks/tips that are more recent than forum posts from 2013 on making this work without bricking my computer?

Thanks!

---

### Post by berninghausen on 2015-08-30
Here's an update on the Samsung issue.  After reading lots of horror and success stories, I updated the firmware on my wife's NP300E5C-A0BUS laptop, did the free load on Windows 10, and dove in.  Drilling down through the Windows system structure, I eventually found the 'update and repair' section(it mentioned UEFI and Secure Boot)--tapping that and hitting F10 got me into the standard Setup screen, where I could kill Secure Boot.  I also killed the track pad, since my wife wears bracelets and dragging them over the track pad drives her crazier.  Plugging in a USB stick with Mint 17 on it, I rebooted and crossed my fingers.  I had previously created a 100G partition to use for Linux, so I installed it.  Rebooted, and here's Grub2 with both Linux and Windows available.  I have been back and forth between them several times--no brick, no hassle, just the usual patch delays on the Windows side.  Problem seems to be solved.

---

