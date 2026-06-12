---
title: "Windows inaccessible after 16.10 install"
date: 2017-01-20
forum: Installation &amp; Upgrades
---

### Post by john97 on 2017-01-20
EDIT  Managed to create a windows liveusb and restore windows. Had to reinstall grub but it didn't interfere with the windows install this time.
_______________________

I installed Ubuntu 16.10 alongside Windows 10 on a new partition on my second hard drive. During installation I got an error saying grub would have to be installed manually afterwards. After installation I could not boot to any OS nor access bios options (see [https://www.tonymacx86.com/threads/solved-gigabyte-boot-loop.48820/](https://www.tonymacx86.com/threads/solved-gigabyte-boot-loop.48820/) . I managed to reset the bios, boot to the ubuntu live usb and install grub with boot-repair. I can still not access windows though. Using boot-repair from the 16.10 install now returns an error asking me to disable secure boot, but I can find no secure boot setting in my bios options. I am unable to boot from any external media except the ubuntu live usb previously created on windows (I have tried a boot-repair live usb and a windows 10 installation iso burned to cd and usb).

After having no luck with the boot-repair live usb or the windows disk I just don't know what to try and would appreciate some help regaining access to windows.

I'm really not sure what's going on with my partitions (I have had other OS's installed and cloned the drive before) so I might as well post screenshots - it doesn't look that good to me to be honest. If there's any other information you need from me that could help, please ask.

Thanks   

[ATTACH=CONFIG]273274[/ATTACH] [ATTACH=CONFIG]273275[/ATTACH]  
The warning on sda1 is "failed to translate partition name".
I have no idea what partition sda2 is for. The warning is "Unable to detect file system! Possible reasons are:[INDENT=8]- The file system is damaged [/INDENT]
[INDENT=8]- The file system is unknown to GParted - There is no file system available (unformatted) - The device entry /dev/sda2 is missing"[/INDENT]
Sda3 is my C:\ and sda4 is apparently a recovery drive. 
The second drive seems pretty self explanatory.

---

### Post by efflandt on 2017-01-21
Apparently is normal for Win10 to have 1 small unknown partition, that is on the only Win10 computer I have (a laptop).

I have not used boot-repair, but I believe it has some way to upload results somewhere, so you could post a link to that here. That might allow someone to spot something right away, like whether you put grub in the mbr of one of the drives typical for legacy BIOS when Win10 is using UEFI. If grub is not using UEFI it is not going to see the Windows installation. Also make sure that Fast Boot (a form of hibernation) is disabled in Win10 itself or Linux or grub is not going to be able to access it.

If you go into the UEFI boot manager (using whatever hot key during boot) do you see something like the following in either order and possibly also USB if booting live/install system from that:
OS boot Manager (UEFI) - Windows Boot Manager (*drive_model*)
OS boot Manager (UEFI) - ubuntu (*drive_model*)
Boot From EFI file

In this case Win10 seems to insist on booting by default, so I have to go into Boot Manager menu by tapping Esc once per sec until menu, then F9 and select ubuntu like in list above. But that may vary on your computer.

---

### Post by oldfred on 2017-01-21
Did you leave Windows fast startup or always on hibernation on?
       Fast Start up off (always on hibernation)
[http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472](http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472)
[http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html](http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html)
[http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html](http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html)

Windows requires the system reserved. It is unformatted so gparted and other Linux tools show an error as it is not formatted.

 Microsoft suggested partitions including reserved partition for gpt & UEFI:
[https://msdn.microsoft.com/en-us/windows/hardware/commercialize/manufacture/desktop/configure-uefigpt-based-hard-drive-partitions](https://msdn.microsoft.com/en-us/windows/hardware/commercialize/manufacture/desktop/configure-uefigpt-based-hard-drive-partitions)
[https://msdn.microsoft.com/en-us/windows/hardware/commercialize/manufacture/desktop/windows-recovery-environment--windows-re--technical-reference](https://msdn.microsoft.com/en-us/windows/hardware/commercialize/manufacture/desktop/windows-recovery-environment--windows-re--technical-reference) 

       
 Order on drive is important: msftres
[http://en.wikipedia.org/wiki/Microsoft_Reserved_Partition](http://en.wikipedia.org/wiki/Microsoft_Reserved_Partition) 
    
Did you manually partition sdb as gpt? And you should include an ESP - efi system partition even if not immediately used as grub only installs to ESP on sda.
[https://help.ubuntu.com/community/DiskSpace](https://help.ubuntu.com/community/DiskSpace)       

 UEFI/gpt partitioning in Advance:
[http://askubuntu.com/questions/743095/how-to-prepare-a-disk-on-an-efi-based-pc-for-ubuntu](http://askubuntu.com/questions/743095/how-to-prepare-a-disk-on-an-efi-based-pc-for-ubuntu)

You show an error on sda1, you may need to run chkdsk from Windows or dosfsck from Linux.
Will be mounted if you are in your install. Best to use live installer.

 Must be unmounted
sudo dosfsck -t -a -w /dev/sda1
The -a seems to help in clearing dirty bit
[https://bbs.archlinux.org/viewtopic.php?id=164185](https://bbs.archlinux.org/viewtopic.php?id=164185)

---

