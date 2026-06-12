---
title: "Ubuntu 18.04 LTS and Windows 10 Dual Boot Hung up"
date: 2019-01-12
forum: Installation &amp; Upgrades
---

### Post by G0at1 on 2019-01-12
Hello,

I did a fresh Windows 10 install and allocated 110 GB during the partitioning/installation process. Then I installed Ubuntu 18.04 LTS along side it which has another 140 GB. I was able to dual boot a couple of times but mainly use Ubuntu now. I can no longer load Windows though and not sure what happened all of a sudden. When I select Windows 10 on the boot screen, my system gets hung up and all I see is the faint orange color of what it looks like right before Ubuntu tries to load. If I reset and select Ubuntu, I'm able to boot right up.

Any ideas how to fix this?

Thank you!

---

### Post by oldfred on 2019-01-12
May be best to see details, use ppa version with your live installer or any working install,  not older Boot-Repair ISO:
Please copy & paste link to the summary report ( not post full report), the auto fix sometimes can create more issues.
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by G0at1 on 2019-01-12
Not savvy enough to understand most of what you said (ppa?) lol; but I think this is what you're looking for? <removed by OP>

By the way, now my Windows 10 partition is showing on my Ubuntu desktop as "110 GB Volume" for some reason...

And... there's my hard drive serial # on a public forum. That can't be good, can it?

---

### Post by oldfred on 2019-01-12
It looks like you have a newer UEFI system, but have Windows & Ubuntu installed in the older BIOS/MBR configuration.
        CSM - UEFI Compatibility Support Module (CSM), which emulates a BIOS mode  
UEFI has the old BIOS mode, for backwards compatibility.

Grub only boots working Windows. Or Windows that is not hibernated. And Windows default is fast start up which sets a hibernation flag, so the Linux NTFS driver will  not fully see the NTFS partitions. You need to boot Windows and turn off fast start up.
But BIOS installs of new Windows 10 are not particularly dual boot friendly. With UEFI, you would only have to directly boot Windows from UEFI boot menu. But with BIOS you only have one MBR to boot from.
So you need to use your Windows repair disk to temporarily install a Windows boot loader, turn off fast start up, or make other Windows repairs. Then restore grub2's boot loader to MBR to boot Ubuntu & a working Windows. Often easier to use Boot-Repair to restore grub.

      
 Fast Start up off (always on hibernation), note that Windows turns this back on with updates
[http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472](http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472)
[http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html](http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html)
[http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html](http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html)

UEFI has two boot modes, both for installs and separately for USB flash drive or DVD installers. How you boot install media UEFI or BIOS is then how it installs.
And UEFI and BIOS are not really compatible, you can boot from UEFI mode to change modes. And you cannot have both modes on one drive if one of the installs is Windows.

---

### Post by G0at1 on 2019-01-12
I don’t have a windows repair disk. Can I boot from the install disk and install the boot loader? If so, how? I can’t boot into windows to try any of the steps in the 3 links you provided unfortunately. Should I turn off any of the secure boot options in UEFI? Do I need to do anything with the Boot repair program that I installed? My knowledge is very limited with this stuff...

---

### Post by oldfred on 2019-01-12
I do turn off UEFI Secure boot settings for now. In future, I may change and turn it back on.
Its been more of a marketing label for Microsoft. When you have a system that is known for having virus what better than having "Secure Boot" in name. But boot virus' are rare. Largest boot virus with BIOS years ago was actually by Sony, designed to prevent you from having music on PC, that you did not pay for, even if you had the DVD.

Do not really know newer Windows. If you have full installer you may be able to boot into repair/recovery mode with f8?
       Windows 10 repair disk
[http://www.tenforums.com/tutorials/4200-recovery-drive-create-windows-10-a.html](http://www.tenforums.com/tutorials/4200-recovery-drive-create-windows-10-a.html)
[http://www.tenforums.com/tutorials/36083-system-repair-disc-create-windows-10-a.html](http://www.tenforums.com/tutorials/36083-system-repair-disc-create-windows-10-a.html)
Repair/backup/restore
[https://support.microsoft.com/en-us/instantanswers/3a747883-b706-43a5-a286-9e98f886d490/create-a-recovery-drive](https://support.microsoft.com/en-us/instantanswers/3a747883-b706-43a5-a286-9e98f886d490/create-a-recovery-drive)
[http://windows.microsoft.com/en-us/windows-10/windows-10-recovery-options](http://windows.microsoft.com/en-us/windows-10/windows-10-recovery-options)

---

### Post by G0at1 on 2019-01-12
Thank you for the help. Looks like secure boot is already disabled. Looks like also I can’t fix it using the install disk. I’ll see if I can install windows 7 over 10 and see what happens.

---

### Post by oldfred on 2019-01-12
If reinstalling, you may want to use UEFI boot mode.
As I understand it the original Windows 7 DVD had to be copied to flash drive and files moved around to make it UEFI bootable. But an update to the Windows 7 installer has the UEFI boot option.
How you boot install media for both Windows & Ubuntu is then how it installs. From UEFI you should see two option options, one UEFI:name and the other just name where name is name, label or brand of the flash drive.

Windows in UEFI mode uses the newer gpt partitioning, where Windows in BIOS boot mode uses the now 35 year old MBR partitioning with its 4 primary partition limits. The gpt also has a backup partition table at end of drive which can help if issues.

       How to: Create a Recovery Drive for reinstalling Windows 10 from Windows 10
[http://answers.microsoft.com/en-us/windows/wiki/windows_10-win_upgrade/how-to-create-a-recovery-drive-for-reinstalling/58df9c7d-84de-4652-9952-8bac34abc6c5](http://answers.microsoft.com/en-us/windows/wiki/windows_10-win_upgrade/how-to-create-a-recovery-drive-for-reinstalling/58df9c7d-84de-4652-9952-8bac34abc6c5)
[URL="http://www.howtogeek.com/239312/how-to-restore-system-image-backups-on-windows-7-8-and-10/"]http://www.howtogeek.com/239312/how-to-restore-system-image-backups-on-windows-7-8-and-10/

      [/URL]
 BIOS & UEFI Windows partitions, note system has totally different format  & meaning between BIOS & UEFI
[https://msdn.microsoft.com/en-us/library/windows/hardware/dn898504%28v=vs.85%29.aspx](https://msdn.microsoft.com/en-us/library/windows/hardware/dn898504%28v=vs.85%29.aspx) & 
[https://msdn.microsoft.com/en-us/library/windows/hardware/dn898510%28v=vs.85%29.aspx#RecommendedPartitionConfigurations](https://msdn.microsoft.com/en-us/library/windows/hardware/dn898510%28v=vs.85%29.aspx#RecommendedPartitionConfigurations) 
    [URL="http://www.howtogeek.com/239312/how-to-restore-system-image-backups-on-windows-7-8-and-10/"]
[/URL]

---

### Post by G0at1 on 2019-01-13
You know what I discovered? On the boot screen, if I scroll down to Windows 10 > Press E > Press Esc > press Enter to select Windows 10, the computer boots to it.... ? Isn't that strange?

---

### Post by Balamku on 2019-01-13
I do have a dual boot and on my notebook and installed it on a friends machine alongside Windows 10 using UEFI with a similar behaviour. 
I had to run the Boot Repair Tool with the suggested settings, found this in a thread and it resolved the boot issues. [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
(In Windows I had to run the advanced boot options to reboot into Ubuntu to run the repair). 
Unfortunately, as stated before, I have to fix the boot every time I start Windows and it runs an update.... 
This is why I am researching to run Windows in VM/ Wine, I only use it for one programme once a month and the updates are a pain.

---

### Post by G0at1 on 2019-01-13
That's actually a good idea to run Windows in VM! I found this and might give it a try. I can't escape Windows either! :( 
[https://www.howtogeek.com/howto/18768/run-windows-in-ubuntu-with-vmware-player/](https://www.howtogeek.com/howto/18768/run-windows-in-ubuntu-with-vmware-player/)

---

