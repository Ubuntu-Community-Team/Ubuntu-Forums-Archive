---
title: "Can't boot in windows 10 after installed ubunt 16 LTS"
date: 2017-03-27
forum: Installation &amp; Upgrades
---

### Post by seemo2 on 2017-03-27
Hello everyone

I have windows 10 and i installed ubuntu 16 LTS in separate partition , ubuntu installed successfully and windows 10 loader appear in boot but when i click on it nothing happen and i can log in ubuntu only , i tried many methods like install grub again and repair my windows but all faild and i tried boot repair it gives me this link :
 
[http://paste2.org/dA9EeMyz](http://paste2.org/dA9EeMyz)

please help me

---

### Post by oldfred on 2017-03-28
It looks like you have a newer UEFI system, but Windows installed in BIOS boot mode.
But you did not post entire script from Boot-Repair, so not sure of all details.

Most common issue is that you did not turn off Windows fast start up or its always on hibernation.
And it can be an on-going issue as Windows updates will probably turn it back on and often reinstall Windows boot loader to MBR.
So you need a Windows 10 Repair disk and the Ubuntu live installer, so you can update MBR with whichever system you need to boot to make repairs.
If Windows has not updated, it still should boot thru grub menu.

       Fast Start up off (always on hibernation)
[http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472](http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472)
[http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html](http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html)
[URL="http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html"]http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html

[/URL]
 How to restore the Ubuntu/XP/Vista/7/8/10 BIOS bootloader 
[https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader](https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader)
[https://help.ubuntu.com/community/Grub2/Installing#Fixing_a_Broken_System](https://help.ubuntu.com/community/Grub2/Installing#Fixing_a_Broken_System) 

      
 [http://www.tenforums.com/tutorials/4200-recovery-drive-create-windows-10-a.html](http://www.tenforums.com/tutorials/4200-recovery-drive-create-windows-10-a.html)
[http://windows.microsoft.com/en-us/windows-10/create-a-recovery-drive](http://windows.microsoft.com/en-us/windows-10/create-a-recovery-drive) 
    [URL="http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html"]
[/URL]

---

