---
title: "After Ubuntu 18.04.1 windows 10 doesn't boot. Keeps going into recovery mode."
date: 2018-09-11
forum: Installation &amp; Upgrades
---

### Post by maheshnihar on 2018-09-11
Hi 
I recently installed Ubuntu 18.04.1. Windows was already on the  laptop. When I tried to load back into windows after Ubuntu got installed it dint allow me and was always going to repair mode.

I have my Ubuntu summaru created by boot repair tool here

[https://paste.ubuntu.com/p/JrBv3qpJ8H/](https://paste.ubuntu.com/p/JrBv3qpJ8H/)

---

### Post by westie457 on 2018-09-11
Hi, the problem is right at the start of your report 'No valid partition table found'.

Boot from your Ubuntu install media to 'Try' mode and open a terminal. Type and run the following commands ```
sudo apt update
sudo apt install testdisk
sudo testdisk
```
If your ssd is not detected in the drive selection screen restart testdisk with a parameter, something like this **&#8203;**[COLOR=#333333][FONT=&amp]testdisk /dev/nvme0
A step by step guide is here' [/FONT][/COLOR]https://www.cgsecurity.org/wiki/Running_TestDisk

---

### Post by maheshnihar on 2018-09-11
Hi I tried to install testdisk and when I go through it doesn't show the HDD on the list. Tried with parameter too.

---

### Post by oldfred on 2018-09-11
That is not issue, but bootinfoscript has not been updated to correctly see NVMe drives.
Author needs someone with NVMe to test code to know if changes are correct.
       Support NVMe and MMC devices 
[https://github.com/arvidjaar/bootinfoscript/issues](https://github.com/arvidjaar/bootinfoscript/issues)

Boot-Repair uses the script based (non-gui) bootinfoscript for about the first third of its report to parse drive info.

Have you updated UEFI from Dell and NVMe firmware?

Grub only boots working Windows. 
Can you directly boot Windows from UEFI boot menu, usually f12 on Dell.
What model Dell?

Have you tried turning off UEFI Secure Boot, but still boot in UEFI mode?

---

### Post by maheshnihar on 2018-09-11
[COLOR=#000000]Have you updated UEFI from Dell and NVMe firmware? **I remember I updated it.**[/COLOR]
[COLOR=#000000]Grub only boots working Windows. : **My windows was working before normally. Only after installing Ubuntu this happened.**[/COLOR]
[COLOR=#000000]Can you directly boot Windows from UEFI boot menu, usually f12 on Dell.: **I tried but still goes into recover mode.**[/COLOR]
[COLOR=#000000]What model Dell?** It is Dell xps 9550**[/COLOR]

[COLOR=#000000]Have you tried turning off UEFI Secure Boot, but still boot in UEFI mode? **I will try this one and let you know.**[/COLOR]

---

### Post by oldfred on 2018-09-11
Some older 9550 threads. Newer version of Ubuntu should be better.
With the mega-thread often better to start at end and work forward. Early issues are often solved.

       Ubuntu 16 on the DELL XPS15 9550 Tutorial
[https://ubuntuforums.org/showthread.php?t=2345444](https://ubuntuforums.org/showthread.php?t=2345444)
Ubuntu 16.04 on Dell Xps 15 9550 (i7-6700HQ - 1TB SSD - UHD 4k touch) mega-thread
[http://ubuntuforums.org/showthread.php?t=2317843](http://ubuntuforums.org/showthread.php?t=2317843)
Dell Xps 15 9550  Ubuntu 15.10 on new Infinity display (i7 6gen 16gbr UHD 4k touch) post 272 says 16.04 good
[http://ubuntuforums.org/showthread.php?t=2301071](http://ubuntuforums.org/showthread.php?t=2301071)

---

### Post by maheshnihar on 2018-09-11
Hi

The version I installed was 18.04.1. Is that still an issue?

---

### Post by oldfred on 2018-09-11
It should not be, but a few users seem to be having issues.
Generally better to use newest release as it has newer kernel & drivers that fix issues. And then older hardware works or works better or newer hardware then works without leaping thru hoops.

But Windows boot issues, are not related to Ubuntu install.
Windows settings, how you shrank NTFS partition and some other Windows related issues are the problem.
You may need to use your Windows repair disk and run chkdsk. Make sure Windows fast start up is off, not just a "full" shutdown but type of shutdown. You may be able to get to internal Windows repair condole with f12 then f8.

       Fast Start up off (always on hibernation), note that Windows turns this back on with updates
[http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472](http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472)
[http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html](http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html)
[http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html](http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html)

---

### Post by maheshnihar on 2018-09-11
[COLOR=#000000]Have you tried turning off UEFI Secure Boot, but still boot in UEFI mode?[B]Tried this but still goes into recovery mode.

[/B][/COLOR][COLOR=#000000]Make sure Windows fast start up is off:** I am going to try this now. Is there a way we can turn it off?**[/COLOR]

---

### Post by maheshnihar on 2018-09-11
Tried everything. But dint work. Disabled Fast boot and then tried to get back to Windows Still goes to recovery.

---

### Post by oldfred on 2018-09-11
I have seen this, but no idea if still valid.
Better to use Windows repair tools for Windows issues.

       Force removal of hiberfil from Ubuntu
[URL="http://askubuntu.com/questions/145902/unable-to-mount-windows-ntfs-filesystem-due-to-hibernation"]http://askubuntu.com/questions/145902/unable-to-mount-windows-ntfs-filesystem-due-to-hibernation

      [/URL]
 Windows 10 repair disk
[http://www.tenforums.com/tutorials/4200-recovery-drive-create-windows-10-a.html](http://www.tenforums.com/tutorials/4200-recovery-drive-create-windows-10-a.html)
[http://www.tenforums.com/tutorials/36083-system-repair-disc-create-windows-10-a.html](http://www.tenforums.com/tutorials/36083-system-repair-disc-create-windows-10-a.html)
Repair/backup/restore
[https://support.microsoft.com/en-us/instantanswers/3a747883-b706-43a5-a286-9e98f886d490/create-a-recovery-drive](https://support.microsoft.com/en-us/instantanswers/3a747883-b706-43a5-a286-9e98f886d490/create-a-recovery-drive)
[http://windows.microsoft.com/en-us/windows-10/windows-10-recovery-options](http://windows.microsoft.com/en-us/windows-10/windows-10-recovery-options) 
    [URL="http://askubuntu.com/questions/145902/unable-to-mount-windows-ntfs-filesystem-due-to-hibernation"]
[/URL]

---

### Post by maheshnihar on 2018-09-12
I think I accidentally formatted the Win OS partition.
I was trying TEST DISK to recover files on my windows.
But when I run test disk it doesn't show up my internal hard drive at all. It just shows up only the external pen drive

---

### Post by oldfred on 2018-09-12
Post this:
sudo parted -l

And post link to a new copy of summary report from Boot-Repair.

---

### Post by maheshnihar on 2018-09-12
Hi Fred. This is what I have as below and here is the summary after boot repair. 
**[http://paste.ubuntu.com/p/VGVK35fJnw/](http://paste.ubuntu.com/p/VGVK35fJnw/)**

[B]Model: NVMe Device (nvme)
Disk /dev/nvme0n1: 1024GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt
Disk Flags: 

Number     Start     End         Size        File system         Name                                                  Flags
[/B] 1              1049kB   525MB    524MB   fat32                     EFI system partition                        boot, esp
 2              525MB    660MB    134MB                                 Microsoft reserved partition          msftres
 3              660MB    510GB    510GB   ext4
 4              510GB    511GB    964MB   ntfs                                                                                  hidden, diag
 5              511GB    958GB    447GB   ntfs                        Basic data partition                        msftdata
 6              958GB    1012GB  53.7GB  ntfs                        Basic data partition                        msftdata
 7              1012GB  1012GB  472MB   ntfs                                                                                  hidden, diag
 8              1012GB  1024GB  11.7GB  ntfs                                                                                  hidden, diag

---

### Post by oldfred on 2018-09-12
It is unusual to see an ext4 partition before any NTFS partitions when you have a system with Windows pre-installed. Not sure how you forced that there?
And is then /dev/nvme0n1p5      your Windows install? 

If you moved the NTFS partition, it will need chkdsk and hibernation removed. You can only do that from Windows repair console or your Windows installer with a repair console.

If you still can directly boot Windows from UEFI, can you also immediately press f8 and get into Windows internal repair console?
Have you tried with UEFI Secure Boot off?

If not you have to use a Windows repair flash drive. Buy two new flash drives and talk a friend or neighbor running Windows 10 to let you make two repair flash drives. And let him/her keep one. They will need it someday. And convince friend to make a full backup.

---

### Post by maheshnihar on 2018-09-13
Hey Fred
[COLOR=#000000]/dev/nvme0n1p5  is just data drive not an OS one[/COLOR]

I did a full format yesterday and reloaded win 10.

What will be the best way to use Ubuntu?
Through Dual boot or Just use it through a virtual box?

---

### Post by oldfred on 2018-09-13
I am a dual booter (actually many Ubuntu installs), but have not yet tried virtual install. 

Many here recommend virtual installs if you have newer hardware and extra RAM as that is shared.

---

### Post by maheshnihar on 2018-09-13
Is there a good tutorial on how to dual boot it with windows.
Also a way to selecting the OS not from GRUB menu but instead through a windows menu.

My laptop is Dell XPS 15 9550 which currently runs windows 10

---

### Post by oldfred on 2018-09-13
If you look at my signature, I posted lots of detail on dual booting with many more links for anything that you may not understand.

It looks like you may have replaced your Windows partition with the Ubuntu partition. You use Windows to shrink an NTFS partition to make room for an ext4 partition or two if you want separate /home. Always reboot into Windows so it can run chkdsk as after any resize it needs chkdsk. And make sure fast start up is off, note that Windows keeps turning it back on with updates.

Dell's need UEFI updates, and RAID or Intel SRT turned off.
       Dell UEFI Dual boot instructions using Something Else
[https://www.dell.com/support/article/us/en/19/SLN301754/how-to-install-ubuntu-and-a-recent-windows-operating-system-as-a-dual-boot-on-your-dell-pc?lang=EN](https://www.dell.com/support/article/us/en/19/SLN301754/how-to-install-ubuntu-and-a-recent-windows-operating-system-as-a-dual-boot-on-your-dell-pc?lang=EN)
[https://www.dell.com/support/article/us/en/19/sln142679/how-to-enable-boot-from-dvd-option-with-uefi-boot-mode-enabled--windows-8--81--10-?lang=en](https://www.dell.com/support/article/us/en/19/sln142679/how-to-enable-boot-from-dvd-option-with-uefi-boot-mode-enabled--windows-8--81--10-?lang=en)
Dell with NVMe needs AHCI & boot option nvme_load=YES
[https://www.dell.com/support/article/us/en/19/sln299303/loading-ubuntu-on-systems-using-pcie-m2-drives?lang=en](https://www.dell.com/support/article/us/en/19/sln299303/loading-ubuntu-on-systems-using-pcie-m2-drives?lang=en)

---

