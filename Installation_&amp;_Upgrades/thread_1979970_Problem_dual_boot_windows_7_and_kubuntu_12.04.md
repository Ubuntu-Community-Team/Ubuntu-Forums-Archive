---
title: "Problem dual boot windows 7 and kubuntu 12.04"
date: 2012-05-14
forum: Installation &amp; Upgrades
---

### Post by San32 on 2012-05-14
Hi,
I have a AMD64 computer with windows 7 on it.
I tried to install kubuntu 12.04 with a livecd kubuntu-12.04-desktop-amd64.iso.
After booting on the cd, i got a message that kubuntu was sucessfully installed.
I restarted my computer and i don't have a boot menu with my kubuntu.
My computer directly goes on windows7.
I tried EASYBCD to add kubuntu on my boot menu.
I have a boot menu with my kubuntu choice but it doesn't work.
I wonder if I have Grub2 installed.
I would like to know how can I know if I have Grub2 installed from windows ?
If I don't have Grub2 installed, can I download Grub2 from windows?
Thanks for your help!

---

### Post by wilee-nilee on 2012-05-14
Did you install Kubuntu from windows, a wubi install?

---

### Post by darkod on 2012-05-14
If you have more than one hdd, grub2 might have been installed on another hdd. Try booting from a different hdd.

---

### Post by Blasphemist on 2012-05-14
Assuming you'll answer the question about WUBI above that you didn't, where did you choose to install the bootloader during the installation of Kubuntu? And yes, do you have more than one drive?

We can likely help fix this manually but you could also use boot_repair to fix it. You'll learn more fixing it manually and you'll learn how to do the safest thing.

---

### Post by YannBuntu on 2012-05-14
Hello 
> **San32 said:**
> I wonder if I have Grub2 installed.
I would like to know how can I know if I have Grub2 installed from windows ?

Please indicate your [BootInfo URL]("http://ubuntuforums.org/showpost.php?p=11136267&postcount=1"), this will answer all these questions, and give us clues for helping you.

---

### Post by San32 on 2012-05-14
Hi,
Thanks to help me.
To install kubuntu, I booted on a livecd. I didn<t choose the wubi option (another icon with wubi was available on the website and I didn<t choose that icon). But there is an wubi option on my liveCd, I dont know if wubi was used to install my kubuntu, but I dont think so
I did the boot-info summary and my URL is : [http://paste.ubuntu.com/987652/](http://paste.ubuntu.com/987652/)
Thanks to help me,

---

### Post by San32 on 2012-05-14
Here my output of fdisk -l, I hope that help you help me:

sudo fdisk -l

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x30b99ef2

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1            2048    40962047    20480000   27  Hidden NTFS WinRE
/dev/sda2   *    40962048    41166847      102400    7  HPFS/NTFS/exFAT
/dev/sda3        41166848  1953523119   956178136    7  HPFS/NTFS/exFAT

Disk /dev/sdb: 4013 MB, 4013948928 bytes
5 heads, 32 sectors/track, 48998 cylinders, total 7839744 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *        8064     7839743     3915840    b  W95 FAT32

---

### Post by wilee-nilee on 2012-05-14
So I see no kubuntu anywhere in the script or the fdisk, in a full install or a wubi. 

Did you try and install it to a NTFS partition?

I see that the boot-repair sees the kubuntu on a usb though.

Your windows set up boots fine and runs right?

---

### Post by San32 on 2012-05-14
Hi,
I think I installed my kubuntu on NTFS partition,
I booted on the livecd of 12.04-amd64 and choose all default option.
On my boot menu, my windows option works well,
Do you have an advice ?
I have windows 7, and I want kubuntu too, 
How can I prepare my computer to be able to install for a second time kubuntu?
thanks

---

### Post by wilee-nilee on 2012-05-14
So you need an unallocated area to put a extended partition in. In the extended would go a logical ext4 for the Kubuntu and a swap.

So you will need to shrink probably best the sda3 partition on the script which looks like the  C partition in windows, using the looks like W7 disk manager, it is a virtual manager and can be used while Windows is running. Leave a unallocated space big enough for your Kubuntu install, and the swap.

So make that unallocated, by shrinking the C partition, then boot the Kubuntu disc and from here I think a person more familiar with Kubuntu will be helpful, I don't even know the name of the partitioner in Kubuntu to set up the partitions. so sit tight after the resize, you will get some help shortly I believe.

I always do custom installs as well so I'm not real familiar with the auto-installs offered in the install section asking where you want the Kubuntu put.

---

### Post by darkod on 2012-05-14
As mentioned, you first need to shrink the C: partition using win7 Disk Management. Shrink it for as much as you want to allocate to kubuntu. Do NOT create any partition from windows, leave that space as unallocated.

Restart win7 few times.

Then boot with the kubuntu cd and use what ever option you want, either manual install or the "install alongside windows" auto method.

That should be it.

---

### Post by takku on 2012-05-18
I just bought a HP Pavilion with Win7. I previously had some box with Windblows XP and the kubuntu 12.04 which I use mostly. I loaded the kubuntu iso for amd64, and burned the iso to CD.

I have installed the kubuntu now three times and the installer will run smoothly until the reboot. At first the machine just booted to Windows, with no option to boot to kubuntu. Then I ran the kubuntu CD from Windows and used some option to try to fix the boot. After this, the machine let me choose between Windows 7 and kubuntu (this was the windows boot menu).

And whenever I choose the kubuntu, the following message is shown:

"Completing the Ubuntu installation"

Then the machine tries to do something, but finally the error message is shown:

"unable to find a medium containing a live file system"

And no other error is shown. 

I have searched the net and some had this problem when (1) machine has disk storage option (don't recall the exact name for it) changed from IDE to ACPI. This did not help in my case.

Another issue had been reported with (2) some USB-device plugged in. No USB-devices plugged, and still the same error is produced. 

I suspected that the wireless card could do this (3), and opened the machine but it seems to be integrated. I even tried to unplug the usb-wired from the motherboard, but still got the same error.

The only way I was able to install was to load the wubi, but this was possible only when I had created another drive and then let the wubi do the magic. 

However, I will most definitely NOT use a machine with 30GB / partition and 1.7TB NTFS mounted to /host, so is there any way I could just install the kubuntu as before? :confused:

Edit: If I recall it correctly, the windows has /dev/sda1, /dev/sda3 and some third partition. I suspect that the sda1 is the boot for win, sda3 is the "C" and the third is HP specific patition. I have created, deleted and recreated the partition for kubuntu, and tried to install the kubuntu boot loader to "/dev/sda" and for the kubuntu-partition "/dev/sda6". I thought that installing the boot loader to kubuntu would work as the windows boot menu probably lets the kubuntu boot at the sda6. 

Any help would be highly appreciated..

---

### Post by darkod on 2012-05-18
Load kubuntu in live mode and run the boot info script from the link in my signature. Post the results as explained there. It will show many details that could help diagnose this.

---

### Post by takku on 2012-05-18
Ok, here goes:

kubuntu@kubuntu:/tmp$ sudo ./bootinfoscript 

Boot Info Script 0.61      [1 April 2012]


"gawk" could not be found, using "busybox awk" instead.
This may lead to unreliable results.

Identifying MBRs...
Computing Partition Table of /dev/sda...
Computing Partition Table of /dev/sdc...
Searching sda1 for information... 
Searching sda2 for information... 
Searching sda3 for information... 
Searching sda5 for information... 
Searching sda5/Wubi for information... 
Searching sda6 for information... 
Searching sda4 for information... 
Searching sdc1 for information... 

Finished. The results are in the file "RESULTS.txt"
located in "/tmp/".


kubuntu@kubuntu:/tmp$ cat RESULTS.txt 
                  Boot Info Script 0.61      [1 April 2012]


============================= Boot Info Summary: ===============================

 => Windows is installed in the MBR of /dev/sda.
 => Grub Legacy (v0.97) is installed in the MBR of /dev/sdc and looks on boot 
    drive #2 in partition #2 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /Boot/BCD

sda2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files:        /Windows/System32/winload.exe /wubildr /wubildr.mbr

sda3: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info: 

sda5: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  According to the info in the boot sector, sda5 starts 
                       at sector 2. But according to the info from fdisk, 
                       sda5 starts at sector 586057728.
    Operating System:  
    Boot files:        /ubuntu/winboot/wubildr /ubuntu/winboot/wubildr.mbr 
                       /ubuntu/disks/root.disk /ubuntu/disks/swap.disk

sda5/Wubi: _____________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Mounting failed:   mount: wrong fs type, bad option, bad superblock on /dev/loop1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so


sda6: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info: 

sda4: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /boot/bcd

sdc1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  -
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders, total 3907029168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *          2,048       206,847       204,800   7 NTFS / exFAT / HPFS
/dev/sda2             206,848   586,055,782   585,848,935   7 NTFS / exFAT / HPFS
/dev/sda3         586,057,726 3,875,364,863 3,289,307,138   5 Extended
/dev/sda5         586,057,728 3,862,978,559 3,276,920,832   7 NTFS / exFAT / HPFS
/dev/sda6       3,862,980,608 3,875,364,863    12,384,256  82 Linux swap / Solaris
/dev/sda4       3,875,364,864 3,907,026,943    31,662,080   7 NTFS / exFAT / HPFS


Drive: sdc _____________________________________________________________________

Disk /dev/sdc: 999 MB, 999817216 bytes
21 heads, 20 sectors/track, 4649 cylinders, total 1952768 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdc1                 128     1,952,767     1,952,640   6 FAT16


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        DC8A4B5A8A4B3076                       ntfs       SYSTEM
/dev/sda2        7060DF9B60DF667E                       ntfs       OS
/dev/sda4        82BE4E35BE4E2251                       ntfs       HP_RECOVERY
/dev/sda5        6A8C49C68C498D8F                       ntfs       New Volume
/dev/sda6        71ecc2d2-7e6d-41c3-9f97-98d58c283114   swap       
/dev/sdc1        E0FD-1813                              vfat       KINGSTON
/dev/sr0                                                iso9660    Kubuntu 12.04 LTS amd64

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sdc1        /media/KINGSTON          vfat       (rw,nosuid,nodev,uid=999,gid=999,shortname=mixed,dmask=0077,utf8=1,showexec,uhelper=udisks)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)


========= Devices which don't seem to have a corresponding hard drive: =========

sdb

---

### Post by darkod on 2012-05-18
As you can see, there is no kubuntu installation on any of the partitions. Only a linux swap partition.

There is a wubi install on sda5, but that's only wubi.

Do you have any important data on sda5? If you don't, you can boot windows, deinstall wubi from Programs, and then start the kubuntu installation booting with the cd (not from windows).

Select the manual option (Something Else), select the sda5 partition and choose to use it as ext4. Mount point /. Tick the format box.
Select sda6 to use as swap. There is no mount point for swap.

Leave the bootloader to be installed on /dev/sda.

That should install it correctly using all of sda5 for kubuntu. Note that formatting sda5 will destroy all data on it, so move the data you need first.

---

### Post by takku on 2012-05-18
Thanks for the help, very kind of you.

I did as you instructed. Now the circle has completed, and I am in the same situation where I was after the first installation: the computer boots directly to Windblows 7 and there is no boot menu available.

Last time I "fixed" this by running some "help booting windows" option from the live cd, which obviously messed the installation for good.

May I ask what I should do next..?

---

### Post by darkod on 2012-05-18
Because you did a new installation there are changes. Run the script again and post the new results.

---

### Post by takku on 2012-05-18
Now it seems that the filesystem contains kubuntu 12.04. The question is, how to enable either the windows boot menu from where kubuntu could be booted, or the good old grub where I could occasionally boot to the windows.._

And the output:


kubuntu@kubuntu:/tmp$ cat RESULTS.txt 
                  Boot Info Script 0.61      [1 April 2012]


============================= Boot Info Summary: ===============================

 => Windows is installed in the MBR of /dev/sda.
 => Grub Legacy (v0.97) is installed in the MBR of /dev/sdc and looks on boot 
    drive #2 in partition #2 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /Boot/BCD

sda2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files:        /Windows/System32/winload.exe

sda3: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info: 

sda5: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Ubuntu 12.04 LTS
    Boot files:        /boot/grub/grub.cfg /etc/fstab

sda6: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info: 

sda4: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /boot/bcd

sdc1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  -
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders, total 3907029168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *          2,048       206,847       204,800   7 NTFS / exFAT / HPFS
/dev/sda2             206,848   586,055,782   585,848,935   7 NTFS / exFAT / HPFS
/dev/sda3         586,057,726 3,875,364,863 3,289,307,138   5 Extended
/dev/sda5         586,057,728 3,862,979,602 3,276,921,875  83 Linux
/dev/sda6       3,862,980,608 3,875,364,863    12,384,256  82 Linux swap / Solaris
/dev/sda4       3,875,364,864 3,907,026,943    31,662,080   7 NTFS / exFAT / HPFS


Drive: sdc _____________________________________________________________________

Disk /dev/sdc: 999 MB, 999817216 bytes
21 heads, 20 sectors/track, 4649 cylinders, total 1952768 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdc1                 128     1,952,767     1,952,640   6 FAT16


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        DC8A4B5A8A4B3076                       ntfs       SYSTEM
/dev/sda2        7060DF9B60DF667E                       ntfs       OS
/dev/sda4        82BE4E35BE4E2251                       ntfs       HP_RECOVERY
/dev/sda5        bd06164d-4f31-44f4-bf65-5bd0ffac8f67   ext4       
/dev/sda6        71ecc2d2-7e6d-41c3-9f97-98d58c283114   swap       
/dev/sdc1        E0FD-1813                              vfat       KINGSTON
/dev/sr0                                                iso9660    Kubuntu 12.04 LTS amd64

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sdc1        /media/KINGSTON          vfat       (rw,nosuid,nodev,uid=999,gid=999,shortname=mixed,dmask=0077,utf8=1,showexec,uhelper=udisks)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)


=========================== sda5/boot/grub/grub.cfg: ===========================

--------------------------------------------------------------------------------
#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s $prefix/grubenv ]; then
  set have_grubenv=true
  load_env
fi
set default="0"
if [ "${prev_saved_entry}" ]; then
  set saved_entry="${prev_saved_entry}"
  save_env saved_entry
  set prev_saved_entry=
  save_env prev_saved_entry
  set boot_once=true
fi

function savedefault {
  if [ -z "${boot_once}" ]; then
    saved_entry="${chosen}"
    save_env saved_entry
  fi
}

function recordfail {
  set recordfail=1
  if [ -n "${have_grubenv}" ]; then if [ -z "${boot_once}" ]; then save_env recordfail; fi; fi
}

function load_video {
  insmod efi_gop
  insmod efi_uga
  insmod video_bochs
  insmod video_cirrus
}

insmod part_msdos
insmod ext2
set root='(hd0,msdos5)'
search --no-floppy --fs-uuid --set=root bd06164d-4f31-44f4-bf65-5bd0ffac8f67
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
  insmod part_msdos
  insmod ext2
  set root='(hd0,msdos5)'
  search --no-floppy --fs-uuid --set=root bd06164d-4f31-44f4-bf65-5bd0ffac8f67
  set locale_dir=($root)/boot/grub/locale
  set lang=en_US
  insmod gettext
fi
terminal_output gfxterm
if [ "${recordfail}" = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
if background_color 75,75,75; then
  clear
fi
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
function gfxmode {
        set gfxpayload="$1"
        if [ "$1" = "keep" ]; then
                set vt_handoff=vt.handoff=7
        else
                set vt_handoff=
        fi
}
if [ ${recordfail} != 1 ]; then
  if [ -e ${prefix}/gfxblacklist.txt ]; then
    if hwmatch ${prefix}/gfxblacklist.txt 3; then
      if [ ${match} = 0 ]; then
        set linux_gfx_mode=keep
      else
        set linux_gfx_mode=text
      fi
    else
      set linux_gfx_mode=text
    fi
  else
    set linux_gfx_mode=keep
  fi
else
  set linux_gfx_mode=text
fi
export linux_gfx_mode
if [ "$linux_gfx_mode" != "text" ]; then load_video; fi
menuentry 'Ubuntu, with Linux 3.2.0-23-generic' --class ubuntu --class gnu-linux --class gnu --class os {
        recordfail
        gfxmode $linux_gfx_mode
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='(hd0,msdos5)'
        search --no-floppy --fs-uuid --set=root bd06164d-4f31-44f4-bf65-5bd0ffac8f67
        linux   /boot/vmlinuz-3.2.0-23-generic root=UUID=bd06164d-4f31-44f4-bf65-5bd0ffac8f67 ro   quiet splash $vt_handoff
        initrd  /boot/initrd.img-3.2.0-23-generic
}
menuentry 'Ubuntu, with Linux 3.2.0-23-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
        recordfail
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='(hd0,msdos5)'
        search --no-floppy --fs-uuid --set=root bd06164d-4f31-44f4-bf65-5bd0ffac8f67
        echo    'Loading Linux 3.2.0-23-generic ...'
        linux   /boot/vmlinuz-3.2.0-23-generic root=UUID=bd06164d-4f31-44f4-bf65-5bd0ffac8f67 ro recovery nomodeset 
        echo    'Loading initial ramdisk ...'
        initrd  /boot/initrd.img-3.2.0-23-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
        insmod part_msdos
        insmod ext2
        set root='(hd0,msdos5)'
        search --no-floppy --fs-uuid --set=root bd06164d-4f31-44f4-bf65-5bd0ffac8f67
        linux16 /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
        insmod part_msdos
        insmod ext2
        set root='(hd0,msdos5)'
        search --no-floppy --fs-uuid --set=root bd06164d-4f31-44f4-bf65-5bd0ffac8f67
        linux16 /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" --class windows --class os {
        insmod part_msdos
        insmod ntfs
        set root='(hd0,msdos1)'
        search --no-floppy --fs-uuid --set=root DC8A4B5A8A4B3076
        chainloader +1
}
menuentry "Windows Recovery Environment (loader) (on /dev/sda4)" --class windows --class os {
        insmod part_msdos
        insmod ntfs
        set root='(hd0,msdos4)'
        search --no-floppy --fs-uuid --set=root 82BE4E35BE4E2251
        drivemap -s (hd0) ${root}
        chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

### BEGIN /etc/grub.d/41_custom ###
if [ -f  $prefix/custom.cfg ]; then
  source $prefix/custom.cfg;
fi
### END /etc/grub.d/41_custom ###
--------------------------------------------------------------------------------

=============================== sda5/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda5 during installation
UUID=bd06164d-4f31-44f4-bf65-5bd0ffac8f67 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=71ecc2d2-7e6d-41c3-9f97-98d58c283114 none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sda5: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

               =                boot/grub/grub.cfg                             1
               =                boot/initrd.img-3.2.0-23-generic               2
               =                boot/vmlinuz-3.2.0-23-generic                  1
               =                initrd.img                                     2
               =                vmlinuz                                        1

========= Devices which don't seem to have a corresponding hard drive: =========

sdb 

=============================== StdErr Messages: ===============================

awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in

---

### Post by darkod on 2012-05-18
Out of what ever reason, grub2 didn't install fully. From live mode enter your installation with chroot and install it:
```
sudo mount /dev/sda5 /mnt
sudo mount --bind /proc /mnt/proc
sudo mount --bind /dev /mnt/dev
sudo mount --bind /sys /mnt/sys
sudo chroot /mnt
```

Just in case remove grub2 and reinstall again recreating the config files:
```
apt-get remove --purge grub-pc grub-common
apt-get install grub-pc
grub-mkconfig
update-grub
grub-install /dev/sda
```

It should now be installed. Exit the chroot and unmount everything:
```
exit
sudo umount /mnt/sys
sudo umount /mnt/dev
sudo umount /mnt/proc
sudo umount /mnt
```

Restart and if the /dev/sda disk is your first option to boot from you should see the grub2 boot menu.

---

### Post by takku on 2012-05-18
WONDERFUL!

Now the system boots like a charm! No more windows boot menu, default boot goes to kubuntu. Hooray to the boot-guru darkod ! :KS

 Even though I'm not quite newbie with linux, I would have never (TM) solved this one without your help! THANK YOU!

---

### Post by rirùta on 2012-07-02
I have mainly the same problem but the comments I found in this post didn't really help me. I have freshly kubuntu12.04 in a separate partition of my hard drive next to windows7. After installation, I got a message that kubuntu was successfully installed. But after restarting, instead of the grub menu, my system booted automatically on windows7. Now I can't access my kubuntu partition :( I seeked in many forums but I found no solution to my problem :(

---

### Post by YannBuntu on 2012-07-02
**@rirùta:** welcome among us. Please open a new thread, and indicate your [BootInfo URL]("http://ubuntuforums.org/showpost.php?p=11136267&postcount=1").

---

### Post by rirùta on 2012-07-02
thank you :) check here [http://ubuntuforums.org/showthread.php?p=12069435#post1206943](http://ubuntuforums.org/showthread.php?p=12069435#post1206943)

---

