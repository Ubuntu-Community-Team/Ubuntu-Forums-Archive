---
title: "Recommended way of cloning entire SSD with UEFI"
date: 2018-06-07
forum: Installation &amp; Upgrades
---

### Post by invisibleshadowghost on 2018-06-07
Hey,

I'm running a LM 18.3 (and so an Ubuntu 16.04) as a dualboot with Windows 10 using UEFI to boot.

What would be the recommended way of cloning the entire SSD to a new (larger one), so I can boot from this one (it should be an exact clone). I thought about doing it the simplest way and using dd, but I have heard that that doesn't work that well with UEFI. Is that true? 

So what would you recommend? 

Beste regards

---

### Post by oldfred on 2018-06-07
I am not a fan of cloning.
Often easier to just re-install if just Ubuntu and restore from your backups. 
But Windows makes it more difficult and it generally needs a full image backup & restore.

If you do clone, you cannot leave old SSD plugged in when you reboot or you will have major issues.
You cannot have duplicate UUIDs or duplicate GUIDS. So old drive must be unplugged or at least all UUID & GUIDs changed which would make it non-bootable.

You may be able to use dd, but dd not normally recommended with gpt partitioned drives. Only can be used for entire drive as with gpt, you have GUID in partition table, backup partition table & partition that must match. Bit more difficult to change/fix.

       Backup windows before install - post by Mark Phelps
[http://ubuntuforums.org/showthread.php?t=2137439&p=12611710#post12611710](http://ubuntuforums.org/showthread.php?t=2137439&p=12611710#post12611710)
[http://www.macrium.com/reflectfree.asp](http://www.macrium.com/reflectfree.asp)
Another suggestion by srs5694
[http://www.runtime.org/driveimage-xml.htm](http://www.runtime.org/driveimage-xml.htm)
Microsoft Windows 8.1 reinstall/refresh
[http://windows.microsoft.com/en-us/windows-8/create-reset-refresh-media](http://windows.microsoft.com/en-us/windows-8/create-reset-refresh-media)

       
 Gui tool:
[http://www.teejeetech.in/p/aptik.html](http://www.teejeetech.in/p/aptik.html)
discussion of alternatives/strategy backups
[https://ubuntuforums.org/showthread.php?t=2368992&p=13677224#post13677224](https://ubuntuforums.org/showthread.php?t=2368992&p=13677224#post13677224)
[https://help.ubuntu.com/community/BackupYourSystem](https://help.ubuntu.com/community/BackupYourSystem)

---

