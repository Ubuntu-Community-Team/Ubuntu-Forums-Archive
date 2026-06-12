---
title: "Need to fix Grub - help needed"
date: 2012-01-14
forum: Installation &amp; Upgrades
---

### Post by biosol on 2012-01-14
Hi,
I had ubuntu 64 11.10 with 3 swap files from previous installs I guess.  Another post, recommended to delete any 2 of the swap partitions and ubuntu would use the other one.  I used gparted to delete 2 of the 3 swap partitions and then resized the home partition to reclaim the (now) unused space.

Now I get this error:
error: no such partition.
grub rescue> _

This is a dual boot setup. Win7/Ubuntu.

Please advise how to recover the boot/grub

Thanks!

---

### Post by darkod on 2012-01-14
Follow the link in my signature to run the boot info script. Post the results as explained there. It will show more details.

I think it's not exactly true that it will use any swap file, you would need to make a change in /etc/fstab.

---

### Post by biosol on 2012-01-14
Thank you for your help.  I have the Ubuntu 11.10 64-bit install CD.  So I will boot to it and get the info you requested.  One question.  It's possible to download and install/run software on a LiveCD system?  How?

---

### Post by darkod on 2012-01-14
Depending what software you are asking about.
The script can be run from live mode, in case the internet is working. For wired connections it works almost always.
So just download the script, run it, and post the content of the results file, included inside [ code ] text [ / code ] tags to make it readable better.

---

### Post by biosol on 2012-01-14
So far I have this info.  Will try your script.

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1            2048    28155903    14076928   27  Hidden NTFS WinRE
/dev/sda2   *    28155904    28360703      102400    7  HPFS/NTFS/exFAT
/dev/sda3        28360704   162578431    67108864    7  HPFS/NTFS/exFAT
/dev/sda4       162580478   976771071   407095297    f  W95 Ext'd (LBA)
/dev/sda5       162580480   784179246   310799383+   7  HPFS/NTFS/exFAT
/dev/sda6       960038912   976771071     8366080   82  Linux swap / Solaris
/dev/sda7       784181248   960036863    87927808   83  Linux

Partition table entries are not in disk order

---

### Post by biosol on 2012-01-14
Ok, I have the boot_into_script.sh in my Documents folder and it is the pwd.  I tried running with ./boot_into_script.sh but get a permission denied.  How do I run it?

---

### Post by darkod on 2012-01-14
You need sudo bash in front. If it's in Documents, it would be:

sudo bash ~/Documents/boot_info_script*.sh

---

### Post by biosol on 2012-01-14
Thanks.

ubuntu@ubuntu:~/Documents$ sudo bash ~/Documents/boot_info_script*.sh

boot_info_script version: 0.60        [17 May 2011]


"gawk" could not be found, using "busybox awk" instead.
This may lead to unreliable results.

Identifying MBRs...
Computing Partition Table of /dev/sda...
Searching sda1 for information... 
Searching sda2 for information... 
Searching sda3 for information... 
Searching sda4 for information... 
Searching sda5 for information... 
Searching sda6 for information... 
Searching sda7 for information... 

Finished. The results are in the file "RESULTS.txt"
located in "/home/ubuntu/Documents/".

---

### Post by biosol on 2012-01-14
Sorry, here's the info.  The forum turned some charaters into smile faces.  I had to delete 2 of them to post.

                  ```
Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for  on this drive.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /boot/bcd

sda2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /Boot/BCD

sda3: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files:        /Windows/System32/winload.exe

sda4: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   According to the info in the boot sector, sda5 starts 
                       at sector 2048.
    Operating System:  
    Boot files:        

sda6: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda7: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.10
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1               2,048    28,155,903    28,153,856  27 Hidden NTFS (Recovery Environment)
/dev/sda2    *     28,155,904    28,360,703       204,800   7 NTFS / exFAT / HPFS
/dev/sda3          28,360,704   162,578,431   134,217,728   7 NTFS / exFAT / HPFS
/dev/sda4         162,580,478   976,771,071   814,190,594   f W95 Extended (LBA)
/dev/sda5         162,580,480   784,179,246   621,598,767   7 NTFS / exFAT / HPFS
/dev/sda6         960,038,912   976,771,071    16,732,160  82 Linux swap / Solaris
/dev/sda7         784,181,248   960,036,863   175,855,616  83 Linux


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        6CDE92DEDE929FBE                       ntfs       Recovery
/dev/sda2        B098935C98932040                       ntfs       System Reserved
/dev/sda3        AE5E961D5E95DE81                       ntfs       
/dev/sda5        9C0699110698ED90                       ntfs       
/dev/sda6        7e6758d3-c246-4fc0-bbd4-a18db36ee430   swap       
/dev/sda7        1c8179bb-2b3a-44b9-b345-8a99688f8154   ext4       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)


=========================== sda7/boot/grub/grub.cfg: ===========================

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
  insmod vbe
  insmod vga
  insmod video_bochs
  insmod video_cirrus
}

insmod part_msdos
insmod ext2
set root='(hd0,msdos'
search --no-floppy --fs-uuid --set=root 1c8179bb-2b3a-44b9-b345-8a99688f8154
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
  insmod part_msdos
  insmod ext2
  set root='(hd0,msdos'
  search --no-floppy --fs-uuid --set=root 1c8179bb-2b3a-44b9-b345-8a99688f8154
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
if background_color 44,0,30; then
  clear
fi
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
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
menuentry 'Ubuntu, with Linux 3.0.0-14-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos8)'
    search --no-floppy --fs-uuid --set=root 1c8179bb-2b3a-44b9-b345-8a99688f8154
    linux    /boot/vmlinuz-3.0.0-14-generic root=UUID=1c8179bb-2b3a-44b9-b345-8a99688f8154 ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-3.0.0-14-generic
}
menuentry 'Ubuntu, with Linux 3.0.0-14-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos8)'
    search --no-floppy --fs-uuid --set=root 1c8179bb-2b3a-44b9-b345-8a99688f8154
    echo    'Loading Linux 3.0.0-14-generic ...'
    linux    /boot/vmlinuz-3.0.0-14-generic root=UUID=1c8179bb-2b3a-44b9-b345-8a99688f8154 ro recovery nomodeset 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-3.0.0-14-generic
}
submenu "Previous Linux versions" {
menuentry 'Ubuntu, with Linux 3.0.0-13-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos8)'
    search --no-floppy --fs-uuid --set=root 1c8179bb-2b3a-44b9-b345-8a99688f8154
    linux    /boot/vmlinuz-3.0.0-13-generic root=UUID=1c8179bb-2b3a-44b9-b345-8a99688f8154 ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-3.0.0-13-generic
}
menuentry 'Ubuntu, with Linux 3.0.0-13-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos8)'
    search --no-floppy --fs-uuid --set=root 1c8179bb-2b3a-44b9-b345-8a99688f8154
    echo    'Loading Linux 3.0.0-13-generic ...'
    linux    /boot/vmlinuz-3.0.0-13-generic root=UUID=1c8179bb-2b3a-44b9-b345-8a99688f8154 ro recovery nomodeset 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-3.0.0-13-generic
}
menuentry 'Ubuntu, with Linux 3.0.0-12-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos8)'
    search --no-floppy --fs-uuid --set=root 1c8179bb-2b3a-44b9-b345-8a99688f8154
    linux    /boot/vmlinuz-3.0.0-12-generic root=UUID=1c8179bb-2b3a-44b9-b345-8a99688f8154 ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-3.0.0-12-generic
}
menuentry 'Ubuntu, with Linux 3.0.0-12-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos8)'
    search --no-floppy --fs-uuid --set=root 1c8179bb-2b3a-44b9-b345-8a99688f8154
    echo    'Loading Linux 3.0.0-12-generic ...'
    linux    /boot/vmlinuz-3.0.0-12-generic root=UUID=1c8179bb-2b3a-44b9-b345-8a99688f8154 ro recovery nomodeset 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-3.0.0-12-generic
}
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos8)'
    search --no-floppy --fs-uuid --set=root 1c8179bb-2b3a-44b9-b345-8a99688f8154
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos8)'
    search --no-floppy --fs-uuid --set=root 1c8179bb-2b3a-44b9-b345-8a99688f8154
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows Recovery Environment (loader) (on /dev/sda1)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set=root 6CDE92DEDE929FBE
    drivemap -s (hd0) ${root}
    chainloader +1
}
menuentry "Windows 7 (loader) (on /dev/sda2)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos2)'
    search --no-floppy --fs-uuid --set=root B098935C98932040
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

=============================== sda7/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda8 during installation
UUID=1c8179bb-2b3a-44b9-b345-8a99688f8154 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda9 during installation
UUID=d6b71a9a-9563-44d5-8339-e4b534fa0b21 none            swap    sw              0       0
#
# To mount network drives

//10.4.1.126/users/rheppe /media/Y cifs credentials=/home/robert/.smbcredentials,workgroup=CUDANET,nounix,user,noexec,noauto 0 0
//10.4.1.126/corp /media/Z cifs credentials=/home/robert/.smbcredentials,workgroup=CUDANET,nounix,user,noexec,noauto 0 0

--------------------------------------------------------------------------------

=================== sda7: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

               =                boot/grub/core.img                             1
               =                boot/grub/grub.cfg                             1
               =                boot/initrd.img-3.0.0-12-generic               2
               =                boot/initrd.img-3.0.0-13-generic               1
               =                boot/initrd.img-3.0.0-14-generic               2
               =                boot/vmlinuz-3.0.0-12-generic                  1
               =                boot/vmlinuz-3.0.0-13-generic                  1
               =                boot/vmlinuz-3.0.0-14-generic                  1
               =                vmlinuz                                        1
               =                vmlinuz.old                                    1

======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on sda4

00000000  ee ff 7e 7b c8 e2 1f 1a  9e 7a 1d 19 9b 06 ff ff  |..~{.....z......|
00000010  ff 00 ff ff ff 00 11 0f  c9 59 81 80 dd ff ef ee  |.........Y......|
00000020  f9 ff eb eb f1 ff f2 f2  f9 ff f2 f2 f8 ff f0 f0  |................|
00000030  f7 ff 59 57 ab ff eb eb  f5 ff e9 e9 f4 ff e9 e9  |..YW............|
00000040  f4 ff d5 d4 ee ff 7c 79  c5 e5 1c 19 9d 5c ff ff  |......|y.....\..|
00000050  ff 00 10 0f d4 17 4f 4d  d9 ed e1 e1 f4 ff f4 f4  |......OM........|
00000060  f9 ff 4d 4b af ff f4 f4  fa ff f5 f5 fa ff f3 f3  |..MK............|
00000070  f9 ff 48 46 a0 ff ef ef  f7 ff 7d 7c bb ff 90 8f  |..HF......}|....|
00000080  c1 ff e9 e9 f4 ff d8 d8  ef ff 4f 4d b4 df 1d 1a  |..........OM....|
00000090  9d 1a 0f 0c db 57 a1 a0  ed ff f5 f5 fa ff f6 f6  |.....W..........|
000000a0  fa ff 22 1e bd ff 4c 49  bf ff 4e 4b b9 ff 89 87  |.."...LI..NK....|
000000b0  cc ff 4c 4b a9 ff c5 c5  d5 ff 81 80 bd ff 2f 2d  |..LK........../-|
000000c0  9c ff ea ea f4 ff e9 e9  f4 ff 93 90 d4 de 1c 19  |................|
000000d0  9e 5d 0b 0a e0 a2 dd dc  f6 ff f8 f8 fb ff f9 f9  |.]..............|
000000e0  fc ff 54 50 cc ff e4 e4  e6 ff ec ec ed ff f5 f5  |..TP............|
000000f0  f6 ff 50 4d bc ff e6 e6  e9 ff ed ec f1 ff 4a 49  |..PM..........JI|
00000100  a8 ff da da e4 ff e1 e1  eb ff c9 c8 eb ff 1c 19  |................|
00000110  a1 a9 0a 09 e9 e3 f7 f7  fc ff fb fb fd ff fc fc  |................|
00000120  fe ff 55 50 cf ff e3 e3  e4 ff e5 e5 e6 ff ef ef  |..UP............|
00000130  ef ff 4f 4c c5 ff e7 e7  e9 ff f0 ef f3 ff 4c 4b  |..OL..........LK|
00000140  ac ff dd dd e5 ff e2 e2  ec ff e0 e0 ef ff 1b 18  |................|
00000150  a5 e7 07 06 ef e3 fa fa  fd ff fe fe ff ff fe fe  |................|
00000160  ff ff 26 22 c7 ff 51 4e  c9 ff 52 4e ca ff 8f 8c  |..&"..QN..RN....|
00000170  dc ff 54 50 cb ff eb eb  ec ff f2 f2 f5 ff 4f 4d  |..TP..........OM|
00000180  b0 ff e0 e0 e6 ff e4 e4  ec ff e2 e2 f1 ff 1b 19  |................|
00000190  a9 e7 05 05 f3 9e e8 e9  fd ff ff ff ff ff ff ff  |................|
000001a0  ff ff 57 53 d3 ff e9 e9  e9 ff eb eb eb ff f4 f4  |..WS............|
000001b0  f4 ff 54 50 cc ff e9 e9  ea ff ed ed ef ff 00 fe  |..TP............|
000001c0  ff ff 07 fe ff ff 02 00  00 00 2f d8 0c 25 00 fe  |........../..%..|
000001d0  ff ff 05 fe ff ff 02 38  88 2f 00 58 ff 00 00 00  |.......8./.X....|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


=============================== StdErr Messages: ===============================

unlzma: Decoder error
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
```

---

### Post by darkod on 2012-01-14
You need to open the results.txt and post the content here. The results are inside the file.

After you paste the text, while still selected, try hitting the # button above, in the toolbar when creating the post. It will make the code tags for you.

---

### Post by darkod on 2012-01-14
It looks fine, except the info that sda5 seems to start at 2048 according to the information in the boot sector.

Lets try the easy way first, reinstalling grub2. Boot into live mode and in terminal execute:

```
sudo mount /dev/sda7 /mnt
sudo grub-install --root-directory=/mnt /dev/sda
```

Reboot and see if that helped.

---

### Post by biosol on 2012-01-14
Ok, updated.  I guess doing that would have removed the smile faces.  I did delete two out so let me know if I should repost the info.

---

### Post by biosol on 2012-01-14
ubuntu@ubuntu:~$ sudo mount /dev/sda7 /mnt
ubuntu@ubuntu:~$ sudo grub-install --root-directory=/mnt /dev/sda
Installation finished. No error reported.

---

### Post by darkod on 2012-01-14
> **biosol said:**
> ubuntu@ubuntu:~$ sudo mount /dev/sda7 /mnt
ubuntu@ubuntu:~$ sudo grub-install --root-directory=/mnt /dev/sda
Installation finished. No error reported.

? Did you reboot the computer? Still the same grub error?

---

### Post by biosol on 2012-01-14
It worked!!  Thanks so much.

Both OS's booting normally.

When I deleted the other two swap partitions they were sda 8 and 9.  Maybe I should have deleted sda 7 and 8 as 9 might have been from the latest install?

I will change this to resolved in hopes it helps others.

---

### Post by darkod on 2012-01-14
Glad it worked. Enjoy it. :)

---

