---
title: "Installing Ubuntu 12.04, 12.10 or 13.10 on Asus Vivobook (A400C) with Windows 8 fails"
date: 2013-06-07
forum: Installation &amp; Upgrades
---

### Post by cdoebbler on 2013-06-07
Trying to install Ubuntu (12.04, 12.10, 13.04 or even 13.10) on an i5/4GB computer (Asus S400CA) that came with Windows 8 pre-installed. I cannot computer to boot from USB stick. Tried turning off Secureboot and checking that USB is recognized by system ( I can read disk), but still system just boots into Windows. I have trolled the forum and several others and tried several attempted fixes without any luck during the last 21 days. Is there any way to get around this apparent SecureBoot lock, which appears to stay on even when turned off?

Asus tech support says they don't support Windows 8, but that computer is hard blocked from installing new operating system (which seems to be illegal, so I wonder if it is true), so no new operating system (they said 'downgraded operating system', even though I would view Ubuntu 13.04 an upgrade from Windows 8) is possible. Is this possible?

---

### Post by arpanaut on 2013-06-07
Are You using the 64 bit version of ubuntu?
How are you preparing the USB sticks?

Take a look at this:  [http://ubuntuforums.org/showthread.php?t=2147295](http://ubuntuforums.org/showthread.php?t=2147295)

---

### Post by cdoebbler on 2013-06-12
Tired with 32 and 64 bit versions. Used Ubuntu website ISO creator and WUBI and neither worked. Wubi seems to load 12.04 through 13.04. With these three versions after Wubi setup I  get to dual boot screen but get an error about missing files when trying to boot Ubuntu, Windows 8 boots from this screen. 

For more information see this tread (which was closed although unresolved): [http://ubuntuforums.org/showthread.php?t=2146936](http://ubuntuforums.org/showthread.php?t=2146936)

---

### Post by fantab on 2013-06-12
> **cdoebbler said:**
> Trying to install Ubuntu (12.04, 12.10, 13.04 or even 13.10) on an i5/4GB computer (Asus S400CA) that came with Windows 8 pre-installed. I cannot computer to boot from USB stick. Tried turning off Secureboot and checking that USB is recognized by system ( I can read disk), but still system just boots into Windows. I have trolled the forum and several others and tried several attempted fixes without any luck during the last 21 days. Is there any way to get around this apparent SecureBoot lock, which appears to stay on even when turned off?

**Asus tech support says they don't support Windows 8, but that computer is hard blocked from installing new operating system** (which seems to be illegal, so I wonder if it is true), so no new operating system (they said 'downgraded operating system', even though I would view Ubuntu 13.04 an upgrade from Windows 8) is possible. Is this possible?

With Windows8 pre-installed you will have [disable 'fast startup']("http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html"). Disable Intel SRT. Check if you have RAID, for this check what mode is SATA is set to in BIOS/UEFI. Also disable 'fast boot'.

Then 'Shrink' the any partition from Windows only and create space for Ubuntu but do not create any partition for Ubuntu from Windows.

For More Info:[ http://ubuntuforums.org/showthread.php?t=2147295]("http://ubuntuforums.org/showthread.php?t=2147295") 

Please explain the bold part in your above quote. In your first sentence you say you have Windows8 pre-installed then you say Windows8 is not supported by ASUS tech.... please clarify.

---

### Post by Omizuk on 2013-08-24
Hi, I have also problem in trying to install Ubuntu on ASUS S400CA. When I plug in the USB and boot the computer from it I get the menu to try or install Ubuntu, but no matter what I choose I get a black screen and it doesn't seem that the computer is doing something..

How can I check it I have Intel SRT? How can I disable it? 

I haven't found in BIOS something that sounds like Intel SRT..

---

