---
title: "Grub crashed during dual boot install, now Windows 10 won't load"
date: 2017-06-14
forum: Installation &amp; Upgrades
---

### Post by mr.ryan on 2017-06-14
During my install of Ubuntu 16.04 grub crashed. I restarted my computer and finished the installation, but now when I select to load Windows Boot Manager (on/dev/sda1), from my boot menu, I get a message saying "**error cant load image**". I installed and ran boot repair, but this did not help. I don't have an install or recovery disk for windows either. I wish I could just abandon windows all together, but I need it for school. I can still see the windows disk on my Ubuntu desk top, and can still access all my files through it. [B]Please Help
  [https://paste2.org/FMfhjd7M](https://paste2.org/FMfhjd7M)
[/B]is the link boot repair gave me.

---

### Post by yancek on 2017-06-14
You forgot to post the link to the boot repair output so you need to run it again with the option to Create BootInfo Summary and post the link here.  Otherwise, all anyone can do here is to guess and there are a lot of possibilities.

---

### Post by oldfred on 2017-06-15
If Windows 10 was pre-installed then it is UEFI boot from gpt partitioned drive.
Then can you directly boot Windows from UEFI boot menu, often f10 or f12 check your manual.

You really need to have a Windows repair flash drive, so you can run the recovery console if needed.
       Windows 10 repair disk
[http://www.tenforums.com/tutorials/4200-recovery-drive-create-windows-10-a.html](http://www.tenforums.com/tutorials/4200-recovery-drive-create-windows-10-a.html)
[http://www.tenforums.com/tutorials/36083-system-repair-disc-create-windows-10-a.html](http://www.tenforums.com/tutorials/36083-system-repair-disc-create-windows-10-a.html)
Repair/backup/restore
[https://support.microsoft.com/en-us/instantanswers/3a747883-b706-43a5-a286-9e98f886d490/create-a-recovery-drive](https://support.microsoft.com/en-us/instantanswers/3a747883-b706-43a5-a286-9e98f886d490/create-a-recovery-drive)
[http://windows.microsoft.com/en-us/windows-10/windows-10-recovery-options](http://windows.microsoft.com/en-us/windows-10/windows-10-recovery-options) 
   How to: Create a Recovery Drive for reinstalling Windows 10 from Windows 10
[http://answers.microsoft.com/en-us/windows/wiki/windows_10-win_upgrade/how-to-create-a-recovery-drive-for-reinstalling/58df9c7d-84de-4652-9952-8bac34abc6c5](http://answers.microsoft.com/en-us/windows/wiki/windows_10-win_upgrade/how-to-create-a-recovery-drive-for-reinstalling/58df9c7d-84de-4652-9952-8bac34abc6c5)
[http://www.howtogeek.com/239312/how-to-restore-system-image-backups-on-windows-7-8-and-10/](http://www.howtogeek.com/239312/how-to-restore-system-image-backups-on-windows-7-8-and-10/)

---

### Post by mr.ryan on 2017-06-15
**[https://paste2.org/FMfhjd7M](https://paste2.org/FMfhjd7M)** is the url it gave me, thanks.

---

### Post by mr.ryan on 2017-06-15
Trying to use the boot override in UEFI doesn't do anything. I will look into the repair stick, thank you.

---

### Post by ubfan1 on 2017-06-15
The "Can't load image..." error when trying to start Windows happens on some machines when secure boot is enabled.  Either turn secure boot off, or boot Windows directly through the EFI menu (some function key at power-up, varies by machine). The link you posted is blank, it's just the site.

---

### Post by oldfred on 2017-06-15
Others have gotten just pastebin site, while many still have full report.
Please add your issue on missing report to this Boot-Repair bug.
Was Internet working?  I have working Internet & same issue when run from inside my main working install.
[https://bugs.launchpad.net/boot-repair/+bug/1692778](https://bugs.launchpad.net/boot-repair/+bug/1692778)

You probably have a copy of the Summary report in you /var/log/boot-sav/log folder.

---

### Post by mr.ryan on 2017-06-17
I figured out how to post the result file
[https://paste2.org/FMfhjd7M](https://paste2.org/FMfhjd7M)

---

### Post by oldfred on 2017-06-17
Shows standard UEFI boot.
Boot-Repair sees all the .efi boot files in the ESP - efi system partition and creates a new grub file 25_custom for all those entries which often just make a long list in grub menu. Many often edit 25_custom or turn it off, so not added to grub menu.

What brand/model system?
Do you get grub menu ok?

If issue is booting Windows from grub, it can be Secure boot, or Windows hibernation/fast start up is on.
Can you directly boot Windows from UEFI boot menu, often f10 or f12?
If so turn off fast start up.
       Fast Start up off (always on hibernation)
[http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472](http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472)
[http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html](http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html)
[http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html](http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html)

---

### Post by mr.ryan on 2017-06-17
I get the menu that lets me select from ubuntu or windows, but choosing windows just gives an error message that says cannot load image. Fast boot and secure boot are both off. I have an ASUS 303UB. Im not sure how to boot directly from the UEFI menu. I select Windows from the boot list and hit enter but it just returns to the same screen. My dual boot worked fine before there was a windows update that killed my dual boot. So I tried to reinstall Ubuntu and grub crashed during install. This is when the problem started. Thanks for your help

---

### Post by oldfred on 2017-06-17
Now with re-install not sure what issue may be.
Does Ubuntu boot ok from grub?

Run this, but I think issue is really Windows and you have to directly boot Windows from UEFI boot menu. check if f10 or f12, info should be in your manual. And you may immediately need to press f8 to get into Windows repair console.

sudo update-grub

Windows also turns on fast start up with major updates, so double check that it is off, or after any auto reboot by Windows.
       Windows 10 repair disk
[http://www.tenforums.com/tutorials/4200-recovery-drive-create-windows-10-a.html](http://www.tenforums.com/tutorials/4200-recovery-drive-create-windows-10-a.html)
[http://www.tenforums.com/tutorials/36083-system-repair-disc-create-windows-10-a.html](http://www.tenforums.com/tutorials/36083-system-repair-disc-create-windows-10-a.html)
Repair/backup/restore
[https://support.microsoft.com/en-us/instantanswers/3a747883-b706-43a5-a286-9e98f886d490/create-a-recovery-drive](https://support.microsoft.com/en-us/instantanswers/3a747883-b706-43a5-a286-9e98f886d490/create-a-recovery-drive)
[http://windows.microsoft.com/en-us/windows-10/windows-10-recovery-options](http://windows.microsoft.com/en-us/windows-10/windows-10-recovery-options)

---

### Post by mr.ryan on 2017-06-19
Here is the link **[https://paste2.org/FMfhjd7M](https://paste2.org/FMfhjd7M)**

---

### Post by oldfred on 2017-06-19
You show UEFI boot of both Ubuntu & Windows.
And  a left over /EFI/fedora folder in the ESP, that you can delete.

what brand/model system?

Can you boot Ubuntu from UEFI boot menu, often f10 or f12, check your manual.

---

### Post by mr.ryan on 2017-06-26
Here's the print out when I ran update-grub. [https://paste2.org/21ZLXmZx](https://paste2.org/21ZLXmZx)
Didn't seem to change anything though.

---

### Post by ubfan1 on 2017-06-26
Please figure out how to boot using the UEFI menu (some function key at power-up, maybe F12 or F10), and try to boot Windows.  If that fails, grub has been eliminated as a cause of the problem, and you might have a filesystem problem.

---

### Post by mr.ryan on 2017-06-27
I assume you mean use the boot override in the UEFI menu. I have tried that, and it doesn't do anything for windows.

---

### Post by oldfred on 2017-06-27
If you are directly booting Windows from  UEFI boot menu and Windows still does not boot then it is only a Windows issue. And then you need to see if you can run Windows repairs using f8 to get into Windows repair console or use your Windows repair/recovery flash drive to make repairs.

       Windows 10 repair disk
[http://www.tenforums.com/tutorials/4200-recovery-drive-create-windows-10-a.html](http://www.tenforums.com/tutorials/4200-recovery-drive-create-windows-10-a.html)
[http://www.tenforums.com/tutorials/36083-system-repair-disc-create-windows-10-a.html](http://www.tenforums.com/tutorials/36083-system-repair-disc-create-windows-10-a.html)
Repair/backup/restore
[https://support.microsoft.com/en-us/instantanswers/3a747883-b706-43a5-a286-9e98f886d490/create-a-recovery-drive](https://support.microsoft.com/en-us/instantanswers/3a747883-b706-43a5-a286-9e98f886d490/create-a-recovery-drive)
[http://windows.microsoft.com/en-us/windows-10/windows-10-recovery-options](http://windows.microsoft.com/en-us/windows-10/windows-10-recovery-options)

---

### Post by mr.ryan on 2017-06-28
The F8 key does not put me into Windows repair. I looked it up on-line and read that no longer works. I don't have a install or repair disk, as Windows 10 was pre-installed on my machine, and I cannot find a way to make a repair disk without being able to first boot into Windows to create the disk. Everything I read requires the user to be able to access Windows in some way, to use the boot repair tools. I also cannot boot windows from the boot override in the UEFI menu.

---

### Post by oldfred on 2017-06-28
I think you can download the full Windows installer which includes a repair console. New license required within 30 days if used to install. But UEFI systems have Microsoft Product Key embedded in UEFI. Not sure if then Windows installer will install the Microsoft copy or if key is only valid for the OEM or vendor version of Windows which would also include any special drivers. 

But there are a lot of posts of users finding it difficult to create Windows bootable flash drives from Ubuntu. Best to use another Windows system. If you have access to another Windows 10 system, friend, work, school you can use that to create a repair disk.

       Windows 10 ISO
[URL="https://www.microsoft.com/en-us/software-download/windows10ISO"]https://www.microsoft.com/en-us/software-download/windows10ISO
[/URL]
 How to: Create a Recovery Drive for reinstalling Windows 10 from Windows 10
[http://answers.microsoft.com/en-us/windows/wiki/windows_10-win_upgrade/how-to-create-a-recovery-drive-for-reinstalling/58df9c7d-84de-4652-9952-8bac34abc6c5](http://answers.microsoft.com/en-us/windows/wiki/windows_10-win_upgrade/how-to-create-a-recovery-drive-for-reinstalling/58df9c7d-84de-4652-9952-8bac34abc6c5)
[http://www.howtogeek.com/239312/how-to-restore-system-image-backups-on-windows-7-8-and-10/](http://www.howtogeek.com/239312/how-to-restore-system-image-backups-on-windows-7-8-and-10/) 
      
 Windows bootable USB from Ubuntu BIOS or UEFI, uses grub for BIOS boot.
[http://onetransistor.blogspot.ch/2014/09/make-bootable-windows-usb-from-ubuntu.html](http://onetransistor.blogspot.ch/2014/09/make-bootable-windows-usb-from-ubuntu.html)
[http://www.omgubuntu.co.uk/2017/06/create-bootable-windows-10-usb-ubuntu](http://www.omgubuntu.co.uk/2017/06/create-bootable-windows-10-usb-ubuntu) 
    


[URL="https://www.microsoft.com/en-us/software-download/windows10ISO"]
[/URL]

---

### Post by mr.ryan on 2017-07-05
Managed to create a recovery drive off another Windows 10 system and then used a restore point to finally get Windows back. Now all I have to do is reinstall Ubuntu along side Windows AGAIN! Thanks for your help.

---

