---
title: "laptop not responding while installing ubuntu"
date: 2012-03-10
forum: Installation &amp; Upgrades
---

### Post by dvait on 2012-03-10
Hi All,

I'm new to linux and Ubuntu. I've downloaded ubuntu, prepare a cd and try to install it on my laptop which had windows XP SP3. Initially it worked fine, when I start my laptop it asked to choose between windows or ubuntu.
When I  asked to remove windows and install ubuntu permanently, then a blank screen appeared and stayed there for  3 hours, then I switched it off. Laptop's keyboard stopped responding.
Any idea how I can install  ubutnu on it and how should I proceed now on installation.

Thanks

---

### Post by darkod on 2012-03-10
What do you mean, install ubuntu permanently? What was the first install, wubi inside windows or proper dual boot?

In any case, if you boot with the ubuntu cd in live mode (Try Ubuntu option), does it load correctly and can you run it from the cd? That's the first thing to check so you know if you can expect problems.

---

### Post by dvait on 2012-03-11
> **In any case, if you boot with the ubuntu cd in live mode (Try  Ubuntu option), does it load correctly and can you run it from the cd?  That's the first thing to check so you know if you can expect  problems.[/QUOTE]

That's what I tried first and it worked  perfectly fine.
After seeing the result,  I try to make Ubuntu permanent i.e. remoivng windows XP. I did it with some option from ubuntu installer.

[QUOTE=darkod said:**
> What do you mean, install ubuntu permanently? What was the first install, wubi inside windows or proper dual boot?

Permanently means removing windows and installing ubuntu only.

---

### Post by dvait on 2012-03-16
I discussed the issue with my friend and he suggested that windows OS is not cleaned properly, so while booting laptop is not finding anything. He gave me CD it started an FDOS session. Now, when I ran FDISK I can see the partition (there's only one) is called "Linux native". status 131. Is tehre any way to recover data on the laptop an install linux without clearing the partition?

---

### Post by Quackers on 2012-03-16
You can try Testdisk, which may recover the Windows partition and its contents.
I'm intrigued though why you intended to install Ubuntu over the top of Windows but you now want to recover your Windows files.

[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)

A better howto by Herman
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)

---

### Post by dvait on 2012-03-22
Finally, I able to install Ubuntu 11.10 32 bit on my laptop.
First I used a cd provided by one of my friend to boot the laptop and use freedos to run fdisk and clear the harddisk.
Then I install Ubuntu the CD taht I cut after downloading it.
It installed successfully. At the end it stopped at the final shutdown screen for around an hour. I thought it might be the way ubuntu shut dow so I pressed the laptop button to shutdown and restart.
But during restart it is just showing the laptop banner screen and not doing anything else.
Any idea what went wrong and how to fix it?

---

