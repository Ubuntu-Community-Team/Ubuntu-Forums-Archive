---
title: "GRUB2 - Dual boot Windows 7 and Ubuntu 15.10"
date: 2016-01-10
forum: Installation &amp; Upgrades
---

### Post by mats8 on 2016-01-10
Hi Installed Windows 7 and Ubuntu 15.10 with dualboot, bootloader is Grub2. The Grub is installed on a **NTFS drive** at 100 MB at  hd0,1 (sda1). hd0,2 (sda2) is Windows 7 installed and hd0,4 (sda4) is Ubuntu installed. The reason why Grub is installed on a NTFS drive is simlpe, it should be possible to modify default start from Windows. The reason for that is Ubuntu is serving as a Backup function with dd for hd0,2 (sda2). 
Windows 7 is not relyable at 100% and sometimes Windows doesn't start up. It hangs on boot and can be rebooted remote with a power shutdown 10 seconds and power on. The problem is that Windows tries to start again with same result.
My solution is (if there is a support for that), is it possible for GRUB to change boot order direct after Chainloader +1 => Windows7? If Windows hangs one more the system can be rebooted remote with power cycle and Ubuntu starts upp with changed boot order and flash hd0,2 (sda2) with dd=DiscDump. 
Is it possible? Any ideas?

---

### Post by oldfred on 2016-01-10
I think once grub chainloads to Windows it has passed control over to Windows. So then if it does not work you have to reboot.

You will also have to manually maintain your grub.cfg.
       How to: Create a Customized GRUB2 Screen that is Maintenance Free.- Cavsfan
[https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen](https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen)
[https://help.ubuntu.com/community/Grub2/CustomMenus](https://help.ubuntu.com/community/Grub2/CustomMenus)
[http://ubuntuforums.org/showthread.php?t=2076205](http://ubuntuforums.org/showthread.php?t=2076205)

---

### Post by mats8 on 2016-01-10
Hi oldfred

I have already an customized grub.cfg so there is no problem to add functionality, I don't know the limits of GRUB yet. Is it possible to load to a second GRUB to use a step by step method?

/Mats

---

### Post by yancek on 2016-01-10
> My solution is (if there is a support for that), is it possible for GRUB  to change boot order direct after Chainloader +1 => Windows7

No.  Once you select the windows entry in Grub, you are no longer using Grub but are using the windows bootloader.  Grub doesn't boot windows but chainloads it by pointing to the location on the drive where the windows boot code is or should be.  I don't see the purpose of putting Grub on an ntfs partition.  

> Is it possible to load to a second GRUB to use a step by step method?


Yes, you can chainload to another Grub on another partition.  Step by step method for what?

---

### Post by mats8 on 2016-01-11
Hi 
The reason why I mension the step by step method is if there are **not **possible to save settings in grub.cfg before Chainloader starts. The solution could be to start a new Grub with possibility to save grub.cfg in first Grub. I just want to change boot order *before *Windows is started. When Windows is succesfully started then Windows change back boot order again. If Windows doesn't starts correcly then a power cycle can do a hard reboot and Ubuntu is starting uo for recovery Windows partition.
The purpose of putting Grub on NTFS is as described, it should be possible to change boot order *even *from Windows. I know there is 3rd part software with possibility to read ext2, ext3 etc. But the focus must be: Can Grub support to change grub.cfg "live" before Windows is loaded? Or is it any better method for my request of solution?  
/Mats

---

### Post by oldfred on 2016-01-11
Still not sure what you want.
Do you want to change default boot to Windows?

With grub in a NTFS partition, you can write .bat files in Windows and .sh files in Ubuntu to modify grub boot stanza to change default boot. Normally we would not recommend changing grub.cfg as update script automatically update it when in Ubuntu's /boot folder.

---

### Post by mats8 on 2016-01-11
I want Grub to change boot order to Ubuntu (next boot) but load Windows direct. If Windows loads successfully, a Batch-file talk to watchdog and will remain power and change bootorder back to Windows in grub.cfg. 

If system hangs on Windows boot a watchdog will cut power after 90 minutes and boot again. Grub is now changed and will boot to Ubuntu. Ubuntu has a script and use DD to flash /dev/sda2 and change back boot order to Windows in grub.cfg and reboot. 

DD=DiscDump is using a working mirrorfile from a previous setup with working file system.

See attached file.

/Mats

---

### Post by oldfred on 2016-01-11
I do not know of a way to reset automatically if Windows does not boot.
You can set grub to boot one time to Windows and set reboot to then use Ubuntu, but you have to manually reboot.
Grub also will reboot to recovery mode if Ubuntu has not shutdown correctly, but does not know about Windows.
Perhaps better to then run Windows in virtual mode. Many recommend that unless you need really fast response to run games. I have not tried it.

---

### Post by mats8 on 2016-01-11
The watchdog is handle power toggle to restart Windows. That problem is solved. But after power toggles the Windows OS is starting up again with same result=stuck in boot and hangs. And watchdog do a power toggling and same problem over and over again. 
If there are a good solution for GRUB to set next prio the problem is solved. 
On GRUB manual page the are a list of commands:
[http://www.gnu.org/software/grub/manual/html_node/Command_002dline-and-menu-entry-commands.html#Command_002dline-and-menu-entry-commands](http://www.gnu.org/software/grub/manual/html_node/Command_002dline-and-menu-entry-commands.html#Command_002dline-and-menu-entry-commands)
Any idéa how to change boot priority with these commands?

---

### Post by oldfred on 2016-01-11
I have not tried it so do not know details, if you set Windows to the one time boot then it should defalt back to whatever is default boot:
> **grub-reboot** This command sets the default boot entry *for the next boot only*. The format of the command is the same as for grub-set-default (see above).
[https://help.ubuntu.com/community/Grub2/Setup#Specific_Entries](https://help.ubuntu.com/community/Grub2/Setup#Specific_Entries)

---

### Post by mats8 on 2016-01-14
I have tried the grub-reboot on this configuration. The switch does not work. 
Did a new installation with Ubuntu and GRUB on same partition with ext4 file system. 
Did a edit /etc/default/grub
Add these lines:
GRUB_DEFAULT=saved
GRUB_SAVEDEFAULT=true
Change GRUB_TIMEOUT=10 to GRUB_TIMEOUT=2
Uncomment GRUB_ DISABLE_RECOVERY=&#8221;true&#8221;
Edit /boot/grub/grub.cfg Change name &#8216;Windows loader /dev/sda1&#8217; to &#8216;WIN7&#8217;
Command grub-reboot WIN7
Copy /boot/grub/grubenv to /boot/boot/grubenv.Boot_WIN7_once

Installed software "Ext2 File System Driver for Windows" and mounted EXT4 system to permanent L:
Every login on Windows do a copy:
Copy /Y L:\boot\grub\grubenv.Boot_WIN7_once L:\boot\grub\grubenv

When this batchscript is replacing grubenv the settings remains=Boot WIN7 once then Ubuntu. If Windows hangs and power is cutted and reboot the Ubuntu starts up with a DD script and command grub-reboot WIN7. 

SOLVED!!!

---

### Post by oldfred on 2016-01-14
Thanks for details.
You can change to [Solved] so others that search forum find a good solution.

---

