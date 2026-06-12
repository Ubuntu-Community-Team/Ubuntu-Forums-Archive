---
title: "Lynx  (kermic to) installation/livecd not working"
date: 2010-11-16
forum: Installation &amp; Upgrades
---

### Post by mccarthyl on 2010-11-16
Hello, I hope that someone can help me as I am not sure where else to turn, I am new to ubuntu (to unix as a whole in fact) I had used it a few years ago but decided to give it another try because xp went BSOD. I am attempting to load the system on to my think-pad t40. A few days ago (shortly before I decided to drop windows) I installed a better processor and added more RAM (I desperately hope it is not so, but i feel that this holds potential to be the source of my problems) after becoming sick of blue screens I decided to give ubuntu another try (originally because I suspected it to be an quick easy installation)I downloaded the newest version, 10.01, and burned the image to a cd, I popped it in my drive started up the machine, the install screen appeared, i clicked install and followed the steps, after installation I was left at the desktop as I do after most installations I restarted my computer, upon restart system booted into ubuntu did not reach the desktop, I shut it down and tried again to no avail. I attempted the installation many different times on multiply hard drives with multiple versions of ubuntu, the results of these attempts were very similar to the original with a few variations. At this point When i boot from the cd it boots to the install screen  but this install screen seems to be less flashy than the first one i saw, most of the time when I select an option from the menu such as install I receive about a screens worth of text with various page faults and error codes, the cd stops spinning and I am left with a blinking cursor on the bottom of the screen. Other times after I select an option from the install screen i get a blinking cursor for a second then the cd stops spinning and the computer restarts. Please help me to get this system on my computer. I will gladly provide any more information necessary.

---

### Post by mörgæs on 2010-11-17
Hi, welcome to the forum.

I assume that you mean you have been trying to install 10.10. How does 10.04.1 work?
[http://www.releases.ubuntu.com/](http://www.releases.ubuntu.com/)

Have you tried running memtest from the boot menu? Might take all night.

---

### Post by mccarthyl on 2010-11-19
ok so I ran the memory test i got a number of errors took out one of the RAM chips out this seemed to stop the restarts and I was able to boot 9.1 to the live cd and after some trys was able to install 9.1 on the computer after restarted it ran alot of text and then black screen with "error: no such device: 088e487f-3395-4bb9-9f31-0ff7efbb9cb5   Press any key to continue..._" I still have a feeling that the hard drive is not formatted correctly but then again I dont really know at all. I clean formatted it using windows diskmanager but I could not format it to an ext3 or 4 file system in windows so I figured it would format through ubuntu when I started the installation with that formatted hard drive ubuntu did not list it as a device, so I tried it with a different hard drive that had an old windows system and a few failed attempts at ubuntu, I selected the "erase and use entire disk option at the partitioning tool in the ubuntu setup and that is how I ended up with this no such device error. Please any more help would be greatly appreciated, sorry it took me awhile to find this post again I am not used to the forum. Thank you

---

### Post by mörgæs on 2010-11-20
Partitioning and formatting are done during the installation. No need to worry about that.

Windows does not know ext3 and 4. They are only available in Linux.

How much memory is in the machine, after you removed the faulty stick?


I have collected some advice here. Maybe it will help:

[http://ubuntuforums.org/showthread.php?t=1580857](http://ubuntuforums.org/showthread.php?t=1580857)

---

