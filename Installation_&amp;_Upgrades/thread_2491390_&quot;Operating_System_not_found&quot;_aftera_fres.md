---
title: "&quot;Operating System not found&quot; aftera fresh install of Lubuntu 22.04"
date: 2023-10-06
forum: Installation &amp; Upgrades
---

### Post by tomcatpi on 2023-10-06
[COLOR=#000000]Hello everyone,[/COLOR]
[COLOR=#000000]
[/COLOR]
[COLOR=#000000]I installed Lubuntu version 22.04.3 on an old Toshiba Satellite P500-16J laptop. Everything goes well during the installation, except that when I restart the machine, I get a &#8220;Operating System not found&#8221; screen.[/COLOR]
[COLOR=#000000]I understood that this could be due to the fact that my machine was in legacy bios (no UEFI on it) and so I remade a USB key with Rufus by forcing legacy bios mode, same result[/COLOR]
[COLOR=#000000]By searching the forums, I tried to install grub then a boot repair, always the same result.[/COLOR]
[COLOR=#000000]
[/COLOR]
[COLOR=#000000]
[/COLOR]
[COLOR=#000000]I'm posting boot-info content to you

```
boot-repair-4ppa2056                                              [20231004_1704]
```[/COLOR]```

[COLOR=#000000]
============================== Boot Info Summary ===============================

 => Grub2 (v2.00) is installed in the MBR of /dev/sdb and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (,msdos1)/boot/grub. It also embeds following components:
    
    modules
    ---------------------------------------------------------------------------
    fshelp ext2 part_msdos biosdisk
    ---------------------------------------------------------------------------

sdb1: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Ubuntu 22.04.3 LTS
    Boot files:        /boot/grub/grub.cfg /etc/fstab /etc/default/grub 
                       /boot/grub/i386-pc/core.img

sda: ___________________________________________________________________________

    File system:       iso9660
    Boot sector type:  Grub2 (v1.99-2.00)
    Boot sector info:  Grub2 (v1.99-2.00) is installed in the boot sector of 
                       sda and looks at sector 0 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location.
    Mounting failed:   mount: /mnt/BootInfo/FD/sda: /dev/sda already mounted or mount point busy.


================================ 1 OS detected =================================

OS#1:   Ubuntu 22.04.3 LTS on sdb1

================================ Host/Hardware =================================

CPU architecture: 64-bit
Video: GT216M [GeForce GT 330M] from NVIDIA Corporation
Live-session OS is Ubuntu 64-bit (Ubuntu 22.04.3 LTS, jammy, x86_64)

===================================== UEFI =====================================

BIOS/UEFI firmware: 1.90     from TOSHIBA
This live-session is in Legacy/BIOS/CSM mode (not in EFI mode).



============================= Drive/Partition Info =============================

Disks info: ____________________________________________________________________

sdb    : notGPT,    no-BIOSboot,    has-noESP,     not-usb,    not-mmc, has-os,    no-wind,    2048 sectors * 512 bytes

Partitions info (1/3): _________________________________________________________

sdb1    : is-os,    64, apt-get,    grub-pc ,    grub2,    grub-install,    grubenv-ok,    update-grub,    farbios

Partitions info (2/3): _________________________________________________________

sdb1    : isnotESP,    fstab-without-efi,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot

Partitions info (3/3): _________________________________________________________

sdb1    : not--sepboot,    with-boot,    fstab-without-boot,    not-sep-usr,    with--usr,    fstab-without-usr,    std-grub.d,    sdb

fdisk -l (filtered): ___________________________________________________________

Disk sda: 7.47 GiB, 8021606400 bytes, 15667200 sectors
Disk identifier: ACD8E4DC-CD7D-47B7-AA33-3F5B801A30B9
        Start      End Sectors  Size Type
sda1       64  5699387 5699324  2.7G Microsoft basic data
sda2  5699388  5709455   10068  4.9M EFI System
sda3  5709456  5710055     600  300K Microsoft basic data
sda4  5713920 15667136 9953217  4.7G Linux filesystem
Disk sdb: 465.76 GiB, 500107862016 bytes, 976773168 sectors
Disk identifier: 0x4ac7e31a
      Boot Start       End   Sectors   Size Id Type
sdb1  *     2048 976768064 976766017 465.8G 83 Linux
Disk zram0: 1.84 GiB, 1976573952 bytes, 482562 sectors

parted -lm (filtered): _________________________________________________________

sda:8022MB:scsi:512:512:gpt:JetFlash Transcend 8GB:;
1:32.8kB:2918MB:2918MB::ISO9660:hidden, msftdata;
2:2918MB:2923MB:5155kB::Appended2:boot, esp;
3:2923MB:2924MB:307kB::Gap1:hidden, msftdata;
4:2926MB:8022MB:5096MB:ext4::;
sdb:500GB:scsi:512:512:msdos:ATA TOSHIBA MK5055GS:;
1:1049kB:500GB:500GB:ext4::boot;

blkid (filtered): ______________________________________________________________

NAME   FSTYPE   UUID                                 PARTUUID                             LABEL                     PARTLABEL
sda    iso9660  2023-08-07-15-52-22-00                                                    Lubuntu 22.04.3 LTS amd64 
&#9500;&#9472;sda1 iso9660  2023-08-07-15-52-22-00               acd8e4dc-cd7d-47b7-aa32-3f5b801a30b9 Lubuntu 22.04.3 LTS amd64 ISO9660
&#9500;&#9472;sda2 vfat     F7DB-4D56                            acd8e4dc-cd7d-47b7-aa31-3f5b801a30b9 ESP                       Appended2
&#9500;&#9472;sda3                                               acd8e4dc-cd7d-47b7-aa30-3f5b801a30b9                           Gap1
&#9492;&#9472;sda4 ext4     aaba4e6c-5cb4-441b-ae22-51ff83ebefd7 b81e673f-4f1f-964d-a222-4189febdba2f writable                  
sdb                                                                                                                 
&#9492;&#9472;sdb1 ext4     550521f2-185d-4cd3-9754-3c1c0cfa684d 4ac7e31a-01                                                    

Mount points (filtered): _______________________________________________________

                                                               Avail Use% Mounted on
/dev/disk/by-label/writable[/install-logs-2023-10-04.5/crash]   4.3G   0% /var/crash
/dev/disk/by-label/writable[/install-logs-2023-10-04.5/log]     4.3G   0% /var/log
/dev/sda1                                                          0 100% /cdrom
/dev/sdb1                                                       427G   2% /mnt/boot-sav/sdb1

Mount options (filtered): ______________________________________________________


====================== sdb1/boot/grub/grub.cfg (filtered) ======================

Ubuntu   550521f2-185d-4cd3-9754-3c1c0cfa684d
Ubuntu, with Linux 6.2.0-26-generic   550521f2-185d-4cd3-9754-3c1c0cfa684d
### END /etc/grub.d/30_os-prober ###
### END /etc/grub.d/30_uefi-firmware ###

========================== sdb1/etc/fstab (filtered) ===========================

# <file system>             <mount point>  <type>  <options>  <dump>  <pass>
UUID=550521f2-185d-4cd3-9754-3c1c0cfa684d /              ext4    defaults   0 1
/swapfile                                 swap           swap    defaults   0 0

======================= sdb1/etc/default/grub (filtered) =======================

GRUB_DEFAULT=0
GRUB_TIMEOUT_STYLE=menu
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""
GRUB_DISABLE_OS_PROBER=false

==================== sdb1: Location of files loaded by Grub ====================

           GiB - GB             File                                 Fragment(s)
 364.378303528 = 391.248224256  boot/grub/grub.cfg                             1
 364.382156372 = 391.252361216  boot/grub/i386-pc/core.img                     1
   3.258464813 = 3.498749952    boot/vmlinuz                                   2
   3.258464813 = 3.498749952    boot/vmlinuz-6.2.0-26-generic                  2
   3.258464813 = 3.498749952    boot/vmlinuz.old                               2
   3.856601715 = 4.140994560    boot/initrd.img                                1
   3.856601715 = 4.140994560    boot/initrd.img-6.2.0-26-generic               1
   3.856601715 = 4.140994560    boot/initrd.img.old                            1

===================== sdb1: ls -l /etc/grub.d/ (filtered) ======================

-rwxr-xr-x 1 root root 18683 Dec 18  2022 10_linux
-rwxr-xr-x 1 root root 43031 Dec 18  2022 10_linux_zfs
-rwxr-xr-x 1 root root 14387 Dec 18  2022 20_linux_xen
-rwxr-xr-x 1 root root 13369 Dec 18  2022 30_os-prober
-rwxr-xr-x 1 root root  1372 Dec 18  2022 30_uefi-firmware
-rwxr-xr-x 1 root root   700 May 17 05:35 35_fwupd
-rwxr-xr-x 1 root root   214 Dec 18  2022 40_custom
-rwxr-xr-x 1 root root   215 Dec 18  2022 41_custom



Suggested repair: ______________________________________________________________

The default repair of the Boot-Repair utility would reinstall the grub2 of
sdb1 into the MBR of sdb.
Grub-efi would not be selected by default because no ESP detected. [/COLOR][COLOR=#000000]Additional repair would be performed: unhide-bootmenu-10s[/COLOR]
```[COLOR=#000000]

if it can help, here is some picture of my bios, I don't see any UEFI mode

[/COLOR][COLOR=#000000]see post #5 for the last 2 screenshots

I don't know what I can do else ?

Thanks for your help



[/COLOR]

---

### Post by sudodus on 2023-10-06
I have also an old Toshiba  (satellite-pro-c850-19w, I think slightly newer than yours, bought 2013), and I can install and run it both in BIOS mode (alias CSM alias legacy mode) and UEFI mode.

Through the years it has been very willing to boot with all current versions of Lubuntu. So I think I can help you.

[hr][/hr]
- Did you check that the downloaded iso file was good (check with **[FONT=Courier New]sha256sum[/FONT]**)?

- Did you check that the internal drive is good (check the S.M.A.R.T. status with **[FONT=Courier New]sudo smartctl -H /dev/sdx[/FONT]** where x is the drive letter e.g. **[FONT=Courier New]a[/FONT]**)?

- You can try with Rufus in **dd-mode** which means cloning. (Cloned USB drives work well for me in the Toshiba.)

- It might help if you prepare the target drive (I guess an internal drive in your case) by creating a fresh GUID partition table, GPT. You need not create any partition. [This link might be helpful](https://discourse.lubuntu.me/t/install-lubuntu-mantic-to-the-same-drive-as-you-booted-live-from/4596/1), but I think your case is simpler, (assuming that you intend to install into the internal drive).

---

### Post by tomcatpi on 2023-10-06
I tried to create a usb drive by forcing UEFI mode with Rufus, and the laptop refuse toi boot saying that I was trying to use a UEFI drive with a legacy bios, so I doubt my laptop is UEFI compatible
I checked the downloade file, it is ok
I can rebuit a fresh GUID partition table, but which kind I should use, the actual said it is msdos, and I understand that GPT is only for UEFI computer

---

### Post by oldfred on 2023-10-06
Please do not post screenshots or photos in line. Just attach.
If you use the Forum's advanced editor, you can use the paperclip icon to attach screenshots or other info. Post #4 , also no larger than1024x768 if photo
[https://ubuntuforums.org/showthread.php?t=2054969&p=12229098#post12229098](https://ubuntuforums.org/showthread.php?t=2054969&p=12229098#post12229098)

Do you have latest UEFI (even if older) firmware from vendor?

You can (and should, but not required) use gpt with BIOS boot with Ubuntu.
The only time you must have MBR(msdos) partitioning is if installing Windows in old BIOS boot mode.

But with gpt and BIOS boot you must have a 1MB unformatted partition with the bios_grub partition. Not sure if installer auto creates that if drive seen as gpt or not?

I used gpt with my 2006 Toshiba BIOS only system starting in about 2010 or 2011.

GPT Advantages (older 2010 but still valid)  see post#2 by srs5694:
[gpt Advantages]([http://ubuntuforums.org/showthread.php?t=1457901](http://ubuntuforums.org/showthread.php?t=1457901)) & 
[https://wiki.archlinux.org/title/Partitioning#Choosing_between_GPT_and_MBR](https://wiki.archlinux.org/title/Partitioning#Choosing_between_GPT_and_MBR)
[http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface](http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface)

Be sure to choose to install optional restricted drivers to get get nVidia driver if still available for your older nVidia.

---

### Post by tomcatpi on 2023-10-06
> **oldfred said:**
> Please do not post screenshots or photos in line. Just attach.
If you use the Forum's advanced editor, you can use the paperclip icon to attach screenshots or other info. Post #4 , also no larger than1024x768 if photo
[https://ubuntuforums.org/showthread.php?t=2054969&p=12229098#post12229098](https://ubuntuforums.org/showthread.php?t=2054969&p=12229098#post12229098)

I didn't know
I edited my post and attache the image
since I've got seven one, I put the 2 last ones in this post


> [COLOR=#000000]Do you have latest UEFI (even if older) firmware from vendor?[/COLOR]
Unfortunately I was unable to find an update of the bios for my laptop. The only one I found needs windows to run, which I don't have

---

### Post by tomcatpi on 2023-10-06
> **oldfred said:**
> 

But with gpt and BIOS boot you must have a 1MB unformatted partition with the bios_grub partition. Not sure if installer auto creates that if drive seen as gpt or not?.

How can I do that with gparted, is there is any tutorial on how to do that ?

---

### Post by sudodus on 2023-10-06
**It should work to boot in BIOS (legacy) mode.** Now I suspect that your computer is too old to have a good UEFI mode, maybe it has an experimental UEFI mode. (I had an HP computer with the same generation CPU, that worked best in BIOS mode.)

* You can try with Rufus in dd-mode which means cloning. (Cloned USB drives work well for me in the Toshiba.)

[hr][/hr]
* Actions to prepare the internal drive, the target of the installation:

You can find 'full tutorials' about **[FONT=Courier New]gparted[/FONT]** via the internet, but quickly:

- Unmount all partitions of the target drive before starting gparted

- Select target drive at the top right corner of the gparted window

- Select the pull down menu 'Device' -- 'Create partition table' -- msdos (the default)

- 'Apply' 

I don't think you need to do more with gparted. The installer should fix the partition(s) for you, at least for booting in BIOS (legacy) mode with an msdos partition table (which is what I suggest for this computer).

---

### Post by guiverc on 2023-10-06
If your ISO is written correctly to thumb-drive (*ISO was valid; ie. checksum check, and write as perfect - I verify this step*) the ISO will boot in all of

- legacy/BIOS hardware
- uEFI 
- modern Secure-uEFI

without any change. The installation will determine what mode your machine is using during boot, however a reformat of the ISO (*using rufus modes/features*) can cause this self-detection of your hardware to be incorrect & thus the problem you are experiencing.

I prefer simple *clones* of the ISO to media; as this is what is QA tested to work in all hardware.  Please note @sudodus will be the expert here though 

(*I've done >10 installs in this last week on legacy devices as old as from 2005* *using Lubuntu*)

---

### Post by oldfred on 2023-10-06
You still posted in line, not just attachments.
You can also use gparted but must change device label to gpt or default partitioning first.
With gparted select gpt under device, advanced over msdos(MBR) default partitioning before starting.
Some older gparted screen shots. Still the same, but now graphics may be slightly different.
Note that change from MBR to gpt (or vice-versa) totally erases entire hard drive. So if other partitions have data, be sure to have good backups.

---

### Post by tomcatpi on 2023-10-07
@guiverc and @sudodus

I try, but after re-intsalling lubuntu, I still have the same problem

---

### Post by jeremy31 on 2023-10-07
Can you post results from terminal for ```
sudo parted -l
```

---

### Post by MAFoElffen on 2023-10-07
I have a way that ensures that is has a ms-dos partition table to start out the install with... And gets around any hard places where there might be a problem.

But first:
*** In post #5, in the first attached photo, you have many options that are set wrong. Though they do not affect the booting of Ubuntu, you might want to reset your BIOS to it's defaults. That would be easier and faster than resetting all those options in Power Management individually. 

Let me try to explain this in a sort of way they we ensure you start out with a partition format that will both from Legacy Bios, but also give you the added, updated abilities to create more than 4 primary partitions. These instruction will create a GPT partitioned disk, with a bios-boot partition for legacy Grub to install to for Legacy BIOS boot, and set up all your other partitions for Lubuntu to install to.

I think that if you just created a GPT partition table and a boot_bios partition, that if you select "Erase all and Install", that event though it would see un-allocated space on the drive, it would delete the bios_boot partition, so these instructions will get you past that point. 

Boot from the Lubuntu installation live USB media. On boot select Try.

When you get to the desktop, open a terminal session.
```

lsblk -e7 -o name,size,model

```
Write down the disk id that is not the USB drive. It will be either sda or sdb. Let's say it said your 500GB drive came back in the output as "sdb"... (Adjust according to your own output>) Note that in these instructions, any line starting with a "#" character is just a comment to try to explain what each command means... You do not have to type that line. 
```

#  This will zero the disk, be sure you have the disk id correct.
sudo sgdisk --zap-all /dev/sdb
# This will create a bios_boot partition for legacy Grub to install stage 2 to on a GPT partitioned disk.
sudo sgdisk     -n1:2:+5M   -c1:boot_bios    -t1:EF02 /dev/sdb
# This will create a Swap partition
sudo sgdisk     -n2:0:+8G     -c2:swap            -t2:8200 /dev/sdb
# This will create a partion for your system to install to
sudo sgdisk     -n3:0:+60G   -c3:root              -t3:8300 /dev/sdb
# This will create a separate home directory.
sudo sgdisk     -n4:0:0          -c4:home           -t4:EF02 /dev/sdb

```
Go to the Desktop and start the installer. When it comes to the screen the selects the installation type, choose Do something else to get to the partitioner.

Highlight the second partition, sdb2, and select the "Change" icon. In the dialog that appears, select "Use As" to Swap. Save.

Highlight the third partition, sdb3, and select the "Change" icon. In the dialog that appears, change "Use As" to ext4, format checkbox, mount at "/". Save

Highlight the fourth partition, sdb4, and select the "Change" icon. In the dialog that appears, change "Use As" to ext, format checkbox, mount at "/home". Save

At the bottom of partitioner, Change where to install the bootloader to "sdb"... Not to a partition. To the base of the drive.

Select the "Continue" Button in the lower left of the panel to continue the Install.

That should get you around everything where there might be a problem, plus give you some plus'es in your your installation.

---

### Post by MAFoElffen on 2023-10-07
Of course if you just want a canned install (easier)...

Then booted in the Live Image EnvironMent (Try), in a terminal do:
```

sudo sgdisk --zap-all /dev/sdb
sudo fdisk /dev/sdb

```
Press <o> <Enter>, to add a new MS-DOS partition table. 

Press <w> <Enter> to write the changes and quit fdisk. 

Start the installer and install with any options. You can use any "Erase All" option and it will see that partition table and know what to do.

---

### Post by tomcatpi on 2023-10-08
here is the result of the command

```
sudo parted -l
```

```
Model: JetFlash Transcend 8GB (scsi)
Disk /dev/sda: 8022MB
Sector size (logical/physical): 512B/512B
Partition Table: msdos
Disk Flags: 

Number  Start   End     Size    Type     File system  Flags
 1      65.5kB  8022MB  8021MB  primary  fat32        boot, lba
 2      8022MB  8022MB  32.3kB  primary               bls_boot


Model: ATA TOSHIBA MK5055GS (scsi)
Disk /dev/sdb: 500GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos
Disk Flags: 

Number  Start   End    Size   Type     File system  Flags
 1      1049kB  500GB  500GB  primary  ext4         boot


Model: Unknown (unknown)
Disk /dev/zram0: 1977MB
Sector size (logical/physical): 4096B/4096B
Partition Table: loop
Disk Flags: 

Number  Start  End     Size    File system     Flags
 1      0.00B  1977MB  1977MB  linux-swap(v1)


```

---

### Post by tomcatpi on 2023-10-08
@MAFoElffen

I load the default options of the bios and boot from the live USB disk of Lubuntu
Here is the result of the command you gave to me

```
sblk -e7 -o name,size,model
NAME     SIZE MODEL
sda    465.8G TOSHIBA MK5055GSX
sdb      7.5G Transcend 8GB
&#9500;&#9472;sdb1   7.5G 
&#9492;&#9472;sdb2  31.5K 
sr0     1024M HL-DT-ST DVDRAM GT20N
zram0    1.8G 

```

```
sudo sgdisk --zap-all /dev/sda
Creating new GPT entries in memory.
GPT data structures destroyed! You may now partition the disk using fdisk or
other utilities.

```

```
sudo sgdisk     -n1:2:+5M   -c1:boot_bios    -t1:EF02 /dev/sda
Creating new GPT entries in memory.
Could not create partition 1 from 2 to 10241
Setting name!
partNum is 0
Unable to set partition 1's name to 'boot_bios'!                             
Could not change partition 1's type code to EF02!                            
Error encountered; not saving changes.  
```

```
sudo sgdisk     -n2:0:+8G     -c2:swap            -t2:8200 /dev/sda
Creating new GPT entries in memory.                                          
Setting name!                                                                
partNum is 1                                                                 
The operation has completed successfully.  

```

```
sudo sgdisk     -n3:0:+60G   -c3:root              -t3:8300 /dev/sda                                                                  
Setting name!                                                                
partNum is 2                                                                 
The operation has completed successfully.  
```

```
sudo sgdisk     -n4:0:0          -c4:home           -t4:EF02 /dev/sda
Setting name!
partNum is 3
Warning: The kernel is still using the old partition table.
The new table will be used at the next reboot or after you
run partprobe(8) or kpartx(8)
The operation has completed successfully.


```

since, the creation of bios partition didn't work, I guess I just can't continue ?
Sould I ?

---

### Post by tomcatpi on 2023-10-08
> **MAFoElffen said:**
> Of course if you just want a canned install (easier)...

Then booted in the Live Image EnvironMent (Try), in a terminal do:
```

sudo sgdisk --zap-all /dev/sdb
sudo fdisk /dev/sdb

```
Press <o> <Enter>, to add a new MS-DOS partition table. 

Press <w> <Enter> to write the changes and quit fdisk. 

Start the installer and install with any options. You can use any "Erase All" option and it will see that partition table and know what to do.


I did what you said in the post above, and I still have the same result after the install ](*,)

---

### Post by sudodus on 2023-10-08
- Did you check that the internal drive is good (check the S.M.A.R.T. status with
```

sudo smartctl -H /dev/sdx

```
where x is the drive letter e.g. a)?

[hr][/hr]
- When you can run the computer live (booted from a USB drive, and the internal drive is good, but installing seems to fail somehow, I suggest that you try extracting and cloning from a compressed image file of Ubuntu Server according to

[this link to another thread at our Ubuntu Forums](https://ubuntuforums.org/showthread.php?t=2474692)

**Please read the whole thread before doing anything**. I suggest that you download the compressed image of the **Jammy preinstalled server** (22.04.x LTS). After extracting and cloning to the internal drive, the system is there ready to boot.

If this works for you, the next step is to install a desktop environment, and for an old computer I suggest installing a lightweight environment, Lubuntu:
```

sudo apt install lubuntu-desktop

```
or Xubuntu:
```

sudo apt install xubuntu-desktop

```
and reboot.

---

### Post by tomcatpi on 2023-10-09
> **sudodus said:**
> - Did you check that the internal drive is good (check the S.M.A.R.T. status with
```

sudo smartctl -H /dev/sdx

```
where x is the drive letter e.g. a)?

[HR][/HR]
- When you can run the computer live (booted from a USB drive, and the internal drive is good, but installing seems to fail somehow, I suggest that you try extracting and cloning from a compressed image file of Ubuntu Server according to

[this link to another thread at our Ubuntu Forums]("https://ubuntuforums.org/showthread.php?t=2474692")

**Please read the whole thread before doing anything**. I suggest that you download the compressed image of the **Jammy preinstalled server** (22.04.x LTS). After extracting and cloning to the internal drive, the system is there ready to boot.

If this works for you, the next step is to install a desktop environment, and for an old computer I suggest installing a lightweight environment, Lubuntu:
```

sudo apt install lubuntu-desktop

```
or Xubuntu:
```

sudo apt install xubuntu-desktop

```
and reboot.

The smart status is OK
I installed the **Jammy preinstalled server, **Everything looks fine but after that, the laptop still refuse to boot. This thing is driving me crazy ](*,) :-k :frown: :cry:

Here is the command I use

```
zsync http://cdimage.ubuntu.com/ubuntu-server/jammy/daily-preinstalled/current/jammy-preinstalled-server-amd64.img.xz.zsync[COLOR=#000000][FONT=&amp]
[/FONT][/COLOR]dus jammy-preinstalled-server-amd64.img.xz[COLOR=#000000][FONT=&amp]
[/FONT][/COLOR]
```

---

### Post by sudodus on 2023-10-10
I share your frustration. It is common that a computer is willing to boot from an internal drive, but unwilling to boot from a USB drive. If I understand correctly, this computer behaves in the opposite way.

Maybe you can accept a workaround instead of a solution, at least temporarily. I'm thinking of booting from a USB drive (have a **[FONT=Courier New]'/boot'[/FONT]** partition there), and then running from the internal drive (have the root partition **[FONT=Courier New]'/'[/FONT]** there). This might work (but it means that you will occupy one USB port for that purpose).

I can check if I can create such a system in a test computer and let you know the result ...

---

### Post by sudodus on 2023-10-10
It works to make an installed system in my Toshiba (which is slightly newer than yours) to boot from a USB pendrive, yet run from the internal drive according to the following instructions.

### Before installation ###

Clear the partition tables of 1. the internal drive and 2. the target usb drive

Install gparted
- select target at top right corner of the gparted window
- in gparted: Device -- Create Partition Table -- msdos and Apply

### During installation (booted from a live USB with Lubuntu 22.04.3 LTS) ###

Select manual partitioning:
- create root partition '/' in the internal drive with label 'root'
- create boot partition '/boot' in the target usb drive with label 'usbboot'

### After installation, still running the live system ###

- unmount the partition in the target usb drive
- unplug the target usb drive
- plug it in again (to automount to '/media/lubuntu/usbboot')

Assuming /dev/sdd is the target usb drive, to help booting the installed system:

```

lubuntu@lubuntu:~$ sudo grub-install --boot-directory=/media/lubuntu/usbboot /dev/sdd
Installing for i386-pc platform.
Installation finished. No error reported.
lubuntu@lubuntu:~$ 

```

### When booted into the installed system it should look similar to this ###

```

tester@tester-satelliteproc85019w:~$ neofetch
           `-mddhhhhhhhhhddmss`             tester@tester-satelliteproc85019w 
        ./mdhhhhhhhhhhhhhhhhhhhhhh.         ---------------------------------                                                         
     :mdhhhhhhhhhhhhhhhhhhhhhhhhhhhm`       OS: Lubuntu 22.04.3 LTS x86_64                                                            
   :ymhhhhhhhhhhhhhhhyyyyyyhhhhhhhhhy:      Host: SATELLITE PRO C850-19W PSCBXE-00C00VN5                                              
  `odhyyyhhhhhhhhhy+-````./syhhhhhhhho`     Kernel: 6.2.0-34-generic                                                                  
 `hhy..:oyhhhhhhhy-`:osso/..:/++oosyyyh`    Uptime: 2 mins                                                                            
 dhhs   .-/syhhhhs`shhhhhhyyyyyyyyyyyyhs    Packages: 1761 (dpkg), 7 (snap)                                                           
:hhhy`  yso/:+syhy/yhhhhhshhhhhhhhhhhhhh:   Shell: bash 5.1.16                                                                        
hhhhho. +hhhys++oyyyhhhhh-yhhhhhhhhhhhhhs   Resolution: 1366x768                                                                      
hhhhhhs-`/syhhhhyssyyhhhh:-yhhhhhhhhhhhhh   DE: LXQt 0.17.1                                                                           
hhhhhhs  `:/+ossyyhyyhhhhs -yhhhhhhhhhhhh   WM: Openbox                                                                               
hhhhhhy/ `syyyssyyyyhhhhhh: :yhhhhhhhhhhs   Theme: Arc-Darker [GTK3]                                                                  
:hhhhhhyo:-/osyhhhhhhhhhhho  ohhhhhhhhhh:   Icons: Adwaita [GTK3]                                                                     
 sdhhhhhhhyyssyyhhhhhhhhhhh+  +hhhhhhhhs    Terminal: qterminal                                                                       
 `shhhhhhhhhhhhhhhhhhhhhhy+` .yhhhhhhhh`    CPU: Intel i5-3210M (4) @ 3.100GHz                                                        
  +sdhhhhhhhhhhhhhhhhhyo/. `/yhhhhhhhd`     GPU: Intel 3rd Gen Core processor Graphics Controller                                     
   `:shhhhhhhhhh+---..``.:+yyhhhhhhh:       Memory: 510MiB / 11835MiB                                                                 
     `:mdhhhhhh/.syssyyyyhhhhhhhd:`                                                                                                   
        `+smdhhh+shhhhhhhhhhhhdm`                                                                                                     
           `sNmdddhhhhhhhddm-`                                                                                                        


tester@tester-satelliteproc85019w:~$ sudo parted -ls
[sudo] lösenord för tester: 
Modell: ATA KINGSTON SV300S3 (scsi)
Disk /dev/sda: 120GB
Sektorstorlek (logisk/fysisk): 512B/512B
Partitionstabell: msdos
Diskflaggor: 

Nummer  Början  End    Storlek  Typ      Filsystem  Flaggor
 1      1049kB  120GB  120GB    primary  ext4


Modell: SanDisk Extreme (scsi)
Disk /dev/sdb: 15,7GB
Sektorstorlek (logisk/fysisk): 512B/512B
Partitionstabell: msdos
Diskflaggor: 

Nummer  Början  End     Storlek  Typ      Filsystem  Flaggor
 1      1049kB  15,7GB  15,7GB   primary  ext4       startbar


tester@tester-satelliteproc85019w:~$ lsblk -e7 -o model,name,size,fstype,label,mountpoints
MODEL                    NAME     SIZE FSTYPE LABEL MOUNTPOINTS
KINGSTON SV300S37A120G   sda    111,8G              
                         &#9492;&#9472;sda1 111,8G ext4   root         /var/snap/firefox/common/host-hunspell
                                                           /
Extreme                  sdb     14,6G              
                         &#9492;&#9472;sdb1  14,6G ext4   usbboot      /boot
Multi-Card               sdc        0B              
TSSTcorp CDDVDW SN-208AB sr0     1024M              

tester@tester-satelliteproc85019w:~$ df -h
Filsystem      Storlek Använt Ledigt Anv% Monterat på
tmpfs             1,2G   1,5M   1,2G   1% /run
/dev/sda1         110G   8,1G    96G   8% /
tmpfs             5,8G      0   5,8G   0% /dev/shm
tmpfs             5,0M   4,0K   5,0M   1% /run/lock
tmpfs             5,8G      0   5,8G   0% /tmp
/dev/sdb1          15G   306M    14G   3% /boot
tmpfs             1,2G    72K   1,2G   1% /run/user/1000
tester@tester-satelliteproc85019w:~$ 

```

---

### Post by tomcatpi on 2023-10-10
> **sudodus said:**
> I share your frustration. It is common that a computer is willing to boot from an internal drive, but unwilling to boot from a USB drive. If I understand correctly, this computer behaves in the opposite way.

Maybe you can accept a workaround instead of a solution, at least temporarily. I'm thinking of booting from a USB drive (have a **[FONT=Courier New]'/boot'[/FONT]** partition there), and then running from the internal drive (have the root partition **[FONT=Courier New]'/'[/FONT]** there). This might work (but it means that you will occupy one USB port for that purpose).

I can check if I can create such a system in a test computer and let you know the result ...

Yes I can accept this workaround
Thanks for your help I will try tonight or tomoroww

Somes questions for you Sudodus:
1. I assume I use another usb disk than the one I use to boot with the live USB Lubuntu ?
2. I was wondering if I chnage my hard drive for a SSD one, if that can chnage anything ?

What I don't undestand is why I can't boot from my hard drive, while I could before
Here is the story of this laptop
Initially he was on Win7
I install Ubuntu 22.04 and Home Assistant server, and it works fine and booted normaly
Then I move my home server to a raspberry Pi, and think to reuse the laptop
I reinstall a win7, and I've got some problem with win7 to recognize the hard drive, so I wipe the harddrive with diskpart, and change the Sata controler mode form "ACPI" to "Compatibility" in BIOS
It worked, but the laptop was so slow that I decide to switch to Lubuntu, and since then I was unable to boot to the hard drive, and here we are

I thought I may help to understand, I hope I didn't screw up the hard drive (I just don't see how, since I continue to see, and can install the OS, I just can't boot from it). Maybe a new hard drive (witch I thnink to do to speed up the laptop) can do the trick ?

Thanks for you help and the time you use for me 

TomcatPI

---

### Post by oldfred on 2023-10-10
Good to not use Windows 7, that is not supported anymore and should never connect to Internet.
If thinking of and can afford a SSD, it is a good choice to improved an old system. SSDs are now a lot lower in cost than years ago, but do not buy some of the very cheap Chinese ones. They just have flash drives installed in them. Not faster and often not even the stated size.

But an SSD is just another drive. It will work just like HDD.
I might change to AHCI, if you changed to compatibility. 

My 2006 laptop was last used with 12.04 & then retired. Both batterys, main & coin battery are dead. But it boots. I tried 20.04 Ubuntu as a test & it would not even install. Server 20.04 did install & with lightweight gui worked. I normally use Kubuntu which is more of a mid-weight system and was surprised it worked when I installed it. 

I then had to use old laptop and added a BIOS boot stanza on HDD to boot the UEFI install on my external SSD. I had upgraded M.2 SSD to larger M.2 NVMe drive on my 2017 desktop and put M.2 SSD into external USB adapter. Install is Kubuntu 22.04. Bit surprised how well it worked as long as I did not load so many apps that RAM filled & it went to swap.
I now will not buy anymore flash drives as external SSD is so much faster, but still have lots of flash drives.

---

### Post by sudodus on 2023-10-10
> **tomcatpi said:**
> Yes I can accept this workaround
Thanks for your help I will try tonight or tomoroww

Somes questions for you Sudodus:
1. I assume I use another usb disk than the one I use to boot with the live USB Lubuntu ?

Yes, USB disk, SSD or pendrive. Some computers (but far from all) can even boot from a memory card.
> 
2. I was wondering if I chnage my hard drive for a SSD one, if that can chnage anything ?

An internal SSD will be very fast. An SSD connected via USB3 will be fast too, I think faster than an internal HDD.
> 
... and change the **Sata controler mode form "ACPI" to "Compatibility"** in BIOS
It worked, but the laptop was so slow that I decide to switch to Lubuntu, and since then I was unable to boot to the hard drive, and here we are ...

TomcatPI

> **oldfred said:**
> Good to not use Windows 7, that is not supported anymore and should never connect to Internet.
If thinking of and can afford a SSD, it is a good choice to improved an old system. SSDs are now a lot lower in cost than years ago, but do not buy some of the very cheap Chinese ones. They just have flash drives installed in them. Not faster and often not even the stated size.

But an SSD is just another drive. It will work just like HDD.
I might change to AHCI, if you changed to compatibility. 

My 2006 laptop was last used with 12.04 & then retired. Both batterys, main & coin battery are dead. But it boots. I tried 20.04 Ubuntu as a test & it would not even install. Server 20.04 did install & with lightweight gui worked. I normally use Kubuntu which is more of a mid-weight system and was surprised it worked when I installed it. 

I then had to use old laptop and added a BIOS boot stanza on HDD to boot the UEFI install on my external SSD. I had upgraded M.2 SSD to larger M.2 NVMe drive on my 2017 desktop and put M.2 SSD into external USB adapter. Install is Kubuntu 22.04. Bit surprised how well it worked as long as I did not load so many apps that RAM filled & it went to swap.
I now will not buy anymore flash drives as external SSD is so much faster, but still have lots of flash drives.

Oldfred knows more than I about fixing problems with Ubuntu. I can only agree. Particularly, I think you should switch back Sata controler mode to AHCI. 'Compatibility mode' might even be the cause of your problems.

---

### Post by tomcatpi on 2023-10-10
I should have said, that I already reset the Sata controler mode to "ACPI" without effect on my problem
I will try to boot on usb disk and I come back to give you the result

---

### Post by tomcatpi on 2023-10-11
> **sudodus said:**
> 
Assuming /dev/sdd is the target usb drive, to help booting the installed system:

```

lubuntu@lubuntu:~$ sudo grub-install --boot-directory=/media/lubuntu/usbboot /dev/sdd
Installing for i386-pc platform.
Installation finished. No error reported.
lubuntu@lubuntu:~$ 

```


I did what you said, but I'm stuck ate the last command
It said: grub-install: error: failed to get canonical path of '/cow'

---

### Post by sudodus on 2023-10-11
It worked without any problems for me. I ran this command from the live system (booted from the system that contains the installer). **[FONT=Courier New]/cow[/FONT]** 'copy on write' is the virtual device where the live root file system is located. I don't understand why it is not found.

Please notice that

- you must have the correct target drive, **[FONT=Courier New]/dev/sdd[/FONT]** might be changed to **[FONT=Courier New]/dev/sdb[/FONT]** or **[FONT=Courier New]/dev/sdc[/FONT]** ...

- you must select the correct target boot-directory. If you did not create the label, you must select the mountpoint manually (and use it in **[FONT=Courier New]--boot-directory=/path/to/mountpoint[/FONT]**)

Edit: Another quick check:

- Please run the following command line in order to check that you have booted in BIOS mode (alias CSM alias legacy mode)
```

test -d /sys/firmware/efi && echo efi || echo bios

```

---

### Post by tomcatpi on 2023-10-11
I ran the test, and I boot in BIOS mode
I create the label as you said and select the correct drive, aka the /dev/sdc (usb boot disk) in my case, but still i've got this weird message

To what I undestand in the forum, it seems that the live usb I used to boot an install the Lubuntu is RO, and therefore I cannot run grub on it. Is that right ?

---

### Post by yancek on 2023-10-11
>  grub-install: error: failed to get canonical path of '/cow' 				

That error means you tried to install Grub on the 'live' usb you are booting from rather than the hard drive.  When booted into the usb, you need to find which drive it is on which your system is which you want to install to (sdd?).  You then need to create a mount point and then mount that partition before running the grub-install command.  If you go to the Ubuntu site at the link below, it explains various methods for installing Grub.  Scroll about half way down the page to a section headed Fixing a Broken System via LiveCD terminal and it is explained in detail with examples.

[https://help.ubuntu.com/community/Grub2/Installing](https://help.ubuntu.com/community/Grub2/Installing)

---

### Post by sudodus on 2023-10-11
You should install grub into a second USB pendrive, not back onto the drive, that you booted the live system from. Is this what you did? In that case the error message is difficult to understand.

1. The live system is booted from the first USB pendrive. This is the system where you have the installer.

2. The root partition, /, is located in the internal drive of the computer.

3. The /boot partition is located in the second USB pendrive. The intention is to install grub into this pendrive with the **[FONT=Courier New]grub-install[/FONT]** command line.

But if you did what yancek indicates, tried to install grub back onto the first and live pendrive, then his explanation is correct.

[hr][/hr]
Anyway, now you have two explanations of what I think is the same problem. They are slightly different and I hope that it helps you see what to do.

---

