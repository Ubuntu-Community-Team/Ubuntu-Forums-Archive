---
title: "Install problems on Adaptec 2610sa/Dell CERC SATA RAID card"
date: 2017-07-25
forum: Installation &amp; Upgrades
---

### Post by ccsav on 2017-07-25
Hello,
I have an old Dell PowerVault 745N that I'm trying to install Ubuntu on. It's got four drives on an Adaptec 2610sa/Dell CERC SATA RAID card that I've configured in a RAID 10 setup using the onboard utility, for a total volume size of 460 GB. Initially, I tried installing 16.04 LTS (which I've read has the aacraid driver built in standard), but the drive(s)/RAID volume never showed up during install. I read somewhere that the driver for the RAID card had been removed since it was such old hardware, but that it still existed under 14.04 LTS, so I tried that, without any luck. I've tried swapping the card with a known good card, and there was no change. The drives all show up fine in the onboard utility, and the array is in an optimal state. I've rebuilt the array a couple of times to see if it made a difference, with no change.

This isn't a production server or anything, just an old cast off I was able to get my hands on and wanted to try messing around with Ubuntu for the first time. Not being able to install the OS is a bit of a frustrating start! It previously had Windows Server 2003 SBS on it, but I thought I'd try something new. Now I'm wondering if I should just go back to Windows with it, since it doesn't look like this hardware is supported by Ubuntu.

Any ideas on how I might be able to get Ubuntu installed on this thing?

---

