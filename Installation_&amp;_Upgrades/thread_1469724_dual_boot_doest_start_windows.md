---
title: "dual boot doest start windows"
date: 2010-05-02
forum: Installation &amp; Upgrades
---

### Post by vinod_home on 2010-05-02
Hi All,


All this started when I decided to upgrade Ubuntu 9.10 to 10.04. Now Windows XP gives me a blank screen and doesnt run. I have tried a bunch of things but didnt help. I also clean installed Ubuntu 9.10 into a new partition and removed the deleted the other partition. 

```

sudo fdisk -l
   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       78331   629193726    7  HPFS/NTFS
/dev/sda2           78332       91201   103378275    5  Extended
/dev/sda5           78332       84577    50170932   83  Linux
/dev/sda6           84578       84849     2184808+  82  Linux swap / Solaris

```os-prober has this added for windows to grub.cfg

```

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Professional (on /dev/sda1)" {
    insmod ntfs
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set c2b8a534b8a5283d
    drivemap -s (hd0) ${root}
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

```Current Status:
1. Windows XP on sda1 wont start from grub2 (version 1.97-beta4). 
2. I can access the windows partition from Linux and see all the files.
3. When I boot using windows cd, and go to recovery mode it doesnt list Windows XP. 
4. From windows Recovery mode when I try "diskpart" it says no partitions in c drive.

What can I do to get my Windows XP work.

TIA

---

### Post by mtdave on 2010-05-02
I have exactly the same problem. Hope you get an answer!

---

### Post by wilee-nilee on 2010-05-02
post this boot script.
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

---

### Post by vinod_home on 2010-05-02
here is the results.txt file that it generated.

---

### Post by vinod_home on 2010-05-02
I do see sda1 in the Results.txt showing the following.
Boot sector info:  Grub 2 is installed in the boot sector of sda1 and 
                       looks at sector 1363381360 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location. No errors found in the Boot Parameter Block.

What does that mean, Why is it looking for core.img file. I read somewhere that its because grub was installed on this partition (which I did when I had issues). I used the testdrive approach and it said the BootSector was "OK". But it still doesnt help. What else can I do to fix this. 

TIA

---

### Post by akeem_da_dream on 2010-05-02
> **vinod_home said:**
> I do see sda1 in the Results.txt showing the following.
Boot sector info:  Grub 2 is installed in the boot sector of sda1 and 
                       looks at sector 1363381360 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location. No errors found in the Boot Parameter Block.

What does that mean, Why is it looking for core.img file. I read somewhere that its because grub was installed on this partition (which I did when I had issues). I used the testdrive approach and it said the BootSector was "OK". But it still doesnt help. What else can I do to fix this. 

TIA
i have a very similar message. someone plz help since i need to use windows to upgrade my phone and my zune.

---

### Post by vinod_home on 2010-05-02
I have tried testdrive approach and it didnt help me, hopefully it helps others.

When I select windows, I get a blank screen and my motherboard POST code is 6F. When I googled it, it has something to do with the floppy-drive. I thought that was what grub2 fixed. I went through my bios and I dont have anything for floppy drive and I dont have a floppy drive on my machine. 

Any help on this would be great.

TIA

---

### Post by frantid on 2010-05-02
you have to run fixboot from the xp recovery console.

You don't have to run fixmbr.

or...

run testdisk and "rebuildbs"  -- far easiest, just make sure you highlight the right partition.

[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)

---

### Post by oldfred on 2010-05-02
This has instructions on using testdisk to repair the install of grub to the boot sector for windows.
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector)

You can also use windows cd/dvd to repair with fixboot command. Instructions are slightly different for XP and vista/7 but you want to get into the repair console and go to command line.

XP:
FIXBOOT  C:

Vista/7
BootRec.exe /FixBoot  #updates PBR partition boot

[http://support.microsoft.com/kb/927392](http://support.microsoft.com/kb/927392)
[http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html](http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html)
[http://windows7ultimate.windowsreinstall.com/repairwin7startup/indexthumbs.ht](http://windows7ultimate.windowsreinstall.com/repairwin7startup/indexthumbs.ht)

---

### Post by akeem_da_dream on 2010-05-02
Here's how I solved my problem. step by step

[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector)

---

### Post by vinod_home on 2010-05-03
I did try TestDisk and it says the Boot sector and Backup boot sector are 'OK'. So that didnt help.

I think I tried "fixboot" from the windows recovery console. It said I need to select the windows first. When  I go to Recovery console it doesnt ask me to select windows it just goes to the C: prompt.  When I have gone to the recovery console in the past, you always get 1) Windows XP Professional and it says select which windows system you want. But I dont get that now.

---

### Post by mtdave on 2010-05-03
Whew, got my dual boot fixed. I downloaded a XP Home sp3 CD iso from my MSDN account and booted to it and ran the Restore. I got to the commandline and ran:
 
C:\Windows>fixboot c:
 
Then I rebooted. Got the Grub menu and arrowed down to Windows XP and it loaded.
 
Prior to this i had reinstalled Grub2 at /dev/sda and run update-grub. I had Windows XP in the Grub menu but it would not boot.
 
I'm a much happier boy now! Too bad I spent a large chunk of the weekend fooling with this. I shouldn't have been so hasty to upgrade from 9.10 to 10.04. Next time I won't be.#-o

---

### Post by vinod_home on 2010-05-03
@mtdave: same thoughts going through my head 

Thanks for the info, I will try this approach and hope that fixes it. 

When you went to the restore option, did it ask you select which windows environment you want. Also did it go to C:\> or C:\Windows>

---

### Post by vinod_home on 2010-05-07
Today I tried to use fixboot from my windows xp cd, when that didnt work, i tried to use bootsect.exe /nt52 from windows 7 rc cd. 

Now I am in a bigger mess. I think the partition table is messed up. When I start my computer I get a J<heart>J<heart> and thats it. 

I booted with ubuntu 9.10 live cd and when i mount my 750gb, all I see is one file with a some funny name with all kinda characters. when i run sudo fdisk from a terminal I get the following. Any help is appreciated.  The actual partition is in the first page of this post.

Disk /dev/sda: 750.2 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x69737369

This doesn't look like a partition table
Probably you selected the wrong device.

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   ?      116388      126889    84344761   69  Unknown
Partition 1 does not end on cylinder boundary.
/dev/sda2   ?      105915      222310   934940732+  73  Unknown
Partition 2 does not end on cylinder boundary.
/dev/sda3   ?           1           1           0   74  Unknown
Partition 3 does not end on cylinder boundary.
/dev/sda4               1      213826  1717556736    0  Empty
Partition 4 does not end on cylinder boundary.

Partition table entries are not in disk order

---

### Post by oldfred on 2010-05-07
This should only change MBR:

When used with /nt52 option, the Master Boot Record (MBR)
is *compatible* with operating systems older (XP) than Windows Vista.

When used with the /nt60 option, the Master Boot Record (MBR) is
*compatible* with Windows Vista, Windows Server 2008 or later


I would try testdisk:

repairs including testdisk info & link to testdisk, testdisk is in repository and on most repairCDs
[http://members.iinet.net.au/~herman546/p21.html](http://members.iinet.net.au/~herman546/p21.html)
[http://www.psychocats.net/ubuntucat/recoverdeletedfiles/](http://www.psychocats.net/ubuntucat/recoverdeletedfiles/)
download TestDisk [http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)

Instructions
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)

---

### Post by joao82 on 2010-05-08
> **oldfred said:**
> This has instructions on using testdisk to repair the install of grub to the boot sector for windows.
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector)

You can also use windows cd/dvd to repair with fixboot command. Instructions are slightly different for XP and vista/7 but you want to get into the repair console and go to command line.

XP:
FIXBOOT  C:

Vista/7
BootRec.exe /FixBoot  #updates PBR partition boot

[http://support.microsoft.com/kb/927392](http://support.microsoft.com/kb/927392)
[http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html](http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html)
[http://windows7ultimate.windowsreinstall.com/repairwin7startup/indexthumbs.ht](http://windows7ultimate.windowsreinstall.com/repairwin7startup/indexthumbs.ht)

Thank you, this was instant and helpful. It saved my windows7.

---

### Post by vinod_home on 2010-05-08
Thank you, I used testdisk and it built the partition table back. I am backing up some data to an external drive before I try anything. 

I see /dev/sda2 which looks like a total of sda5, 6, 7, 8 after using testdisk. Is that ok or do i need to fix anything.
 
Disk /dev/sda: 750.2 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x69737369

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       78331   629193726    7  HPFS/NTFS
/dev/sda2           78332       91201   103378243+   f  W95 Ext'd (LBA)
/dev/sda5           78332       84577    50170932   83  Linux
/dev/sda6           84578       84849     2184808+  82  Linux swap / Solaris
/dev/sda7           84850       90935    48885763+  83  Linux
/dev/sda8           90936       91201     2136613+  82  Linux swap / Solaris


I dont get grub anymore, so will try to reinstall grub2 on /dev/sda and see how that goes.

TIA

---

### Post by vinod_home on 2010-05-08
now I think I am in a loop. 

I fixed my partitions using testdisk, rebooted into the live-cd. fixed my grub. restarted the computer. I got grub, logged into ubuntu and update-grub.  So all of linux is running fine. Now I put my windows cd and run fixboot c:, when i reboot, it ends up with Y<funnychar>Y<funnychar). So i put my ubuntu live-cd and reboot into that. when i run fdisk -l, i get what i had 4 posts ago. 

So now I go get testdisk, run it and fix the partition table. Restart it with the live-cd, reinstall grub to sda, restart go into linux. I still cannot boot into Windows XP. 

Any ideas on how to get this fixed. When i look at the disk utility within ubuntu, i see fat12 along with NTFS (attaching pic). dont know what that means. 
XP - sda1
Linux - sda7 (10.04)
Linux - sda5 (9.10) - i will be removing this after everything else is fixed.
[ATTACH]156034[/ATTACH]

TIA

---

### Post by oldfred on 2010-05-08
Rerun the bootinfo script. Post it here with code tags. As you paste it click on the # - right side of the edit panel above to put it in a scroll box.

It should show if the windows partition boot sector is ok or not.

---

### Post by vinod_home on 2010-05-08
Reran the bootscript. I have also removed other linux partition that I had. So now I only have one Windows XP partition (sda1) and Ubuntu 10.04 (sda5). 

```

                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #5 for /boot/grub.
 => No boot loader is installed in the MBR of /dev/sdd

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdd1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat16
    Boot sector info:  According to the info in the boot sector, sdd1 starts 
                       at sector 1. But according to the info from fdisk, 
                       sdd1 starts at sector 135. According to the info in 
                       the boot sector, sdd1 has 0 sectors.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 750.2 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders, total 1465149168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63 1,258,387,514 1,258,387,452   7 HPFS/NTFS
/dev/sda2       1,258,387,578 1,465,144,064   206,756,487   f W95 Ext d (LBA)
/dev/sda5       1,363,099,248 1,460,870,774    97,771,527  83 Linux
/dev/sda6       1,460,870,838 1,465,144,064     4,273,227  82 Linux swap / Solaris


Drive: sdd ___________________ _____________________________________________________

Disk /dev/sdd: 1973 MB, 1973420032 bytes
60 heads, 59 sectors/track, 1088 cylinders, total 3854336 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdd1                 135     3,854,335     3,854,201   6 FAT16


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        C2B8A534B8A5283D                       ntfs                                     
/dev/sda2: PTTYPE="dos" 
/dev/sda5        7b473825-ba23-4852-a13f-6d91f3a009ca   ext4                                     
/dev/sda6        949aa2da-e87e-493e-b866-ee8b35fd5138   swap                                     
/dev/sda                                                vfat                                     
/dev/sdd1                                               vfat                                     
/dev/sdd: PTTYPE="dos" 
error: /dev/sdb: No medium found
error: /dev/sdc: No medium found
error: /dev/sde: No medium found

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda5        /                        ext4       (rw,errors=remount-ro)
/dev/sdd1        /media/disk              vfat       (rw,nosuid,nodev,uhelper=udisks,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,flush)
/dev/sr0         /media/cdrom0            iso9660    (ro,nosuid,nodev,utf8,user=vappukut)


================================ sda1/boot.ini: ================================

[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /FASTDETECT /NOEXECUTE=OPTIN 

=========================== sda5/boot/grub/grub.cfg: ===========================

#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by /usr/sbin/grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s $prefix/grubenv ]; then
  load_env
fi
set default="0"
if [ ${prev_saved_entry} ]; then
  set saved_entry=${prev_saved_entry}
  save_env saved_entry
  set prev_saved_entry=
  save_env prev_saved_entry
  set boot_once=true
fi

function savedefault {
  if [ -z ${boot_once} ]; then
    saved_entry=${chosen}
    save_env saved_entry
  fi
}

function recordfail {
  set recordfail=1
  if [ -n ${have_grubenv} ]; then if [ -z ${boot_once} ]; then save_env recordfail; fi; fi
}
insmod ext2
set root='(hd0,5)'
search --no-floppy --fs-uuid --set 7b473825-ba23-4852-a13f-6d91f3a009ca
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  insmod gfxterm
  insmod vbe
  if terminal_output gfxterm ; then true ; else
    # For backward compatibility with versions of terminal.mod that don't
    # understand terminal_output
    terminal gfxterm
  fi
fi
insmod ext2
set root='(hd0,5)'
search --no-floppy --fs-uuid --set 7b473825-ba23-4852-a13f-6d91f3a009ca
set locale_dir=($root)/boot/grub/locale
set lang=en
insmod gettext
if [ ${recordfail} = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
insmod ext2
set root='(hd0,5)'
search --no-floppy --fs-uuid --set 7b473825-ba23-4852-a13f-6d91f3a009ca
insmod tga
if background_image /usr/share/images/grub/UbuntuSwirls.tga ; then
  set color_normal=black/black
  set color_highlight=magenta/black
else
  set menu_color_normal=white/black
  set menu_color_highlight=black/light-gray
fi
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry 'Ubuntu, with Linux 2.6.32-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 7b473825-ba23-4852-a13f-6d91f3a009ca
    linux    /boot/vmlinuz-2.6.32-22-generic root=UUID=7b473825-ba23-4852-a13f-6d91f3a009ca ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 7b473825-ba23-4852-a13f-6d91f3a009ca
    echo    'Loading Linux 2.6.32-22-generic ...'
    linux    /boot/vmlinuz-2.6.32-22-generic root=UUID=7b473825-ba23-4852-a13f-6d91f3a009ca ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 7b473825-ba23-4852-a13f-6d91f3a009ca
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=7b473825-ba23-4852-a13f-6d91f3a009ca ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 7b473825-ba23-4852-a13f-6d91f3a009ca
    echo    'Loading Linux 2.6.32-21-generic ...'
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=7b473825-ba23-4852-a13f-6d91f3a009ca ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 7b473825-ba23-4852-a13f-6d91f3a009ca
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 7b473825-ba23-4852-a13f-6d91f3a009ca
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Professional (on /dev/sda1)" {
    insmod ntfs
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set c2b8a534b8a5283d
    drivemap -s (hd0) ${root}
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sda5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda5 during installation
UUID=7b473825-ba23-4852-a13f-6d91f3a009ca /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=949aa2da-e87e-493e-b866-ee8b35fd5138 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda5: Location of files loaded by Grub: ===================


 698.0GB: boot/grub/core.img
 711.1GB: boot/grub/grub.cfg
 708.0GB: boot/initrd.img-2.6.32-21-generic
 708.0GB: boot/initrd.img-2.6.32-22-generic
 699.9GB: boot/vmlinuz-2.6.32-21-generic
 704.5GB: boot/vmlinuz-2.6.32-22-generic
 708.0GB: initrd.img
 708.0GB: initrd.img.old
 704.5GB: vmlinuz
 699.9GB: vmlinuz.old
=======Devices which don't seem to have a corresponding hard drive==============

sdb sdc sde 

```Also when I look at the Disk Utility and GParted now, I see some info that I dont know how to translate. I do see some unallocated space /dev/sda but its got -ve bytes. I also have exclamation sign next to my ntfs and when i look at info, i see some information about it. Picture attached. 

[ATTACH]156072[/ATTACH]

---

### Post by oldfred on 2010-05-08
Boot script looks good. I cannot see anything that looks out of place. Winddows boot sector shows that it is there.

Are you still not able to boot windows? The only thing more I can think of is to run window chkdsk from your XP CD.

---

### Post by vinod_home on 2010-05-08
I just saw another thread, does this apply to windows xp (thought it was only for windows 7). 
[http://ubuntuforums.org/showthread.php?t=1463451&highlight=chkdsk&page=2](http://ubuntuforums.org/showthread.php?t=1463451&highlight=chkdsk&page=2)

what options should i use. 
chkdsk c: /f
chkdsk c: /r

---

### Post by vinod_home on 2010-05-08
I went to windows recovery console and tried to run chkdsk c: /r  and the output says

The volume appears to contain one or more unrecoverable problems.
10344 kilobytes total disk space
1108 kilobytes are available

4096 bytes in each allocation unit
2586 total allocation units on disk
277 allocation units available on disk


and i just restarted and it says 
"Read Error"

---

### Post by oldfred on 2010-05-08
More info on chkdsk:

[http://www.microsoft.com/resources/documentation/windows/xp/all/proddocs/en-us/chkdsk.mspx?mfr=true](http://www.microsoft.com/resources/documentation/windows/xp/all/proddocs/en-us/chkdsk.mspx?mfr=true)

I understand that it only fixes one thing at a time so you often have to run it until it gives no errors. But do not know about an unrecoverable error.

---

### Post by vinod_home on 2010-05-08
thanks for your help oldfred. I guess I may as well give up on fixing this. 

Thanks to all that tried to help.

---

### Post by vinod_home on 2010-05-12
I was going through my posts and I see that after i used testdisk to rebuild my partitions, I have a new line in the fdisk and the start and ends are different. 

Old fdisk: 
```

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63 1,258,387,514 1,258,387,452   7 HPFS/NTFS
/dev/sda2       1,258,387,515 1,465,144,064   206,756,550   5 Extended
/dev/sda5       1,258,387,641 1,358,729,504   100,341,864  83 Linux
/dev/sda6       1,358,729,568 1,363,099,184     4,369,617  82 Linux swap / Solaris

```New fdisk
```

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63 1,258,387,514 1,258,387,452   7 HPFS/NTFS
/dev/sda2       1,258,387,578 1,465,144,064   206,756,487   f W95 Ext d (LBA)
/dev/sda5       1,363,099,248 1,460,870,774    97,771,527  83 Linux
/dev/sda6       1,460,870,838 1,465,144,064     4,273,227  82 Linux swap / Solaris

```Is there a way to fix this ? maybe that will fix my XP boot. 

TIA

---

### Post by oldfred on 2010-05-12
I do not think it is related to windows. It changed the extended partition type from 5 to f and slightly moved the linux partitions. Windows does not even see the linux partitions so that should not relate to windows issues.

---

