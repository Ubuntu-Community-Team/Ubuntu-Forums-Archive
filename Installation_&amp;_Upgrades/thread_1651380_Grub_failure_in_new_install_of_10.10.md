---
title: "Grub failure in new install of 10.10"
date: 2010-12-23
forum: Installation &amp; Upgrades
---

### Post by jeff3211 on 2010-12-23
Just finished trying to solve this by using other threads / tutorials...no success! Fresh install today of Ubuntu 10.10 configured as dual-boot with WIN XP. Grub loads latest kernel with no problem at all as long as the keyboard is NOT touched in any way. Touch any key and grub hangs infinitely. There is never any success in changing boot selection in any way. I tried reloading grub from the LiveCD version 10.10 with no success, then I tried reloading it from a 10.04LTS LiveCD which totally blanked grub from the boot process entirely, then I tried purging grub and downloading new code as instructed in another tutorial here on the forums. After the final effort I have restored access to 10.10 on the HDD so that I can boot without the LiveCD, but I am back to the choice-less grub! It's 10.10 or nothing!
I need complete instructions on how to obtain and document the diagnostic information needed to trouble-shoot the issue so that I can provide the data you need to assist me in repairing this boot loader...When I downloaded the new code and installed it, the system recognized and properly identified all partitions and OSes on the system. I should boot from /dev/sda and the linux partition is located on /dev/sda6 the WIN partition is on /dev/sda5. I did notice some strange information concerning the starting and ending locations of the partitions when I was attempting  to correct this issue. If that information seems relevant I will post it upon request. (if instructed on how to do so) Should I repost this as a bug report? (Am I posting in the wrong location?)

---

### Post by theasprint on 2010-12-23
Hi,

Have you tried removing and reinstalling grub?

Because I don't get the meaning of "reloading grub from LiveCD".

To uninstall and reinstall grub: [http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)
Navigate your way to: "12. Uninstalling Grub2"

---

### Post by wilee-nilee on 2010-12-23
So from a booted live Ubuntu cd or thumbdrive lets see the bootscript read out; in my signature just click on it and follow the instructions. Come back to the thread and click on the # in the reply panel this makes code tags paste all the text in between.

So also see if the computer acts this way by as soon as you turn the computer on to boot the live cd hold down the shift to get the early choice menu, choose try Ubuntu and run this script and post it.

Did you try out Ubuntu from a live cd or thumb first to see that it worked?

Did you resize the XP partition with the install partitioner?

Did XP do a chkdsk on resizing?

Do you have a XP install cd?

---

### Post by jeff3211 on 2010-12-23
I did a purge of grub and installed new code. I am able to boot to the latest kernel without using the LiveCD.
I performed the boot_info_script*.sh program and obtained the results, but NOT from CD booted system.
Do I need to shut down and reboot from CD to get new results for accuracy?
I let the installation of Ubuntu 10.10 proceed with the defaults and made no attempt to change the partition sizes myself. I have successfully destroyed installations by trying to make partition size changes myself, and still have a machine with 2 unused partitions because I didn't perform a proper resize of existing partitions. Now I let the installer size them without interference from me! XP never performed chkdsk because I have never been close to getting it to boot yet. If I have to repair the WIN boot records I will start pretty much from scratch by using the LiveCD to mount the partitions that are still readable so that I can copy the existing files to other media before making any changes in Windows that may result in data loss.

---

### Post by jeff3211 on 2010-12-23
I did try the LiveCD versions of the Ubuntu 10.10 AND the 10.04LTS and both CDs worked on this system. I do have a WIN XP install disc so I can do a system repair & rewrite the MBR repair if necessary.

---

### Post by jeff3211 on 2010-12-23
I did perform this procedure...
sudo apt-get purge grub-common grub-pc


I also performed a new install after certifying that I had an active internet connection and my machine was connected and capable of downloading the new code.

---

### Post by garvinrick4 on 2010-12-23
Boot in sda looking in sda6 sounds ok but why is XP in sda5 a logical partition.
What is going on with sda1 thru sda4

---

### Post by jeff3211 on 2010-12-23
These results are from system booted from hdd. If I MUST boot from CD I will have to shut down and reboot to post new results.


```
                                 Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #6 for (,msdos6)/boot/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda5 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sda6: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda7: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63    76,549,724    76,549,662   7 HPFS/NTFS
/dev/sda2          76,549,786   156,301,311    79,751,526   f W95 Ext d (LBA)
/dev/sda5          76,549,788   133,479,369    56,929,582   7 HPFS/NTFS
/dev/sda6         133,480,448   155,236,351    21,755,904  83 Linux
/dev/sda7         155,238,400   156,301,311     1,062,912  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        F600F0E700F0B02B                       ntfs                                     
/dev/sda2: PTTYPE="dos" 
/dev/sda5        66605851605829D7                       ntfs       DISK4_VOL2                    
/dev/sda6        85e24286-53f7-4e23-9a1b-2572017e707e   ext4                                     
/dev/sda7        aff2edfa-aba2-4b87-884a-a4daf92af826   swap                                     
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda6        /                        ext4       (rw,errors=remount-ro,commit=0)


================================ sda1/boot.ini: ================================

[boot loader] 
timeout=3 

================================ sda5/boot.ini: ================================

[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Home Edition" /noexecute=optin /fastdetect /usepmtimer 

=========================== sda6/boot/grub/grub.cfg: ===========================

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
set root='(hd0,msdos6)'
search --no-floppy --fs-uuid --set 85e24286-53f7-4e23-9a1b-2572017e707e
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos6)'
search --no-floppy --fs-uuid --set 85e24286-53f7-4e23-9a1b-2572017e707e
set locale_dir=($root)/boot/grub/locale
set lang=en
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
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set 85e24286-53f7-4e23-9a1b-2572017e707e
    linux    /boot/vmlinuz-2.6.35-24-generic root=UUID=85e24286-53f7-4e23-9a1b-2572017e707e ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-24-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set 85e24286-53f7-4e23-9a1b-2572017e707e
    echo    'Loading Linux 2.6.35-24-generic ...'
    linux    /boot/vmlinuz-2.6.35-24-generic root=UUID=85e24286-53f7-4e23-9a1b-2572017e707e ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set 85e24286-53f7-4e23-9a1b-2572017e707e
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=85e24286-53f7-4e23-9a1b-2572017e707e ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set 85e24286-53f7-4e23-9a1b-2572017e707e
    echo    'Loading Linux 2.6.35-22-generic ...'
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=85e24286-53f7-4e23-9a1b-2572017e707e ro single 
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
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set 85e24286-53f7-4e23-9a1b-2572017e707e
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set 85e24286-53f7-4e23-9a1b-2572017e707e
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows NT/2000/XP (loader) (on /dev/sda1)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set f600f0e700f0b02b
    drivemap -s (hd0) ${root}
    chainloader +1
}
menuentry "Microsoft Windows XP Home Edition (on /dev/sda5)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set 66605851605829d7
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

=============================== sda6/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda6 during installation
UUID=85e24286-53f7-4e23-9a1b-2572017e707e /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda7 during installation
UUID=aff2edfa-aba2-4b87-884a-a4daf92af826 none            swap    sw              0       0

=================== sda6: Location of files loaded by Grub: ===================


  77.1GB: boot/grub/core.img
  71.1GB: boot/grub/grub.cfg
  69.5GB: boot/initrd.img-2.6.35-22-generic
  69.6GB: boot/initrd.img-2.6.35-24-generic
  78.1GB: boot/vmlinuz-2.6.35-22-generic
  78.0GB: boot/vmlinuz-2.6.35-24-generic
  69.6GB: initrd.img
  69.5GB: initrd.img.old
  78.0GB: vmlinuz
  78.1GB: vmlinuz.old
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda2

00000000  65 6a 65 63 74 65 64 53  69 74 65 73 20 00 70 72  |ejectedSites .pr|
00000010  6f 70 65 72 74 79 20 41  63 74 69 76 61 74 65 64  |operty Activated|
00000020  42 75 74 4e 6f 74 52 65  62 6f 6f 74 65 64 57 57  |ButNotRebootedWW|
00000030  13 00 70 72 6f 70 65 72  74 79 20 49 73 44 69 73  |..property IsDis|
00000040  61 62 6c 65 64 57 57 57  1e 00 70 72 6f 70 65 72  |abledWWW..proper|
00000050  74 79 20 54 69 6d 65 72  52 65 6d 61 69 6e 69 6e  |ty TimerRemainin|
00000060  67 53 65 63 6f 6e 64 73  12 00 6d 65 74 68 6f 64  |gSeconds..method|
00000070  20 46 6f 72 63 65 52 65  62 6f 6f 74 22 00 70 72  | ForceReboot".pr|
00000080  6f 70 65 72 74 79 20 44  65 61 63 74 69 76 61 74  |operty Deactivat|
00000090  65 64 42 75 74 4e 6f 74  52 65 62 6f 6f 74 65 64  |edButNotRebooted|
000000a0  17 00 70 72 6f 70 65 72  74 79 20 52 65 62 6f 6f  |..property Reboo|
000000b0  74 52 65 71 75 69 72 65  64 57 57 57 17 00 70 72  |tRequiredWWW..pr|
000000c0  6f 70 65 72 74 79 20 4c  53 50 4c 61 79 65 72 65  |operty LSPLayere|
000000d0  64 49 6e 66 6f 57 57 57  14 00 70 72 6f 70 65 72  |dInfoWWW..proper|
000000e0  74 79 20 4d 63 41 66 65  65 43 68 65 63 6b 57 57  |ty McAfeeCheckWW|
000000f0  1a 00 08 40 08 00 08 80  1a 00 03 40 03 00 03 80  |...@.......@....|
00000100  1a 00 03 40 16 00 03 80  08 00 3e 00 00 00 43 72  |...@......>...Cr|
00000110  65 61 74 65 64 20 62 79  20 4d 49 44 4c 20 76 65  |eated by MIDL ve|
00000120  72 73 69 6f 6e 20 36 2e  30 30 2e 30 33 34 37 20  |rsion 6.00.0347 |
00000130  61 74 20 54 75 65 20 4a  75 6e 20 30 38 20 30 31  |at Tue Jun 08 01|
00000140  3a 32 36 3a 35 35 20 32  30 30 34 0a 13 00 20 4e  |:26:55 2004... N|
00000150  c5 40 57 57 13 00 5b 01  00 06 57 57 18 00 00 00  |.@WW..[...WW....|
00000160  00 00 00 00 ff ff ff ff  30 00 00 00 44 00 00 00  |........0...D...|
00000170  00 00 00 00 48 00 00 00  4c 00 00 00 0c 00 00 00  |....H...L.......|
00000180  88 06 00 00 2c 00 00 00  19 00 19 80 00 00 00 00  |....,...........|
00000190  1c 00 4c 00 11 44 00 00  01 00 00 00 00 00 00 00  |..L..D..........|
000001a0  50 00 00 00 00 00 00 00  6c 00 00 00 0a 00 00 00  |P.......l.......|
000001b0  2c 00 01 00 19 00 19 80  00 00 00 00 20 00 00 01  |,........... ...|
000001c0  c1 ff 07 fe ff ff 02 00  00 00 2e ad 64 03 00 fe  |............d...|
000001d0  ff ff 05 fe ff ff 30 ad  64 03 36 fc 4b 01 00 00  |......0.d.6.K...|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200
```

---

### Post by jeff3211 on 2010-12-23
This machine had an automatic back-up program from CMS peripherals called bounce back. It would periodically copy the entire contents of C: to another drive or partition for recovery purposes in case of viral attack. The 80Gb drive was partitioned into two equal sized partitions before the Ubuntu install. I did not change or erase any existing data before the installation of Ubuntu 10.10 The partitions were supposed to be identical, so theoretically I should be able to boot to D: the second partition, and I have been able to in other machines with this software, but I hadn't tried on this machine.

---

### Post by garvinrick4 on 2010-12-23
Got two installs of Windows sda1 and sda5 linux on sda6
I would just install grub again and then boot into ubuntu and update-grub
In live cd.
```
sudo mount /dev/sda6 /mnt
``````
sudo grub-install --recheck --root-directory=/mnt /dev/sda
``````
sudo umount /mnt
```boot into ubuntu on HDD and
```
sudo update-grub
```os-prober now suppose to find other operating systems and put in grub config and grub menu.

I have heard Windows does not like logical partitions (sda5) but if it works it works.
Always had Windows in primary myself.
#As you just stated sda1 and sda5 are something I have never dealt with.
But do not see why grub would not work in mbr and looking in sda6 for files.
and updated.

---

### Post by jeff3211 on 2010-12-23
```
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.35-24-generic
Found initrd image: /boot/initrd.img-2.6.35-24-generic
Found linux image: /boot/vmlinuz-2.6.35-22-generic
Found initrd image: /boot/initrd.img-2.6.35-22-generic
Found memtest86+ image: /boot/memtest86+.bin
Found Windows NT/2000/XP (loader) on /dev/sda1
Found Microsoft Windows XP Home Edition on /dev/sda5
done

```

---

### Post by garvinrick4 on 2010-12-23
You got it, looking good. Have a nice Christmas.

---

### Post by jeff3211 on 2010-12-23
results:
grub rescue>
grub rescue>

I will install a new grub loader again tomorrow and try again...

Must note that I was already booted up on the machine with the issue from hdd when I performed your steps. I was not booted from CD. Any blame is mine for not adhering exactly to the steps described as to booting from CD before performing the steps you provided. Thanks everyone for your contributions, I will continue when time permits. All additional assistance will be appreciated, as is the effort to this point! Don't give up!!! (I sure am not ready to!) :)

---

### Post by theasprint on 2010-12-23
Hi,

LoL, ended up reinstalling Grub. Just like I mentioned in 1st post.

But its ok, the experts just now have accessed your problems.

Good Luck :D

---

### Post by jeff3211 on 2010-12-23
This is the fifth time I've reinstalled grub. I actually reinstalled it twice before I posted this thread... I couldn't resist, I just did it again!

---

### Post by jeff3211 on 2010-12-23
I still have a useless grub loader. I may as well have just a pure linux installation here. Characteristics are the same as they were in the first post in this thread! I'm off to sleep now. 4 AM in Texas right now...

---

### Post by jeff3211 on 2010-12-23
I stand corrected! My grub loader is not totally useless...It just appears to be that way because it takes about 360 seconds for it to react to a key press!!!! I walked away from it, and then when I returned it had progressed to the 4th menu choice, one more and it would be on the XP option so I pressed the down arrow key and started counting... a full 20 seconds later and it moved to the fifth selection! XP booted and is now running chkdsk! I will update in the morning! (later in the morning!) :)

---

### Post by jeff3211 on 2010-12-23
Anyone have any ideas why my grub loader response is so slow? Everything else on the machine is really fast and instantly responsive, but the grub menu appears as if it is frozen for almost 3 minutes before any reaction at all takes place. Once I see the selection change the first time, any additional key strokes for item selection take 20 seconds before a response occurs. Once the selection is highlighted, it will launch immediately on press of the enter key. The first linux kernel will launch and I've launched both XP installations. XP has completed a chkdsk and now boots normally once selected.

---

### Post by garvinrick4 on 2010-12-23
> **jeff3211 said:**
> Anyone have any ideas why my grub loader response is so slow? Everything else on the machine is really fast and instantly responsive, but the grub menu appears as if it is frozen for almost 3 minutes before any reaction at all takes place. Once I see the selection change the first time, any additional key strokes for item selection take 20 seconds before a response occurs. Once the selection is highlighted, it will launch immediately on press of the enter key. The first linux kernel will launch and I've launched both XP installations. XP has completed a chkdsk and now boots normally once selected.
Will bump this up to front for you, glad you have a working system again but never have seen nor heard
 of a slow grub-menu maybe something to do with that piece of dos software to clone sda1 to sda5. But I would
 be quessing and that does know one no good. Here is your bump to front of line.

---

### Post by oldfred on 2010-12-23
I also have not seen grub2 being really slow in booting. Ubuntu sometimes is when it has issues with loading a driver or runs its fsck.

I have had issues with both Ubuntu & gparted not seening my NTFS drive even though it booted XP ok. After running chkdsk then gparted saw my NTFS without issue.

Windows chkdsk does not always fix everything on one pass. I might rerun chkdsk on all your NTFS partitions until there are no errors.

Are you sure you are booting sda5? Its boot.ini says to boot partition 1 - rdisk(0)partition(1), so it would not boot sda5 anyway.

chkdsk drive /p /r
The chkdsk command checks the specified drive and repairs or recovers the drive if the drive requires it. The command also marks any bad sectors and it recovers readable information. Run chkdsk several times, until no more errors are detected.
chkdsk c: /r
You can use the following options:
/p Does an exhaustive check of the drive and corrects any errors.
/r Locates bad sectors and recovers readable information.
Note If you specify the /r option, the /p option is implied. When you specify the chkdsk command without arguments, the command checks the current drive with no options in effect. 
[http://www.microsoft.com/resources/documentation/windows/xp/all/proddocs/en-us/chkdsk.mspx?mfr=true](http://www.microsoft.com/resources/documentation/windows/xp/all/proddocs/en-us/chkdsk.mspx?mfr=true)

---

### Post by jeff3211 on 2010-12-24
I have only booted to sda5 once, it is the final choice in the grub menu, and I had never booted to it at all for any reason until now! It booted without any problem, and since sda5 was never changed, chkdsk did not run automatically, and I *haven't run it yet. But* I will run it as you suggested and will post the results. *Should I label this thread solved at THIS time since the grub loads the OS even though I still consider it to have a serious problem?* Should I post the unsatisfactory performance of the grub in a different (new) thread which is NOT a failure complaint but a performance complaint? Just want to comply with the appropriate forum policies...

Also gentlemen please remember that grub isn't slow when loading the chosen OS. It is only slow in responding to keyboard input if choosing a choice other than the default choice already highlighted when grub appears. Grub appears frozen after ANY key-press and the count-down suspends until grub responds to the input from the keyboard. Once grub moves off of the default position the count-down no longer appears. Then subsequent key strokes to the chosen position also appear to make grub freeze, but after twenty seconds the menu responds to the key strokes and changes the selection to the desired choice. Once the desired choice is highlighted, an "Enter" key stroke launches the chosen OS immediately as if the delay had never taken place. If no input takes place (because the default OS is the one desired) no delay is apparent, the OS launches when the count-down expires with no apparent delay. I have not tried to launch the default OS immediately, I will try that during my procedures to run chkdsk on two partitions until no errors report. I will post results when obtained. 

Please let me know if the distinctions I just described change your thinking on the nature of this problem. I do not know if the distinctions are relevant or if I misunderstood your appraisal of the situation. 

Thank you (EVERYONE who has contributed information to this issue) I sincerely appreciate ALL of your expertise and information. I learn much from you all! :)

---

### Post by jeff3211 on 2010-12-24
If I strike "Enter" immediately after grub appears, there is NO delay in launching the linux kernel.
I have verified that If I choose to boot into sda1 I am actually booting to C: drive since chkdsk will not run on a mounted partition from a dos terminal running in the OS native to that partition. I was able to run it on drive D: though from the dos terminal running on C:. Next when I boot to what I think is a bootable install of D: I will verify by running chkdsk C: /r from a dos terminal in that installation. If I am able to do that I will verify a boot load to sda5...

---

### Post by jeff3211 on 2010-12-24
Notice to ALL
This has been an exercise in futility chasing problems with the grub loader. 

I have discovered that this issue is a problem with the bios on the motherboard! It has NOTHING at all to do with Linux of any flavor!

Changing this thread to [solved]

Sincerest appreciation to ALL who assisted me in this effort!

---

