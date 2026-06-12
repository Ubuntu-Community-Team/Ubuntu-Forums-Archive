---
title: "GRUB2 doesn't launch after turning on laptop"
date: 2015-01-24
forum: Installation &amp; Upgrades
---

### Post by vladislav7 on 2015-01-24
Hello everybody! I have some problems with switching 2 OS on my laptop. I installed Windows 8.1 then Ubuntu 14.10 64bit. Now I can't run Ubuntu, because Windows launch right away. I want to see the GRUB window to choose OS. I tried to use Boot-repair utility [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair), but it doesn't solve my problem. Report about that is [http://paste.ubuntu.com/9839570/](http://paste.ubuntu.com/9839570/). Help me, please:)

---

### Post by oldfred on 2015-01-24
Boot-Repair is saying you left fast boot or the always on hibernation on. You must turn that off if you want to dual boot.
       WARNING for Windows 8 Dual-Booters 
[http://ubuntuforums.org/showthread.php?t=1953674](http://ubuntuforums.org/showthread.php?t=1953674)
It defaults shutdown to a hybrid hibernation/off state for fast boot 
[http://www.kapilarya.com/how-to-enable-disable-fast-start-up-in-windows-8](http://www.kapilarya.com/how-to-enable-disable-fast-start-up-in-windows-8)
But then files may be corrupted similar to Windows 7 Hibernation:
[http://ubuntu-with-wubi.blogspot.ca/2012/09/windows-8-fast-start-and-hybrid-sleep.html](http://ubuntu-with-wubi.blogspot.ca/2012/09/windows-8-fast-start-and-hybrid-sleep.html)
[http://superuser.com/questions/144720/missing-files-when-windows-7-returns-from-hibernate-w-dual-boot](http://superuser.com/questions/144720/missing-files-when-windows-7-returns-from-hibernate-w-dual-boot)
Fast Startup off/hibernation
[http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html](http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html)
[http://www.kapilarya.com/how-to-enable-disable-fast-start-up-in-windows-8](http://www.kapilarya.com/how-to-enable-disable-fast-start-up-in-windows-8)
Fast boot is hidden.
If issues you may need these?
Control Panel -> Power icon -> Choose what power buttons do -> Change settings that are currently unavaliable, make sure fast startup is unchecked 
powercfg /h off

    
What model Asus?
Some other threads with Asus, may be similar issues?
 Asus ROG G75VW  with Windows 7 in UEFI boot mode.
[http://ubuntuforums.org/showthread.php?t=2251167](http://ubuntuforums.org/showthread.php?t=2251167)
Asus ASUS D550MA-DS01 - 14.04 only Ubuntu
[http://ubuntuforums.org/showthread.php?t=2223928](http://ubuntuforums.org/showthread.php?t=2223928)
 Installation of Ubuntu 14.04 on ASUS N550JV (a Status Report)
[http://ubuntuforums.org/showthread.php?t=2208852](http://ubuntuforums.org/showthread.php?t=2208852)
[http://ubuntuforums.org/showthread.php?t=2184383](http://ubuntuforums.org/showthread.php?t=2184383)
[https://wiki.archlinux.org/index.php/ASUS_N550JV](https://wiki.archlinux.org/index.php/ASUS_N550JV)
ASUS Zenbook UX301LAA ultrabook under Linux  - reboot, power issues
[http://www.phoronix.com/scan.php?page=news_item&px=MTcwOTQ](http://www.phoronix.com/scan.php?page=news_item&px=MTcwOTQ)

   UEFI may have setting that is Windows 8 or Windows 7, which probably is to turn off secure boot
 Asus X401U notebook
[http://ubuntuforums.org/showthread.php?t=2169462](http://ubuntuforums.org/showthread.php?t=2169462)
  [SOLVED] Dual Boot on Asus K55vd SX696H - 8 GB (Solved) EFI
[http://ubuntuforums.org/showthread.php?t=2151394](http://ubuntuforums.org/showthread.php?t=2151394)
Asus N56VJ-SH71-CD Shows default Windows partitions Post #25 install instructions
[http://ubuntuforums.org/showthread.php?t=2105622](http://ubuntuforums.org/showthread.php?t=2105622)

---

