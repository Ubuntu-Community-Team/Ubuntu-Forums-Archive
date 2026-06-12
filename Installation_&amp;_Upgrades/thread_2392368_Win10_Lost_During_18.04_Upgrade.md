---
title: "Win10 Lost During 18.04 Upgrade"
date: 2018-05-20
forum: Installation &amp; Upgrades
---

### Post by Norway719 on 2018-05-20
Hi everyone, I can no longer boot into Windows 10 and I'm about out of guesses. I have been running Win10 plus Ubuntu on a pair of NVME's on a custom desktop PC. There is also a shared storage drive consisting of a pair of SATAs in RAID0. I recently tried to upgrade from 17.04 to 18.04. It didn't work so well so I made a boot stick and put a fresh 18.08 on. I've done similar things before on other machines and in my experience the grub is almost always messed up after something like this, but it is always an easy fix with the most basic boot repair iteration. This time boot repair is unsuccessful.

It looks to me that Boot Repair has me uninstall the grub and then select on which drive I would like to reload it. It then leaves me with:

[I]An error occurred during the repair. ... You can now reboot your computer.
Please do not forget to make your BIOS boot on nvme1n1 (NVMe Device) disk![/I]

[http://paste.ubuntu.com/p/nrs4CpSMSD/](http://paste.ubuntu.com/p/nrs4CpSMSD/)


Interestingly (and possibly related?) If I open GParted I get three messages in succession: 

[I]Could not stat device /dev/mapper/isw_ecdbigdjbc_Raid0 Storage - No such file or directory.
[/I]
[I]Invalid argument during seek for read on /dev/sda
[/I]
[I]The backup GPT table is corrupt, but the primary appears OK, so that will be used
[/I]
There is a grub 2 menu when I boot up but it doesn't contain an option for Windows. If I select Ubuntu 18.04 it boots up and runs okay. Also, I think that the Windows install in still largely intact because I can mount and browse it from the live session.

Any ideas? Thanks! It was a pain in the neck to get this config up and running the first place. (Dual boot from 2 NVME's + a Striped RAID) I think much of the effort getting the setup to work in the first place came from BIOS settings. I'm going to upgrade the firmware to see if that helps me at all.

---

### Post by oldfred on 2018-05-20
Did you also update Windows?
Windows on update turns fast start up back on, then the Linux NTFS driver will not mount read/write and grub does not add to menu.
From Report:
      >  Windows is hibernated, refused to mount.
Falling back to read-only mount because the NTFS partition is in an
unsafe state. Please resume and shutdown Windows fully (no hibernation
or fast restarting.) 


       Fast Start up off (always on hibernation)
[http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472](http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472)
[http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html](http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html)
[http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html](http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html) 
    
With multiple drives, do not run Boot-Repairs auto fix. Use only advanced mode and choose install & drive for boot loader. Only choose drive, not partition.

I have seen others with gpt errors that may not be valid with RAID or LVM. Partition & drive have to have same info with gpt, but when partition is not just on one drive gpt partitions & drive info may not match.

Can you directly boot Windows from  UEFI boot menu.
Grub only boots working Windows. Or Windows that is not hibernated nor needs chkdsk.

---

### Post by Norway719 on 2018-06-16
Thanks oldfred,

I've been away from my computer for a couple of weeks. Sorry for the late reply. I think I see what you mean with the issue of hibernation. I found while browsing the root C:\ drive a file called "hiberfil.sys" that is 17.1 GB; does this file mean that windows is in a hibernation state? All solutions that I was able to find for disabling hibernation required actually being able to boot into Windows which I cannot currently do. I tried using the Win10 boot stick to recover the partition but nothing seemed to work there. Can you continue to explain what you mean by "do not run Boot-Repairs auto fix"? I don't think that I could find the settings that you were mentioning.

I have not been able to boot directly into Windows from the BIOS. Selecting to boot from either NVME drive just brings be to the grub menu which contains no options for Windows.

I've been away from this topic for a few weeks now but I am working on it again now. If I don't figure this out soon, Ill probably just reload Win10.

Thanks!

---

### Post by yancek on 2018-06-17
According to the microsoft site at the link below, the hiberfile.sys file should be approximately equivalent to your total RAM.  The solution there also requires being able to boot windows.  You might take a look in the BIOS for settings for hibernation but if you make any changes be sure to make note of what you do so you can change back if the initial change doesn't help.  I have no idea of what the consequences of deleting this file would be.

[https://support.microsoft.com/en-us/help/920730/how-to-disable-and-re-enable-hibernation-on-a-computer-that-is-running](https://support.microsoft.com/en-us/help/920730/how-to-disable-and-re-enable-hibernation-on-a-computer-that-is-running)

---

### Post by Norway719 on 2018-06-17
Thanks yancek,

I agree. There is also a setting in the BIOS for something like "fast boot" I think. That was always off, but one of the many things that I tried was to turn it on. It didn't seem to make any difference. I don't think I have any problem with deleting the hiberfil.sys but I'm almost certain that that alone will not fix this. I will try today.

Thanks again.

---

### Post by oldfred on 2018-06-17
It looks like you have NVMe drives and sda/sdb in RAID. Those are gpt, so Windows has to be UEFI boot. But you do not have a Windows UEFI boot entry??
And you have grub in the MBR of drive sdd.

This was the default repair:
      > **[B][FONT=arial][SIZE=1]Recommended repair[/SIZE][/FONT]**[/B]

   The default repair of the Boot-Repair utility will purge (in order to enable-raid) and reinstall the grub2 of nvme1n1p2 into the MBRs of all disks (except live-disks and removable disks without OS).
Additional repair will be performed: unhide-bootmenu-10s   fix-windows-boot 



But since UEFI system and other drives are gpt partitioned, grub will not install correctly to those drive's MBR without a bios_grub partition. But you do not want that anyway. It would be better to have Ubuntu in UEFI boot mode.

You need to always boot in UEFI boot mode. And to boot Windows will need UEFI boot mode on in UEFI settings. You should not need UEFI Secure Boot on, Windows will work either way, but UEFI only, not BIOS/CSM/Legacy.
       CSM - UEFI Compatibility Support Module (CSM), which emulates a BIOS mode  

Since you are not showing a UEFI Windows entry, your Windows may need repair. Always best to have Windows repair flash drive (and Ubuntu's live installer), so you can repair systems. 
You may be able to boot a hard drive entry in UEFI mode as that often is a fallback entry.

I think hiberfile.sys exists whether used or not. But before have seen where you could just delete it. Not sure then what Windows does, it may go to repair mode or need immediate press of f8 to get into internal repair console.
      
 Force removal of hiberfil from Ubuntu
[URL="http://askubuntu.com/questions/145902/unable-to-mount-windows-ntfs-filesystem-due-to-hibernation"]http://askubuntu.com/questions/145902/unable-to-mount-windows-ntfs-filesystem-due-to-hibernation

      [/URL]
 Windows 10 repair disk
[http://www.tenforums.com/tutorials/4200-recovery-drive-create-windows-10-a.html](http://www.tenforums.com/tutorials/4200-recovery-drive-create-windows-10-a.html)
[http://www.tenforums.com/tutorials/36083-system-repair-disc-create-windows-10-a.html](http://www.tenforums.com/tutorials/36083-system-repair-disc-create-windows-10-a.html)
Repair/backup/restore
[https://support.microsoft.com/en-us/instantanswers/3a747883-b706-43a5-a286-9e98f886d490/create-a-recovery-drive](https://support.microsoft.com/en-us/instantanswers/3a747883-b706-43a5-a286-9e98f886d490/create-a-recovery-drive)
[http://windows.microsoft.com/en-us/windows-10/windows-10-recovery-options](http://windows.microsoft.com/en-us/windows-10/windows-10-recovery-options) 
    
On first Boot-Repair screen is a small carrot/icon for Advanced options:
       [https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

---

### Post by Norway719 on 2018-06-17
Thanks oldfred,

I was able to remove the hiberfile.sys using *[FONT=courier new]sudo ntfs-3g -o remove_hiberfile /dev/nvme0n1p2 /media/...[/FONT]* and I could verify that it was no longer there when I mounted and browsed [FONT=courier new]/dev/nvme0n1p2.[/FONT]

The topic of UEFI has been troubling me since I built this machine about a year ago:

My BIOS has 2 options for "Boot Mode Select": "UEFI" and "UEFI+Legacy".

I have found that generally "UEFI+Legacy" seems to be the only option that can produce a usable configuration. If I select "UEFI" it reduces the number of options under the "Boot Queue" and nothing will boot(Boots into the BIOS menu because there are no bootable options). It seems that all installs are "legacy" because none of them show up in UEFI only... I fooled with this for a considerable duration while building this machine. I don't totally understand what it all means but it didn't seem right to me to have to run anything with the word "legacy" in it because I was running New Windows and new Ubuntu. Despite that, it was the only way that I could get this system to run.

Based on what you are saying here, this should be abnormal.

---

### Post by oldfred on 2018-06-17
Legacy/CSM/BIOS only boots with UEFI Secure Boot off. Not sure if then it automatically turns it off.
But you may need another UEFI setting to turn off Secure Boot. But on my system it is "Windows" or "Other". Fine print says if using Windows 7 use "Other" as Windows 7 does not support Secure Boot.

My system did not like UEFI+Legacy. It only boots in UEFI to install with UEFI only setting.
I also had to turn on allow USB boot, turn off UEFI fast boot (different than Windows fast start up), and some other settings.
Some of my settings:
       Asus-ar screenshots oldfred
[http://ubuntuforums.org/showthread.php?t=2258575&page=2](http://ubuntuforums.org/showthread.php?t=2258575&page=2) 
    
What brand/model system?
Grub often has issues with RAID on desktop installs. RAID drivers work better with Server install. But Boot-Repair may work if booted in correct mode.

---

### Post by Norway719 on 2018-07-15
Hi oldfred,

I think it's time to move on. I'm just going to install Win10 clean on top of the old install. I normally don't mind continuing to mess with this kind of stuff, but work is not currently affording me enough free time this time around. Thanks for your help on this one. Talk to you next time.

---

### Post by oldfred on 2018-07-15
With new UEFI hardware, how you boot install media, UEFI or BIOS boot is then how it installs. This is for both Windows & Ubuntu.

So be sure to choose the mode you want.
Not that Windows only installs in UEFI boot mode to gpt partitioned drivers.
Windows only installs in BIOS boot mode to MBR(msdos) partitioned drives.
And if drive is converted from one partitioning to another, it is in effect erased.

---

### Post by Norway719 on 2018-07-15
Thanks again. I'll talk to you next time.

---

