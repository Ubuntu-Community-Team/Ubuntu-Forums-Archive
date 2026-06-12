---
title: "Problems in getting Ubuntu 13.04 and Windows 8 to dual boot after using boot-repair"
date: 2013-08-03
forum: Installation &amp; Upgrades
---

### Post by parthjoshi.iitm on 2013-08-03
I have been using ubuntu for a while but I recently bought a new HP Envy Touchsmart laptop with Windows 8. I have earlier been able to install ubuntu along with windows quite easily but was unable to do so this time. After extensive searching on online forums I was able to install ubuntu following the guidelines on this blog [http://blog.brianhosie.com/2013/05/dual-boot-ubuntu-1204-and-windows-8-on.html](http://blog.brianhosie.com/2013/05/dual-boot-ubuntu-1204-and-windows-8-on.html). I manged to install ubuntu 13.04 and after a bios upgrade managed to get the wifi working as well. However, some problems occurred after I restored my backed up data and I had to re-install ubuntu. Fortunately I had created a separate partition for my /home directory and my data was not last. But now my computer boots directly into Windows 8 without giving me the option to boot ubuntu. To open Ubuntu I need to go into my BIOS boot options (by pressing Esc followed by F9) and select Ubuntu after which I enter the GRUB start screen. I've tried doing the recommended repair option in boot-repair but it doesn't solve my problem. Here's the boot-repair report [http://paste.ubuntu.com/5940617/](http://paste.ubuntu.com/5940617/). At the end of the running boot-repair it gives me the following info 

[FONT=courier new]The boot files of [COLOR=#666666][[/COLOR]The OS now in use - Ubuntu 13.04[COLOR=#666666]][/COLOR] are far from the start of the disk. Your BIOS may not detect them. You may want to retry after creating a /boot partition [COLOR=#666666]([/COLOR]EXT4, >200MB, start of the disk[COLOR=#666666])[/COLOR]. This can be performed via tools such as gParted. Then [COLOR=#AA22FF]**select **[/COLOR]this partition via the [COLOR=#666666][[/COLOR]Separate /boot partition:[COLOR=#666666]][/COLOR] option of [COLOR=#666666][[/COLOR]Boot Repair[COLOR=#666666]][/COLOR]. [COLOR=#666666]([/COLOR]https://help.ubuntu.com/community/BootPartition[/FONT][COLOR=#666666][FONT=courier new])
[/FONT]
[/COLOR][FONT=arial]I can't create a /boot partition near the start of the disk as my windows partitions are there and I'm apprehensive about fiddling around with them (also I don't exactly know how). Any help will be greatly appreciated. If anyone needs additional info, I'd be happy to provide it.[/FONT]

---

### Post by oldfred on 2013-08-04
I have not seen a UEFI system need the separate /boot partition. Some BIOS based systems need that if grub gives error on booting like grub rescue or sometimes out of disk error.

If you set ubuntu as default in UEFI does it not reboot to that. Or when you boot Windows is it always running repairs and resetting the UEFI default back to Windows? That may be fast boot or hibernation related?

       WARNING for Windows 8 Dual-Booters
[http://ubuntuforums.org/showthread.php?t=1953674](http://ubuntuforums.org/showthread.php?t=1953674)
It defaults shutdown to a hybrid hibernation/off state for fast boot 
[http://www.kapilarya.com/how-to-enable-disable-fast-start-up-in-windows-8](http://www.kapilarya.com/how-to-enable-disable-fast-start-up-in-windows-8)
But then files may be corrupted similar to Windows 7 Hibernation:
[http://ubuntu-with-wubi.blogspot.ca/2012/09/windows-8-fast-start-and-hybrid-sleep.html](http://ubuntu-with-wubi.blogspot.ca/2012/09/windows-8-fast-start-and-hybrid-sleep.html)
[http://superuser.com/questions/144720/missing-files-when-windows-7-returns-from-hibernate-w-dual-boot](http://superuser.com/questions/144720/missing-files-when-windows-7-returns-from-hibernate-w-dual-boot)
Fast Startup off/hibernation
[http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html](http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html)
Force removal of hiberfil from Ubuntu
[http://www.hecticgeek.com/2013/01/mount-windows-8-partition-ubuntu-hybrid-boot/](http://www.hecticgeek.com/2013/01/mount-windows-8-partition-ubuntu-hybrid-boot/)

---

