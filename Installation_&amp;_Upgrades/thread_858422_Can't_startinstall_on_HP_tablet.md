---
title: "Can't start/install on HP tablet"
date: 2008-07-13
forum: Installation &amp; Upgrades
---

### Post by tC_Crazy on 2008-07-13
So, I just got a brand new HP tx2500z Tablet PC. I want to dual-boot with Ubuntu Hardy, but can't even get started. When I boot to the disc, and choose either install or start Live, it loads for a few minutes, then ejects the disc and tells me to remove and press enter. I do that, and it just shuts down the computer. I tried booting with options noapic irqpoll noirqdebug, but the noapic caused a kernel panic. With just irqpoll noirqdebug, I got about 15 seconds further into the process: I got the mouse cursor, a really distorted image in the top 1/5 of my screen, and then it went back and ejected my disc. I then tried the CD Check, which seemed to complete, and then restart my machine automatically.

Any ideas?? The system has a 2.4Ghz AMD Turion X2 Ultra processor, 3GB of RAM, Vista Home Premium. Other than being a tablet, there's nothing else out of the ordinary. 

Any ideas??

---

### Post by pluckster on 2008-07-14
Yeah I'm having the same problem. I have a tx2524ca (a 2500 derivative) that I just bought and was hoping it could run Ubuntu as opposed to Vista. I've tried LiveCDs of Ubuntu Hardy and Xubuntu Hardy and an install of Ubuntu Hardy but they all end in the way described above, it will get the the Ubuntu boot splash and the progress bar and after about 3-4 ticks on the bar it goes the complete and the bar continues like its shutting down, eject the disc and then reboots. I was able to get it to work very slowly by disabling apci noapic nolapic but then it didn't work after the install. I followed some other trick I saw floating around but none of them worked to any good degree of success. It seems that once its on its good to go really so I'm just looking for the first step.

---

### Post by Sef on 2008-07-14
Try the alternate cd.  To get it, click on the box at the bottom of the download page.  

To dual boot with the alternate cd, read the [Illustrated Dual Boot]("http://users.bigpond.net.au/hermanzone/").

---

### Post by pluckster on 2008-07-14
Okay well it seems to have the same problem to start with so I'm disabling apic and apci and whatnot to see if it will install. Its currently installing so I'll report back later with results.

EDIT: Okay well it tried to install the kernel and then came up with an error saying that it could not find the correct one from the apt sources and that I could manually install it but it was not recommended. I'm taking its advice for the time being because I have no idea what to do really.

---

