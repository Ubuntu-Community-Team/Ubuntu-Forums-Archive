---
title: "Installation hangs at 75% &quot;Storing Language...&quot;"
date: 2008-04-27
forum: Installation &amp; Upgrades
---

### Post by DoddyUK on 2008-04-27
Hi, I'm having big problems installing Ubuntu 8.04 Server AMD64 at the moment. When I'm installing Ubuntu, the installer hangs on 75%, with the task name "Storing language...". I had a previous problem with partitioning, but it was just the way my HD didn't like Ext3 so using reiserFS instead solve that. Anyway, here's my hardware:

ASUS K8V-X Motherboard
Western DIgital WD5000AAJ 500GB SATA Hard Drive
Athlon 64 processor 2.2GHz
1GB Kingston DDR 333 RAM
Lite-On DH-1602P DVD-ROM drive
2 Blue Cold-Cathode lights :)

And my Partitioning is as such:

Pri   24.0GB   ReiserFS   /
Log   375.0GB   ReiserFS   /home
Log   100.0GB   ReiserFS   /music
Pri   98.7MB   BOOT   ReiserFS   /boot
Pri   1.0GB   Swap

I've done Alt-F4 to try and see what appears on screen, but I just get a huge mass of text, which looks like error tracing for a Kernel panic:

in-target: UNPACKING LINUX-IMAGE-2.6.23-16-SERVER (FROM .../LINUX-IMAGE-2.6.24-16-SERVER_2.6.24-16.30_AMD64.DEB) ... ^M
debconf: Obsolete command TITLE Configuring linux-image-2.6.24-16-server called
in-target: DONE.^m

So, any ideas what might be causing this freeze?

---

**EDIT**

About 10 minutes later the kernel panic came up. Here's the last few lines of the text:

[1520.997903] Code 48 4b 41 28 48 8d 71 28 48 39 d6 0f 18 08 74 3e 90 0f ba 29

[1521.025723] RIP[<ffffffff802a4fd8>] get_partial_node+0x28/0x90
[1521.035201] RSP <ffffffff8062ad50>
[1521.044640] ---[ end trace a20829ae74339cb8 ]---
[1521.054149] Kernel Panic - not syncing: Aiee, killing interrupt handler!

---

### Post by DoddyUK on 2008-04-27
Sorted it out. Just needed to flash my mobo. Thanks.

---

### Post by purplepaint on 2008-07-11
I'm having exactly this problem installing Xubuntu in VirtualBox.  I'm using the Alternate CD as I don't think the desktop I want to install it on will handle booting from the Live CD (at least it didn't with the Live CD for Ubuntu 7.04).  The same thing happens when I try and install the minimal CD following [these instructions]("http://www.psychocats.net/ubuntu/minimal#barebones") (also in VirtualBox - I'm trying to find out what will run best on a slightly old desktop and an even older desktop, neither of which will boot from Live CDs when I've tried them).  I don't understand what the fix you posted means.

---

### Post by MichaelB2010 on 2010-09-26
FWIW, I've gotten a kernel panic once and just plain hung (or seems to be) numerous times. Mobo Gigabyge GA-K8NSNXP, CPU Athlon64 3000+, 512MB. I flashed this board's BIOS for the 1st time ever hoping I'd have the same luck as DoddyUK, but it didn't do anything (short of convincing the machine that my CPU is rated at 200 Mhz and cannot be clocked over 455 Mhz...I'm thinking someone in the bios coding dept made an oopsy...)
 
A bunch of ppl [here say good things come to those who wait]("https://bugs.launchpad.net/ubuntu/+bug/219263")...and wait...and wait

---

