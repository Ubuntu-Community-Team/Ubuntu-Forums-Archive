---
title: "Ubuntu &amp; WinXP"
date: 2006-09-01
forum: Installation &amp; Upgrades
---

### Post by Icoo on 2006-09-01
OK guys I tried Ubuntu last night on VMWare and I just loved it! Now I want to install it on my hard drive. Here is my current situation:

250 GB HDD:
200 GB - NTFS - My Files
25 GB - NTFS - WinXP
5 GB - NTFS - Small Partition for my VMs
20 GB - Unpartitioned Free Space

Now I want to use the unpartitioned space to install Ubuntu onto it! I got the new Ubuntu 6.06 via Shipit and I want to install it! Will the installer allow me to choose the unpartitioned space, will it recognise WinXP as another OS and setup the bootloader? Or will I end up with a messed up system? Please help! :confused:

---

### Post by schorem on 2006-09-01
Yes, it will be recognized. I just installed it myself. But do not use the automatic partitioning. Do it manually.

Remember to set a root (/) and a swap partition. But the installer will remind you ;)

---

### Post by Icoo on 2006-09-01
So I should create 2 ext3 partitions, how big should the swap one be...I have 1 GB RAM...so swap should be small...

---

### Post by schorem on 2006-09-01
The installer recommends at least 256, but it depends on your RAM.

---

### Post by Icoo on 2006-09-01
OK I just inserted the CD into my drive and rebooted. But when i choose "Run or install Ubuntu" it gave me an error that X has failed?

---

### Post by mojoman on 2006-09-01
> **Icoo said:**
> So I should create 2 ext3 partitions, how big should the swap one be...I have 1 GB RAM...so swap should be small...

Take a look at this site, I found it useful

[http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)

Best regards
/Mojoman

---

### Post by Icoo on 2006-09-01
Well the x server porblem is still here, I have a ATI Radeon X800 graphics card...Ubuntu should have driver for it since the card is more then a year old! Or does the X Server problem lies somewhere else?

---

### Post by bobosity on 2006-09-01
It sounds like you've already booted the cd successfully once. If it won't boot again, I'd look at cleaning the cd. It happened to me.

The partitioning thing was a bit confusing at first but Ubuntu did an excellent job of splitting my winxp disk. I'm reading this forum now because my plans are similar to yours.

---

### Post by Icoo on 2006-09-02
Nope I'm sure thats not the problem! It's becauseI have 2 CD (one from Shipit and from the LXF magazine - both don't work!). Yes I managed to get the CD working once, but in VMware (virtual PC)...any ideas why it doesn't work on my real PC?

Edit:

OK i ran the CD defection test and it went well. I even pressed F4 and changed different VGA modes...still nothing. The error X server gives me is:

FATAL ERROR:
NO SCREENS FOUND

WTF? There are no screens, but how can I see the error then? ](*,)

---

### Post by Icoo on 2006-09-02
I just managed to start Ubuntu in safe graphics mode! Why can't I start it in standard mode? Anyone?

---

