---
title: "ubuntu 10.10 + win7, grub2, SFS partitions unbootable"
date: 2010-12-26
forum: Installation &amp; Upgrades
---

### Post by poitiers on 2010-12-26
Hi All, I tried to search and read as much as my brain could hold, and it might be that I'm reporting a new variety of the "windows won't boot anymore" problem. I'm not a geek, just an average XP+cygwin user coming back to linux after a few years' break. I'm also new to some Win 7 concepts, having used XP up till now.

The context is HP ProBook-4520s, with 4 partitions used up as basic volumes (some of them very little, used by HP tools), so that you can't create another without having to change all of them into dynamic volumes (as the Disk Management utility told me, I'll get to that). This is similar to at least Compaq Presario CQ56 (as 
[reported by svegress elsewhere]("http://ubuntuforums.org/showthread.php?t=1580857&page=4"), which may mean that more cases like mine might crop up, because the four partitions seem to be at the root of the problem).

The story before grub enters the scene is this: 
* I need linux in addition to win7, tried wubi at first but then decided to put linux on a separate partition, so I downloaded and burnt Ubuntu 10.10 LiveCD;
* shrank the main windows partition with the win7 disk management utility, to leave some 80GB or so for linux. Actually, at first I gave it more space, but then decided to extend the previously shrunk windows partition somewhat, and used full decimal offsets for that (like leaving something like 80000MB unpartitioned), which might be relevant to the output of fdisk below, not sure.
* still in Disk Management, right-clicked on the unpartitioned space and was offered just one option, to create a basic volume, so I did, gave it the letter D: and quickly formatted it as NTFS.
* upon OK-ing, I learned that because of the "only 4 basic volumes" restriction (and the newly created volume was the 5th), all the volumes would be turned into dynamic, which might pose a boot problem for other OSs, and that the change is irreversible; decided to go ahead anyway, and all the volumes displayed by Disk Management nicely changed colour; rebooted windows to see if I was in trouble but everything was fine at that point still.

Enter Ubuntu. Decided not to let it take the whole disk, of course, and entered the partitioning options screen. Later on, looking at the various screenshots, I was quite sure that I hadn't been offered the option to install systems side-by-side; I believe there were only two radio bullets: "set up partions" and "use the entire disk". If my recollection is true then perhaps my problems began already at that stage. I chose the manual setup option, erased the D: partition, and in that space, created a 10GB ext3 partition for "/", then, at the end of the unpartitioned space, a 2GB swap partition, and used the rest of the space in the middle for "/home" (ext3). Everything was fine, coped with some wireless problems thanks to these forums :-), updated linux and finally tried to boot into windows. No go. Grub discovered two possible windows entry points, but each of them would give me a quick blue screen that would go away faster than I could read it.

Started reading the forums again, found the diagnostics, tried the "3 times repair" trick, but it didn't help (tried it more than once, the results are as in this post by sicieler: [http://ww.ubuntuforums.org/showpost.php?p=10204240&postcount=18](http://ww.ubuntuforums.org/showpost.php?p=10204240&postcount=18)), then tried using the command line options, and was able only to restore the MBR. Which led me nowhere, i.e. to a black screen telling me that windows can't be started.

Reinstalled grub without problems ([https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)), then repeated the "3 times" trick, reinstalled grub again. And decided to ask for help here :-)

Results of bootrec /scanos OR bootrec /rebuildbcd:
```

Scanning all disks for Windows installations.

Please wait, since this may take a while...

Successfully scanned Windows installations.
Total identified Windows installations: 0
The operation completed successfully.

```bootrec /fixmbr said that the operation completed successfully.

bootrec /fixboot wouldn't work ("the volume does not contain a recognized file system")

In diskpart, i did: 'list disk', 'select disk 0', 'detail disk' -- it shows "no volumes".


This is the output of fdisk -l:
```

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xdd43a43b

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1           1         992+  42  SFS
Partition 1 does not end on cylinder boundary.
/dev/sda2   *           1          39      307200   42  SFS
Partition 2 does not end on cylinder boundary.
/dev/sda3              39       26496   212515840   42  SFS
/dev/sda4           26496       38914    99745793    5  Extended
/dev/sda5           26496       27741     9999360   83  Linux
/dev/sda6           38665       38914     1999872   82  Linux swap / Solaris
/dev/sda7           27741       38664    87742464   83  Linux

Partition table entries are not in disk order

```(I'm wondering whether the "cylinder boundary" issue comes from me using rounded decimal offsets in Disk Management.) And I gather that the "changed disk order" message comes from me defining the swap partition at the end of the unpartitioned space, before I defined /home that precedes it.

And the boot info script says:
```

                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #5 for (,msdos5)/boot/grub.

sda1: _________________________________________________________________________

    File system:       
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot/BCD

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /bootmgr /boot/BCD /Windows/System32/winload.exe

sda4: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda7: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63         2,047         1,985  42 SFS
/dev/sda2    *          2,048       616,447       614,400  42 SFS
/dev/sda3             616,448   425,648,127   425,031,680  42 SFS
/dev/sda4         425,650,174   625,141,759   199,491,586   5 Extended
/dev/sda5         425,650,176   445,648,895    19,998,720  83 Linux
/dev/sda6         621,142,016   625,141,759     3,999,744  82 Linux swap / Solaris
/dev/sda7         445,650,944   621,135,871   175,484,928  83 Linux


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda2        8AA46D9FA46D8E8F                       ntfs       SYSTEM                        
/dev/sda3        C642F54E42F543A9                       ntfs                                     
/dev/sda4: PTTYPE="dos" 
/dev/sda5        3904ab79-dd69-4f5d-93cb-e50417c04f92   ext3                                     
/dev/sda6        6a6384c4-a2f2-438e-aeb3-89b3a55a6bea   swap                                     
/dev/sda7        6de86622-b0e3-4d88-a151-be5cd9b9b4b6   ext3                                     
/dev/sda: PTTYPE="dos" 
error: /dev/sdb: No medium found

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda5        /                        ext3       (rw,errors=remount-ro,commit=0)
/dev/sda7        /home                    ext3       (rw,commit=0)
/dev/sr0         /media/Repair disc Windows 7 64-bit udf        (ro,nosuid,nodev,uhelper=udisks,uid=1000,gid=1000,iocharset=utf8,umask=0077)


=========================== sda5/boot/grub/grub.cfg: ===========================

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
  insmod vbe
  insmod vga
}

insmod part_msdos
insmod ext2
set root='(hd0,msdos5)'
search --no-floppy --fs-uuid --set 3904ab79-dd69-4f5d-93cb-e50417c04f92
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos5)'
search --no-floppy --fs-uuid --set 3904ab79-dd69-4f5d-93cb-e50417c04f92
set locale_dir=($root)/boot/grub/locale
set lang=pl
insmod gettext
if [ "${recordfail}" = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry 'Ubuntu, with Linux 2.6.35-24-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set 3904ab79-dd69-4f5d-93cb-e50417c04f92
    linux    /boot/vmlinuz-2.6.35-24-generic root=UUID=3904ab79-dd69-4f5d-93cb-e50417c04f92 ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-24-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set 3904ab79-dd69-4f5d-93cb-e50417c04f92
    echo    'Loading Linux 2.6.35-24-generic ...'
    linux    /boot/vmlinuz-2.6.35-24-generic root=UUID=3904ab79-dd69-4f5d-93cb-e50417c04f92 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set 3904ab79-dd69-4f5d-93cb-e50417c04f92
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=3904ab79-dd69-4f5d-93cb-e50417c04f92 ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set 3904ab79-dd69-4f5d-93cb-e50417c04f92
    echo    'Loading Linux 2.6.35-22-generic ...'
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=3904ab79-dd69-4f5d-93cb-e50417c04f92 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-22-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set 3904ab79-dd69-4f5d-93cb-e50417c04f92
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set 3904ab79-dd69-4f5d-93cb-e50417c04f92
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda2)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos2)'
    search --no-floppy --fs-uuid --set 8aa46d9fa46d8e8f
    chainloader +1
}
menuentry "Windows 7 (loader) (on /dev/sda3)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos3)'
    search --no-floppy --fs-uuid --set c642f54e42f543a9
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

=============================== sda5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/sda5       /               ext3    errors=remount-ro 0       1
# /home was on /dev/sda7 during installation
UUID=6de86622-b0e3-4d88-a151-be5cd9b9b4b6 /home           ext3    defaults        0       2
# swap was on /dev/sda6 during installation
UUID=6a6384c4-a2f2-438e-aeb3-89b3a55a6bea none            swap    sw              0       0

=================== sda5: Location of files loaded by Grub: ===================


 223.3GB: boot/grub/core.img
 223.3GB: boot/grub/grub.cfg
 223.3GB: boot/initrd.img-2.6.35-22-generic
 223.3GB: boot/initrd.img-2.6.35-24-generic
 223.4GB: boot/vmlinuz-2.6.35-22-generic
 223.4GB: boot/vmlinuz-2.6.35-24-generic
 223.3GB: initrd.img
 223.3GB: initrd.img.old
 223.4GB: vmlinuz
 223.4GB: vmlinuz.old
=======Devices which don't seem to have a corresponding hard drive==============

sdb 

```And here's some output of testdisk -- it shows some many various and different readings that I am not sure which of them are helpful here.

```

TestDisk 6.11, Data Recovery Utility, April 2009
Christophe GRENIER <grenier@cgsecurity.org>
http://www.cgsecurity.org

Disk /dev/sda - 320 GB / 298 GiB - CHS 38914 255 63
     Partition               Start        End    Size in sectors
D HPFS - NTFS              0  32 33    38  94 56     614400 [SYSTEM]
D HPFS - NTFS             38  94 56    76 157 16     614400
D HPFS - NTFS             38  94 57 20085 177 60  322060288
D HPFS - NTFS             38  94 57 20092  18 22  322162688
D HPFS - NTFS             38  94 57 23945 185 48  384071680
D HPFS - NTFS             38  94 57 26495  94 31  425031680
D HPFS - NTFS             38  94 57 36694  16 58  588873728
D Linux                 6271 122 60  8406  10 52   34291712
D Linux                 6271 187 61  8406  75 53   34291712
D HPFS - NTFS          20085 177 61 36693 239 26  266811392 [Linux]
D Linux                26495 127  1 27740  91 63   19998720
D Linux                27107  40  6 28352   5  5   19998720
D Linux                27109  82 46 28354  47 45   19998720
D Linux                27111 157 55 28356 122 54   19998720
D Linux                27114 205 36 28359 170 35   19998720
D Linux                27740 124 33 38663 234 35  175484928
D HPFS - NTFS          36694  16 59 38652  48 52   31457280 [HP_RECOVERY]
D FAT32 LBA            38652  48 53 38912 162 34    4184064 [HP_TOOLS]
D Linux Swap           38664  77  6 38913  69 52    3999728

```

From reading about the SFS problems somewhere else in this forum, I'm beginning to be afraid that I won't manage without a win7 reinstall, which I'd rather avoid, if possible. I'll be grateful for all possible advice. [back in a few hours, need some sleep now]

---

### Post by oldfred on 2010-12-26
I saved this, do not know for sure if it works. SFS is a logical volume system that is windows only. If you want to create partitions for Linux use Linux tools. You can use windows tools to repairs windows, but sometimes you still can use Linux tools to fix windows.:)

SFS converting:
[http://www.sevenforums.com/tutorials/26829-convert-dynamic-disk-basic-disk.html](http://www.sevenforums.com/tutorials/26829-convert-dynamic-disk-basic-disk.html)
You can use a third-party tool, such as Partition Wizard 4.2. to convert a convert a dynamic disk to a basic disk without having to delete or format them.
The Partition Wizard software for Windows is supposed to be able to convert dynamic disks to regular partitions without data loss, so it may be what you need to get around this problem; however, I've never used it and so I can't be sure it will work.
Dynamic volume is a Microsoft proprietary format developed together with Veritas (now acquired by Symantec)

Edit:
I have not used testdisk to recover a partition nor SFS partitions. 

D HPFS - NTFS              0  32 33    38  94 56     [COLOR=Red]614400[/COLOR] [SYSTEM]
D HPFS - NTFS             38  94 56    76 157 16     614400
D HPFS - NTFS             38  94 57 20085 177 60  322060288
D HPFS - NTFS             38  94 57 20092  18 22  322162688
D HPFS - NTFS             38  94 57 23945 185 48  384071680
D HPFS - NTFS             38  94 57 26495  94 31  [COLOR=Red]425031680[/COLOR]
D HPFS - NTFS             38  94 57 36694  16 58  588873728

The above sizes are the same as your SFS partitions. Does testdisk tell you if the are basic or logical?

---

### Post by poitiers on 2010-12-28
Hi oldfred, thanks for the reply and apologies for coming back late, I'm babysitting :-)

> **oldfred said:**
> I saved this, do not know for sure if it works. SFS is a logical volume system that is windows only. If you want to create partitions for Linux use Linux tools. You can use windows tools to repairs windows, but sometimes you still can use Linux tools to fix windows.:)

I probably wasn't clear enough: I did use linux tools to create the partitions for linux. But it appeared to me that first, I needed to create a windows partition, otherwise ubuntu wouldn't access the unpartitioned space left by Disk Management (it showed up as 'unusable' or some such word on the partitioning screen of LiveCD). So I created the NTFS partition only to delete it under ubuntu/LiveCD, in order to create linux partitions in its place. Except that I'm sure I must have messed something up on the way :-/ 

> **oldfred said:**
> 
SFS converting:
[http://www.sevenforums.com/tutorials/26829-convert-dynamic-disk-basic-disk.html](http://www.sevenforums.com/tutorials/26829-convert-dynamic-disk-basic-disk.html)
You can use a third-party tool, such as Partition Wizard 4.2. to convert a convert a dynamic disk to a basic disk without having to delete or format them.
The Partition Wizard software for Windows is supposed to be able to convert dynamic disks to regular partitions without data loss, so it may be what you need to get around this problem; however, I've never used it and so I can't be sure it will work.
Dynamic volume is a Microsoft proprietary format developed together with Veritas (now acquired by Symantec)
Thanks, I read that and burnt the PW bootdisk, except that all it offered to me was to delete partitions, and I preferred to ask here if either (a) anyone was able to solve that problem without deleting partitions or (b) if anyone was able to solve this particular sort of a problem by deleting partitions and turning them back into basic volumes.

I'm afraid that the mess I created is not just about SFS, but also about those cylinders, and possibly also about one more issue: the volume that I decided to use for ubuntu was not at the end of the disk, it was *between* other volumes. But after creating partitions for ubuntu, with the LiveCD, it looks to me like all the windows volumes that were supposed to follow the linux volumes (containing some kind of HP tools) have gone missing and only show up on that single screen in testdisk that I attached above.

In other words, I'm a bit afraid of the following happening:

initial state, coming with the laptop:

| NTFS-1 | [COLOR=Blue]NTFS-2 [/COLOR]| NTFS-3 | NTFS-4 |

I think NTFS-2 was the huge volume, containing win7 and lots of free space. Volumes 1,3,4 were system/HP volumes. Crucially, there were four of them, the upper limit.

I shrank NTFS-2, creating a new volume:

| NTFS-1 | [COLOR=Blue]NTFS-2-shrunk| NTFS-new[/COLOR] | NTFS-3 | NTFS-4 |

I think I may have messed the cylinders thing in doing so, by using full decimal offsets (frankly, I'd counted on being warned against something like that, maybe I hadn't RTFM-ed enough).

Upon trying to save the changes, win7 told me that it wouldn't tolerate more than 4 basic (or 'simple' -- I may be confusing the terminology here) volumes, and that it had to turn them all into dynamic. I agreed. Sigh. Windows still worked after that.

Then I booted the LiveCD, and deleted [COLOR=Blue]NTFS-new[/COLOR], and set up the three new partitions for ubuntu, in the space thus created.

My next mistake (just guessing!) might have been delegating the swap partition to the end of the **disk**, while thinking that I was merely putting it at the end of the **un-partitioned space** (which was located before NTFS-3 and NTFS-4). That would mean that I actually wrote over the space that LiveCD *perhaps* shouldn't have let me. Does that make sense to anyone or am I beginning to imagine things?

I'll post more testdisk output in a moment, in response to your last question.

---

### Post by poitiers on 2010-12-28
> **oldfred said:**
> 
D HPFS - NTFS              0  32 33    38  94 56     [COLOR=Red]614400[/COLOR] [SYSTEM]
D HPFS - NTFS             38  94 56    76 157 16     614400
D HPFS - NTFS             38  94 57 20085 177 60  322060288
D HPFS - NTFS             38  94 57 20092  18 22  322162688
D HPFS - NTFS             38  94 57 23945 185 48  384071680
D HPFS - NTFS             38  94 57 26495  94 31  [COLOR=Red]425031680[/COLOR]
D HPFS - NTFS             38  94 57 36694  16 58  588873728

The above sizes are the same as your SFS partitions. Does testdisk tell you if the are basic or logical?

Sigh, I have tried to make some sense of these messages and decided that it might be better to post the full log of a single run through the "analyse" option of testdisk. The directory listings appear there because I dived into the Boot/ directory in the first partition, to see what it contained, whether it's windows stuff or grub stuff.

The log contains some scary things like "NTFS found using backup sector!" or "This partition ends after the disk limits", or "The following partitions can't be recovered", so I thought that perhaps someone might have tell me from looking at it whether there is any hope or whether I should just kiss the old setup goodbye and do a full reinstall. Let me stress that I can mount both the initial NTFS volumes from ubuntu desktop. BTW, I'm rather sure that the disk *is* 320 GB, despite what testdisk suggests.

Thanks in advance for your time spent on looking at this!

```

Mon Dec 27 13:47:15 2010
Command line: TestDisk

TestDisk 6.11, Data Recovery Utility, April 2009
Christophe GRENIER <grenier@cgsecurity.org>
http://www.cgsecurity.org
OS: Linux, kernel 2.6.35-24-generic (#42-Ubuntu SMP Thu Dec 2 02:41:37 UTC 2010)
Compiler: GCC 4.4 - Jun 23 2009 17:48:38
ext2fs lib: 1.41.12, ntfs lib: 10:0:0, reiserfs lib: none, ewf lib: none
/dev/sda: LBA, LBA48, DCO support
/dev/sda: size       625142448 sectors
/dev/sda: user_max   625142448 sectors
/dev/sda: dco        625142448 sectors
Warning: can't get size for Disk /dev/mapper/control - 0 B - CHS 1 1 1, sector size=512
Hard disk list
Disk /dev/sda - 320 GB / 298 GiB - CHS 38913 255 63, sector size=512 - ATA SAMSUNG HM320HJ

Partition table type (auto): Intel
/dev/sda: Device Configuration Overlay (DCO) present.
Disk /dev/sda - 320 GB / 298 GiB - ATA SAMSUNG HM320HJ
Partition table type: Intel

Analyse Disk /dev/sda - 320 GB / 298 GiB - CHS 38913 255 63
Geometry from i386 MBR: head=255 sector=63
check_part_i386 1 type 42: no test
check_part_i386 2 type 42: no test
check_part_i386 3 type 42: no test
get_geometry_from_list_part_aux head=255 nbr=2
get_geometry_from_list_part_aux head=8 nbr=5
get_geometry_from_list_part_aux head=16 nbr=4
get_geometry_from_list_part_aux head=32 nbr=4
get_geometry_from_list_part_aux head=64 nbr=4
get_geometry_from_list_part_aux head=128 nbr=4
get_geometry_from_list_part_aux head=240 nbr=1
get_geometry_from_list_part_aux head=255 nbr=2
Current partition structure:
 1 P W2K Dynamic/SFS          0   1  1     0  32 32       1985
 2 * W2K Dynamic/SFS          0  32 33    38  94 56     614400
 3 P W2K Dynamic/SFS         38  94 57 26495  94 31  425031680
 4 E extended             26495 126 62 38913  70  5  199491586
 5 L Linux                26495 127  1 27740  91 63   19998720
   X extended             38664   0  1 38913  70  5    4004600
 6 L Linux Swap           38664  77  6 38913  70  5    3999744
   X extended             27740  92  1 38663 234 35  175486976
 7 L Linux                27740 124 33 38663 234 35  175484928
Computes LBA from CHS for Disk /dev/sda - 320 GB / 298 GiB - CHS 38914 255 63
Allow partial last cylinder : Yes
search_vista_part: 1

search_part()
Disk /dev/sda - 320 GB / 298 GiB - CHS 38914 255 63
NTFS at 0/32/33
filesystem size           614400
sectors_per_cluster       8
mft_lcn                   25600
mftmirr_lcn               2
clusters_per_mft_record   -10
clusters_per_index_record 1
     HPFS - NTFS              0  32 33    38  94 56     614400 [SYSTEM]
     NTFS, 314 MB / 300 MiB
NTFS at 38/94/57
filesystem size           425031680
sectors_per_cluster       8
mft_lcn                   786432
mftmirr_lcn               2
clusters_per_mft_record   -10
clusters_per_index_record 1
     HPFS - NTFS             38  94 57 26495  94 31  425031680
     NTFS, 217 GB / 202 GiB

recover_EXT2: s_block_group_nr=0/76, s_mnt_count=19/34, s_blocks_per_group=32768, s_inodes_per_group=8128
recover_EXT2: s_blocksize=4096
recover_EXT2: s_blocks_count 2499840
recover_EXT2: part_size 19998720
     Linux                26495 127  1 27740  91 63   19998720
     EXT3 Large file Sparse superblock Recover, 10239 MB / 9765 MiB

recover_EXT2: s_block_group_nr=0/669, s_mnt_count=17/21, s_blocks_per_group=32768, s_inodes_per_group=8192
recover_EXT2: s_blocksize=4096
recover_EXT2: s_blocks_count 21935616
recover_EXT2: part_size 175484928
     Linux                27740 124 33 38663 234 35  175484928
     EXT3 Large file Sparse superblock Recover, 89 GB / 83 GiB
     Linux Swap           38664  77  6 38913  69 52    3999728
     SWAP2 version 1, 2047 MB / 1952 MiB
get_geometry_from_list_part_aux head=8 nbr=2
get_geometry_from_list_part_aux head=16 nbr=2
get_geometry_from_list_part_aux head=32 nbr=2
get_geometry_from_list_part_aux head=64 nbr=2
get_geometry_from_list_part_aux head=128 nbr=2
Warning: the current number of heads per cylinder is 255 but the correct value may be 128.

Results
   * HPFS - NTFS              0  32 33    38  94 56     614400 [SYSTEM]
     NTFS, 314 MB / 300 MiB
   P HPFS - NTFS             38  94 57 26495  94 31  425031680
     NTFS, 217 GB / 202 GiB
   P Linux                26495 127  1 27740  91 63   19998720
     EXT3 Large file Sparse superblock Recover, 10239 MB / 9765 MiB
   L Linux                27740 124 33 38663 234 35  175484928
     EXT3 Large file Sparse superblock Recover, 89 GB / 83 GiB
   L Linux Swap           38664  77  6 38913  69 52    3999728
     SWAP2 version 1, 2047 MB / 1952 MiB
ntfs_device_testdisk_io_ioctl() unimplemented


dir_partition inode=5
   * HPFS - NTFS              0  32 33    38  94 56     614400 [SYSTEM]
     NTFS, 314 MB / 300 MiB
Directory /
       5 dr-xr-xr-x     0      0         0  3-Sep-2010 16:43 .
       5 dr-xr-xr-x     0      0         0  3-Sep-2010 16:43 ..
      38 dr-xr-xr-x     0      0         0  3-Sep-2010 16:31 $RECYCLE.BIN
      43 dr-xr-xr-x     0      0         0 14-Oct-2010 15:47 Boot
      97 -r--r--r--     0      0    383562 14-Oct-2010 15:47 bootmgr
      35 -r--r--r--     0      0        33  3-Sep-2010 16:43 SYSTEM
      36 dr-xr-xr-x     0      0         0  3-Sep-2010 16:24 System Volume Information

dir_partition inode=43
   * HPFS - NTFS              0  32 33    38  94 56     614400 [SYSTEM]
     NTFS, 314 MB / 300 MiB
Directory /Boot
      43 dr-xr-xr-x     0      0         0 14-Oct-2010 15:47 .
       5 dr-xr-xr-x     0      0         0  3-Sep-2010 16:43 ..
     104 -r--r--r--     0      0     28672 14-Oct-2010 15:47 BCD
     105 -r--r--r--     0      0     25600 14-Oct-2010 15:47 BCD.LOG
     106 -r--r--r--     0      0         0 14-Oct-2010 15:47 BCD.LOG1
     107 -r--r--r--     0      0         0 14-Oct-2010 15:47 BCD.LOG2
      44 -r--r--r--     0      0     65536 14-Oct-2010 15:47 BOOTSTAT.DAT
      45 dr-xr-xr-x     0      0         0 14-Oct-2010 15:47 cs-CZ
      47 dr-xr-xr-x     0      0         0 14-Oct-2010 15:47 da-DK
      49 dr-xr-xr-x     0      0         0 14-Oct-2010 15:47 de-DE
      51 dr-xr-xr-x     0      0         0 14-Oct-2010 15:47 el-GR
      54 dr-xr-xr-x     0      0         0 14-Oct-2010 15:47 en-US
      57 dr-xr-xr-x     0      0         0 14-Oct-2010 15:47 es-ES
      59 dr-xr-xr-x     0      0         0 14-Oct-2010 15:47 fi-FI
      98 dr-xr-xr-x     0      0         0 14-Oct-2010 15:47 Fonts
      61 dr-xr-xr-x     0      0         0 14-Oct-2010 15:47 fr-FR
      63 dr-xr-xr-x     0      0         0 14-Oct-2010 15:47 hu-HU
      66 dr-xr-xr-x     0      0         0 14-Oct-2010 15:47 it-IT
      68 dr-xr-xr-x     0      0         0 14-Oct-2010 15:47 ja-JP
      70 dr-xr-xr-x     0      0         0 14-Oct-2010 15:47 ko-KR
      72 -r--r--r--     0      0    485440 14-Oct-2010 15:47 memtest.exe
      73 dr-xr-xr-x     0      0         0 14-Oct-2010 15:47 nb-NO
      75 dr-xr-xr-x     0      0         0 14-Oct-2010 15:47 nl-NL
      77 dr-xr-xr-x     0      0         0 14-Oct-2010 15:47 pl-PL
      80 dr-xr-xr-x     0      0         0 14-Oct-2010 15:47 pt-BR
      82 dr-xr-xr-x     0      0         0 14-Oct-2010 15:47 pt-PT
      84 dr-xr-xr-x     0      0         0 14-Oct-2010 15:47 ru-RU
      86 dr-xr-xr-x     0      0         0 14-Oct-2010 15:47 sv-SE
      88 dr-xr-xr-x     0      0         0 14-Oct-2010 15:47 tr-TR
      91 dr-xr-xr-x     0      0         0 14-Oct-2010 15:47 zh-CN
      93 dr-xr-xr-x     0      0         0 14-Oct-2010 15:47 zh-HK
      95 dr-xr-xr-x     0      0         0 14-Oct-2010 15:47 zh-TW
Directory /
       5 dr-xr-xr-x     0      0         0  3-Sep-2010 16:43 .
       5 dr-xr-xr-x     0      0         0  3-Sep-2010 16:43 ..
      38 dr-xr-xr-x     0      0         0  3-Sep-2010 16:31 $RECYCLE.BIN
      43 dr-xr-xr-x     0      0         0 14-Oct-2010 15:47 Boot
      97 -r--r--r--     0      0    383562 14-Oct-2010 15:47 bootmgr
      35 -r--r--r--     0      0        33  3-Sep-2010 16:43 SYSTEM
      36 dr-xr-xr-x     0      0         0  3-Sep-2010 16:24 System Volume Information

interface_write()
 1 * HPFS - NTFS              0  32 33    38  94 56     614400 [SYSTEM]
 2 P HPFS - NTFS             38  94 57 26495  94 31  425031680
 3 P Linux                26495 127  1 27740  91 63   19998720
 4 E extended LBA         27740  93  1 38913 254 63  179504451
 5 L Linux                27740 124 33 38663 234 35  175484928
 6 L Linux Swap           38664  77  6 38913  69 52    3999728

search_part()
Disk /dev/sda - 320 GB / 298 GiB - CHS 38914 255 63
NTFS at 0/32/33
filesystem size           614400
sectors_per_cluster       8
mft_lcn                   25600
mftmirr_lcn               2
clusters_per_mft_record   -10
clusters_per_index_record 1
     HPFS - NTFS              0  32 33    38  94 56     614400 [SYSTEM]
     NTFS, 314 MB / 300 MiB
NTFS at 38/94/56
filesystem size           614400
sectors_per_cluster       8
mft_lcn                   25600
mftmirr_lcn               2
clusters_per_mft_record   -10
clusters_per_index_record 1
     HPFS - NTFS              0  32 33    38  94 56     614400 [SYSTEM]
     NTFS found using backup sector!, 314 MB / 300 MiB
NTFS at 38/94/57
filesystem size           425031680
sectors_per_cluster       8
mft_lcn                   786432
mftmirr_lcn               2
clusters_per_mft_record   -10
clusters_per_index_record 1
     HPFS - NTFS             38  94 57 26495  94 31  425031680
     NTFS, 217 GB / 202 GiB

recover_EXT2: s_block_group_nr=0/130, s_mnt_count=2/25, s_blocks_per_group=32768, s_inodes_per_group=8192
recover_EXT2: s_blocksize=4096
recover_EXT2: s_blocks_count 4286464
recover_EXT2: part_size 34291712
     Linux                 6271 122 60  8406  10 52   34291712
     EXT4 Large file Sparse superblock Recover, 17 GB / 16 GiB

recover_EXT2: s_block_group_nr=0/130, s_mnt_count=1/25, s_blocks_per_group=32768, s_inodes_per_group=8192
recover_EXT2: s_blocksize=4096
recover_EXT2: s_blocks_count 4286464
recover_EXT2: part_size 34291712
     Linux                 6271 187 61  8406  75 53   34291712
     EXT4 Large file Sparse superblock Recover, 17 GB / 16 GiB
NTFS at 19525/105/37
filesystem size           588873728
sectors_per_cluster       8
mft_lcn                   786432
mftmirr_lcn               2
clusters_per_mft_record   -10
clusters_per_index_record 1
     HPFS - NTFS          19525 105 37 56181  27 38  588873728
     NTFS, 301 GB / 280 GiB
This partition ends after the disk limits. (start=313675776, size=588873728, end=902549503, disk end=625153410)
NTFS at 19635/239/61
filesystem size           588873728
sectors_per_cluster       8
mft_lcn                   786432
mftmirr_lcn               2
clusters_per_mft_record   -10
clusters_per_index_record 1
     HPFS - NTFS          19635 239 61 56291 161 62  588873728
     NTFS, 301 GB / 280 GiB
This partition ends after the disk limits. (start=315451392, size=588873728, end=904325119, disk end=625153410)
NTFS at 20085/177/60
filesystem size           322060288
sectors_per_cluster       8
mft_lcn                   786432
mftmirr_lcn               2
clusters_per_mft_record   -10
clusters_per_index_record 1
     HPFS - NTFS             38  94 57 20085 177 60  322060288
     NTFS found using backup sector!, 164 GB / 153 GiB
NTFS at 20085/177/61
filesystem size           266811392
sectors_per_cluster       8
mft_lcn                   786432
mftmirr_lcn               2
clusters_per_mft_record   -10
clusters_per_index_record 1
     HPFS - NTFS          20085 177 61 36693 239 26  266811392 [Linux]
     NTFS, 136 GB / 127 GiB
NTFS at 20092/18/22
filesystem size           322162688
sectors_per_cluster       8
mft_lcn                   786432
mftmirr_lcn               2
clusters_per_mft_record   -10
clusters_per_index_record 1
     HPFS - NTFS             38  94 57 20092  18 22  322162688
     NTFS found using backup sector!, 164 GB / 153 GiB
NTFS at 23945/185/48
filesystem size           384071680
sectors_per_cluster       8
mft_lcn                   786432
mftmirr_lcn               2
clusters_per_mft_record   -10
clusters_per_index_record 1
     HPFS - NTFS             38  94 57 23945 185 48  384071680
     NTFS found using backup sector!, 196 GB / 183 GiB
NTFS at 26495/94/31
filesystem size           425031680
sectors_per_cluster       8
mft_lcn                   786432
mftmirr_lcn               2
clusters_per_mft_record   -10
clusters_per_index_record 1
     HPFS - NTFS             38  94 57 26495  94 31  425031680
     NTFS found using backup sector!, 217 GB / 202 GiB

recover_EXT2: s_block_group_nr=0/76, s_mnt_count=19/34, s_blocks_per_group=32768, s_inodes_per_group=8128
recover_EXT2: s_blocksize=4096
recover_EXT2: s_blocks_count 2499840
recover_EXT2: part_size 19998720
     Linux                26495 127  1 27740  91 63   19998720
     EXT3 Large file Sparse superblock Recover, 10239 MB / 9765 MiB

recover_EXT2: s_block_group_nr=0/76, s_mnt_count=10/34, s_blocks_per_group=32768, s_inodes_per_group=8128
recover_EXT2: s_blocksize=4096
recover_EXT2: s_blocks_count 2499840
recover_EXT2: part_size 19998720
     Linux                27107  40  6 28352   5  5   19998720
     EXT3 Large file Sparse superblock Recover, 10239 MB / 9765 MiB

recover_EXT2: s_block_group_nr=0/76, s_mnt_count=10/34, s_blocks_per_group=32768, s_inodes_per_group=8128
recover_EXT2: s_blocksize=4096
recover_EXT2: s_blocks_count 2499840
recover_EXT2: part_size 19998720
     Linux                27109  82 46 28354  47 45   19998720
     EXT3 Large file Sparse superblock Recover, 10239 MB / 9765 MiB

recover_EXT2: s_block_group_nr=0/76, s_mnt_count=10/34, s_blocks_per_group=32768, s_inodes_per_group=8128
recover_EXT2: s_blocksize=4096
recover_EXT2: s_blocks_count 2499840
recover_EXT2: part_size 19998720
     Linux                27111 157 55 28356 122 54   19998720
     EXT3 Large file Sparse superblock Recover, 10239 MB / 9765 MiB

recover_EXT2: s_block_group_nr=0/76, s_mnt_count=10/34, s_blocks_per_group=32768, s_inodes_per_group=8128
recover_EXT2: s_blocksize=4096
recover_EXT2: s_blocks_count 2499840
recover_EXT2: part_size 19998720
     Linux                27114 205 36 28359 170 35   19998720
     EXT3 Large file Sparse superblock Recover, 10239 MB / 9765 MiB

recover_EXT2: s_block_group_nr=0/669, s_mnt_count=17/21, s_blocks_per_group=32768, s_inodes_per_group=8192
recover_EXT2: s_blocksize=4096
recover_EXT2: s_blocks_count 21935616
recover_EXT2: part_size 175484928
     Linux                27740 124 33 38663 234 35  175484928
     EXT3 Large file Sparse superblock Recover, 89 GB / 83 GiB

recover_EXT2: s_block_group_nr=0/669, s_mnt_count=17/21, s_blocks_per_group=32768, s_inodes_per_group=8192
recover_EXT2: s_blocksize=4096
recover_EXT2: s_blocks_count 21935616
recover_EXT2: part_size 175484928
     Linux                33174 170 21 44098  25 23  175484928
     EXT3 Large file Sparse superblock Recover, 89 GB / 83 GiB
This partition ends after the disk limits. (start=532951040, size=175484928, end=708435967, disk end=625153410)
NTFS at 36693/239/26
filesystem size           266811392
sectors_per_cluster       8
mft_lcn                   786432
mftmirr_lcn               2
clusters_per_mft_record   -10
clusters_per_index_record 1
     HPFS - NTFS          20085 177 61 36693 239 26  266811392 [Linux]
     NTFS found using backup sector!, 136 GB / 127 GiB
NTFS at 36694/16/58
filesystem size           588873728
sectors_per_cluster       8
mft_lcn                   786432
mftmirr_lcn               2
clusters_per_mft_record   -10
clusters_per_index_record 1
     HPFS - NTFS             38  94 57 36694  16 58  588873728
     NTFS found using backup sector!, 301 GB / 280 GiB
NTFS at 36694/16/59
filesystem size           31457280
sectors_per_cluster       8
mft_lcn                   786432
mftmirr_lcn               2
clusters_per_mft_record   -10
clusters_per_index_record 1
     HPFS - NTFS          36694  16 59 38652  48 52   31457280 [HP_RECOVERY]
     NTFS, 16 GB / 15 GiB
NTFS at 38652/48/52
filesystem size           31457280
sectors_per_cluster       8
mft_lcn                   786432
mftmirr_lcn               2
clusters_per_mft_record   -10
clusters_per_index_record 1
     HPFS - NTFS          36694  16 59 38652  48 52   31457280 [HP_RECOVERY]
     NTFS found using backup sector!, 16 GB / 15 GiB
FAT32 at 38652/48/53
FAT1 : 8242-12312
FAT2 : 12313-16383
start_rootdir : 16384 root cluster : 2
Data : 16384-4184063
sectors : 4184064
cluster_size : 8
no_of_cluster : 520960 (2 - 520961)
fat_length 4071 calculated 4071

FAT32 at 38652/48/53
     FAT32 LBA            38652  48 53 38912 162 34    4184064 [HP_TOOLS]
     FAT32, 2142 MB / 2043 MiB
FAT32 at 38652/48/59
FAT1 : 8242-12312
FAT2 : 12313-16383
start_rootdir : 16384 root cluster : 2
Data : 16384-4184063
sectors : 4184064
cluster_size : 8
no_of_cluster : 520960 (2 - 520961)
fat_length 4071 calculated 4071

FAT32 at 38652/48/59
     FAT32 LBA            38652  48 53 38912 162 34    4184064 [[HP_Tools]]
     FAT found using backup sector!, 2142 MB / 2043 MiB
     Linux Swap           38664  77  6 38913  69 52    3999728
     SWAP2 version 1, 2047 MB / 1952 MiB
NTFS at 38/94/56
filesystem size           614400
sectors_per_cluster       8
mft_lcn                   25600
mftmirr_lcn               2
clusters_per_mft_record   -10
clusters_per_index_record 1
NTFS at 38/94/56
filesystem size           614400
sectors_per_cluster       8
mft_lcn                   25600
mftmirr_lcn               2
clusters_per_mft_record   -10
clusters_per_index_record 1
NTFS at 38/94/56
filesystem size           614400
sectors_per_cluster       8
mft_lcn                   25600
mftmirr_lcn               2
clusters_per_mft_record   -10
clusters_per_index_record 1
NTFS at 38/94/56
filesystem size           614400
sectors_per_cluster       8
mft_lcn                   25600
mftmirr_lcn               2
clusters_per_mft_record   -10
clusters_per_index_record 1
Disk /dev/sda - 320 GB / 298 GiB - CHS 38914 255 63
Check the harddisk size: HD jumpers settings, BIOS detection...
The harddisk (320 GB / 298 GiB) seems too small! (< 463 GB / 431 GiB)
The following partitions can't be recovered:
     HPFS - NTFS          19525 105 37 56181  27 38  588873728
     NTFS, 301 GB / 280 GiB
     HPFS - NTFS          19635 239 61 56291 161 62  588873728
     NTFS, 301 GB / 280 GiB
     Linux                33174 170 21 44098  25 23  175484928
     EXT3 Large file Sparse superblock Recover, 89 GB / 83 GiB
get_geometry_from_list_part_aux head=8 nbr=2
get_geometry_from_list_part_aux head=16 nbr=2
get_geometry_from_list_part_aux head=32 nbr=2
get_geometry_from_list_part_aux head=64 nbr=2
get_geometry_from_list_part_aux head=128 nbr=2
Warning: the current number of heads per cylinder is 255 but the correct value may be 128.

Results
     HPFS - NTFS              0  32 33    38  94 56     614400 [SYSTEM]
     NTFS, 314 MB / 300 MiB
     HPFS - NTFS             38  94 56    76 157 16     614400
     NTFS, 314 MB / 300 MiB
     HPFS - NTFS             38  94 57 20085 177 60  322060288
     NTFS found using backup sector!, 164 GB / 153 GiB
     HPFS - NTFS             38  94 57 20092  18 22  322162688
     NTFS found using backup sector!, 164 GB / 153 GiB
     HPFS - NTFS             38  94 57 23945 185 48  384071680
     NTFS found using backup sector!, 196 GB / 183 GiB
     HPFS - NTFS             38  94 57 26495  94 31  425031680
     NTFS, 217 GB / 202 GiB
     HPFS - NTFS             38  94 57 36694  16 58  588873728
     NTFS found using backup sector!, 301 GB / 280 GiB
     Linux                 6271 122 60  8406  10 52   34291712
     EXT4 Large file Sparse superblock Recover, 17 GB / 16 GiB
     Linux                 6271 187 61  8406  75 53   34291712
     EXT4 Large file Sparse superblock Recover, 17 GB / 16 GiB
     HPFS - NTFS          20085 177 61 36693 239 26  266811392 [Linux]
     NTFS, 136 GB / 127 GiB
     Linux                26495 127  1 27740  91 63   19998720
     EXT3 Large file Sparse superblock Recover, 10239 MB / 9765 MiB
     Linux                27107  40  6 28352   5  5   19998720
     EXT3 Large file Sparse superblock Recover, 10239 MB / 9765 MiB
     Linux                27109  82 46 28354  47 45   19998720
     EXT3 Large file Sparse superblock Recover, 10239 MB / 9765 MiB
     Linux                27111 157 55 28356 122 54   19998720
     EXT3 Large file Sparse superblock Recover, 10239 MB / 9765 MiB
     Linux                27114 205 36 28359 170 35   19998720
     EXT3 Large file Sparse superblock Recover, 10239 MB / 9765 MiB
     Linux                27740 124 33 38663 234 35  175484928
     EXT3 Large file Sparse superblock Recover, 89 GB / 83 GiB
     HPFS - NTFS          36694  16 59 38652  48 52   31457280 [HP_RECOVERY]
     NTFS, 16 GB / 15 GiB
     FAT32 LBA            38652  48 53 38912 162 34    4184064 [HP_TOOLS]
     FAT32, 2142 MB / 2043 MiB
     Linux Swap           38664  77  6 38913  69 52    3999728
     SWAP2 version 1, 2047 MB / 1952 MiB

interface_write()
 
No partition found or selected for recovery
simulate write!

write_mbr_i386: starting...
write_all_log_i386: starting...
No extended partition

TestDisk exited normally.

```

---

### Post by Quackers on 2010-12-28
You are correct in that the 4 primary partitions are the root of the problem. HP is notorious for using up the maximum number of primary partitions on any one disc. Your problem arose when you created a 5th "basic" partition. At this point Windows changed your primary partitions into "Dynamic Disks".
What you needed to do originally, was to delete one partition and create an extended partition in its place.
It appears that you have Ubuntu installed! I'm amazed the installer didn't crash, or at least fail to recognise your partition structure.
In his first post oldfred gives a link for details on how to convert dynamic disks to basic partitions. Obviously that is one option.
I also notice that sda1 is shown as "unknown file system type" and is unmounted.
It could be a better option to get back what you can and re-install everything.

I wouldn't worry about the cylinder boundary issue. It's not part of the problem.

---

### Post by oldfred on 2010-12-28
In the win7 link I gave in post #73 is this link to the older free verison of partition wizard 4.2. 

Do not know if this is valid or not, or if it works. All the other methods seem to require you to backup everything & erase drive. Then repartition and restore from backups. But you should have backups anyway.

[http://cid-24a0e9031e104daf.office.live.com/self.aspx/.Public/partition%20wizard%204.2%20free.zip](http://cid-24a0e9031e104daf.office.live.com/self.aspx/.Public/partition%20wizard%204.2%20free.zip)

---

### Post by poitiers on 2010-12-28
> **Quackers said:**
> You are correct in that the 4 primary partitions are the root of the problem. HP is notorious for using up the maximum number of primary partitions on any one disc. Your problem arose when you created a 5th "basic" partition. At this point Windows changed your primary partitions into "Dynamic Disks".
What you needed to do originally, was to delete one partition and create an extended partition in its place.

In my case, that was out of the question -- the laptop came set up like this from the manufacturer, and it wasn't a private purchase, so I had no contact with the source. Sigh, it is so arrogant of HP (and not only them, as far as I can see) to leave no choice to the client in this matter. From what you are saying, it would be enough if they themselves made the data partition extended from the start. An average Joe wouldn't notice or mind, others could manipulate that one partition alone.

> It appears that you have Ubuntu installed! I'm amazed the installer didn't crash, or at least fail to recognise your partition structure.It might have failed to some extent, if my speculation about it confusing the end of disk with the end of unpartitioned space is correct. If this alone were to be the outcome of my 'adventure', and in connection with other similar cases got to the developers as a bug report, and resulted in improving Ubuntu setup, I'd be most happy.

Otherwise, yes, Ubuntu is the only thing that currently works on this laptop, and it works like a breeze, I'm very satisfied. :-)

> In his first post oldfred gives a link for details on how to convert dynamic disks to basic partitions. Obviously that is one option.
I also notice that sda1 is shown as "unknown file system type" and is unmounted.
It could be a better option to get back what you can and re-install everything.

I wouldn't worry about the cylinder boundary issue. It's not part of the problem.I'll try the Wizard when I have a win7 dvd in hand. I'm not hoping for much from the conversion -- like you say: it looks like a re-install is the wisest way out. I was just hoping for some miraculous advice to save all those hours of needless setting up my software for win7 :-) Thanks for your time.

---

### Post by poitiers on 2010-12-28
> **oldfred said:**
> In the win7 link I gave in post #73 is this link to the older free verison of partition wizard 4.2. 

Do not know if this is valid or not, or if it works. All the other methods seem to require you to backup everything & erase drive. Then repartition and restore from backups. But you should have backups anyway.

[http://cid-24a0e9031e104daf.office.live.com/self.aspx/.Public/partition%20wizard%204.2%20free.zip](http://cid-24a0e9031e104daf.office.live.com/self.aspx/.Public/partition%20wizard%204.2%20free.zip)

Thanks, oldfred. I burnt the newest version -- it was one of the things I did before I posted here, but the conversion looked like the last resort (and maybe even the wrong way out), so I decided to ask for help first. Yeah, I'll try the PW just to see how it works, and will report any interesting results here. And then, I'm afraid, it will be re-install time.

---

### Post by bludgard on 2010-12-28
I tried latest version of ESEAUS Partition Master Professional.Partition Wizard.And a couple of others.None recognized ext4 file system.Only Ubuntu 10.10 LiveMedia-that I could find.

There is an option to use other file systems.

"bootrec /fixmbr said that the operation completed successfully."

Was it [ Bootrec.exe /FixMbr ]?Without the brackets.

---

### Post by oldfred on 2010-12-28
Yes it the windows repair commands are without the brackets.

The Partition Master would be used just to convert the type of the three SFS partitions back to basic. It should have a command to do that.  The data for a windows SFS/LVM logical partition is stored somehow different than standard MBR/msdos/basic partitions.

I am surprised it does not see the ext4 partitions. Any partition program that does not see valid partitions is not something I would want to use to add or move partitions around.

---

### Post by poitiers on 2010-12-28
Bludgard, both syntaxes work, '.exe' or not, CamelCase or lowercase.

---

### Post by bludgard on 2010-12-29
> **poitiers said:**
> Bludgard, both syntaxes work, '.exe' or not, CamelCase or lowercase.
 
 
Ok.
 
Is there a 100MB partition System Reserved.If so mark partition as Active.
 
If not,mark Windows (C:) drive as Active.

---

### Post by poitiers on 2010-12-29
Hi again. I believe this story won't have a happy ending but the conclusion may turn out to be somewhat important nevertheless: apart from the Ubuntu-external issue of HP's arrogance in setting up a drive in such a way that an average Joe won't be able to repartition it easily, there is also an Ubuntu-internal problem, of the LiveCD not being able to recognize the SFS volumes. Or rather, the problem is that the LiveCD recognizes them partially, and the user is able to mess up his partition structure thinking he is only operating within the unpartitioned space, while in fact he is operating on the existing SFS partitions that follow the unpartitioned space.

Summary/steps to **reproduce the problem**:
[please note: some details here may be completely irrelevant for the  proper reproduction of the problem, but I haven't tested other ways to achieve  that; what I think might be [COLOR=Blue]worth addressing by Ubuntu developers is in blue[/COLOR]]

[LIST]
[*]take one ProBook-4520s ;-) with Win7 and the following, sadly standard, HP partition structure (all four are primary):
[LIST]
[*]System: 300MB
[*](data): any amount
[*]HP_RECOVERY: 15GB
[*]HP_TOOLS: 2GB
[/LIST]
 
[*]shrink the data partition with Win7 Disk Management; [COLOR=Blue]LiveCD will not be able to operate on the space unpartitioned in this manner[/COLOR], so
[LIST]
[*]follow the suggestion of DM and create a basic volume; format the unpartitioned space as e.g. NTFS, possibly give it a letter (I did);
[*]upon saving, DM will ask you if you want to turn all the volumes into dynamic (and duly warn you of some consequences), say yes;
[/LIST]
 
[*]enter Ubuntu LiveCD (noting that[COLOR=Blue] it doesn't offer a side-by-side install[/COLOR]) and erase the new partition, setting up three Linux partitions:
[LIST]
[*]10GB ext3 for /
[*]2GB for swap, marking the radio button for putting it at the end of the... ('disk'? I forget the exact wording, anyway, [COLOR=Blue]it makes you think you only operate within the freshly deleted partition[/COLOR])
[*]the rest ext3 for /home
[/LIST]
 
[/LIST]

At this point, your HD should be messed up: the HP_RECOVERY and HP_TOOLS partitions that you never deleted are [COLOR=Blue]overwritten by the new Ubuntu partitions[/COLOR], and the MBR/grub info is adjusted to the new state of affairs; grub should offer you booting from the two initial Win7 partitions, but both will send you to the blue screen.

Partition Wizard scan shows the deleted partitions, and also the overlaps among them. I attach a screenshot of the initial PW screen, which agrees with the info given by fdisk adduced above.

Because of those overlaps, I won't try to recover Win7 -- I've backed up what I could and will attempt a clean Win7 reinstall tomorrow, either with HP stuff but an extended partition for the data (and one logical partition for Ubuntu -- I hope the LiveCD only has problems with SFS), or without the HP stuff altogether (oh well).

HTH in case someone decides this is material for a bug report.

Quackers and oldfred -- thanks for your time! :-)

---

### Post by bludgard on 2010-12-30
This is my setup for dual booting Win 7 and Ubuntu Maverick-ext4 (highlighted).
 
I used Startup Manager from Packet Manager to configure boot priorities.
 
No worries,though I did read everything 5 times before selecting the next step of installing Ubuntu.I do love to click "next" buttons!
 
Anyway.I feel your frustration and if permitted would suggest that you install Ubuntu on a seperate drive altogether.I've been advised that this will eliminate a great deal of uneeded stress.
 
Sorry for your misfortune.
 
edit:When you custom install Win 7,after updating,I would create a backup image of Windows C: and System Reserved (if you choose to add that partition) straight-off to forego lenghty future installs.Honestly,if you had image backups,you probably wouldn't be here now.

---

### Post by Quackers on 2010-12-30
Please note that if you already have 4 primary partitions on any one hard drive you should not create any other partition at all until you have deleted one of your primary partitions. It is the creation of a 5th partition that causes Windows to change existing partitions to dynamic discs (SFS). It is not a bug, it is what Windows does nowadays! It is not a bug that Ubuntu can't deal with SFS partitions. It doesn't know what they are.

---

### Post by poitiers on 2010-12-30
> **Quackers said:**
> Please note that if you already have 4 primary partitions on any one hard drive you should not create any other partition at all until you have deleted one of your primary partitions. It is the creation of a 5th partition that causes Windows to change existing partitions to dynamic discs (SFS). It is not a bug, it is what Windows does nowadays!

I haven't called that a bug. I have called HP's leaving the average user no say as to the partition structure (by saturating all 4 primaries) arrogance. But this merely provides a setting for what I marked in blue.

> It is not a bug that Ubuntu can't deal with SFS partitions. It doesn't know what they are.Call it "lack of a feature" then ;-)

However, recognizing the presence of SFS partitions on the one hand, and overwriting them as if they weren't visible on the other, appears to carry some indicators of buggy functionality. It might be better to produce a message like "SFS partitions found that Ubuntu can't handle properly; proceed at your own risk or use different partitioning software" or something like that. 


[LIST]
[*]Ubuntu doesn't know what SFS is, but Ubuntu developers do,
[*]They also know that the number of users trying to install Ubuntu on SFS will increase,
[*]It might be sensible to face that rather than not -- is all I'm saying :-)
[/LIST]

---

### Post by Quackers on 2010-12-30
In all honesty, if users don't try to create a 5th primary partition on any one disc (which is contravening the MBR limit) they won't have to deal with SFS partitions. This is not a Linux thing. I'm pretty sure Windows XP doesn't know what SFS is either. :-)

---

### Post by poitiers on 2010-12-30
> **Quackers said:**
> In all honesty, if users don't try to create a 5th primary partition on any one disc (which is contravening the MBR limit) they won't have to deal with SFS partitions. This is not a Linux thing. I'm pretty sure Windows XP doesn't know what SFS is either. :-)

Hi again -- we're getting academic here ;-) , but let me point out a weakness in what you said:


[LIST]
[*]winXP and Vista are irrelevant for this argument -- they are the past, while you want to say exactly the opposite about Ubuntu :-) And it's not the case that Ubuntu doesn't want to cater for M$ market (or rather: that Linux doesn't care about Win users); ergo: Ubuntu should learn to handle SFS and I'm sure it will, in time (or rather: the Linux kernel will, and Ubuntu will adopt this hopefully painlessly). So I think it's fairly honest to call the lack of SFS handling a feature that is still missing.
[*]the 5th partition is only one way to arrive at SFS, there are many others; really the HP issue is far in the background here, it merely provided the setting;
[*]the problem that I believe should be addressed somehow (and, possibly the only thing that may make this entire thread useful for Ubuntu as such) is the LiveCD installer's stance towards a fairly generic policy, a hidden premise that you expect when approaching systems of this kind: "don't promise more than you can handle" or "state your limits clearly", etc. What I wanted to point out is that, **if I am not mistaken about the install process**, the Ubuntu installer doesn't follow that policy: it makes one think it sees the SFS volumes in one step, and then it overwrites them in the next one. It would be much better to simply abort in the presence of SFS, with an appropriate message.
[/LIST]

*If I'm not mistaken* -- this is the point of possible (and welcome) attack on what I report (and this is why I provided the 'recipe' -- in order to make it easy for someone to prove me wrong). Not my silliness in creating the 5th partition (there will be more people like myself, and there already have been), and not the issue of whether Linux will have to handle SFS in time, to which the only imaginable answer is "yes, and probably rather soon, given that XP and Vista are already scheduled for execution, and Linux doesn't want to turn its back on Windows users".

As I said, we seem to be getting academic here, so please don't mind me possibly falling silent on this topic now :-) I have one more thing to do: I've already zeroed out the entire disk and I'm preparing to repartition it and to install Win7+Ubuntu, without the HP stuff, which I don't think I need anyway. Should anything interesting come out of this (which I don't expect ;-)), I'll be sure to post here about that. Thanks again for your involvement.

---

### Post by bludgard on 2010-12-30
I found out the hard way that dual/multi booting is not for the average user.
 
Only after hours of research and multiple trial and error attempts do I feel comfortable with it.
 
However,I *did* know that manipulating my partition structure in any way can cause catastrophic results if not done properly (and sometimes when done properly) and that if I was to continue,I should have a safe path back to where I started-for I am prone to conjure up strange reactions from my machine when I go afiddlin'. 
 
I do not post this to rub salt into your wounds.Merely to inform the unsuspecting that things can and will go wrong.Backups should be an active part of ***every*** computer users maintenance plan. 
 
One

---

