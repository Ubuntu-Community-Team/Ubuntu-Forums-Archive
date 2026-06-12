---
title: "No other operating systems detected"
date: 2013-09-05
forum: Installation &amp; Upgrades
---

### Post by Julius_Sugioka on 2013-09-05
I bought a refurbished Acer Aspire 5 laptop with windows 5 installed on it, and I tried installing Ubuntu 13.04 amd64 by booting from my pendrive alongside windows 8. When I got to the third screen, it told me that there was no other operating system detected, and didn't give me the option of installing Ubuntu alongside windows. I didn't understand the other posts about how to fix this problem.

Please help!

---

### Post by grahammechanical on 2013-09-05
You need to provide more information. Please download and run bootinfoscript

[http://sourceforge.net/projects/boot info script/]("http://sourceforge.net/projects/bootinfoscript/")

It will collect useful information and put it in a file called RESULTS.txt. Then come back to this post and paste the contents of RESULTS.txt between code tags. You can do that by selecting the text you have put into the post and then clicking on the bubble/speech icon.

Then we can see something about your system that might help us understand what is causing this.

Regards.

---

### Post by Julius_Sugioka on 2013-09-05
Thanks for the reply, here's what I got:

>                   Boot Info Script 0.61      [1 April 2012]


============================= Boot Info Summary: ===============================

 => No boot loader is installed in the MBR of /dev/sda.
 => Syslinux MBR (4.04 and higher) is installed in the MBR of /dev/sdb.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sda2: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  Windows 7: FAT32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /efi/Boot/bootx64.efi

sda3: __________________________________________________________________________

    File system:       
    Boot sector type:  -
    Boot sector info: 
    Mounting failed:   mount: unknown filesystem type ''

sda4: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /Windows/System32/winload.exe

sda5: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sdb1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  SYSLINUX 4.06 2012-10-23
    Boot sector info:  Syslinux looks at sector 1375738 of /dev/sdb1 for its 
                       second stage. SYSLINUX is installed in the  directory. 
                       The integrity check of the ADV area failed. No errors 
                       found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /boot/grub/grub.cfg /syslinux/syslinux.cfg 
                       /efi/BOOT/grubx64.efi /ldlinux.sys

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
256 heads, 63 sectors/track, 60563 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1                   1 4,294,967,295 4,294,967,295  ee GPT

/dev/sda1 ends after the last sector of /dev/sda

GUID Partition Table detected.

Partition    Start Sector    End Sector  # of Sectors System
/dev/sda1           2,048       821,247       819,200 Windows Recovery Environment (Windows)
/dev/sda2         821,248     1,435,647       614,400 EFI System partition
/dev/sda3       1,435,648     1,697,791       262,144 Microsoft Reserved Partition (Windows)
/dev/sda4       1,697,792   943,720,447   942,022,656 Data partition (Windows/Linux)
/dev/sda5     943,720,448   976,773,119    33,052,672 Windows Recovery Environment (Windows)

Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 4007 MB, 4007264256 bytes
28 heads, 52 sectors/track, 5375 cylinders, total 7826688 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1    *          2,048     7,825,407     7,823,360   c W95 FAT32 (LBA)


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        2E24AF3324AEFD49                       ntfs       Recovery
/dev/sda2        E6B1-5517                              vfat       ESP
/dev/sda4        0298DD6C98DD5EAB                       ntfs       Acer
/dev/sda5        5C4EB41A4EB3EAC2                       ntfs       Push Button Reset
/dev/sdb1        16DD-303B                              vfat       PENDRIVE

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sdb1        /cdrom                   vfat       (ro,noatime,fmask=0022,dmask=0022,codepage=437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)


=========================== sdb1/boot/grub/grub.cfg: ===========================

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
    linux    /casper/vmlinuz.efi  file=/cdrom/preseed/ubuntu.seed boot=casper quiet splash --
    initrd    /casper/initrd.lz
}
menuentry "Install Ubuntu" {
    set gfxpayload=keep
    linux    /casper/vmlinuz.efi  file=/cdrom/preseed/ubuntu.seed boot=casper only-ubiquity quiet splash --
    initrd    /casper/initrd.lz
}
menuentry "OEM install (for manufacturers)" {
    set gfxpayload=keep
    linux    /casper/vmlinuz.efi  file=/cdrom/preseed/ubuntu.seed boot=casper only-ubiquity quiet splash oem-config/enable=true --
    initrd    /casper/initrd.lz
}
menuentry "Check disc for defects" {
    set gfxpayload=keep
    linux    /casper/vmlinuz.efi  boot=casper integrity-check quiet splash --
    initrd    /casper/initrd.lz
}
--------------------------------------------------------------------------------

========================= sdb1/syslinux/syslinux.cfg: ==========================

--------------------------------------------------------------------------------
# D-I config version 2.0
include menu.cfg
default vesamenu.c32
prompt 0
timeout 0
ui gfxboot bootlogo
--------------------------------------------------------------------------------

=================== sdb1: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

            ?? = ??             boot/grub/grub.cfg                             1

================= sdb1: Location of files loaded by Syslinux: ==================

           GiB - GB             File                                 Fragment(s)

            ?? = ??             ldlinux.sys                                    1
            ?? = ??             syslinux/chain.c32                             1
            ?? = ??             syslinux/gfxboot.c32                           1
            ?? = ??             syslinux/menu.c32                              1
            ?? = ??             syslinux/syslinux.cfg                          1
            ?? = ??             syslinux/vesamenu.c32                          2

============== sdb1: Version of COM32(R) files used by Syslinux: ===============

 syslinux/chain.c32                 :  COM32R module (v4.xx)
 syslinux/gfxboot.c32               :  COM32R module (v4.xx)
 syslinux/menu.c32                  :  COM32R module (v4.xx)
 syslinux/vesamenu.c32              :  COM32R module (v4.xx)

=============================== StdErr Messages: ===============================

/home/ubuntu/Desktop/bootinfoscript: line 1646: [: 2.73495e+09: integer expression expected
  No volume groups found


---

### Post by oldfred on 2013-09-05
You have an UEFI system.
But script did not see the Windows boot file, just BOOTX64.EFI. this one not shown, not sure if script or your system?
      /boot/efi/EFI/Microsoft/Boot/bootmgfw.efi

Does system boot ok?
Also if you have hibernation on Ubuntu installer cannot see the Windows partition as hibernation flag or chkdsk flag will prevent Linux NTFS driver from opening the partition.
And Windows 8 is always hibernated. You need to turn off fast boot.

      
 Fast Startup off/hibernation
[http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html](http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html)

 [http://ubuntuforums.org/showthread.php?t=1953674](http://ubuntuforums.org/showthread.php?t=1953674)
It defaults shutdown to a hybrid hibernation/off state for fast boot 
[http://www.kapilarya.com/how-to-enable-disable-fast-start-up-in-windows-8](http://www.kapilarya.com/how-to-enable-disable-fast-start-up-in-windows-8)

Best to also turn off secure boot, but have UEFI boot on, not CSM/BIOS boot.
Use Windows disk tools to shrink the Windows NTFS partition and reboot so it can run chkdsk and make repairs for its new size.
Lots more info in link in my signature. But this is most important of those.
      
 Shows install with screen shots.
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)
Also shows Windows 8 screens
[http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-uefi-supported-windows-8-system](http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-uefi-supported-windows-8-system)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot. required for UEFI & grub bug fixes
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by Julius_Sugioka on 2013-09-05
Thank you for the reply, sorry I forgot to mention that jI turned off secure boot in order to boot off the live USB, so my windows and the live USB boot fine. I've turned off fast boot and shrunk the NTFS partition by 60 gigabytes. The ubuntu installer unfortunately still does not see the windows OS...

---

### Post by oldfred on 2013-09-06
Is this an UltraBook with Intel SRT that uses RAID. Standard desktop installer does not have RAID drivers. 
See info on Ultrabook in link in my signature if that is the case.

Have you rebooted Windows after resize as it has to run chkdsk on resize. And both hibernation flag (fast boot) or chkdsk also prevent Linux NTFS driver from seeing NTFS partitions.

---

### Post by Julius_Sugioka on 2013-09-06
I'm not sure whether it uses raid or has intel SRT, my computer is an Acer Aspire V5 and my specs are here: [http://us.acer.com/ac/en/US/content/model-datasheet/NX.M3AAA.002](http://us.acer.com/ac/en/US/content/model-datasheet/NX.M3AAA.002)

I'm not sure how to run chkdsk on resize... How should I go about doing that?

---

### Post by oldfred on 2013-09-06
Windows will automatically run chkdsk if you resize using Windows disk tools and then reboot. Otherwise you have to go into Windows repair console. Chkdsk is run before booting or from a Wincdows repair flash drive which it is a good idea to have.

Other Acer:
 Acer Aspire S7 can't install ubuntu - UltraBook erased RAID meta-data
[http://ubuntuforums.org/showthread.php?t=2121187](http://ubuntuforums.org/showthread.php?t=2121187)
Acer V5-571P-6815 secure boot off worked Shows Diskpart
[http://ubuntuforums.org/showthread.php?t=2081311](http://ubuntuforums.org/showthread.php?t=2081311)


 Windows 8 UEFI repair USB flash drive must be FAT32
[http://www.eightforums.com/tutorials/2855-system-repair-disc-create-windows-8-a.html](http://www.eightforums.com/tutorials/2855-system-repair-disc-create-windows-8-a.html)
[http://social.msdn.microsoft.com/Forums/en-US/samsungpcgeneral/thread/e7ed293e-b565-44ee-a536-166dddf32205/](http://social.msdn.microsoft.com/Forums/en-US/samsungpcgeneral/thread/e7ed293e-b565-44ee-a536-166dddf32205/)
[http://www.ghacks.net/2012/11/01/how-to-create-a-windows-8-system-repair-disc/](http://www.ghacks.net/2012/11/01/how-to-create-a-windows-8-system-repair-disc/)

---

### Post by Julius_Sugioka on 2013-09-07
Chkdsk has run and when I tried installing ubuntu again with the live usb it still did not recognise windows 8 but it did recognise the partition map. My new artition map is as follows:

[ATTACH=CONFIG]246064[/ATTACH]

Is it realistic to just install ubuntu using the last option on the install?

---

### Post by oldfred on 2013-09-07
I prefer to use manual install or Something Else as the auto options are just that. It may not choose what you want. But then you do have to understand partitions and have an idea of what partitions you may want and a new user is fine with just the defaults.

I normally suggest both a shared NTFS data partition so you do not write into the Windows system partition and maybe a separate /home. If most data is in data partition(s) then the /home is less important. I use two data partitions and still have my NTFS from when I still used XP, but have not yet moved that data to Linux formatted data partition where all new data now goes. I prefer smaller system partitions and large data partitions for both Windows & Linux. I make a 25GB / (root) but only use 9GB with /home inside it. And my /home is 2GB because of the Windows version of Picasa. Or you may only need 15 to 20GB for / (root).

---

### Post by Julius_Sugioka on 2013-09-09
Thank you for all of your help, I'll install ubuntu manually partitioning the hard drive.

---

