---
title: "Installation Issues...frustrated, need advice."
date: 2007-10-19
forum: Installation &amp; Upgrades
---

### Post by Opus7 on 2007-10-19
I have been unsuccessful in my attempts to install Gutsy on an old Compaq system (2.5Mhz, 256MB Mem, 50GB Hdd). I have reformatted the hard drive to remove all old windows, software, viruses, etc...so I should not have any problems. It runs through the install process and gets to an "off-white page" and seems to freeze. I noticed that it had one error when running through install, about midway, that said "CPU scaling frequency not supported". I let the system sit for about an hour and when I came back the screen was blank -- nothing...

So I thought perhaps I should try to download an older version to install. I have tried Ubuntu 6.06, 7.04, 7.04 alternate, and now 7.10. And I have tried Knoppix 5.1.1 --- but none of these will install on this old Compaq system. I have been able to use the 7.10 CD successfully on an even older notebook with less resources, so the CD seems okay...

Error Message with older versions (not 7.10) -
Int 14: cr2 cf800000 err00000000 eipc020c384 cs00000060 flags00010007
stack: c00f7da0 c03f129b c0371d8c 00000002 c00f7da9 000f7da0 00000000 000000000

I am pulling my hair out trying to figure out what the real issue is with the old system. The hardware seems to check out, and it was running windows xp okay until viruses corrupted it. I was able to reinstall XP and it ran okay, but it was my legal version for another machine, so I removed and planned to use for Linux. But no success to date.

Can anyone help me???

---

### Post by Opus7 on 2007-10-19
I have tried to install Ubuntu 7.10 now several times on the old Compaq desktop and I get to the "White Screen of Death" during the install procedure.

The "White screen of Death" sucks....no error messages...no warnings...just a white screen.   This feature during install must be something shared with the Microsoft family of products, so it seems that the  Linux folks have more in common with Windows than I thought.   Microsoft would give you an error that gives you no choice but to choose "okay" when this was the last thing you wanted. 

I was hoping for something better in the Linux world.   Why a "White screen of Death" instead of something useful when installing Ubuntu 7.10 (gutsy gibbon).    I really wanted to set up this old system but I am getting close to throwing my hands up in the air and walking away from Linux -- too fickle to install on a system gets a rating of ZERO in my book....particularly when windows will install and run.

---

### Post by Wobedraggled on 2007-10-19
Sounds like a possible memory issue that windows is ignoring.

---

### Post by milton1 on 2007-10-19
> **Wobedraggled said:**
> Sounds like a possible memory issue that windows is ignoring.

ditto. This sort of symptom often means too little memory, or corrupt memory. How much RAM do you have?

---

### Post by Opus7 on 2007-10-19
I did a check on the memory and it seemed to be okay....256MB of memory should be enough to run one of the versions....   And the older notebook with 256MB started up.

I have tried Ubuntu 6.06, 7.04, 7.04 alternate, and now 7.10 -- along with Knoppix 5.1.1 -- so you would think one of these would actually run on this system with 256MB of memory.   If Linux won't run on old systems with 256MB of memory then it rules out a lot of older systems like this one.

---

### Post by milton1 on 2007-10-19
256MB is more than enough for xubuntu, and for install of any version. The conflict must be elsewhere (assuming none of the RAM is corrupted, but you can check this by replacing ram and trying again)

---

### Post by milton1 on 2007-10-19
If that many versions are refusing to run, it suggests a hardware conflict.

---

### Post by jrasmussen0 on 2007-10-19
Your description suggests looking at the video driver and running with special options like noacpi.

Can you run the liveCD without a problem?  If not then try booting any disk with boot: live acpi=off at the beginning menu where you can choose to run memtest.  ACPI is a BIOS method for describing hardware to an operating system and it can be misconfigured/ wrong in earlier versions.  You could try to update the BIOS to see if that helps or just run without ACPI but you will not get the CPU scaling without it.  CPU frequency scaling is useful to save battery.

Were you able to run memtest off of the liveCD?

---

### Post by Opus7 on 2007-10-19
Perhaps it is a hardware conflict...i do not know, but it seems weird that windows will account for the issue and run.

I was able to run the mem test from CD without incident....seems okay.   I have not played with the BIOS at all, I thought it was okay since windows ran.   Since it is a desktop I am not worried about battery life...so can I turn off ACPI and run the 7.10 install?

---

