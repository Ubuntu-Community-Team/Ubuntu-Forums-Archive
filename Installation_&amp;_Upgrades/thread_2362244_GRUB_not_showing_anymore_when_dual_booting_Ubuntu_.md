---
title: "GRUB not showing anymore when dual booting Ubuntu MATE and Windows 10"
date: 2017-05-25
forum: Installation &amp; Upgrades
---

### Post by liberator48 on 2017-05-25
Hello, i am still novice at Ubuntu but am a veteran Windows user, and i need to use Linux in the future so decided to install Ubuntu MATE alongside Windows 10 and this is my story:


So, I have an issue with dual booting Ubuntu MATE with Windows 10 x64-bit

I have two HDDs, one SSD where Windows 10 is installed, and one 5400RPM 1TB drive which is mainly formatted in NTFS and for use
with Windows 10 as storage.

On the secondary 5400RPM HDD i have partitioned and formatted 64GB into ext4 and successfully installed Ubuntu MATE on.
I selected the /dev/sdb (secondary HDD) for boot loader during install. Everything seemed fine.

Then i rebooted to test that it was actually fine, and again it seemed fine, the GRUB loader showed up during boot after i
finished installing Ubuntu MATE and restarted.

I booted into Ubuntu MATE and GRUB also showed Windows Boot Manager and allowed me to boot into Windows 10. All dandy so far.
I tried booting both OS's once.

But also in the GRUB loader menu there were 2 more options, one was called "System Settings" or something like that, the other
i can't remember what it was, possibly it was my USB, but nevermind.

I clicked System settings and it took me into UEFI Firmware Settings (the BIOS-like menu that shows up if i spam F2 during boot)

I did not expect this and didn't want it either so i didn't change anything and simply Exited With Discarding Changes
(even though i hadn't made any changes)

Ever since after this, it no longer shows the GRUB loader when i boot, it simply goes into Windows 10 as if Ubuntu is not
even there.


How can i make it show the GRUB boot loader with options to boot Windows 10 or Ubuntu MATE again?
(And also, if i can fix this first, how do i change the default OS for the GRUB loader to Windows 10 and remove the other two
options that was there?)

Things i've already tried:
[LIST]
[*]Booting into live USB and reinstalling GRUB via terminal sudo command
[*]Changing boot mode to legacy instead of UEFI, Ubuntu could still not be booted
[/LIST]


I've done a lot of googling on this and can't find a solution, so hopefully someone here can help.
Please keep in mind that i have 2 HDDs, the main SSD which is 100% NTFS and Windows 10,
and the secondary 5400RPM HDD which is 90% NTFS with Windows 10 and 10% ext4 with Ubuntu MATE

Thanks for any help!

---

### Post by oldfred on 2017-05-25
Did you install Mate in UEFI boot mode on a gpt partitioned drive.
Are all drives gpt.
Is Windows 10 UEFI with gpt? If pre-installed then it will be UEFI.

Do not mix UEFI & BIOS, they are not compatible. While you can dual boot, it only works directly from UEFI and you may have to turn on/off UEFI/BIOS modes to boot system installed in other boot mode. Since you have Windows always boot in same mode as Windows.

How you boot install media is then how it installs.

What brand/model system?

 May be best to see details, you can run from Ubuntu live installer or any working install, use ppa version not ISO:
Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info) and:
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

Some recently have had issues with Boot-Repair automatically posting the Summary Report to a pastebin site. If not auto posted with a link, manually copy entire report to pastebin site. Often too large to post directly.

More details on UEFI in link below in my signature.

---

### Post by liberator48 on 2017-05-26
Hello oldfred
Thanks for your reply.

I didn't know about GPT before but i checked in disk properties in windows disk manager tool and found out that my **main hdd is gpt** but my **secondary hdd is MBR** (where i have the partition with ubuntu installed)

I am not sure how to know if i installed ubuntu in UEFI mode but i think i did, it doesn't help to disable UEFI, and i want to use UEFI so... i of course used the 64-bit version of ubuntu mate when installing, how can i tell?
Also, yes Windows 10 is UEFI with gpt, as it's on the main disk.

The system is an acer laptop, quite new and high-end, bought it about a year ago.

Does any of the new information i gave help you to determine how i can solve my problem?
Also, will automatic boot-repair work on my system seeing as i have 2 hdd's and i DON'T want to mess with Windows?

Thanks, and looking forward to your reply.

---

### Post by oldfred on 2017-05-26
I have seen where users have installer Ubuntu in UEFI mode on a secondary drive that was MBR(msdos).
Normally UEFI uses gpt and Windows requires it, but Ubuntu does not.

If external drive I also suggest manual partitioning to include the ESP - efi system partition on the second drive.
But grub only uses the ESP on the internal drive & adds a /EFI/ubuntu folder next to the /EFI/Microsoft folder with its boot files.

Boot-Repair does not repair most Windows issues. Always best to have a Windows repair flash drive even if not dual booting.
       Windows 10 repair disk
[http://www.tenforums.com/tutorials/4200-recovery-drive-create-windows-10-a.html](http://www.tenforums.com/tutorials/4200-recovery-drive-create-windows-10-a.html)
[http://www.tenforums.com/tutorials/36083-system-repair-disc-create-windows-10-a.html](http://www.tenforums.com/tutorials/36083-system-repair-disc-create-windows-10-a.html)
Repair/backup/restore
[https://support.microsoft.com/en-us/instantanswers/3a747883-b706-43a5-a286-9e98f886d490/create-a-recovery-drive](https://support.microsoft.com/en-us/instantanswers/3a747883-b706-43a5-a286-9e98f886d490/create-a-recovery-drive)
[http://windows.microsoft.com/en-us/windows-10/windows-10-recovery-options](http://windows.microsoft.com/en-us/windows-10/windows-10-recovery-options)

Even if not dual booting always have a full backup of your system & data. Drives fail, users make errors, and "stuff" just happens.
If you have a current backup then you can sleep at night.
       
 Backup windows before install - post by Mark Phelps
[http://ubuntuforums.org/showthread.php?t=2137439&p=12611710#post12611710](http://ubuntuforums.org/showthread.php?t=2137439&p=12611710#post12611710)
[http://www.macrium.com/reflectfree.asp](http://www.macrium.com/reflectfree.asp)
Another suggestion by srs5694
[http://www.runtime.org/driveimage-xml.htm](http://www.runtime.org/driveimage-xml.htm)
Microsoft Windows 8.1 reinstall/refresh
[http://windows.microsoft.com/en-us/windows-8/create-reset-refresh-media](http://windows.microsoft.com/en-us/windows-8/create-reset-refresh-media) 
    
       
 GPT Advantages (older 2010 but still valid)  see post#2 by srs5694:
[http://ubuntuforums.org/showthread.php?t=1457901](http://ubuntuforums.org/showthread.php?t=1457901)
[https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT](https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT)
[http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface](http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface)
[http://askubuntu.com/questions/629470/gpt-vs-mbr-why-not-mbr](http://askubuntu.com/questions/629470/gpt-vs-mbr-why-not-mbr)
UEFI Advantages
[http://askubuntu.com/questions/647303/uefi-or-legacy-which-is-advised-and-why/647604#647604](http://askubuntu.com/questions/647303/uefi-or-legacy-which-is-advised-and-why/647604#647604)
[http://askubuntu.com/questions/446968/legacy-vs-uefi-help](http://askubuntu.com/questions/446968/legacy-vs-uefi-help)
[http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface](http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface)

---

### Post by liberator48 on 2017-05-26
Yes, i have seen the /efi/ubuntu folder with the grub_x64.efi in it when i used EasyUEFI tool and i've tried setting that as the first boot option in that tool, but it didn't help and it still booted straight into Windows 10.
Both drives are internal ones.

Do you think it will work if i re-format the secondary drive back to NTFS then change the partitioning style of it to GPT and then create the ext4 partition and re-install ubuntu on it again? Or what's the best solution for me to get ubuntu to dual boot on my secondary drive?

If all else fails, how do i safely uninstall ubuntu and claim back that partition as NTFS for windows?


EDIT:
Here are some images from disk manager if it helps.
[IMG]https://i.imgur.com/AW4uFaj.jpg[/IMG]
[IMG]https://i.imgur.com/SJFq4hg.jpg[/IMG]

---

### Post by oldfred on 2017-05-26
I prefer to use gpt once you start using UEFI. 
The MBR(msdos) has been the partitioning scheme since original PC or about 35 years old. 

You can convert in place, but best to have good backups as any conversion can cause issues.
And you probably will have to reinstall grub2 boot loader.
       Converting to or from GPT
[http://www.rodsbooks.com/gdisk/mbr2gpt.html](http://www.rodsbooks.com/gdisk/mbr2gpt.html)
gdisk to convert from gpt to MBR
[http://www.rodsbooks.com/gdisk/mbr2gpt.html#gpt2mbr](http://www.rodsbooks.com/gdisk/mbr2gpt.html#gpt2mbr) 
    
What brand/model system?
Some brands will only boot by description which is NOT allowed per UEFI standard. And Ubuntu has a policy statement against that.
But for some reason the only valid description is then "Windows Boot Manager".
But there are many work arounds if you have one of those systems.

---

### Post by liberator48 on 2017-05-27
Ok this is getting a bit off topic, the initial question was what is wrong with grub and why it disappeared all of a sudden for me, and how i can boot my ubuntu installation now?
I'm not even sure if switching to gpt will do anything for me, but i do know that it's not possible if the disk has partitions, so if i were to try that i would have to completely re-install ubuntu.

But i feel like there has to be a simpler solution, because it was all working until i went into UEFI Firmware Settings, then it just stopped showing grub on bootup...
Maybe if i try to re-install grub again, which partition should it be installed in my case?

---

### Post by oldfred on 2017-05-27
Back to question on brand/model.
Often it shows ubuntu UEFI entry one time, then it updates to Windows only.

---

### Post by liberator48 on 2017-05-27
Solved it by simply running automatic setting on Boot-Repair from Ubuntu MATE on live USB.
I don't know what it did, but GRUB is back and i can now boot into Ubuntu MATE and Windows 10.

I've customized GRUB loader so it only shows those 2 options also, so i don't accidentally enter UEFI settings again as presumably it will remove GRUB loader again.
If for some reason i need to go into UEFI settings in the future and it messes it up again i guess i'll just have to run Boot-Repair again.

---

### Post by oldfred on 2017-05-27
If dual booting with Windows, it will reset it on updates and probably turn fast start up back on.
After update to Windows you then have to directly boot from UEFI boot menu to get to Windows as grub will not boot it if fast start up is on.
And Boot-Repair probably reinstall grub which made it first in boot order.

Many find this works, but  a few have reported UEFI just keeps overriding it.

 Change boot order with efibootmgr, some require all 4 hex char others 1 is ok.
To see current order:
sudo efibootmgr -v
sudo efibootmgr -o 2,1
see also 
man efibootmgr
[http://askubuntu.com/questions/485261/change-boot-order-using-efibootmgr](http://askubuntu.com/questions/485261/change-boot-order-using-efibootmgr)

---

