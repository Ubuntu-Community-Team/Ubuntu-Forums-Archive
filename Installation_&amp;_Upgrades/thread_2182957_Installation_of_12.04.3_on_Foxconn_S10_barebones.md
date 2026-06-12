---
title: "Installation of 12.04.3 on Foxconn S10 barebones"
date: 2013-10-23
forum: Installation &amp; Upgrades
---

### Post by pman2 on 2013-10-23
Hello,
after several days of exhaustive testing I am at my wits end, so I hop this forum can give me some answers:
I have a Foxconn barebones machine that was running on Ubuntu 11 and neede to be upgraded. I decided to go for a clean install, so I made a backup of the user's home directory and tried to install Ubuntu 12.04.3 32-bit on it. I tried the following:
- booting from a USB disk made with 'unetbootin'
- booting from a DVD disk with the 12.04.3 image on it
- installing the HD on another machine with the 12.04.3 image, and then inserting the disk in this machine.
In all cases, the result is as follows: the machine boots, and then goes dark, with the disk activity light off most of the time, occasionally flickering. No progress is made (I even let the machine sit through the night one time).
I tried to boot into 'rescue' mode from the installed disk, this works, the menu comes up, I can check disks, go to a prompt, rebuild the dpkg database, etc. But if I try to boot from there, a blank screen again.
Because I saw several posts on foxconn motherboards having problems with Linux, I decided to upgrade the Bios (using a freedos bootimage), and this worked, I now have the latest bios for this motherboard.[SIZE=1][FONT=arial][/FONT][/SIZE]
The motherboard is a Foxconn 45cs, with the following specs:

Specification
Intel® AtomTM single-core 230 processor mounted onboard
Intel® 945GC + ICH7
533 MHz (FSB)

I have 2 GB RAM installed, which I already checked with the memtest program (no errors found after a night's testing...)
I also tried several HDs, but all give the same result.
I have a suspicion that the problem is related to the video settings, so I am thinking of adding a separate videocard instead of the built-in Intel graphics. I also tried to change some of the related bios settings, but nothing worked. I have now reverted back to the 'optimized' defaults again.

Does anybody have any idea how to proceed?

Peter Mansvelder

---

### Post by Bucky Ball on 2013-10-23
Welcome. Are you getting to the screen that say 'Try Ubuntu' 'Install Ubuntu' etc.? If so, hit F6 and choose 'nomodset'. Proceed.

Also, if you are getting to that screen, have you chosen the 'Try Ubuntu' option rather than going straight for the install? This is wise as will give you an idea of how it's going to run, but at the moment that looks like it won't.

Also, what is on the disk you are trying to install to already? As you have attempted using several disks, perhaps this is not the issue, though, and this does point to graphics or motherboard issue.

---

### Post by pman2 on 2013-10-23
Hello Bucky Ball,
Thanks  for the quick reply!
As to your questions: no, that is the problem: I don't even get to the 'Try Ubuntu/Install Ubuntu' screen.
As I said, I tried to install with an empty harddrive, even without a harddrive to see if I could get to the abovementioned screen.
I managed to get to the 'rescue' screen when I booted off the preinstalled disk, and there I saw that the 'rescue' mode is started with the 'nomodeset' option to the kernel. This led me to believe the issue is motherboard or graphics-related.
Peter

---

### Post by pman2 on 2013-11-11
Ok, I admit: I gave up: after trying several things: updating firmware, adding a graphics card, replacing memory, I decided that it wasn't worth the effort and bought a replacement motherboard with the same specs: Intel Atom 2 x 1,6GHz, Mni-ITX...
I installed Ubuntu 12.04.3 without any problems, I upgraded to 13.10, still no problems...
This motherboard works like a charm, so I guess I just had a faulty one..

Peter

---

### Post by linuxguru43 on 2013-11-11
Yeah Foxconn boards are the worse you can buy. Doesn't get any cheaper than Foxconn.

---

### Post by Bucky Ball on 2013-11-11
Good news. Please mark the thread as solved. ;)

---

