---
title: "New install 8.04 fails to see SAT discs"
date: 2008-05-05
forum: Installation &amp; Upgrades
---

### Post by jekyll59 on 2008-05-05
Am in process of moving from the dark side to Linux. On my newer PC I can't get 8.04 past the partitioning step on install. Install runs fine until it gets to hard disc partitioning stage. The partitioning tool is not seeing my SATA hard drive - it does not see any discs at all. This means I can't set partitions and can't continue with install. I have seen similar problems reported since Hardy launched but not many solutions. I am using CDs burnt from ubuntu-8.04-desktop-amd64.iso. CDs are burnt on a Windows XP PC and when CD checks out as fine when run CD check during install.
The PC is Intel core 2 Duo E6750 on Abit IP35-E board with 2G DDR2 RAM, 500 GB Samsung SATAII hard drive, XFX GeForce 9600GT graphics. It has Windows XP on the PC but plenty of space for Hardy install.
All help appreciated!

---

### Post by osage on 2008-05-09
same boat here, I can install the 32 bit version, but not the 64 bit one.......

I was able to get the 64 bit version installed by adding --irqpoll to the boot configuration or whatever it is called.

select Ubuntu from the boot menu/select to start with the APCI workarounds/then press "e" to edit that line/ add --irqpoll/ and then press "b" to boot.  worked for me.  Not sure if I put a space after the last item in the APCI boot config or not, try it both ways if it dosent work the first time.


hope it helps.

Abit IP35-E
Intel E6450

---

