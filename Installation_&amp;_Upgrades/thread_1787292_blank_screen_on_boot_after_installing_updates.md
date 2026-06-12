---
title: "blank screen on boot after installing updates"
date: 2011-06-20
forum: Installation &amp; Upgrades
---

### Post by @rc on 2011-06-20
Hi,
I recently installed ubuntu(32-bit 10.04) alongside windows 7 in my hp laptop(64-bit).When i installed all the updates available and restarted, a blank screen came after i chose to boot ubuntu.On pressing the power button, ubuntu closing animation appeared & it shut down.Is it because of my hardware drivers not supporting some updates.Do I have to re-install ubuntu..if yes, how do i remove it?..is deleting the ubuntu partion ok..how should i know which updates can be installed..also, are there any problems in running 32-bit version on a 64-bit laptop?
Thanks for any advice

---

### Post by YesWeCan on 2011-06-21
Hi.
Running 32bit is fine.
If you want to delete Ubuntu, boot into Windows first and restore your MBR code. Otherwise deleting Ubuntu will stop you being able to boot Windows. Delete your Ubuntu partitions using Windows or a live CD.
It sounds like Ubuntu is getting stuck or taking a long time during the boot for some reason, possibly graphics related. Make sure you give it plenty of time. One thing to try is to type 'e' at the Grub menu and add nomodeset to the kernel command line options, next to quiet, nosplash. If this works and you can boot check for additional hardware drivers and install recommended ones.

---

