---
title: "Ubuntu Install Problems"
date: 2012-04-08
forum: Installation &amp; Upgrades
---

### Post by mysteron75 on 2012-04-08
I have been trying to install ubuntu and when i get to the install it does not see my windows 7 installation. If i am run the cd as a live disk i can see my windows install when i browse my drive. I run a 2 drive setup and I put Ubuntu on the second drive in a 160gig partition. It only gives me the option to the whole drive or partition. So i specify the partition and start the Ubuntu 11.10 install. The 11.10 installation fails. If i try 12.04 beta 2 it installs but when i go to reboot the there is no grub installer and windows boots normally. Any help would be greatly appreciated.

---

### Post by darkod on 2012-04-08
These are few different issues.

If after installing ubuntu windows boots directly and you have two disks, probably the grub2 bootloader was installed to the other disk. Try changing the hdd order in BIOS and it should load grub2.

If win7 doesn't get detected, your windows disk might be Dynamic, which is MS format that ubuntu can't read correctly and detect win7. Another option is if you have used the disk in raid earlier, you have raid meta data remains, and ubuntu can't detect win7 properly.

---

### Post by roelforg on 2012-04-08
I suck at configuring any bootloader other than syslinux.
But you could just remove the win7 drive from you pc,
install ubuntu normally on it's own drive,
assuming ubuntu is on slave, modify boot order to boot from slave,
plugin the win7drive, boot ubuntu, mod grub config to add a chainload entry for the other drives.
Do this all the time with cd's and usb's.

---

### Post by darkod on 2012-04-08
> **roelforg said:**
> 
plugin the win7drive, boot ubuntu, mod grub config to add a chainload entry for the other drives.
Do this all the time with cd's and usb's.

With grub2 there is no need for any special user configuration. To detect any OS installed after ubuntu, you simply run:
sudo update-grub

That will detect all present OSs and create entries in the grub2 boot menu.

---

### Post by roelforg on 2012-04-08
> **darkod said:**
> With grub2 there is no need for any special user configuration. To detect any OS installed after ubuntu, you simply run:
sudo update-grub

That will detect all present OSs and create entries in the grub2 boot menu.
i was kinda assuming the whole reason the installer can't see win was some ms-only fs thingy (dynamic fs?) and update-grub won't work in that case either. and if that's the case, manually overriding grub and adding a chainload to win drive will work in that case.

---

### Post by mysteron75 on 2012-04-08
The drives are not setup as dynamic. I point the bootloader to my c drive I have had linux installed on that partition before. I just recently upgraded my machine to an Intel i7 3820 on a asus rampage IV formula board.

---

### Post by darkod on 2012-04-08
In that case follow the link in my signature to run the boot info script and post the results as explained there. When we have the details we can investigate.

---

### Post by roelforg on 2012-04-08
> **darkod said:**
> In that case follow the link in my signature to run the boot info script and post the results as explained there. When we have the details we can investigate.

Darkod, wanna solve this one together?
2 minds are better than 1

---

### Post by darkod on 2012-04-08
> **roelforg said:**
> Darkod, wanna solve this one together?
2 minds are better than 1

I don't mind your (and anybody's) help. Even better.

But first we need the script results otherwise we are working blind. So far I can't figure out what is the exact situation and often people can't explain it correctly.

---

### Post by roelforg on 2012-04-08
> **darkod said:**
> I don't mind your (and anybody's) help. Even better.

But first we need the script results otherwise we are working blind. So far I can't figure out what is the exact situation and often people can't explain it correctly.

Yeah, it's like when a friend/familymember calls and says "My computer doesn't work! Fix it!" and that's all the info you can get out of them.

What we really need is some sort of software package that can be installed and used to report problems in detail and maybe run some tried and tested commands like "dpkg-reconfigure xserver-xorg" when there are video problems, reboot networking, etc.

---

### Post by mysteron75 on 2012-04-08
I ran the script and these where the results


                  Boot Info Script 0.61      [1 April 2012]


============================= Boot Info Summary: ===============================

 => Windows is installed in the MBR of /dev/sda.
 => Windows is installed in the MBR of /dev/sdb.

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

sdb1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sdb2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info: 

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 300.1 GB, 300069052416 bytes
255 heads, 63 sectors/track, 36481 cylinders, total 586072368 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *          2,048       206,847       204,800   7 NTFS / exFAT / HPFS
/dev/sda2             206,848   586,070,015   585,863,168   7 NTFS / exFAT / HPFS


GUID Partition Table detected, but does not seem to be used.

Partition    Start Sector    End Sector  # of Sectors System
/dev/sda121 3,249,708,430,200,121,5042,690,604,992,659,706,592-559,103,437,540,414,911 -
/dev/sda122 1,425,901,597,030,766,6653,614,295,809,254,880,2042,188,394,212,224,113,540 -
/dev/sda123 3,603,947,394,627,959,512304,673,285,217,524,397-3,299,274,109,410,435,114 -
/dev/sda124 2,929,046,380,248,440,7673,535,345,280,309,198,100606,298,900,060,757,334 -

Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1               2,048 1,640,847,844 1,640,845,797   7 NTFS / exFAT / HPFS
/dev/sdb2       1,640,849,406 1,953,523,711   312,674,306   5 Extended
Empty Partition.


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        5E7CDAD17CDAA357                       ntfs       System Reserved
/dev/sda2        9868E45668E434A2                       ntfs       
/dev/sdb1        F4CCC20FCCC1CC54                       ntfs       Storage
/dev/sr1                                                iso9660    Ubuntu 12.04 LTS amd64

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sda2        /media/9868E45668E434A2  fuseblk    (rw,nosuid,nodev,allow_other,default_permissions,blksize=4096)
/dev/sr1         /cdrom                   iso9660    (ro,noatime)


======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown GPT Partiton Type
d441a0f50300030058e3e221062da044
Unknown GPT Partiton Type
1dfda6631a567b98eeb1fc62168f267b
Unknown GPT Partiton Type
812d99242d7a8309e4350fc84a0f1bab
Unknown GPT Partiton Type
238eddcc7ed4555e18bcdfcd3342c227

---

### Post by darkod on 2012-04-08
Your windows disk, /dev/sda, was earlier used with gpt partition table, and then you created a msdos table. But windows makes an error when you do this, and doesn't delete the backup gpt table from the disk.

This confuses linux whether you are using msdos or gpt. This is the issue on /dev/sda.

You can delete the backup gpt table with fixparts. Just open your disk with fixparts, it will detect this status and ask you if you want to remove the backup gpt table. Just say yes if you are using msdos, and that's it.

All details about fixparts are here:
[http://www.rodsbooks.com/fixparts/](http://www.rodsbooks.com/fixparts/)

EDIT: Also, on the other disk, /dev/sdb, you seem to have empty extended partition with no actual partitions inside. If this is true, I suggest you delete this extended partition before you start installing ubuntu. You need unallocated space for ubuntu, not belonging to any partition. Having an empty extended partition is pointless anyway, it will get created when you need it.

EDIT2: You said in the first post that 12.04 Beta installs but you don't get grub2 when you reboot. There are no linux partitions on any of the disks. So either the install was never finished, or something happened. In any case, sort out the gpt backup table first on /dev/sda, and then try to install ubuntu either 11.10 or 12.04 Beta to its own partitions, onto unallocated space (not trying to use existing ntfs partitions).

---

### Post by mysteron75 on 2012-04-09
I got fixparts but i am having issues using it. I run the cmd as administrator so fixparts will run. When it asks me for the drive or partition i want to use i am having issues on the correct format i should be putting the info in.

---

### Post by darkod on 2012-04-09
If you are using it in windows, once you open the cmd prompt as Administrator, try something like:
fixparts 0

When using it in windows you specify the disks with a number staring from 0 (zero).

Since you want to open the first disk (in linux terms /dev/sda), try with 0 first.

---

### Post by mysteron75 on 2012-04-09
I am getting unable to read MBR data

---

### Post by mysteron75 on 2012-04-10
I figured it out

---

### Post by Echoes88 on 2012-04-10
HI!

I have got  a problem with my laptop. It's a lenovo n200 with 2 ghz c2d and 2 gb ram. I have native windows vista on that. and tried to install ubuntu 11.10 within virtualbox, and it stops in a certain point during the installation. I tried it for a few times, no succes.

It used to work with older version (8.10), so i dont know why it is.

Thanks for the help.
Echoes88

---

### Post by darkod on 2012-04-10
> **Echoes88 said:**
> HI!

I have got  a problem with my laptop. It's a lenovo n200 with 2 ghz c2d and 2 gb ram. I have native windows vista on that. and tried to install ubuntu 11.10 within virtualbox, and it stops in a certain point during the installation. I tried it for a few times, no succes.

It used to work with older version (8.10), so i dont know why it is.

Thanks for the help.
Echoes88

Please open a new thread on your own, because this doesn't sound like the same issue the OP has got.

---

### Post by mysteron75 on 2012-04-11
I ran fixpart. After that i did a new install of ubuntu 12.04 and did a install along side windows 7. Everything seemed to go well. Then i reboot and it booted straight into windows. There was no linux boot loader. Help

---

### Post by darkod on 2012-04-11
Reinstalling grub2 when ubuntu is already installed:
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

You need to check with the fdisk command is it really installed, if there are Linux partitions on the disk.

---

### Post by mysteron75 on 2012-04-18
I was unable to install grub. I boot into ubuntu live cd and ran the install. It sees the multiple os's. I look at the partitions on the c dive but it does not show the boot partition and the windows 7 install as separate partitions on the bar. Its all orange.

---

### Post by al111 on 2012-04-19
Did you set the linux partition as the *active partition*?

I'm always test-driving different linux distro's-

I triple-boot my desktop, sometimes even quadruple-boot...

I see this all the time-

---

### Post by darkod on 2012-04-19
You better run the boot info script from the link in my signature. Post the results as explained there. That will show more details because we don't seem to understand what you have or what are you installing and how.

If the grub2 install finished OK, it should boot at least in ubuntu with grub2, unless you have multiple HDDs and you are booting from another disk.

---

### Post by mysteron75 on 2012-04-19
I will run the script again. I think the issue is with my c drive. Everthing installs on the partition i create on my d drive. I boot into the live cd and look and all the driectories are there. For some reason Grub will not install on the 100mb MBR partition. There is a disk called fixboot that i used to try to install grub and no luck.This is driving me crazy lol!! I looked at the patitions last night and nothing stands out. I ran fixparts a while ago and it removed some all partition info. So i am able to see windows 7 but thats all the progress i have made so far.

---

### Post by darkod on 2012-04-19
Are you talking about wubi install inside windows or a dual boot installation?

It's confusing when you are using windows terminology for D drive because in linux it would not be called D. And if you are installing on D, it can be only wubi.

In that case you need to be careful which tutorials you follow as wubi is not the same as dual boot.

---

### Post by mysteron75 on 2012-04-19
I am not using wubi. I have always done duel boot systems.  Sorry about the using windows terminology. I am running a 2 drive setup with my sda drive being my windows drive and sdb drive is my data drive. I created partition on my sdb drive a 160gig partition for linux. I had linux on that drive until I upgraded my motherboard cpu and ram. I did a reinstall of windows on sda. After that i was going to reinstall linux on my sdb partition and that is when i start having problems.

---

### Post by darkod on 2012-04-19
The partition you created on /dev/sdb, is it ntfs if you created it from windows, or ext4 partition?

Also, do you plan to use it only with a root partition? Because usually you use root + swap, which means minimum two partitions, and many people also use /home partition as a third one.

If the partition you created is ntfs, you need to delete it and leave that space as unallocated. With the ubuntu installer you will create all the partitions you want.

If the existing partition is linux, and you want to use only root partition, you can start the installer and use the manual method. Then select the partition, and click the Change button.

That will allow you to select the filesystem you want to use, and the mount point. Note that formatting it will delete everything on that partition.

Come to think of it, you can do the above even if the partition is ntfs. You can change the filesystem and format it as ext4 with the installer.

---

### Post by mysteron75 on 2012-04-19
i ran the script again and here are the results

                  Boot Info Script 0.61      [1 April 2012]


============================= Boot Info Summary: ===============================

 => Windows is installed in the MBR of /dev/sda.
 => Windows is installed in the MBR of /dev/sdb.

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
    Boot files:        /bootmgr /Boot/BCD /Windows/System32/winload.exe

sdb1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sdb2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info: 

sdb5: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Ubuntu precise (development 
                       branch)
    Boot files:        /boot/grub/grub.cfg /etc/fstab

sdb6: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info: 

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 300.1 GB, 300069052416 bytes
255 heads, 63 sectors/track, 36481 cylinders, total 586072368 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *          2,048       206,847       204,800   7 NTFS / exFAT / HPFS
/dev/sda2             206,848   586,070,015   585,863,168   7 NTFS / exFAT / HPFS


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1               2,048 1,640,847,844 1,640,845,797   7 NTFS / exFAT / HPFS
/dev/sdb2       1,640,849,406 1,953,523,711   312,674,306   5 Extended
/dev/sdb5       1,640,849,408 1,920,018,431   279,169,024  83 Linux
/dev/sdb6       1,920,020,480 1,953,523,711    33,503,232  82 Linux swap / Solaris


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        5E7CDAD17CDAA357                       ntfs       System Reserved
/dev/sda2        9868E45668E434A2                       ntfs       
/dev/sdb1        F4CCC20FCCC1CC54                       ntfs       Storage
/dev/sdb5        54fc1e4a-1026-4c67-9726-53af23ab8c20   ext4       
/dev/sdb6        428324c1-5826-41b1-af5a-685c5a0332d9   swap       
/dev/sr1                                                iso9660    Ubuntu 12.04 LTS amd64

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sda2        /media/9868E45668E434A2  fuseblk    (rw,nosuid,nodev,allow_other,default_permissions,blksize=4096)
/dev/sr1         /cdrom                   iso9660    (ro,noatime)


=========================== sdb5/boot/grub/grub.cfg: ===========================

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
set root='(hd1,msdos5)'
search --no-floppy --fs-uuid --set=root 54fc1e4a-1026-4c67-9726-53af23ab8c20
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
  insmod part_msdos
  insmod ext2
  set root='(hd1,msdos5)'
  search --no-floppy --fs-uuid --set=root 54fc1e4a-1026-4c67-9726-53af23ab8c20
  set locale_dir=($root)/boot/grub/locale
  set lang=en_US
  insmod gettext
fi
terminal_output gfxterm
if [ "${recordfail}" = 1 ]; then
  set timeout=5
else
  set timeout=5
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
if background_color 44,0,30; then
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
    set root='(hd1,msdos5)'
    search --no-floppy --fs-uuid --set=root 54fc1e4a-1026-4c67-9726-53af23ab8c20
    linux    /boot/vmlinuz-3.2.0-23-generic root=UUID=54fc1e4a-1026-4c67-9726-53af23ab8c20 ro   quiet splash $vt_handoff
    initrd    /boot/initrd.img-3.2.0-23-generic
}
menuentry 'Ubuntu, with Linux 3.2.0-23-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos5)'
    search --no-floppy --fs-uuid --set=root 54fc1e4a-1026-4c67-9726-53af23ab8c20
    echo    'Loading Linux 3.2.0-23-generic ...'
    linux    /boot/vmlinuz-3.2.0-23-generic root=UUID=54fc1e4a-1026-4c67-9726-53af23ab8c20 ro recovery nomodeset 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-3.2.0-23-generic
}
submenu "Previous Linux versions" {
menuentry 'Ubuntu, with Linux 3.2.0-20-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    gfxmode $linux_gfx_mode
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos5)'
    search --no-floppy --fs-uuid --set=root 54fc1e4a-1026-4c67-9726-53af23ab8c20
    linux    /boot/vmlinuz-3.2.0-20-generic root=UUID=54fc1e4a-1026-4c67-9726-53af23ab8c20 ro   quiet splash $vt_handoff
    initrd    /boot/initrd.img-3.2.0-20-generic
}
menuentry 'Ubuntu, with Linux 3.2.0-20-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos5)'
    search --no-floppy --fs-uuid --set=root 54fc1e4a-1026-4c67-9726-53af23ab8c20
    echo    'Loading Linux 3.2.0-20-generic ...'
    linux    /boot/vmlinuz-3.2.0-20-generic root=UUID=54fc1e4a-1026-4c67-9726-53af23ab8c20 ro recovery nomodeset 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-3.2.0-20-generic
}
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set=root 5E7CDAD17CDAA357
    chainloader +1
}
menuentry "Windows 7 (loader) (on /dev/sda2)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos2)'
    search --no-floppy --fs-uuid --set=root 9868E45668E434A2
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

=============================== sdb5/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdb5 during installation
UUID=54fc1e4a-1026-4c67-9726-53af23ab8c20 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdb6 during installation
UUID=428324c1-5826-41b1-af5a-685c5a0332d9 none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sdb5: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

               =                boot/grub/grub.cfg                             1
               =                boot/initrd.img-3.2.0-20-generic               2
               =                boot/initrd.img-3.2.0-23-generic               2
               =                boot/vmlinuz-3.2.0-20-generic                  1
               =                boot/vmlinuz-3.2.0-23-generic                  1
               =                initrd.img.old                                 2
               =                vmlinuz                                        1
               =                vmlinuz.old                                    1

=============================== StdErr Messages: ===============================

awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in

---

### Post by darkod on 2012-04-20
Grub2 didn't install correctly, but not only on the MBR. The main file core.img is missing on /dev/sdb5. You better remove all of grub2 and reinstall again. You can do that by booting into live mode with the cd and entering your installation with chroot.
To prepare and enter with chroot:
```
sudo mount /dev/sdb5 /mnt
sudo mount --bind /proc /mnt/proc
sudo mount --bind /dev /mnt/dev
sudo mount --bind /sys /mnt/sys
sudo chroot /mnt
```

Now you are inside the installation with root permissions. Remove grub2 completely and reinstall. Recreate the config files:
```
apt-get remove --purge grub-pc grub-common
apt-get install grub-pc
grub-mkconfig
update-grub
grub-install /dev/sdb
```

That should do it. Exit the chroot and unmount everything:
```
exit
sudo umount /mnt/sys
sudo umount /mnt/dev
sudo umount /mnt/proc
sudo umount /mnt
```

Restart and set in BIOS to boot from the second disk, /dev/sdb. The first disk will continue to have windows bootloader and can boot your windows directly but not ubuntu. Grub2 will be on the second disk and can boot both.

See if that sorts it out.

---

### Post by mysteron75 on 2012-04-23
I am up and running. I only made one change to what you posted and installed grub on /dev/sba so i did have to change boot order. Thanks for the help. I learned something

---

