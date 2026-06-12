---
title: "Cant Install Ubuntu - GParted recognizes SSDs but not Installer"
date: 2017-08-02
forum: Installation &amp; Upgrades
---

### Post by cwlod033 on 2017-08-02
Hello,
I'm trying to install Ubuntu 16.04 alongside a fresh install of Windows 7 on my Alienware 17. The SATA mode is set to AHCI in BIOS and GParted sees all my hard drive partitions, but the only thing that shows up in my installation is the USB key. I've been googling since last night trying to find a solution, and playing with a ton of settings, but nothing seems to have helped. Has anyone else run into this problem and solved it?

---

### Post by oldfred on 2017-08-02
Is this a newer UEFI system?
And Windows 7 default install mode is the 35 year old BIOS/MBR configuration. You have to slightly modify a flash drive copy of installer to install in newer UEFI mode.

Post this:
       sudo parted /dev/sda unit s print 

If drive was gpt and your Windows install converted it to MBR, it may be the issue.
Windows often has incorrectly converted from gpt to MBR leaving backup gpt partition table which is one of the advantages of gpt. But Windows does not seem to care that drive is misconfigured.

 If that is the case.

 FixParts is the easiest way to remove the stray GPT data. GPT fdisk (gdisk or sgdisk) can do it, but the procedure's a bit more involved.
[http://www.rodsbooks.com/fixparts/](http://www.rodsbooks.com/fixparts/)
sudo fixparts /dev/sda 

But really better to install Windows 7 in UEFI boot mode, to take full advantage of UEFI and gpt.

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

### Post by cwlod033 on 2017-08-03
```

ubuntu@ubuntu:~$ sudo parted /dev/sda unit s print
Model: ATA WDC WD10JPVX-75J (scsi)
Disk /dev/sda: 1953525168s
Sector size (logical/physical): 512B/4096B
Partition Table: msdos
Disk Flags: 

Number  Start        End          Size         Type     File system  Flags
 1      2048s        206847s      204800s      primary  ntfs         boot
 2      206848s      1871599615s  1871392768s  primary  ntfs
 3      1871599616s  1953523711s  81924096s    primary  ntfs


```

Not sure if that shows anything glaring.

---

### Post by oldfred on 2017-08-03
Was previous install gpt/UEFI?
Parted does not show if you have backup gpt table still on drive or not.
Fixparts should show if you do or not. Do not write new table from fixparts, but use it to see what it says.

---

### Post by cwlod033 on 2017-08-03
I'll give that a shot. How to I check to see if the previous install was gpt/UEFI? I'm not sure what either of those are. I didn't come across those as an option when I was installing windows 7.

---

### Post by oldfred on 2017-08-03
Windows 7 just default installs in BIOS/MBR mode. You have to copy DVD to flash drive and move a couple of files around to make it UEFI bootable. How it boots is how it installs.

If system was pre-installed with any newer version of Windows it was UEFI/gpt.

---

### Post by cwlod033 on 2017-08-03
The system was originally Windows 7 but was updated to Windows 10 before I reformatted it and switched it back to Windows 7. Ill print out the fixparts info in a moment.

---

### Post by cwlod033 on 2017-08-03
This is what I have from the fixparts partition table:

```
Disk size is 1953525168 sectors (931.5 GiB)
MBR disk identifier: 0xF56988C7
MBR partitions:

                                                   Can Be   Can Be
Number  Boot  Start Sector   End Sector   Status   Logical  Primary   Code
   1      *           2048       206847   primary     Y        Y      0x07
   2                206848   1871599615   primary              Y      0x07
   3            1871599616   1953523711   primary              Y      0x07


```

---

### Post by oldfred on 2017-08-03
It is not seeing a backup gpt, so that is not the issue.
Did you leave Windows hibernated? Newer Windows are always hibernated and you have to turn it off. But Windows 7 is not normally hibernated.

Best then just to use Windows own tools to shrink the Windows 7 NTFS partition and reboot so it can run chkdsk. 
Then with gparted you can create / (root) & swap & if desired a separate partition for /home. Default install is just / & swap.
Then use Something Else and choose(change button) the partition you want for / and ext4.

Newer versions of Ubuntu are really the same.
 Lots of detail, screenshots and essential info.14.04  Something Else example
[http://www.dedoimedo.com/computers/ubuntu-14-04-install-guide.html](http://www.dedoimedo.com/computers/ubuntu-14-04-install-guide.html)
[http://askubuntu.com/questions/343268/how-to-use-manual-partitioning-during-installation](http://askubuntu.com/questions/343268/how-to-use-manual-partitioning-during-installation)
[http://askubuntu.com/questions/163962/install-alongside-option-missing-how-do-i-install-ubuntu-beside-windows-using](http://askubuntu.com/questions/163962/install-alongside-option-missing-how-do-i-install-ubuntu-beside-windows-using) 

      
 Any install with Something Else which is required with  external drives or any second drive or any install with separate /home
Also shows combo box with location of grub2 boot loader
[https://help.ubuntu.com/community/Grub2/Installing](https://help.ubuntu.com/community/Grub2/Installing)

---

### Post by cwlod033 on 2017-08-03
I just checked BIOS. It was booting in UEFI mode. I switched it to Legacy and tried installing, but that didn't change anything.

I've got 2 HDDs. Windows is installed on one, and I partitioned the other HDD for Ubuntu. I'll go into the disk manager now and shrink the Windows 7 partition right now and then give it a shot. Failing this, I'm thinking about just reformatting again and installing Ubuntu as the first OS. Any thoughts on that?

---

### Post by cwlod033 on 2017-08-03
I gave it a shot and it didnt work, so I formatted everything in gparted and tried installing again. The installer still doesnt show any partitions, and when I try to click through it anyway, it gives me an error saying 
"No root file system is defined. Please correct this from the partitioning menu."

Thats the same error I was getting before and I'm guessing its because the installer still doesnt recognize any hard drives to install to.

---

### Post by oldfred on 2017-08-03
If two drives, you can just disconnect the Windows drive and install to the Ubuntu drive.
You should not have to shrink Windows then.

Is second drive shown in gparted?
You only posted info on sda, so I assumed that is where you wanted to install.
What is on sdb. Post details as you did with sda above.

But if not disconnecting, then you have to use Something Else.
And since Windows is in BIOS mode, best to install Ubuntu in BIOS mode. But possibly better to have Windows in UEFI mode & Ubuntu in UEFI mode, if you have new UEFI hardware.

Since hardware is UEFI, and you have a separate disk for Ubuntu, I would use gpt partitioning. And include both the ESP - efi system partition for future use if you later want UEFI and a bios_grub partition to boot in BIOS mode now.

 For the Total space you want for Ubuntu:
Ubuntu's standard install is just / (root) & swap, but it is better to add another partition for /home if allocating over 30GB.:
Only if gpt -  all partitions in gpt are primary (no logicals):
gpt: 300-500 MB efi FAT32 w/boot flag (ESP for UEFI boot or future use for UEFI, you only can have one per drive, so if already existing do not attempt another)
gpt: 1 or 2 MB No Format w/bios_grub flag (for BIOS boot not required for UEFI)
for gpt(GUID) or MBR(msdos) partitioning
Ubuntu partitions - smaller root only where hard drive space is limited.
If total space less than about 30 to 50GB just use / not separate /home or standard install.


[LIST=1]
[*]25-30+ GB Mountpoint / primary or logical beginning ext4 
[*]all but 2 GB Mountpoint /home logical beginning ext4 
[*]2 GB Mountpoint swap logical 
[/LIST]
    Depending on how much memory you have you may not absolutely need swap but having some is still recommended. I do not hibernate (boots fast enough for me) but if hibernating then you need swap equal to RAM in GiB not GB. And if dual booting with windows a shared NTFS partition is also recommended. But you usually cannot create that as part of the install, just leave some space. Or partition in advance (recommended).
One advantage of partitioning in advance is that the installer will use the swap space to speed up the install. Thanks Herman for the tip.
[https://help.ubuntu.com/community/DiskSpace](https://help.ubuntu.com/community/DiskSpace)
suggested partitions for just Ubuntu on 3TB drive.
[http://askubuntu.com/questions/336439/any-problems-with-this-partition-scheme](http://askubuntu.com/questions/336439/any-problems-with-this-partition-scheme)
Another advanced suggestion from TheFu with Multiple / (root) - Post #5 similar to what I actually do
[http://ubuntuforums.org/showthread.php?t=2170308](http://ubuntuforums.org/showthread.php?t=2170308)
[http://ubuntuforums.org/showthread.php?t=2021534](http://ubuntuforums.org/showthread.php?t=2021534)
UEFI/gpt partitioning in Advance:
[http://askubuntu.com/questions/743095/how-to-prepare-a-disk-on-an-efi-based-pc-for-ubuntu](http://askubuntu.com/questions/743095/how-to-prepare-a-disk-on-an-efi-based-pc-for-ubuntu)

---

### Post by cwlod033 on 2017-08-03
```
ubuntu@ubuntu:~$ sudo parted /dev/sdc unit s print
Model: ATA LITEONIT DMT-80M (scsi)
Disk /dev/sdc: 156301488s
Sector size (logical/physical): 512B/512B
Partition Table: msdos
Disk Flags: 

Number  Start  End  Size  Type  File system  Flags


```

Thats what I have for the other hard drive. I've reformatted everything already and am trying to do a fresh install of ubuntu first before windows, but it still doesnt recognize the hard drives.

And yes, GParted shows both hard drives.

---

### Post by cwlod033 on 2017-08-03
I just used sudo apt-get remove dmraid and that seems to have fixed the issue completely. In the process of installing now.

---

### Post by oldfred on 2017-08-03
So how did drive get RAID data on it? Was it RAID before?

And I still suggest gpt, even if currently BIOS as then you have flexibility to change to UEFI, without total redo.
But some advantages to gpt, like backup partition table.

---

### Post by shridhar-kapshikar on 2017-08-04
Use Rufus utility in order to make bootable USB. use GParted partition from the dropdown menu and keep FAT32 partition type.

---

