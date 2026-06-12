---
title: "dual boot oot Win 10 (from Win7) and kubuntu 14.04 LTS"
date: 2015-07-29
forum: Installation &amp; Upgrades
---

### Post by subcook on 2015-07-29
I am running kubuntu 14.04 and Win7 (obviously as far as partitioning, windows is first on the HDD)

Considering on upgrading my Win7 to Win10 ... my question is this .......

I know that kubuntu will not be available when I boot once upgraded to win10.  all I need to do is boot off of a Gparted disk and reinstall Grub2, right ?, tho grub files to make the bootsplash the way I want it needs to be adjusted, I get that, but when I turn on my copmuter it should give me the option of which OS to choose, right ?

thanks in advance !

---

### Post by oldfred on 2015-07-29
BIOS or UEFI?

If BIOS you should just have to restore grub to MBR.
 How to restore the Ubuntu/XP/Vista/7 bootloader 
[https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader](https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader)
[https://help.ubuntu.com/community/Grub2/Installing#Fixing_a_Broken_System](https://help.ubuntu.com/community/Grub2/Installing#Fixing_a_Broken_System)

But Windows 8 and later has its fast startup, which really is just always on hibernation. 
You must have that off to dual boot.
      
 Fast Startup off/hibernation
[http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html](http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html)
[http://www.kapilarya.com/how-to-enable-disable-fast-start-up-in-windows-8](http://www.kapilarya.com/how-to-enable-disable-fast-start-up-in-windows-8)

---

### Post by Mark Phelps on 2015-07-29
Personally, I would hold off updating to Win10 for at least a couple of days.  Folks in the Windows 10 forums are reporting LOTS of failed updates, and not many are reporting success with everything still working.  It's probably going to take MS a few days to tune the update process, probably by pushing out another Windows Update.

You have a year from today to do the free upgrade -- best NOT to rush into it.

---

### Post by oldfred on 2015-07-29
Mark is usually the one to remind users about backups.
If upgrading and it fails, do you have a way to restore system to how it was before? 
And separately all your data backed up?

       Backup windows before install - post by Mark Phelps
[http://ubuntuforums.org/showthread.php?t=2137439&p=12611710#post12611710](http://ubuntuforums.org/showthread.php?t=2137439&p=12611710#post12611710)
[http://www.macrium.com/reflectfree.asp](http://www.macrium.com/reflectfree.asp)
Another suggestion by srs5694
[http://www.runtime.org/driveimage-xml.htm](http://www.runtime.org/driveimage-xml.htm)
Microsoft Windows 8.1 reinstall/refresh
[http://windows.microsoft.com/en-us/windows-8/create-reset-refresh-media](http://windows.microsoft.com/en-us/windows-8/create-reset-refresh-media)

---

