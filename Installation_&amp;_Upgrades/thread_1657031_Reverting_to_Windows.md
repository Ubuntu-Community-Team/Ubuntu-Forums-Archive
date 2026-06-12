---
title: "Reverting to Windows"
date: 2010-12-31
forum: Installation &amp; Upgrades
---

### Post by Shaneiffer on 2010-12-31
Disclaimer: I am aware of the possibility that I may have damaged my hard drive irreparably and do not need any snide remarks about newb mistakes, etc.  Thank you.

SO...though I LOVE Ubuntu and all that it stands for, I realized after installing it that I have absolutely NO TIME to learn to use it well and I want to go back to windows just because of the familiarity factor.  
SYS info:
HP DM1Z with AMD K625 processor (otherwise all factory specs).


In doing all of this, I have done a LOT of research to make sure I was doing the right thing before I did it.  
Initially I did a complete install of Ubuntu (lucid), wiping my drive and reformatting it for Ubuntu.  Upon researching reversion options I knew that in order to install Win7, I needed to reformat the drive to NTFS Filesystem.  So I did more research learned that you can use the WinXP installer to reformat to NTFS.  SO I borrowed a copy just to use for the format so then I could go back and use my Win7 for installing the new OS.  I wiped the HD and then loaded the WinXP files onto a bootable USBStick.  Upon inserting the USBStick, it started to load and then it went to a blue screenstating the following:

"A problem has been detected and Windows has been shut down to prevent damage to your computer.
If this is the first time you've seen the Stop error screen, restart your computer.  I the screen appears again, follow these steps:
Check for viruses on your computer.  Remove any newly installed hard drives or hard drive controllers.  Check your hard drive and make sure it is properly configured and terminated.  Run CHKDSK /F to check for hard drive corruption, and then restart your computer.
Thechnical Information:
*** STOP: 0x0000007B (0xF78D2524, 0x0000034, 0x0000000, 0x0000000)"

I don't know where I went wrong, but I ma in serious need of help!  I am posting this accross other forums in hopes that someone can help me.  If I attempt to boot my computer right now, all I get after the initial HP screen offering BOOT menu entry is the black screen with blinking cursor, so I don't know what my options are from here.

I will gladly supply any other information needed to help your diagnosis as I am able.

Thanks!
Shane

---

### Post by wilee-nilee on 2010-12-31
Can you in one sentence explain what you want on the computer. Is it W7 or XP?

The post is confusing.

---

### Post by Sef on 2010-12-31
I would use the Windows 7 disk to format the hard drive to NTFS.

---

### Post by squenson on 2010-12-31
I have not reformatted an HDD with Windows since several months but you need to run a specific command to format it, not just try to install the software.

---

### Post by wilee-nilee on 2010-12-31
> **squenson said:**
> I have not reformatted an HDD with Windows since several months but you need to run a specific command to format it, not just try to install the software.

Nice answer but makes no sense.:)

---

### Post by presence1960 on 2010-12-31
Boot the Ubuntu Live CD/USB, choose "try ubuntu without changes", when the desktop loads go System > Administration > Gparted Partition Editor. Use gparted to delete every partition one at a time (click Apply which is the green check mark). Apply one deletion at a time. When the entire disk is grey labeled "unallocated" you have 2 options:

1. Make one big NTFS partition, click Apply (green check mark). When completed reboot without the Ubuntu CD and boot from the windows install CD/DVD and select the NTFS partition to install windows to.

2. Once the entire disk is "unallocated" reboot without Ubuntu Live CD and boot the windows CD/DVD and install to the unallocated space.

---

### Post by Shaneiffer on 2011-01-01
Thanks to all for the replies...I will be trying the ideas as I can.  Will let you know...thanks again!

Shane

---

### Post by Beallthere on 2011-10-23
This happened to me too. I was going to install a 1TB HD. But the new upgrade came along and stopped at 'Check Battery.' I couldn't get anything to work so I disconnected the 2 drives and installed XP in the 1TB. No combination of connecting those little ones allows me to boot. Since I have lots of things in them, I'd like to know how to connect them, both at once or 1 at a time and dump enough stuff out of each one in order to defrag and use them again. Would an enclosure help?

---

