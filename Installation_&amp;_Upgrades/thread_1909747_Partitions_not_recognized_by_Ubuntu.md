---
title: "Partitions not recognized by Ubuntu"
date: 2012-01-15
forum: Installation &amp; Upgrades
---

### Post by Gamersfocus on 2012-01-15
Hello :)

I am interested in duel booting Windows & Ubuntu how ever Ubuntu does not seem to recognize the partitions on my hard drive it detects the hard drive it's self without any
problems but it doesn't detect the partitions it just reads them as free space Windows how ever does detect the hard drive and partitions on the system with no problem

I tested Ubuntu as my main system for a week and liked it how ever I still need Windows so I reformatted back and later decided I wanted to duel boot them both when 
I encountered this problem of the Ubuntu Installer not being able to read the partitions on the disk and just seeing it as free space

> **Gamersfocus said:**
> Ubuntu 11.10
Should of mentioned which version at the start

---

### Post by dino99 on 2012-01-16
bios settings:
IDE as Compatible
SATA as AHCI

---

### Post by Gamersfocus on 2012-01-16
> **dino99 said:**
> bios settings:
IDE as Compatible
SATA as AHCI
Didn't work how ever

My Guess as to why Ubuntu is not detecting my partitions it's because of my uEFI board Windows has setup the disk and partitions using GPT (GUID Partition Table) I can install Windows or Ubuntu without any problems as a main system but Ubuntu doesn't detect the partitions so I am unable to setup a duel boot configuration since it just reads it all as free space so guess I am using Windows as my main system and waiting on Linux community to play catch up with the GPT technology

---

### Post by coffeecat on 2012-01-16
> **Gamersfocus said:**
> so guess I am using Windows as my main system and waiting on Linux community to play catch up with the GPT technology

Linux has been GPT and EFI capable since long before Windows, so there will be another reason why the installer is not seeing your partitions.

As a start, boot up the Ubuntu live CD and post the output of this terminal command:

```
sudo parted -l
```

Parted is the backend used by the installer, so this may not give a helpful output. What will be helpful is the output of gdisk which does not come as default on the live CD and would need to be installed. Before we go there, which version of Ubuntu do you have on your live CD?

---

### Post by Gamersfocus on 2012-01-17
> **coffeecat said:**
> Before we go there, which version of Ubuntu do you have on your live CD?
Ubuntu 11.10

---

### Post by coffeecat on 2012-01-17
Boot up into the 11.10 live session. You need to be connected to the internet because you will need to install gdisk to the live session. This will be lost when you power down, of course, but the output may give us something useful. The Universe repository needs to be enabled, so run these three terminal commands:

```
sudo apt-add-repository universe
sudo apt-get update
sudo apt-get install gdisk
```

If you have only one hard drive then this will probably be /dev/sda, but you need to check this. Run this command:

```
sudo fdisk -l
```

fdisk doesn't support GPT, but it will tell you the designation of the hard drive that has the GUID partition table. I'll assume that this is /dev/sda. Run this command (changing sda if necessary):

```
sudo gdisk -l /dev/sda
```

Post the output.

For completeness, run this following also and post the output. We need to see what parted is making of the drive.

```
sudo parted -l
```

---

### Post by Gamersfocus on 2012-01-17
I could get my duel boot setup working by using my spare drive which Ubuntu 11.10 is now installed to so I can just change the hard drive order in uEFI if I want to use it 

I am wondering if I can configure grub to add the windows boot loader which is installed on a separate drive so I don't have to change the boot order to switch between them the new grub confuses me since the old one used a simple text file to do the job now it seems to be overly complicated

---

### Post by coffeecat on 2012-01-18
> **Gamersfocus said:**
> I am wondering if I can configure grub to add the windows boot loader which is installed on a separate drive so I don't have to change the boot order to switch between them the new grub confuses me since the old one used a simple text file to do the job now it seems to be overly complicated

To be honest, I'm not sure, because we still haven't found out why the Ubuntu installer wasn't seeing your GUID partition table partitions. Which it should do.

First thing. Open a terminal in Ubuntu and run:

```
sudo update-grub
```

See if that adds a Windows entry to the grub menu. If not, go to this site:

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

Download and run the boot info script - the instructions are on that page - and post the contents of the RESULTS.txt file between [noparse]```
 and 
```[/noparse] tags for clarity. Also, install gdisk in Ubuntu (you won't have to renable the universe repository - it's already enabled in a permanent installation) and post the output of:

```
sudo gdisk -l /dev/sda
```

...substituting sdb or whatever it is for sda for your GUID drive.

---

### Post by Gamersfocus on 2012-01-18
Gparted does not read the partitions on the disk where I want ubuntu installed but it can read the partitions of the other disks it just sees the main disk as free space like the installer

Disk Utility can actually read the partitions on the disk but any attempt to modify the partitions results in data being corrupted on the disk and having to format and reinstall everything

Thought it might help to post information about other partition programs on the Live CD

---

### Post by Gamersfocus on 2012-01-18
> **coffeecat said:**
> Download and run the boot info script - the instructions are on that page - and post the contents of the RESULTS.txt file
```

                  Boot Info Script 0.60


============================= Boot Info Summary: ===============================

 => Windows is installed in the MBR of /dev/sda.
 => No boot loader is installed in the MBR of /dev/sdb.
 => Syslinux MBR (3.61-4.03) is installed in the MBR of /dev/sdc.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /Boot/BCD

sda2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files:        /Windows/System32/winload.exe

sda3: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   According to the info in the boot sector, sda5 starts 
                       at sector 2048.
    Operating System:  
    Boot files:        

sdb1: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   According to the info in the boot sector, sdb5 starts 
                       at sector 2048.
    Operating System:  
    Boot files:        

sdc1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  SYSLINUX 4.03 2010-10-22 ........>..sr>........._7...0...~.....~...f...M.f.f....f..0~....>E}.u......
    Boot sector info:   Syslinux looks at sector 15260360 of /dev/sdc1 for 
                       its second stage. SYSLINUX is installed in the  
                       directory. The integrity check of the ADV area failed. 
                       No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /boot/grub/grub.cfg /syslinux.cfg /ldlinux.sys

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *          2,048       206,847       204,800   7 NTFS / exFAT / HPFS
/dev/sda2             206,848    84,094,975    83,888,128   7 NTFS / exFAT / HPFS
/dev/sda3         136,527,872   976,771,071   840,243,200   f W95 Extended (LBA)
/dev/sda5         136,529,920   976,771,071   840,241,152   7 NTFS / exFAT / HPFS


GUID Partition Table detected, but does not seem to be used.

Partition    Start Sector    End Sector  # of Sectors System

Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1               2,048   976,771,071   976,769,024   f W95 Extended (LBA)
/dev/sdb5               4,096   976,771,071   976,766,976   7 NTFS / exFAT / HPFS


Drive: sdc _____________________________________________________________________

Disk /dev/sdc: 8006 MB, 8006926336 bytes
116 heads, 38 sectors/track, 3547 cylinders, total 15638528 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdc1    *          2,048    15,638,527    15,636,480   b W95 FAT32


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        34AECA86AECA405A                       ntfs       System Reserved
/dev/sda2        C40AD4E40AD4D510                       ntfs       Windows
/dev/sda5        22E460E3E460BB25                       ntfs       Media
/dev/sdb5        1E5AC1605AC13575                       ntfs       Backup
/dev/sdc1        083B-0F32                              vfat       WLAURITZEN

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sdc1        /cdrom                   vfat       (ro,noatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)


=========================== sdc1/boot/grub/grub.cfg: ===========================

--------------------------------------------------------------------------------

if loadfont /boot/grub/font.pf2 ; then
    set gfxmode=auto
    insmod efi_gop
    insmod efi_uga
    insmod gfxterm
    terminal_output gfxterm
fi

set menu_color_normal=white/black
set menu_color_highlight=black/light-gray

menuentry "Try Ubuntu without installing" {
    set gfxpayload=keep
    linux    /casper/vmlinuz  file=/cdrom/preseed/ubuntu.seed boot=casper quiet splash --
    initrd    /casper/initrd.lz
}
menuentry "Install Ubuntu" {
    set gfxpayload=keep
    linux    /casper/vmlinuz  file=/cdrom/preseed/ubuntu.seed boot=casper only-ubiquity quiet splash --
    initrd    /casper/initrd.lz
}
menuentry "Check disc for defects" {
    set gfxpayload=keep
    linux    /casper/vmlinuz  boot=casper integrity-check quiet splash --
    initrd    /casper/initrd.lz
}
--------------------------------------------------------------------------------

============================== sdc1/syslinux.cfg: ==============================

--------------------------------------------------------------------------------
default menu.c32
prompt 0
menu title UNetbootin
timeout 100

label unetbootindefault
menu label Default
kernel /ubnkern
append initrd=/ubninit file=/cdrom/preseed/ubuntu.seed boot=casper quiet splash --

label ubnentry0
menu label ^Help
kernel /ubnkern
append initrd=/ubninit 

label ubnentry1
menu label ^Try Ubuntu without installing
kernel /casper/vmlinuz
append initrd=/casper/initrd.lz file=/cdrom/preseed/ubuntu.seed boot=casper  quiet splash --

label ubnentry2
menu label ^Install Ubuntu
kernel /casper/vmlinuz
append initrd=/casper/initrd.lz file=/cdrom/preseed/ubuntu.seed boot=casper only-ubiquity  quiet splash --

label ubnentry3
menu label ^Check disc for defects
kernel /casper/vmlinuz
append initrd=/casper/initrd.lz boot=casper integrity-check  quiet splash --

label ubnentry4
menu label Test ^memory
kernel /install/mt86plus
append initrd=/ubninit 

label ubnentry5
menu label ^Boot from first hard disk
kernel /ubnkern
append initrd=/ubninit 

label ubnentry6
menu label Try Ubuntu without installing
kernel /casper/vmlinuz
append initrd=/casper/initrd.lz file=/cdrom/preseed/ubuntu.seed boot=casper quiet splash --

label ubnentry7
menu label Install Ubuntu
kernel /casper/vmlinuz
append initrd=/casper/initrd.lz file=/cdrom/preseed/ubuntu.seed boot=casper only-ubiquity quiet splash --

label ubnentry8
menu label Check disc for defects
kernel /casper/vmlinuz
append initrd=/casper/initrd.lz boot=casper integrity-check quiet splash --

--------------------------------------------------------------------------------

=================== sdc1: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

            ?? = ??             boot/grub/grub.cfg                             1

================= sdc1: Location of files loaded by Syslinux: ==================

           GiB - GB             File                                 Fragment(s)

            ?? = ??             ldlinux.sys                                    1
            ?? = ??             menu.c32                                       1
            ?? = ??             syslinux.cfg                                   1

============== sdc1: Version of COM32(R) files used by Syslinux: ===============

 menu.c32                           :  COM32R module (v4.xx)

=============================== StdErr Messages: ===============================

/home/ubuntu/Desktop/boot_info_script.sh: line 1579: [: 2.73495e+09: integer expression expected

```

---

### Post by coffeecat on 2012-01-19
@Gamersfocus, I'll just post quickly with a first impression because this needs thinking about. This is interesing from your RESULTS.txt:

> GUID Partition Table detected, but does not seem to be used.

And you do indeed seem to have a mbr-type partition layout because you have an extended partition (sda3).

As you say, you have a 26.8GB (= 25GiB) unallocated space between sda2 and sda3. There is no reason, in theory, why you should not be able to create a partition in that space.

Two things:

Please edit your post and replace the quote tags with code tags. You lose formatting with quote tags and in places that makes it near-impossible to read. Code tags will restore the formatting.

I'll pm other members to have a look as well. This is getting to be quite intriguing.

**EDIT**: Just to add. You said this earlier:

>  my uEFI board Windows has setup the disk and partitions using GPT (GUID Partition Table)

Some details of your hardware might be useful. Also - was Windows pre-installed, or did you install it from an installation DVD? What made you think that Windows had setup a GPT?

---

### Post by Gamersfocus on 2012-01-19
> **coffeecat said:**
> What made you think that Windows had setup a GPT?
I planed on installing Vista then installing 7 since it is an upgrade but Vista gave me an error message when I created the partition saying vaguely that it was GPT and install couldn't continue :confused:

I actually had to install 7 and then upgrade over it since my copy is an upgrade not a full install to get the system working 

Vista may have been confused over the partition type :confused: since when I setup Ubuntu as a host OS using GPT Windows 7 refused to install in the free space so it's probably correct to assume that it's still mbr
> **coffeecat said:**
> 
As you say, you have a 26.8GB (= 25GiB) unallocated space between sda2  and sda3. There is no reason, in theory, why you should not be able to  create a partition in that space.
Yes which is why I am confused as to why I can't just fire up the Ubuntu installation and select use free space and install but since it isn't seeing my partitions it would just wipe the entire disk

---

### Post by coffeecat on 2012-01-19
Just a few thoughts to be going on with as I have nothing definite to suggest just yet.

32-bit versions of Windows cannot cope with GUID partition tables. 64-bit versions of Windows can boot from GUID partition tables on EFI machines but not BIOS machines. My guess from what you say is that your version of Vista is 32-bit and Windows 7 64-bit. A GPT partition table keeps an MBR partition table on the first sector of the disk.

Theory: either the Windows 7 installer has done something odd, or the drive you were using previously had a GPT partition table and you've ended up with some sort of hybrid.

One of the people I pm'd suggested that stray GPT data may be confusing the Ubuntu installer and that fixparts can remove this stray data. Here's the fixparts link:

[http://www.rodsbooks.com/fixparts/](http://www.rodsbooks.com/fixparts/)

But I suggest doing nothing just yet. The other person I pm'd is in a different time-zone and is not online yet. I suggest we wait to see if they have any further suggestions, or can see something I've missed, and then get a consensus on how to proceed.

---

### Post by Gamersfocus on 2012-01-19
> **coffeecat said:**
> 
My guess from what you say is that your version of Vista is 32-bit and Windows 7 64-bit. A GPT partition table keeps an MBR partition table on the first sector of the disk.

Yes Vista is 32-bit how ever you are incorrect with 7 since it is actually 32-bit as well

Also please note my replys may be slow seeing as we are in different timezones (Australia) mine being (UTC +10:00) Canberra, Melbourne, Sydney

---

### Post by coffeecat on 2012-01-19
> **Gamersfocus said:**
> Yes Vista is 32-bit how ever you are incorrect with 7 since it is actually 32-bit as well

That's useful to know because Windows 7 32-bit can't cope with GPT at all. Which means that the unused GPT is of no use to Windows and can probably be safely removed leaving a standard MBR partition table.

I guess it's very late at night - if not the early hours - where you are at the moment. It's just gone 2 pm here. :) The second person I pm'd is in the USA so may not come on line for a few hours. I'm fairly sure that fixparts may be the way to go, but let's see what he says first.

---

### Post by oldfred on 2012-01-19
The stray gpt data is the backup partition table it creates. Windows and some other tools only delete the primary gpt table when converting back to MBR from gpt. Then some tools see the backup partition table and get confused on whether drive is gpt or MBR.

Your Windows install is MBR as if you are using UEFI the very first partition must be the efi partition and should be FAT32. Grub makes it FAT16 which is valid efi for removable devices, but is otherwise a bug for fixed hard drives.

As coffeecat suggests use fixparts to remove the stray gpt data.

elete Stray gpt data from MBR drives
[http://ubuntuforums.org/showthread.php?t=1705325](http://ubuntuforums.org/showthread.php?t=1705325) 
[http://www.rodsbooks.com/fixparts/](http://www.rodsbooks.com/fixparts/)
First backup partiton table, use your drive for sdX or sda, sdb etc.
sudo sfdisk -d /dev/sdX > parts_sdX.txt

---

### Post by Gamersfocus on 2012-01-19
I have figured out the reason as to why I can't setup a duel boot environment with Windows and Ubuntu the problem is that Ubuntu wants to use the disk as GPT (Following uEFI Standard) where as Windows 7 (32-Bit) wants to use MBR which means I was attempting (and failing) to create some sort of hybrid MBR/GPT duel boot setup so in theory there is no possible way to setup these 2 operating systems on the same disk

So to make this setup work I would have to use 2 disks one formated as GPT for Ubuntu other disk as MBR for Windows and switch between them under the uEFI settings since Grub2 wont boot into the second disk that's formatted as MBR after adding it into the menu (update-grub command) how ever this setup is getting a bit complicated while it isn't an issue to change the options in the uEFI settings I think I should just stick to a single operating system setup which will be Windows while Ubuntu is fantastic being a PC Gamer I still need Windows

---

### Post by oldfred on 2012-01-20
You definitely do not want a hybrid configuration. Windows 32bit does not work with gpt & UEFI only 64 bit.

But Ubuntu should just install to BIOS/MBR mode if it does not see the gpt data. I always prefer to partition in advance and use manual install to tell it which partitions to use for /, /home & swap.

I use gpt with BIOS, but then have to have a bios_grub 1MB partition for grub's core.img.  But that really only works if you never want Windows on the same drive.

---

### Post by coffeecat on 2012-01-20
@oldfred, I'll ask a question as I'm not sure of the answer myself and with the increasing use of EFI boards, this may come up more and more.

> **Gamersfocus said:**
> the problem is that Ubuntu wants to use the disk as GPT (Following uEFI Standard)

I was surprised by this statement, but don't dispute it. I can see that if you leave the installer to its own devices it will prefer to use GPT with uEFI. However...

> **oldfred said:**
> 
But Ubuntu should just install to BIOS/MBR mode if it does not see the gpt data. I always prefer to partition in advance and use manual install to tell it which partitions to use for /, /home & swap.

Simple question then, and to clarify what you're saying: with a uEFI machine, if you create an mbr partition table and set up your partitions in Gparted beforehand, can you force Ubuntu to install to a drive with an MBR partition table?

---

### Post by oldfred on 2012-01-20
Most new motherboards especially with the i3, i5, i7 series Intel chips seem to be UEFI but have a BIOS mode. It seems that they look for an efi partition and if not found use BIOS mode or just boot from MBR. Users have said there does not seem to be a setting in UEFI screens to choose mode to boot. So it should just boot like any older BIOS system.

Ubuntu's installer defaults to gpt on large drives (somewhere over 1TB). It somehow must know if UEFI enabled as it has created either the efi partition which must be first, or a bios_grub partition which is required for BIOS. Not sure how that works myself.

Because of some bugs in grub2 or the installer, almost everyone installing with UEFI has reported that partitioning in advance works where any of the auto installs seem to have issues. It may be that it cannot always find whether it is BIOS or UEFI? I also believe not all motherboards have UEFI set up exactly the same or follow the standard (which may not be totally clear). They only test with Windows, and then Ubuntu/grub has to figure out the idiosyncrasy of each UEFI implementation. 

There also was  in grub (not sure if fixed yet as I lost link) that it would not boot from very large / partitions or the default of just / & swap on drives somewhat over 500GB. The large root seems to sometimes have some files at the beginning & some near the end of the partition and grub then cannot find the files. Somewhat like the old BIOS issue of not booting from over 137GB. May also just be a BIOS setting but never found out for sure. I have had several users just shrink / to a much smaller partition and work and few could not solve it.

I now use gpt on all new drives but only have BIOS on my system.

---

### Post by Gamersfocus on 2012-01-20
> **coffeecat said:**
> 
Simple question then, and to clarify what you're saying: with a uEFI machine, if you create an mbr partition table and set up your partitions in Gparted beforehand, can you force Ubuntu to install to a drive with an MBR partition table?
That's the thing I can't force any kind of setup seeing as Ubuntu doesn't list the partitions on the drive in either Ubuntu Installer or Gparted it just sees it all as free space Disk Utility does actually see the partitions but any attempt to modify the drive will result in the disk becoming corrupted so I don't think it's possible to force an MBR setup with Ubuntu even if it would work and we already know you can't mix MBR/GPT

---

### Post by nipunshakya on 2012-01-21
Just a thing here...why don't u go for just 2 OSs rather than 3 OSs? won't that work out something with you??

---

### Post by coffeecat on 2012-01-21
> **Gamersfocus said:**
> That's the thing I can't force any kind of setup seeing as Ubuntu doesn't list the partitions on the drive in either Ubuntu Installer or Gparted it just sees it all as free space Disk Utility does actually see the partitions but any attempt to modify the drive will result in the disk becoming corrupted so I don't think it's possible to force an MBR setup with Ubuntu even if it would work and we already know you can't mix MBR/GPT

Just a guess here, but I was wondering if Ubuntu doesn't list the partitions because you've got some sort of hybrid partition table. If you were to completely remove all current partition table data and then use Gparted to create an MBR partition table, it *might* then be possible to create conventional MBR partitions and the installer might then be happy.

Regarding hybrid partition tables, here's an interesting page:

[http://www.rodsbooks.com/gdisk/hybrid.html](http://www.rodsbooks.com/gdisk/hybrid.html)

I'm also wondering if the Windows installation disk created the hybrid partition table when confronted with a GPT, seeing as it's a 32-bit version.

---

### Post by Gamersfocus on 2012-01-21
> **WinuxUser said:**
> Just a thing here...why don't u go for just 2  OSs rather than 3 OSs? won't that work out something with you??
I think your confused I only intended to run a duel boot setup Windows 7 & Ubuntu
> **coffeecat said:**
> Just a guess here, but I was wondering if  Ubuntu doesn't list the partitions because you've got some sort of  hybrid partition table. If you were to completely remove all current  partition table data and then use Gparted to create an MBR partition  table, it *might* then be possible to create conventional MBR partitions  and the installer might then be happy.

I'm also wondering if the Windows installation disk created the hybrid  partition table when confronted with a GPT, seeing as it's a 32-bit  version.
I actually have no idea if it's MBR or some hybrid of MBR/GPT since I am using 32-bit when I tried formatting the disk with Vista it thought it was GPT and refused to install so it's possible that it's some sort of hybrid since I had to use the Windows 7 disk as a retail disk then upgrade over it's self just to get Windows working which is fine since I own a retail copy of Vista
> **coffeecat said:**
> 
Regarding hybrid partition tables, here's an interesting page:
[http://www.rodsbooks.com/gdisk/hybrid.html](http://www.rodsbooks.com/gdisk/hybrid.html)

That is an interesting read and does explain allot about whats going on with Windows and Linux how ever I can't really run any further tests since I have decided to use Windows 7 as a single OS setup

---

### Post by Quackers on 2012-01-21
Did you run Fixparts as suggested by oldfred earlier?
If it's stray GPT data on your disc that is confusing gparted it could also be confusing the Ubuntu installer too. If you remove that stray data with Fixparts you may find that both systems will install ok on the mbr drive.

---

