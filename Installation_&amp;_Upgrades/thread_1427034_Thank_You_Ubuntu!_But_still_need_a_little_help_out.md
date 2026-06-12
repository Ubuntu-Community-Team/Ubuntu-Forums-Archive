---
title: "Thank You Ubuntu! But still need a little help out the Gates!"
date: 2010-03-11
forum: Installation &amp; Upgrades
---

### Post by HookedOnFishing on 2010-03-11
My Gateway MX7515 crashed due to a bad Windows registry thing and was unrecoverable! Have to buy another operating system or pay for a disk to fix whatever corrupted shell32. dll was bad. I tried everything. I removed the drive and recovered my data and confirmed the drive was good. Confirmed memory check was good. First cup Of Ubuntu down.
I burnt a copy of Ubuntu9.10 installed the disk and in an hour I was up and running. Was able to get everything setup and updated within another couple of hours.
I'm watching Youtube videos, printing, and scanning wirelessly with my Brother 495CW, I can connect to my Windows computers on the home network. Everything works as good or faster than windows XP did. Very stable, very fast.
I tried a new install of the 64 bit version, but it did not work very good. Computer would restart with garbled characters and couldn't figure out what to do. Obviously video driver problem. Checked ATI website for my board and found they do not have any Linux drivers for my Model. 
Went back and reinstalled 32 bit and I'm back to everything working real good but knowing i'm losing processing power being only 32 bit when I have AMD 4000+ 64 bit processor. And what can I do about the ATi driver problems for my chipset and video?
Still very, very new to this Linux, Ubuntu 9.10. Learning how to check things out now. It is a big new world out here. I can smell what you guys are brewing, and I'm loving it so far!
Thank you everyone!

---

### Post by dstew on 2010-03-11
> And what can I do about the ATi driver problems for my chipset and video?Probably not much, unless you can convince ATI to write a 64-bit driver. That is the one main drawback for Linux. Since it is a small (but growing!) fraction of the PC operating system "market", hardware makers do not create drivers for Linux as willingly as they do for the "other" operating system. It is partly a business decision. Linux developers would love to help manufacturers write the drivers, but then the manufacturers would have to reveal the inner workings of their hardware to the open source world, and some manufacturers want to keep their proprietary hardware information secret.

The only option I see if you want to run the 64-bit Ubuntu system is to try different open source drivers and see if something works, or use a different video card that is supported. Here is the [Ubuntu Hardware Support document]("https://wiki.ubuntu.com/HardwareSupportComponentsVideoCards"). It is pretty old, and doesn't have the 32- vs. 64-bit information you need. You can try posting on the Multimedia and Video forum. Maybe somebody has kludged together a solution.

Just to be complete, you have checked the "Hardware drivers" menu in System --> Administration, right? And you have enabled the Universe repository (do that in Software Sources).

---

