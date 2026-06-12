---
title: "Duel booting with windows 8"
date: 2013-10-31
forum: Installation &amp; Upgrades
---

### Post by chaosgodkarl on 2013-10-31
I've read that the installer pretty much handles everything when it comes to windows 8. Last time I tried, which was about 6 months? ago, it didn't recognize ubuntu, I had tried to modify stuff, and it worked for a while, but then my windows 8 glitched and I had to restore it to factory settings.

I have a dell HP Envy dv6 notebook with windows 8 - 64 bit. If I run the ubuntu installer is to dual boot, will it work fine with secureboot enabled / EFI mode / etc? not requiring anything special?

---

### Post by oldfred on 2013-11-01
It depends. There still are issues with Ultrabooks that use Intel SRT as it is a non-standard RAID. 
And each vendor has implemented UEFI differently even though it is a standard. 
Some do install without much issue, others with some issues and one or two only work in BIOS/CSM mode where then on every reboot you have to boot from UEFI menu and turn on or off UEFI/secure boot/CSM.

       HP Envy M6
[http://askubuntu.com/questions/346257/install-alongside-windows-8-is-not-working](http://askubuntu.com/questions/346257/install-alongside-windows-8-is-not-working)
HP Envy - Legacy boot seems to mean either UEFI or Legacy depending on which is found to boot from
[http://ubuntuforums.org/showthread.php?t=2167063](http://ubuntuforums.org/showthread.php?t=2167063)
Installing Ubuntu on HP Envy-6  Details of what worked post #11
[http://ubuntuforums.org/showthread.php?t=2123975](http://ubuntuforums.org/showthread.php?t=2123975)

---

