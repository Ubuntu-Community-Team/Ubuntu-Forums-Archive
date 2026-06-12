---
title: "Avoiding black screen on ubuntu 7.10 installation"
date: 2007-10-22
forum: Installation &amp; Upgrades
---

### Post by bernardobraga on 2007-10-22
Hello,

I just installed ubuntu 7.10, I had a lot of frustration when installing it cause after selecting any option on the live-CD boot-screen, a short message would appear and my screen would turn black, as if in sleep mode. 
After searching through the forums, I found that many faced the same problem. I decided to open this tutorial so people could share how they managed to deal with the problem. I tried a few of the solutions and one finally worked.
In my case, what happened was: The splash screen didn't work, so when it turned on, I got a black screen, even though the boot was trying to start the OS. I would eventually assume that the system had locked up and reboot.
What I did to solve: I highlighted the second option, pressed F6. At this point a command line will appear at the bottom of the screen, It shows: :file=/cdrom/preseed/ubuntu.seed boot=casper initrd=/casper/initrd.gz quiet splash--" . I changed it by deleting the "quiet" word and adding "no" to splash so it read: :file=/cdrom/preseed/ubuntu.seed boot=casper initrd=/casper/initrd.gz nosplash--"
After doing that, the system booted normally, now, without the splash screen. I could see the command line instructions going on and after a while, the graphical interface started. No icons appear for a short time, so be patient, it should appear soon enough.

Hope this was helpful
Bernardo.

---

### Post by K.Mandla on 2007-10-26
Moved to Installation and Upgrades.

---

