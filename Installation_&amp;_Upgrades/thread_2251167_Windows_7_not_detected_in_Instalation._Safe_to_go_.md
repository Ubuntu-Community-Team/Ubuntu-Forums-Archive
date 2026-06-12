---
title: "Windows 7 not detected in Instalation. Safe to go foward?"
date: 2014-11-02
forum: Installation &amp; Upgrades
---

### Post by X_Splinter on 2014-11-02
So guys I had problems in the past in dual botting with this PC.

I 2 Drives SSD and HDD

SSD - NTFS Windows 7 installed
        - 14.04 EXtT4 patition (without ./home) waiting for Kubuntu 14.10

HDD - NTFS where I got data for Windows
       - Unloctade Space waiting for Kubuntu home dir

I booted USB Live Kubuntu via UEFI. When installing it shows this:

[IMG]http://s3.postimg.org/ejxrlroyb/snapshot1.png[/IMG]

Isn't suppose to detected Windows 7 and ask to make a side by side Install?

I am going to do it Manualy I just want to make sure I will able to boot windows 7 after this.

I believe both disks are GPT and Windows is using UEFI (but If you could help confirm that)

**Currently I am booting via Grub2**

---

### Post by ajgreeny on 2014-11-02
The installer does appear to have seen the Windows partitions but for some reason is not actually showing them separately in the top disk line that you show; it does, however, mention 1MB free space, 209.7MB fat32 Windows Boot Manager, an unknown 134.2MB sda2 and finally 208GB sda3 ntfs partition, presumably one of your Windows OS partitions.  I have no idea why those partitions appear to be all lumped together

 However, as far as I'm aware the easiest way to find out which mode Windows was installed in is to boot to the live Ubuntu USB or DVD and run ```
sudo parted -l
```If you see a line like ```
1      1049kB  211MB   210MB   fat32           EFI System Partition  boot
```you have a UEFI system; if a line similar to that does not appear you have an MBR system, even if it is using gpt partitions, which I am pretty sure can be used for either mode in Win7, though maybe not Win8.

I do not have Windows any more so I could be wrong with that final comment so wait for more info to be certain, but if you have gpt partitions you will also see ```
Partition Table: gpt
```in the output of that parted command.

---

### Post by oldfred on 2014-11-02
You can & should run the commands suggested by ajgreeny. 

But it looks like the Kubuntu installer is only seeing the Windows boot files in the efi partition which is your first partition.
The second partition is an unformatted partition required by Windows for UEFI booting. 
 Order on drive is important: msftres
[http://en.wikipedia.org/wiki/Microsoft_Reserved_Partition](http://en.wikipedia.org/wiki/Microsoft_Reserved_Partition)

Windows only boots from gpt partitioned drives with UEFI. 
Windows 7 usually is installed in BIOS mode on MBR drives, but can be installed in UEFI mode.

      
 GPT Advantages (older but still valid)  see post#2 by srs5694:
[http://ubuntuforums.org/showthread.php?t=1457901](http://ubuntuforums.org/showthread.php?t=1457901)
[https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT](https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT)
UEFI Advantages
[http://askubuntu.com/questions/446968/legacy-vs-uefi-help](http://askubuntu.com/questions/446968/legacy-vs-uefi-help)

---

### Post by X_Splinter on 2014-11-03
Thanks for the fast replies guys, thats why I love this forum

I did sudo parted -l

```
kubuntu@kubuntu:~$ sudo parted -l
Model: ATA LITEONIT LAT-256 (scsi)
Disk /dev/sda: 256GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt
Disk Flags: 

Number  Start   End    Size    File system  Name                          Flags
 1      1049kB  211MB  210MB   fat32        EFI system partition          boot, esp
 2      211MB   345MB  134MB                Microsoft reserved partition  msftres
 3      345MB   208GB  208GB   ntfs         Basic data partition          msftdata
 4      208GB   230GB  21,5GB  ext4
 5      230GB   256GB  26,2GB  ntfs         Basic data partition          diag


Model: ATA ST9750420AS (scsi)
Disk /dev/sdb: 750GB
Sector size (logical/physical): 512B/4096B
Partition Table: gpt
Disk Flags: 

Number  Start   End    Size   File system  Name                          Flags
 1      17,4kB  134MB  134MB               Microsoft reserved partition  msftres
 2      135MB   375GB  375GB  ntfs         Basic data partition          msftdata


```

As expected they are in GPT.  The problem I had with the previous install was that sdb had currept partition table so Windows could not boot. (I formated sdb and I left 375Gb unloacted for /home)

SDA still has Kubuntu 14.04 (cannot boot because it has no /home). I plan to install 14.10 over it.

The thing is, rigth now when I start my PC it loads Grub2 and thats how I load Windows 7.

Do I have to do anything special? I plan in installing ./ on sda4 (where 14.04 is) and ./home on sdb (unlocated free space) and bootloader on sda

---

### Post by ajgreeny on 2014-11-03
Just make sure you boot the install disk in UEFI mode as you need Kubuntu in UEFI for both OSs to work together as dual boot.

Good luck!

---

### Post by oldfred on 2014-11-03
You should be able to directly boot Windows from UEFI menu or one time boot key often f12 or f10, if you have that.
Or did you run Boot-Repair and it ran its 'buggy' UEFI fix. Then you only can boot from grub menu as it has renamed the Windows boot file. And a reinstall will not have that entry. If so, undo the fix with Boot-Repair first.

---

### Post by X_Splinter on 2014-11-03
Ok, so I dont recall using Boot-Repair before. I pressed ESC (boot selection on my pc) and I notice that was an option to boot directly to Windows. (But I have Grub2 as default)

So, running the usb drive as UEFI I installed Kubuntu the way I said before. All went perfect, after rebooting it loads Grub2 by default and I can choose to boot Kubuntu or Windows 7 with no problems at all. :-D:-D:-D

The only thing that is different now is that before loading Grub2 on the top left corner it says "Boot in unsecured mode" which is strange I dont think I ever had safe boot (thats a Windows 8 thing right)

What it matters is that I now my machine perfect.

By the way this was done on an Asus ROG G75VW

---

### Post by oldfred on 2014-11-03
UEFI update may have added it, or it was hidden before. It is a warning that you are not "secure" which is really Windows marketing and only a tiny bit of security. 
Eventually we may want secure boot, but Windows added it as a requirement for UEFI boot. They have massive marketing issues on virus and other security issues, so what better than to have a "secure" boot as the only way Windows boots.
The only problem is that the only major boot virus was actually from Sony when it tried to implement some DRM so you could not copy videos or music or something.

---

