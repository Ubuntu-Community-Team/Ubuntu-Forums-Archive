---
title: "Install Grub2 to USB flash drive"
date: 2014-04-23
forum: Installation &amp; Upgrades
---

### Post by UbuntuPanda on 2014-04-23
I have a windows 7 PC with only windows 7 installed currently and I intend to install Ubuntu 13.10 to a ext4 partition on my hard drive and install grub2 to a USB flash drive. 7 things I want to know are

1. Will this allow windows to boot normally when I turn it on as if ubuntu was never installed, and only make it possible to boot to ubuntu if I plug in my USB flash drive and boot to it using the bios boot menu?

2. What files system does the Grub2 boot loade require and I would prefer it to be one that is compatible with windows?

3. Will I be able to install the boot loader to USB and at the same time be able to use the USB to store files for on the go?

4. If I ever upgrade ubuntu will it cause any damage to my USB flash drive or hard drive such as corruption?

5. If there's an upgrade to grub and I want to install it, how would I do so without causing any damage to windows or ubuntu?

6. Should I install 14.04 or 13.10 and what are the advantages of each?

7. When upgrading to a new version of ubuntu should it be a clean install or from the pop up notification?

---

### Post by Double.J on 2014-04-23
Hi there,

welcome to the forums!

what you are asking can definitely be done. What would be best is to not use a seperate boot partition (incidentally a boot partition should be ext2/3/4) but instead just install grub to the mbr of the usb stick. This leaves the rest of grub in ubuntu's boot partition and only uses the first 512 bytes of the usb stick. You can then add a single ntfs partition to the usb stick and use as is.

there is no risk of data corruption during normal use. You will only encounter an issue if you accidentally manually move grub. 

Is is there a specific reason to use a usb? You could install grub to your hard drive as in a normal set up and set it to boot windows by default with a wait time of 0 - then to boot ubuntu you just press shift as it loads.

if you do want to put a seperate /boot partition on your usb (not recommended) then grub still needs to be installed to the mbr of the stick and the /boot partition needs to go after your ntfs data partition otherwise windows will not see it. (You would also need to make sure the /etc/fstab was correctly configured. I'm genuinely not sure if the ubuntu installer would let you do it, but it doesn't offer any gains for quite a high risk of error.

Jj

---

### Post by oldfred on 2014-04-23
Several have installed grub to a flash drive.
Is your system BIOS or UEFI. Most Windows 7 systems are BIOS, but some newer hardware with Windows 7 is also UEFI. You need to install Ubuntu in same boot mode to easily dual boot. But you can boot from UEFI/BIOS in either case.

If you set BIOS to boot from flash drive first, then you will get grub menu from /boot/grub in install on hard drive. If you happen to plug flash drive into another system and try to boot you will just get grub> as it is missing the files on the install.

If flash drive is partitioned with MBR it will work to boot. If you have partitioned flash drive with gpt, you will also need a bios_grub partition. Very few have partitioned a flash drive with gpt partitioning and those are mostly for UEFI booting.

You can also use flash drive for data or add a NTFS partition for data if desired.

Flash drives do not have as long of a life as SSD or hard drives, but you are primarily reading. If you do any upgrades that cause a reinstall of grub to MBR, flash drive must be plugged in.

Use 14.04 as it now is LTS or long term support.

I like clean installs, but usually install new version to another / (root) partition to verify it works for me while still booting old version. Others have upgraded. Some have issues with upgrades if they use ppa or  install proprietary software.

---

### Post by UbuntuPanda on 2014-04-23
Thanks Oldfred for the response, I just want to know the following

How do I partition with MBR Or gpt? 

How to check if my flash drive is MBR or gpt?

Do I install the boot loader just by selecting the USB drive as the location when installing?

Oh and if you're wondering why, I want to dual booth this way to keep guests who I know from accidentally booting into ubuntu and complaining that the computer is "broken" as they are usually tech illiterate to the point they don't know their computer runs windows though they see it when they turn on their pcs, so this dual booting method is to avoid even more problems with these guests.

P.S I already have a portable full install of ubuntu 13.10 on another USB flash drive for when I'm bored and at a friend's place.

---

### Post by oldfred on 2014-04-23
Post this to see if internal drive is gpt or MBR.

sudo parted -l

Windows only boots from gpt drives with UEFI.
Windows & Ubuntu only boot from MBR(msdos) drives with BIOS.
Ubuntu will boot from a gpt partitioned drive with either UEFI or BIOS.

You create partition table type first. Gparted still defaults to MBR(msdos). I do not have Windows anymore so all new drives or any drive I totally reformat I convert to gpt.
  I used gparted and selected gpt under device, advanced & select gpt over msdos(MBR) default partitioning....

My full install on a flash drive is gpt, my SSD is gpt and one of old 160GB original drives from this desktop build in 2006 is now gpt. 

      
 In a GPT partition map, the 31 kiB area after Master Boot Record where GRUB is usually embedded to, does not exist. When GRUB can't be embedded, its only option is to use blocklists, which are unreliable and discouraged. Thus, you must make a separate "BIOS boot partition" to hold core.img. BIOS Boot Partition only needs to be about 32 KiB in size, although in most cases make it 1 MiB because of partition alignment issues. It can be anywhere on drive and has no format.


 GPT Advantages (older but still valid)  see post#2 by srs5694:
[http://ubuntuforums.org/showthread.php?t=1457901](http://ubuntuforums.org/showthread.php?t=1457901)
[https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT](https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT)

During install with Something else you can select any MBR for any available drive. All other install options default to install grub to sda.

Only the boot loader in the MBR and the core.img in the sectors after the MBR (or in the bios_grub if gpt) will be on the flash drive. All the rest of grub including menu, configuration files, scripts, os-prober etc are in the Ubuntu install.

You could also add a boot stanza on you current full install in your flash drive to also boot a new install on your hard drive. I regularly do that as a backup way to boot.

       How to: Create a Customized GRUB2 Screen that is Maintenance Free.- Cavsfan
[https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen](https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen)

    
I add entries like this. Drive & partition can be any drive. But do note that when booting from one drive, BIOS reports the boot drive as first and grub sees it as hd0. I boot sdd and it is hd0 and then all other drives are in SATA port order with my BIOS.

       gksudo gedit /etc/grub.d/40_custom
```
menuentry "Daily on sda13 with device selection" {
    set root=(hd0,13)
        linux /vmlinuz root=/dev/sda13 ro quiet splash
        initrd /initrd.img
}
menuentry "Boot from USB Drive with UUID" {
    set root=UUID=XXXX-YYYY
    linux /vmlinuz root=UUID=XXXX-YYYY ro quiet splash
    initrd /initrd.img
}


```

---

### Post by UbuntuPanda on 2014-04-24
I understand and thank you for your help Oldfred, but one more thing I want to know is if it matters how many  partitions the usb flash drive has and does it matter what file system I use on the flash drive (i.e NTFS, fat32, ext2/3/4)?

---

### Post by oldfred on 2014-04-24
I have installed grub as stand alone boot loader to every format. I even installed grub to a Windows repair flash drive to make it directly boot Linux ISOs as well as the Windows repair to have one flash drive as a mulitple repair tool.
But if you want to use data on drive with Windows you need to use FAT32 or NTFS. NTFS is normally better as it has a journal, but for small devices FAT32 is good but cannot store a file over 4GB if device is larger. With a flash drive a journal may be a disadvantage as that is more writing.

If you use ext4 you can also turn journal off and that is considered now as better than ext2. Some internal advantage of ext4, but do not know details.
But with ext4 it is only compatible with Linux and your have to set ownership & permissions which can be an advantage in limiting use by others or a disadvantage if that other is you on another computer. If you need real protection you can also encrypt it.

This is my 32GB flsah drive.
When I get my UEFI system I hope to do this an make it boot both UEFI & BIOS.
       Flash drive to boot in UEFI or BIOS - sudodus
[https://help.ubuntu.com/community/Installation/UEFI-and-BIOS](https://help.ubuntu.com/community/Installation/UEFI-and-BIOS)

    
```
fred@fred-Precise:~$ sudo parted /dev/sde unit s print
[sudo] password for fred: 
Model:   (scsi)
Disk /dev/sde: 60532992s
Sector size (logical/physical): 512B/512B
Partition Table: gpt

Number  Start      End        Size       File system  Name        Flags
 1      40s        976895s    976856s    fat32        EFI System  boot
 2      976896s    978943s    2048s                               bios_grub
 3      978944s    29650943s  28672000s  ext4         sys
 4      29650944s  60532735s  30881792s  ext4         sys

```

---

### Post by UbuntuPanda on 2014-04-24
Anyway about the USB flash drive with the full install, what can I do to optimize the longevity of the flash drive?

---

### Post by oldfred on 2014-04-24
If it is a hard drive, it should not really matter. Even SSDs now have lives comparable to hard drives but not forever.

On my small flash drive I use ext4 with journal off. But then recovery is more difficult, but it is a small drive. Any larger drive needs the journal.
 You normally want journal to speed up system recovery if you have to do repairs or run fsck. But if partition is small then it does not take long to fsck anyway and without journal writing is reduced.

---

### Post by UbuntuPanda on 2014-04-25
I still need to resize my windows partition as I currently have 3 partitions as it came with. My tech friend said I should use windows disk management to resize because it doesn't leave files corrupted so is this true? Do I need to run chkdsk after resize? Is 100 GB a good size for a Ubuntu partition because my windows partition is 2tb roughly and I only used 100 GB of it ?

---

### Post by oldfred on 2014-04-25
Windows 7 installs usually use all 4 primary partitions. You may have a hidden Boot partition.

       My laptop already has 4 primary partitions: how can I install Ubuntu?
[http://askubuntu.com/questions/149821/my-laptop-already-has-4-primary-partitions-how-can-i-install-ubuntu](http://askubuntu.com/questions/149821/my-laptop-already-has-4-primary-partitions-how-can-i-install-ubuntu)
Good advice on how to handle all four primary partitions used. - srs5694
[http://ubuntuforums.org/showthread.php?t=1686440](http://ubuntuforums.org/showthread.php?t=1686440)

Be sure to create recovery DVD(s) first. And a Windows repair CD.

Windows always needs a chkdsk after any resize. Best to use Windows own tools or Windows third party tools to resize Windows. Then immediately reboot so it can run chkdsk. NTFS partition have data in the NTFS partition boot sector on the start & size of NTFS partition and that must match partition table. Chkdsk updates that info.
Do not create new partitions with Windows, it may convert to dynamic partitions which are Windows proprietary and do not work with Linux.

How you set up partitions depends a lot on how you are going to use system. I tend to like smaller system partitions for both Windows & Ubuntu and larger data partitions. But I like to install the next Ubuntu to see if it works on my system while keeping current working install, so I have several / partitions.

      
 For the Total space you want for Ubuntu:
Ubuntu's standard install is just / (root) & swap, but it is better to add another partition for /home if allocating over 30GB.:
Only if gpt -  all partitions in gpt are primary:
gpt: 300 MB efi FAT32 w/boot flag (for UEFI boot or future use for UEFI, you only can have one per drive, so if already existing do not attempt another)
gpt: 1 MB No Format w/bios_grub flag (for BIOS boot not required for UEFI)
for gpt(GUID) or MBR(msdos) partitioning
Ubuntu partitions - smaller root only where hard drive space is limited.
If total space less than about 30GB just use / not separate /home or standard install.
1. 10-25 GB Mountpoint / primary or logical beginning ext4(or ext3)
2. all but 2 GB Mountpoint /home logical beginning ext4(or ext3)
3. 2 GB Mountpoint swap logical

   Depending on how much memory you have you may not absolutely need swap but having some is still recommended. I do not hibernate (boots fast enough for me) but if hibernating then you need swap equal to RAM in GiB not GB. And if dual booting with windows a shared NTFS partition is also recommended. But you usually cannot create that as part of the install, just leave some space. Or partition in advance (recommended).
One advantage of partitioning in advance is that the installer will use the swap space to speed up the install. Thanks Herman for the tip.
[https://help.ubuntu.com/community/DiskSpace](https://help.ubuntu.com/community/DiskSpace)
suggested partitions for just Ubuntu on 3TB drive.
[http://askubuntu.com/questions/336439/any-problems-with-this-partition-scheme](http://askubuntu.com/questions/336439/any-problems-with-this-partition-scheme)
Another advanced suggestion from TheFu with Multiple / (root) - Post #5 similar to what I actually do
[http://ubuntuforums.org/showthread.php?t=2170308](http://ubuntuforums.org/showthread.php?t=2170308)
[http://ubuntuforums.org/showthread.php?t=2021534](http://ubuntuforums.org/showthread.php?t=2021534)

---

### Post by UbuntuPanda on 2014-04-25
How do I check if I have a hidden boot partition? BTW one partition is OS (the one I'm resizing), the other is recovery and the third is a windows recovery tools partition I believe.

---

### Post by oldfred on 2014-04-25
Post this from Ubuntu terminal from Live installer.

sudo parted -l

---

### Post by UbuntuPanda on 2014-04-25
I ran the command you suggested using a live usb and this is what i got. Does this mean i can go ahead and resize it? BTW is not running chkdsk immediately after resizing the reason I see posts about corrupt Windows OS partitions on these forums? and What causes corruption when resizing partitions?

Model: ATA Hitachi HDS72302 (scsi)
Disk /dev/sda: 2000GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type     File system  Flags
 1      1049kB  106MB   105MB   primary  ntfs         boot
 2      106MB   1984GB  1984GB  primary  ntfs
 3      1984GB  2000GB  16.5GB  primary  ntfs

---

### Post by oldfred on 2014-04-26
It is not corrupted after a resize, except to the extent that it needs chkdsk. And best to run chkdsk before installing Ubuntu as booting from Grub menu does not always boot correctly when Windows needs fixes. Grub really only boots working Windows.

The NTFS partition has start and size of its partition in the PBR or partition boot sector. If it does not match Windows will not work. But chkdsk updates the size info when partition is changed.

Some then blame Linux for corrupting Windows when resizing & running chkdsk before install would eliminate all issues.

Always best to have a separate Windows repair CD or flash drive for the current version of you Windows. And the current live installer of Ubuntu even if you upgrade as then you can make repairs if needed.

 Backup windows before install - post by Mark Phelps
[http://ubuntuforums.org/showthread.php?t=2137439&p=12611710#post12611710](http://ubuntuforums.org/showthread.php?t=2137439&p=12611710#post12611710)
[http://www.macrium.com/reflectfree.asp](http://www.macrium.com/reflectfree.asp)
Another suggestion by srs5694
[http://www.runtime.org/driveimage-xml.htm](http://www.runtime.org/driveimage-xml.htm)

   Make your own Windows repairCD (not vendor recovery):
[http://forums.techarena.in/guides-tutorials/1114725.htm](http://forums.techarena.in/guides-tutorials/1114725.htm)
Windows users only - Silverlight
[http://windows.microsoft.com/en-GB/windows7/Create-a-system-repair-disc](http://windows.microsoft.com/en-GB/windows7/Create-a-system-repair-disc)

   Windows 7 repair USB, Also Vista if service pack installed
[http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/](http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/)
[http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html](http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html)

---

