---
title: "Windows missing in grub"
date: 2015-08-22
forum: Installation &amp; Upgrades
---

### Post by argentum2f@gmail.com on 2015-08-22
I haven't booted into windows for probably over a year on this computer, but I want to use some programs on it, so I'm trying to get it to work.

Grub doesn't list windows as a option.

Output from boot-repair:
[http://paste.ubuntu.com/12150917/](http://paste.ubuntu.com/12150917/)

looks to me like the windows 7 partition is there on /dev/sda1

Running boot-repair hasn't helped.

---

### Post by oldfred on 2015-08-22
You are missing Windows boot files. Normally with Windows 7 they were in a separate 100MB boot partition, but do not have to be. So you can repair your sda1 NTFS partition to make it bootable.

You must move boot flag back to sda1 for your Windows repair CD or Flash drive to work. It only sees Windows NTFS primary partitions with boot flag as bootable.

         Vista/7/8 (with 7or 8 the first two files are usually in a separate 100MB boot partition)
[COLOR=#ff0000]/bootmgr /Boot/BCD[/COLOR] /Windows/System32/winload.exe 

You are missing the two files in red above. And that can only be fixed with Windows repairs, not from Linux. If you have a backup that would be good. Or an Windows install disk as you need to get into Windows repair console.

      
 f8 to get to repair install screen, if you can start to boot
[http://www.sevenforums.com/tutorials/666-advanced-boot-options.html](http://www.sevenforums.com/tutorials/666-advanced-boot-options.html)
[http://www.sevenforums.com/tutorials/681-startup-repair.html](http://www.sevenforums.com/tutorials/681-startup-repair.html)
[http://www.w7forums.com/startup-repair-t441.html](http://www.w7forums.com/startup-repair-t441.html)
[https://support.microsoft.com/en-us/kb/927392/](https://support.microsoft.com/en-us/kb/927392/)

If Windows repairs do the full repair, it will probably reinstall the Windows boot loader to MBR. So you need to use Ubuntu live installer and Boot-Repair or manually restore grub to MBR.
Then run this to add Windows to grub menu.
sudo update-grub


 How to restore the Ubuntu/XP/Vista/7 bootloader 
[https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader](https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader)
[https://help.ubuntu.com/community/Grub2/Installing#Fixing_a_Broken_System](https://help.ubuntu.com/community/Grub2/Installing#Fixing_a_Broken_System)

---

