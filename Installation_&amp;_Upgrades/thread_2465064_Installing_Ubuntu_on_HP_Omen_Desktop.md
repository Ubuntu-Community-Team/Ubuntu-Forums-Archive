---
title: "Installing Ubuntu on HP Omen Desktop"
date: 2021-07-20
forum: Installation &amp; Upgrades
---

### Post by technicallytrue on 2021-07-20
I recently decided to try installing Ubuntu on my PC (an HP Omen 25L  desktop) alongside Windows 10 to dual boot. The system has two drives:  an SSD for the OS and a larger HDD for data storage. When I try  installing Ubuntu from a USB, it doesn't detect the SSD and tries to  install on the HDD, which is obviously not what I want. Poking around, I  found that this is often because Windows systems with multiple drives  have a RAID configuration rather than AHCI, which Ubuntu apparently  doesn't like. However, I cannot find any options in the BIOS to change  this.
 My question is this: is installing Ubuntu on this device even possible, or has HP foiled me once again?
Thank you!

---

### Post by ubfan1 on 2021-07-20
There may be other reasons the SSD isn't shown.  Check the Windows Power options and ensure that shutdown is not set to "hibernate".  chkdsk the Windows disk for any errors too.

---

### Post by scorp123 on 2021-07-20
> **technicallytrue said:**
>  is installing Ubuntu on this device even possible, or has HP foiled me once again?


Why wouldn't it be possible? HP overall is very Linux-friendly, e.g. they are one of the biggest contributors to the "Linux Printing Project" and like 99% of their printers/scanners/multi-function devices are super easy to get working under Linux. As for their "Omen" gaming PC's: I myself own a HP Omen 870-290nz Desktop with 1 x 512 GB SSD and 2 x 4 TB HDD. Ubuntu works tip top here.

Please check that BIOS again. Also check that installer again, e.g. go into "Live Session" mode and open a terminal and then type these commands:
```
sudo fdisk -l
sudo lsblk
```

This should list all the disk devices the installer can see. Please copy & paste that output here so we can see it. Maybe the disk you wanted to install Ubuntu on is using a strange name (e.g. /dev/nvme0 instead of /dev/sda ... stuff like that) and it's thus not immediately obvious which device you are supposed to choose...?

---

### Post by ActionParsnip on 2021-07-21
If you boot to Windows, then shut it down (not reboot) then cold boot to the Ubuntu installer, does it help. Windows doesn't fully shut down if you reboot and may still be holding the storage, making it unavailable to the Ubuntu system

---

### Post by oldfred on 2021-07-22
Some perhaps similar Omen systems:
 HP OMEN 15-dh0 UEFI update
[https://ubuntuforums.org/showthread.php?t=2448563](https://ubuntuforums.org/showthread.php?t=2448563)
HP OMEN 15-ce0xx
[https://ubuntuforums.org/showthread.php?t=2407145](https://ubuntuforums.org/showthread.php?t=2407145) & 
[http://martinsosic.com/linux/2015/03/01/arch-linux-on-hp-omen.html](http://martinsosic.com/linux/2015/03/01/arch-linux-on-hp-omen.html) &
[https://jeanbruenn.info/2018/04/01/omen-hp-with-linux/](https://jeanbruenn.info/2018/04/01/omen-hp-with-linux/)

RST info & Windows AHCI driver install:
[https://discourse.ubuntu.com/t/ubuntu-installation-on-computers-with-intel-r-rst-enabled/15347](https://discourse.ubuntu.com/t/ubuntu-installation-on-computers-with-intel-r-rst-enabled/15347)

Used Intel App in Windows to disable Optane, need AHCI driver in Windows.
[https://ubuntuforums.org/showthread.php?t=2458373&p=14022735#post14022735](https://ubuntuforums.org/showthread.php?t=2458373&p=14022735#post14022735)
[https://www.microsoft.com/en-us/p/intel-optane-memory-and-storage-management/9mzng5hzwz1t?activetab=pivot:overviewtab](https://www.microsoft.com/en-us/p/intel-optane-memory-and-storage-management/9mzng5hzwz1t?activetab=pivot:overviewtab)

---

### Post by technicallytrue on 2021-07-28
@scorp123: Oddly enough, the boot ssd *does* show up in the terminal (listed as /dev/nvme0n1), but it a) only shows up as half its actual size, and b) still doesn't appear when actually trying to install (I can only choose to install it on the 1 TB hard drive). It also has the following info:
```
Disklabel type: gpt

Device                Start          End      Sectors      Size    Type
/dev/nvme0n1p1         2048       534527       532480      260M    EFI System
/dev/nvme0n1p2       534528       567295        32768       16M    Microsoft reserved
/dev/nvme0n1p3       567296    498999295    498432000    237.7G    Microsoft basic data
/dev/nvme0n1p4    498999296    500105215      1105920      540M    Windows recovery environment

```

Maybe that has something to do with it.

@ubfan1 and @ActionParsnip: Yes, I fully shut it down before attempting the installation. I like to think I'm not *entirely* hopeless :P

Thanks again for helping!

---

### Post by tea for one on 2021-07-28
> **technicallytrue said:**
> I  found that this is often because Windows systems with multiple drives  have a RAID configuration rather than AHCI, which Ubuntu apparently  doesn't like. However, I cannot find any options in the BIOS to change  this. My question is this: is installing Ubuntu on this device even possible, or has HP foiled me once again?

HP have an interactive BIOS web page - Is this your PC [http://h10032.www1.hp.com/ctg/Manual/c06592756](http://h10032.www1.hp.com/ctg/Manual/c06592756)

If so, then the setting may be Configuration > SATA Emulation > AHCI (with down arrow)

---

### Post by scorp123 on 2021-07-28
> **technicallytrue said:**
> @scorp123: Oddly enough, the boot ssd *does* show up in the terminal (listed as /dev/nvme0n1), but it a) only shows up as half its actual size, and b) still doesn't appear when actually trying to install (I can only choose to install it on the 1 TB hard drive). It also has the following info:
```
Disklabel type: gpt

Device                Start          End      Sectors      Size    Type
/dev/nvme0n1p1         2048       534527       532480      260M    EFI System
/dev/nvme0n1p2       534528       567295        32768       16M    Microsoft reserved
/dev/nvme0n1p3       567296    498999295    498432000    237.7G    Microsoft basic data
/dev/nvme0n1p4    498999296    500105215      1105920      540M    Windows recovery environment

```

According to that list there must be a Microsoft Windows 10 environment on that SSD. You are sure you want to completely destroy that Windows 10 installation and overwrite it with Ubuntu?

OK, boot Ubuntu's live environment, e.g. either via a bootable DVD, or USB stick. Once you're in the live session desktop click the "Start" menu in the lower left corner. You should get this screen where also a program with the name **"GParted"** is being listed.

Screenshot:
[ATTACH=CONFIG]288886[/ATTACH]

Open that program. It should be able to list your SSD, even if the installer can not. Now ... in its menu, go:
***Device > Create new partition table ...***

**BEFORE YOU CLICK ON ANYTHING PLEASE MAKE SURE YOU _REALLY_ SELECTED THE CORRECT DISK, e.g. the SSD you want to overwrite and not the HDD that has the data you want to keep!!**

What follows now is **DESTRUCTIVE** and will **WIPE** whatever was on that disk. Again: Please make sure you selected the correct one!!

The program will also ask you if you are 100% sure if this really is what you want.
Screenshot from a VM, the virtual harddrive here is called "/dev/sda". Your's should be "/dev/nvme0n1" ...

Also make sure you select **"gpt"** as partition type.
Screenshot:

[ATTACH=CONFIG]288887[/ATTACH]

**"GParted"** should be able to wipe your SSD clean and from here onwards it should be possible to select it as installation target in the installer.


Good luck!

---

### Post by tea for one on 2021-07-28
The output from post no.6 has some missing info i.e. the input code and the full size of the disk (irrespective of partition sizes)

```
edited@edited:~$ lsblk /dev/nvme0n1
NAME        MAJ:MIN RM   SIZE RO TYPE MOUNTPOINT
nvme0n1     259:0    0 232.9G  0 disk [COLOR="#0000FF"]This line is missing from your output[/COLOR]
&#9500;&#9472;nvme0n1p1 259:1    0   512M  0 part /boot/efi
&#9500;&#9472;nvme0n1p2 259:2    0    27G  0 part /
&#9500;&#9472;nvme0n1p3 259:3    0    29G  0 part /home
&#9492;&#9472;nvme0n1p4 259:4    0   150G  0 part /mnt/381ee381-e1af-4ca4-9a8d-fcccf8987669
edited@edited:~$ 

```

---

### Post by technicallytrue on 2021-09-17
@tea for one
Sadly, the interactive BIOS doesn't match, despite saying it's for OMEN 30 *and* 25 L. Mine doesn't have the SATA Emulation field.
Also, with regards to your second post, I dunno what to tell you. It didn't have that line.

@scorp123
I think you misunderstand me. I'm not trying to overwrite the Windows partition, it's just that the Windows partition doesn't take up the whole drive, so I want to use the *rest* of the drive (there should be about half left) for Ubuntu. For whatever reason, though, the non-partitioned bit doesn't seem to be appearing in the lsblk and fdisk -l output.

Thanks again!

---

### Post by tea for one on 2021-09-17
Not making much progress yet, but I do not think that it is a forlorn case.
You mention that there is some unused space on your NVME SSD but we do not know the original size of the disk?
> **technicallytrue said:**
> Also, with regards to your second post, I dunno what to tell you. It didn't have that line.
Can you run this and post the output:-
```
lsblk -e 7 -o name,size,type,fstype,fsuse%,fsavail,mountpoint
```
> **technicallytrue said:**
> I'm not trying to overwrite the Windows partition, it's just that the Windows partition doesn't take up the whole drive, so I want to use the *rest* of the drive (there should be about half left) for Ubuntu.
Did you use Windows tools to reduce the Windows partition?
Did you reboot Windows to allow chkdsk to run?

---

### Post by MAFoElffen on 2021-09-19
@scorp123: 

From Post #1...
> **technicallytrue said:**
> I recently decided to try installing Ubuntu on my PC (an HP Omen 25L  desktop) [COLOR=#ff0000]alongside [/COLOR]Windows 10 to [COLOR=#ff0000]dual boot.[/COLOR] 
and confirmed by the OP 2 days back, he is trying to dual boot and not affect his Win 10 Install.

@technicallytrue

Did you use Windows 10 > Storage Manager, to shrink your Windows partitions on that drive to create unused space on that drive for the install to happen on that drive? The reason to do this from within Windows, it that, it is possible to do it with a Linux utility, but those do not care nor keep track internal NTFS indexing, so will cause problems you would have to fix.

So you are saying if you boot from an Ubuntu Desktop LiveCD, that it does not see your NVMe drive at all? 

For example, from an Ubuntu Desktop LiveCD ISO, download and run the system-info script in my signature line (from the UbuntuForum's Github), and lets see what that script says your system and machine information show's as... That will give people a clear picture of what may be happening. That in why I wrote that for the Forum: So that Users can get help, and so Forums Members can see what they are recommending solutions for, in order to help them.

That will tell people if it is seen or not. And if not, if it is a BIOS setting or firmware version that may be causing that oversight. Please help people, to help you.

---

