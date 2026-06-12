---
title: "Can't access Windows 10/Dual Boot Ubuntu 16.04"
date: 2016-07-07
forum: Installation &amp; Upgrades
---

### Post by Tchris on 2016-07-07
I recently installed on my old Linux partition Ubuntu 16.04 and on my other partition I have my Windows 10. I can access Ubuntu but When I try to enter Windows on the Grub menu it freezes on the purple screen and nothing happens. I tried Boot repair and reinstalled Grub but still nothing good happened. 

Here is a [gparted]("http://postimg.org/image/x9zwlfk8x/") image
Here is the log from [URL="http://paste2.org/ZH715yPE"]Boot repair


[/URL]

---

### Post by oldfred on 2016-07-07
You have the red exclamation point on your NTFS partition.
Did you leave Windows 10 fast start up on? That is hibernation. Or after Windows partition resize did you not reboot immediately to run chkdsk.

Grub only boots working Windows, or Windows that is not hibernated nor needing chkdsk.
Easy to fix with your Windows repair flash drive. Boot-Repair can only fix minor Windows issues. 

But if you do not have a Windows flash drive you have to boot into Windows and turn off the fast boot.
You can restore the Windows boot loader to MBR with your Windows repair flash drive. 
Or you can temporarily add a Windows type boot loader syslinux to MBR withe Boot-Repair's advanced options, boot Windows and turn off fast start.
Then restore grib to MBR with Boot-Repair.

       How to restore the Ubuntu/XP/Vista/7/8/10 BIOS bootloader 
[https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader](https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader)
[http://askubuntu.com/questions/63610/how-do-i-remove-ubuntu-in-the-bios-boot-menu-uefi](http://askubuntu.com/questions/63610/how-do-i-remove-ubuntu-in-the-bios-boot-menu-uefi)
[https://help.ubuntu.com/community/Grub2/Installing#Fixing_a_Broken_System](https://help.ubuntu.com/community/Grub2/Installing#Fixing_a_Broken_System)

I may have mentioned that it is a good idea to have a Windows repair flash drive :) 
      
 [http://www.tenforums.com/tutorials/4200-recovery-drive-create-windows-10-a.html](http://www.tenforums.com/tutorials/4200-recovery-drive-create-windows-10-a.html)
[http://windows.microsoft.com/en-us/windows-10/create-a-recovery-drive](http://windows.microsoft.com/en-us/windows-10/create-a-recovery-drive) 
    [URL="https://help.ubuntu.com/community/Grub2/Installing#Fixing_a_Broken_System"]
[/URL]

---

### Post by Tchris on 2016-07-07
> **oldfred said:**
> You have the red exclamation point on your NTFS partition.
Did you leave Windows 10 fast start up on? That is hibernation. Or after Windows partition resize did you not reboot immediately to run chkdsk.

Not sure what I did wrong :)


> **oldfred said:**
> But if you do not have a Windows flash drive you have to boot into Windows and turn off the fast boot.
You can restore the Windows boot loader to MBR with your Windows repair flash drive. 
Or you can temporarily add a Windows type boot loader syslinux to MBR withe Boot-Repair's advanced options, boot Windows and turn off fast start.
Then restore grib to MBR with Boot-Repair.

       How to restore the Ubuntu/XP/Vista/7/8/10 BIOS bootloader 
[https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader](https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader)
[http://askubuntu.com/questions/63610/how-do-i-remove-ubuntu-in-the-bios-boot-menu-uefi](http://askubuntu.com/questions/63610/how-do-i-remove-ubuntu-in-the-bios-boot-menu-uefi)
[https://help.ubuntu.com/community/Grub2/Installing#Fixing_a_Broken_System](https://help.ubuntu.com/community/Grub2/Installing#Fixing_a_Broken_System)

I may have mentioned that it is a good idea to have a Windows repair flash drive :) 
      
 [http://www.tenforums.com/tutorials/4200-recovery-drive-create-windows-10-a.html](http://www.tenforums.com/tutorials/4200-recovery-drive-create-windows-10-a.html)
[http://windows.microsoft.com/en-us/windows-10/create-a-recovery-drive](http://windows.microsoft.com/en-us/windows-10/create-a-recovery-drive)[URL="https://help.ubuntu.com/community/Grub2/Installing#Fixing_a_Broken_System"]
[/URL]

Is there a way to fix this without using Windows? cause right now I have only access to my computer and I can't create this repair flash drive

> **oldfred said:**
> Or you can temporarily add a Windows type boot loader syslinux to MBR  withe Boot-Repair's advanced options, boot Windows and turn off fast  start.
Will this method work without windows and if so which of the links you provided describes this?Sorry,  I am  not very familiar with those things :)

---

### Post by oldfred on 2016-07-07
I provided 3 three links, I think any one should provide you with info on restoring a Windows boot loader.
Looks like middle link was for UEFI. Use either first or third.

       Fast Startup off (always on hibernation)
[http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472](http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472)
[http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html](http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html)
[http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.htmlold](http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.htmlold)

---

