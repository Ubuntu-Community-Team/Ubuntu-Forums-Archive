---
title: "Installing Ubuntu alongside Windows 8.1 on a new MX100 SSD inside a Lenovo T440s"
date: 2014-08-23
forum: Installation &amp; Upgrades
---

### Post by jawknee530 on 2014-08-23
I have a lenovo T440s with windows 8.1. I just purchased a Crucual MX100 SSD and plan to put it in the Levovo. Can I just reinstall windows 8.1 on the new SSD under UEFI and then install Ubuntu after? I'm not sure how Ubuntu works alongside 8.1 and UEFI (only ever single booted it with a legacy bios) and don't know if I would have to install in legacy mode or something. Any info or direction would be appreciated.

---

### Post by oldfred on 2014-08-23
With UEFI it is just a lot more choices which can make it seem more complex.

With BIOS you may have to change some BIOS settings but many just boot BIOS.

With UEFI you have three boot choices, UEFI with secure boot, UEFI and Legacy/CSM/BIOS and not all systems make it clear which switches change those modes. Some even require passwords to allow you to use some other than secure boot.

And then in Windows you have to make sure fast boot is off which is always on hibernation.

As with any system change, backups are required, but with all the issues, backups are even more important. 
You at the minimum want the efi partition and the full Windows image. Perhaps also the DVD set to restore system to as purchased in case later you want to sell system and make sure it has none of your data.

Only use Windows to shrink Windows and reboot immediately so it can run chkdsk and update for its new size. Make sure fastboot is off.

May be similar model:
 Lenovo s440
[http://ubuntuforums.org/showthread.php?t=2189531](http://ubuntuforums.org/showthread.php?t=2189531)

Also see link in my signature for lots of info and many useful links.

---

### Post by jawknee530 on 2014-08-24
Thanks for the info. So my best bet would be to make a usb recovery drive from Windows since my laptop doesn't have a disc drive it seems. Does a revocery drive made in Windows 8.1 just make an OS recovery or is it an OEM specific image? Then the steps after that would be install new ssd, use the recovery drive to reinstall windows, turn off fast startup, shrink the C drive in Windows, reboot system back into Windows, reboot to a usb stick with Ubuntu finally to install it. That's all correct right?

Once I get to that point I'm a bit lost though. Do I have to do a custom install to make sure the correct boot partition is chosen or should doing the "install alongside another OS" option take care of everything fine?

---

### Post by oldfred on 2014-08-24
Not sure with your system.

But generally the vendor recovery is just the image of your hard drive as purchased. As such it is preconfigured just for your system and would not work on other systems. And the Microsoft product key is embedded in the UEFI and only works for your vendor version of Windows. You cannot use any other copy of Windows without purchasing a new product key.

If you have updated Windows and made configuration changes, installed software etc, it often is better to have a image backup that you can restore, so you do not have to reconfigure again. You also want to backup efi partition.

       Backup windows before install - post by Mark Phelps
[http://ubuntuforums.org/showthread.php?t=2137439&p=12611710#post12611710](http://ubuntuforums.org/showthread.php?t=2137439&p=12611710#post12611710)
[http://www.macrium.com/reflectfree.asp](http://www.macrium.com/reflectfree.asp)
Another suggestion by srs5694
[http://www.runtime.org/driveimage-xml.htm](http://www.runtime.org/driveimage-xml.htm)

 Windows 8 UEFI repair USB must be FAT32, not for reinstall, just repairs
[http://www.eightforums.com/tutorials/2855-system-repair-disc-create-windows-8-a.html](http://www.eightforums.com/tutorials/2855-system-repair-disc-create-windows-8-a.html)
[http://www.winhelp.us/create-a-recovery-drive-in-windows-8.html#USB](http://www.winhelp.us/create-a-recovery-drive-in-windows-8.html#USB)
[http://social.msdn.microsoft.com/Forums/en-US/samsungpcgeneral/thread/e7ed293e-b565-44ee-a536-166dddf32205/](http://social.msdn.microsoft.com/Forums/en-US/samsungpcgeneral/thread/e7ed293e-b565-44ee-a536-166dddf32205/)
[http://www.ghacks.net/2012/11/01/how-to-create-a-windows-8-system-repair-disc/](http://www.ghacks.net/2012/11/01/how-to-create-a-windows-8-system-repair-disc/)

It seems like most Windows 8.1 systems are not now seen correctly by the Ubuntu auto installer. Only use Something Else to be safe. But it does require a bit more effort as you have to create and mount your own partitions, minimum is / (root) and swap.

       UEFI install,windows 8 with Something Else screen shots
[http://www.everydaylinuxuser.com/2014/05/install-ubuntu-1404-alongside-windows.html](http://www.everydaylinuxuser.com/2014/05/install-ubuntu-1404-alongside-windows.html)
But I suggest using Windows to shrink Windows and reboot Windows first. But do not create any partitions with Windows disk tools.
[http://www.dedoimedo.com/computers/dual-boot-windows-8-ubuntu.html](http://www.dedoimedo.com/computers/dual-boot-windows-8-ubuntu.html)

[https://help.ubuntu.com/community/DiskSpace](https://help.ubuntu.com/community/DiskSpace)

---

### Post by jawknee530 on 2014-08-24
Well I'm not starting from a good image right now. Last semester I needed to use Linux for a programming class so I managed to hack my way to a crappy "dual boot" set up on the currently installed HDD. I didn't know about fast startup at the time so I switched the BIOS to legacy mode and installed xubuntu that way. When I want to go back into Windows I go into the settings and switch back to UEFI then have to switch it back to legacy when I want to use xubunutu. Neither sees the other and there's no option to select an OS on boot. Don't know how or why it worked but it got me through the semester and now I'm replacing the HDD with an SSD and want an actual dual boot set up. Imaging the current set up wont work out.

---

### Post by oldfred on 2014-08-24
Only your image will work as it has your product key, unless you are purchasing a new copy of Windows. If Windows works then the backup should be good. Otherwise you have to create the vendor image DVD set from recovery partition, restore that and totaly reconfigure again.

Even if in different boot modes you should be able to boot from the one time boot key. But best if both are in same boot mode.

       GPT Advantages (older but still valid)  see post#2 by srs5694:
[http://ubuntuforums.org/showthread.php?t=1457901](http://ubuntuforums.org/showthread.php?t=1457901)
[https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT](https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT)
UEFI Advantages
[http://askubuntu.com/questions/446968/legacy-vs-uefi-help](http://askubuntu.com/questions/446968/legacy-vs-uefi-help)

This seems to be one work around for your type system.

 Another lenovo solution copy grubx64.efi to bootx64.efi & boot hard drive not any other entry
[http://ubuntuforums.org/showthread.php?t=2185869&p=12884470#post12884470](http://ubuntuforums.org/showthread.php?t=2185869&p=12884470#post12884470)

---

