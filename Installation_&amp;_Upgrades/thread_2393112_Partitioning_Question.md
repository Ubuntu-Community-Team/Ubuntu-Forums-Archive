---
title: "Partitioning Question"
date: 2018-05-29
forum: Installation &amp; Upgrades
---

### Post by shankariyer on 2018-05-29
Hi,

I have a Dell Inspiron 15 - 3000 Series, that came with Windows 10. It has the following partition scheme. Windows is needed for my family, I need help to decide the appropriate partition scheme and the right disk.

500 MB - EFI System Partition
900 GB - NTFS, Primary Partition ( c:\ )
500 MB - NTFS, OEM Partition ( e:\ )
11 GB - NTFS, OEM Partition
1.2 GB - NTFS, Dell Support Partition

Ubuntu CD is booted only when I disable secure boot and opt for legacy boot.

Should I re-partition C-drive from Windows and then get onto Ubuntu to use the newly allocated space ?
Or, please suggest tips, that doesn't mess up Windows.

Thanks.

---

### Post by oldfred on 2018-05-29
Only use Windows to shrink NTFS partition. And then immediately reboot to run chkdsk.

Dell usually have drives set for RAID even if one drive or Intel SRT. You need to change to AHCI. But add the AHCI driver into Windows first.
Then UEFI boot should work.

Have you updated UEFI from Dell. That is also required.

       Dell with NVMe needs AHCI & boot option nvme_load=YES
[https://www.dell.com/support/article/us/en/19/sln299303/loading-ubuntu-on-systems-using-pcie-m2-drives?lang=en](https://www.dell.com/support/article/us/en/19/sln299303/loading-ubuntu-on-systems-using-pcie-m2-drives?lang=en) 
            Dell 14z & 17r with Intel SRT
[http://ubuntuforums.org/showthread.php?t=2038121](http://ubuntuforums.org/showthread.php?t=2038121)
Dell 17R Brightness
[http://ubuntuforums.org/showthread.php?t=2195650](http://ubuntuforums.org/showthread.php?t=2195650)
[http://ubuntuforums.org/showthread.php?t=2204287](http://ubuntuforums.org/showthread.php?t=2204287)

---

### Post by shankariyer on 2018-05-29
Thanks... By UEFI update, you mean BIOS update - Yes, it's updated.

I am sorry, I don't understand Intel SRT and AHCI points. I don't believe this laptop is on RAID.

How can I check on these ( Intel SRT, RAID ) ? Thanks.

---

### Post by shankariyer on 2018-05-30
In the BIOS, I see 'SATA Operation' set to 'AHCI'

---

### Post by oldfred on 2018-05-30
+1 on shankariyer comment
I think it may be in advanced options in UEFI.

With Google I found this which may show similar screen shots:
[http://dellwindowsreinstallationguide.com/uefi/sata-operation/](http://dellwindowsreinstallationguide.com/uefi/sata-operation/)

You should have a copy of your manual for your specific model. You may need to download from Dell usually on same page as UEFI/BIOS updates. And that should show & explain various settings & options.

---

### Post by shankariyer on 2018-05-30
Thanks again. Mine is variant B. But as I mentioned above, I see the SATA Operation set to AHCI already. ( There are no other options available such as RAID or others. They are not there )

---

### Post by oldfred on 2018-05-30
Almost all systems need UEFI settings to allow USB boot and legacy off, so it boots in UEFI mode.
And while reconfiguring system, best to have UEFI fast boot off as you may not have time to press a key to get into UEFI to change settings.

Some with Dell have posted it works or seems to work better to have legacy on, but they still can choose to boot in UEFI mode.

For installer to see the NTFS partitions you must have Windows fast start up off. 
       Fast Start up off (always on hibernation)
[http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472](http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472)
[http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html](http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html)
[http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html](http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html)

---

### Post by shankariyer on 2018-06-15
I am sorry, I am not able to follow the instruction here. Yes, I was able to disable Secure Boot. And I have attached my disk layout in this thread.

Once I disable UEFI, I am able to boot into Ubuntu CD. Please tell me whether I'm good to proceed with the installation, pointing to the 195.31GB disk for /boot ?

Please tell me if I need to something else so that Ubuntu installation doesn't mess up Windows as I'd want a dual-boot system.

Thanks.

[ATTACH=CONFIG]280103[/ATTACH]

---

### Post by Dennis N on 2018-06-15
Comments:
There is an EFI system partition, so Windows 10, being pre-installed, is installed as UEFI. Ubuntu should also be installed as UEFI - meaning the installer must be booted into UEFI mode, and Ubuntu will utilize the same EFI system partition as Windows.  The 195 gB should be used as the ext4 root partition (/). You don't need a separate boot partition in most cases. You also don't need to create a swap partition when installing Ubuntu 18.04.

---

