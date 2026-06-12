---
title: "Installing 5.04 on an HP Netserver LH3"
date: 2005-09-17
forum: Installation &amp; Upgrades
---

### Post by Max Payne on 2005-09-17
I have downloaded the 5.04 installation disc (I assume that's all I need to install). I would like to install Unbuntu to switch my Netserver LH3 server (which I have been using at home for two years), to Unbuntu. I have been running Windows 2000 for a while, and got "hacked" in the past because of some of those vulnerabilities everyone has heard about.

For one, I'm starting to value security a little more, and also, I would like my sysem to be more tightly integrated, so I could say, control my FTP server accounts using PHP scripts. I assume this would be easy to do with a Linux FTP daemon (have the scripts edit its config files), but on Windows, without the source code of the server, I would have to reverse engineer its config format. Not to mention that the best FTP server I have has some stupid weaknesses I am aware of, but can't fix.

What I would like to know is, how well I can expect Ubuntu to support the hardware. This server has nothing *too* fancy. Just the stock hardware, plus a tape backup on an Adaptec 2940 SCSI card. What I believe could pose a problem is the IBM NetRAID system which is built into the server... This server dates from 1998 as well, so I don't know how Ubuntu is when it comes to older hardware. Does anybody have ideas about this? Have you installed Ubuntu on an HP Netserver LH3 before? Do you guys think I can expect this to work right with the stock Ubuntu install?

I would rather not just blindly "go ahead and try", because my server (although its not *mission critical*), will have to go down for the time it will take me to perform this switch.

---

### Post by Max Payne on 2005-09-18
Well, I can't even find for sure whether it's a NetRAID 1M or 3Si... The HP site, and all other sites with specs, seem especially shy on information. But I would still like to know how Ubuntu supports that. There are some records of older distros having compatibility problems with those.

---

### Post by Blade Freak on 2006-02-03
Neighter doesn't work for me.
Scsi controller found, NetRaid controller found (disks are configured in RAId 5 on the controller) but Ubuntu does not finds any disks.
No physical nor logical disks found.
Fedora did manage to find teh disks on the NetRaid controller and was able to install.
But i want to use Ubuntu!

---

### Post by aeble on 2006-07-31
> **Blade Freak said:**
> Neighter doesn't work for me.
Scsi controller found, NetRaid controller found (disks are configured in RAId 5 on the controller) but Ubuntu does not finds any disks.
No physical nor logical disks found.
Fedora did manage to find teh disks on the NetRaid controller and was able to install.
But i want to use Ubuntu!

If it's the Integrated NetRAID Adapter based on an LSI card you will have to make sure I2O mode is not activated and the system is running in Mass Storage mode. Only then you can use the megaraid driver. So far, I haven't been lucky to get Ubuntu installed on it, but SuSE 10.1 works for now. 

I expect it's a kernel/driver issue.

Cheers,
Axel

---

### Post by RX7Godfather on 2007-02-27
OK, I may have found an answer, at least it is working for my NetRAID 1Si SCSI controller.

You need to enter the bios of your scsi card, usually Ctrl+M while booting, locate somewhere in your scsi config utility the emulation section, you may have to dig for it, I know I did....

Change your SCSI emulation from I20 to MASS STORAGE, erase your array (you will lose everything on your drives) and rebuild and initialize it. This way Ubuntu will not see multiple installations and will erase the entire disks.

After doing that, try to install it again, so far it is working with my NetRAID 1Si controller.

Hope this helps...

---

