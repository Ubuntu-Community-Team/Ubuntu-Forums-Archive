---
title: "Some questions about UEFI"
date: 2013-09-09
forum: Installation &amp; Upgrades
---

### Post by Romu on 2013-09-09
Hi,
As I need Windows for personal stuff, I wiped my Dell XPS13 SSD, and installed Windows 8 in UEFI, with SecureBoot disabled.

I created an UEFI compliant USB key. From the UEFI documentation on the Ubuntu Wiki, I checked the key starts in UEFI. But when Ubiquity stands to the partitionning page, I don't have the "Install alongside Windows" option. Is this normal? (Tested with 13.04 and 13.10 Beta).

I've also seen that when the Ubuntu Live interface is started, the screen is very very dark, even if the backlight shortcut is at maximum.

Any help? Thanks.

---

### Post by oldfred on 2013-09-09
Is Intel SRT still on or RAID meta-data still on drives? Make sure fastboot is off also in Windows.

Best to use Windows to shrink Windows partition and create unallocated space for Ubuntu, reboot Windows so it can make its repairs. Some install to hard drive, others who are primarily Ubuntu users install / (root) onto SSD.

See Ultrabook sub heading in link in my signature.

Different models of Dells seem to be very similar for install process.
 Dell 14z & 17r with Intel SRT
[http://ubuntuforums.org/showthread.php?t=2038121](http://ubuntuforums.org/showthread.php?t=2038121)
Dell UltraBook - Instructions & Details in Post #15 & 16 Devine Shine
[http://ubuntuforums.org/showthread.php?t=2144853](http://ubuntuforums.org/showthread.php?t=2144853)
Installing Ubuntu 12.10 x64 on Dell XPS 13 Alongside Windows from USB New user with Details post 10
[http://ubuntuforums.org/showthread.php?t=2108450](http://ubuntuforums.org/showthread.php?t=2108450)
Dell Inspiron 17R SE -  12.04.2 but otherwise similar to XPS13 above
[http://ubuntuforums.org/showthread.php?t=2125701](http://ubuntuforums.org/showthread.php?t=2125701)
Dell XPS 14 Ultrabook what works
[http://ubuntuforums.org/showthread.php?t=2116597](http://ubuntuforums.org/showthread.php?t=2116597)
      
 Dell XPS13 general info mega-thread
[http://ubuntuforums.org/showthread.php?t=1932965](http://ubuntuforums.org/showthread.php?t=1932965)
Question about Dell's Ubuntu Preloaded XPS 13 Developer Laptop Link to review, Sputnik
[http://ubuntuforums.org/showthread.php?t=2106590](http://ubuntuforums.org/showthread.php?t=2106590)

---

