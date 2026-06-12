---
title: "Problems with Grub and maybe partition after installing 11.10"
date: 2011-11-28
forum: Installation &amp; Upgrades
---

### Post by Omegus on 2011-11-28
Hey guys and gals,

 I did a fresh install for Ubuntu 11.10 and  replaced 10.10. So anyways I installed and during the installation I had  the critical fail message come up about could not install the grub to  /dev/sda. Anyways I looked the problem up and found out it was my live  CD so I made my Live USB and installed not a problem. But after I  restarted I got this message:

Grub file not found
 Grub rescue

Now I got this when i changed the bios so that the hard drives would boot first. I have 2 500 gb hd's .  

Now  one reasoning I think this was a indicator of a problem was when I  manually partitioned my HD was set to this /dev/mapper  and not /dev/sda  . do you think this may have led to this error? Also I check out the  boot repair but that didn't work. ill post my 
[COLOR=red]sudo fdisk -l [COLOR=Black]in 5 mins.

any help with this would be much apprechiated
[/COLOR][/COLOR]

---

### Post by Rubi1200 on 2011-11-28
Hi,
please post the results of the boot info script as it will give us a better overview of what is going on.

There is a link at the bottom of my post with instructions.

Thanks.

---

### Post by Omegus on 2011-11-28
here is my sudo fdisk -l

```
ubuntu@ubuntu:~$ sudo fdisk -l
Warning: ignoring extra data in partition table 5
Warning: ignoring extra data in partition table 5
Warning: ignoring extra data in partition table 5
Warning: invalid flag 0x5f38 of partition table 5 will be corrected by w(rite)

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00079f72

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1             256     2148607     1074176   83  Linux
/dev/sda2         2148862  1953283583   975567361    5  Extended
/dev/sda5   ?  4178481367  7582521586  1702020110    2  XENIX root

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0009a466

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb2       810719232   976771071    83025920    5  Extended
/dev/sdb5       925294592   964898815    19802112   82  Linux swap / Solaris

Disk /dev/mapper/pdc_cajdjcbgd: 1000.1 GB, 1000081457152 bytes
255 heads, 63 sectors/track, 121586 cylinders, total 1953284096 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 65536 bytes / 131072 bytes
Disk identifier: 0x00079f72

                    Device Boot      Start         End      Blocks   Id  System
/dev/mapper/pdc_cajdjcbgd1             256     2148607     1074176   83  Linux
/dev/mapper/pdc_cajdjcbgd2         2148862  1953283583   975567361    5  Extended
Partition 2 does not start on physical sector boundary.
/dev/mapper/pdc_cajdjcbgd5         2148864    12109567     4980352   82  Linux swap / Solaris
/dev/mapper/pdc_cajdjcbgd6        12109824   600000255   293945216   83  Linux
/dev/mapper/pdc_cajdjcbgd7       600000512  1953283583   676641536   83  Linux

Disk /dev/mapper/pdc_cajdjcbgd1: 1099 MB, 1099956224 bytes
255 heads, 63 sectors/track, 133 cylinders, total 2148352 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 65536 bytes / 131072 bytes
Disk identifier: 0x00000000

Disk /dev/mapper/pdc_cajdjcbgd1 doesn't contain a valid partition table

Disk /dev/mapper/pdc_cajdjcbgd5: 5099 MB, 5099880448 bytes
255 heads, 63 sectors/track, 620 cylinders, total 9960704 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 65536 bytes / 131072 bytes
Disk identifier: 0x00000000

Disk /dev/mapper/pdc_cajdjcbgd5 doesn't contain a valid partition table

Disk /dev/mapper/pdc_cajdjcbgd6: 301.0 GB, 300999901184 bytes
255 heads, 63 sectors/track, 36594 cylinders, total 587890432 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 65536 bytes / 131072 bytes
Disk identifier: 0x00000000

Disk /dev/mapper/pdc_cajdjcbgd6 doesn't contain a valid partition table

Disk /dev/mapper/pdc_cajdjcbgd7: 692.9 GB, 692880932864 bytes
255 heads, 63 sectors/track, 84237 cylinders, total 1353283072 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 65536 bytes / 131072 bytes
Disk identifier: 0x00000000

Disk /dev/mapper/pdc_cajdjcbgd7 doesn't contain a valid partition table


```


and here is my from the results from the "results file"

```
                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => No boot loader is installed in the MBR of /dev/sdb.
 => Grub2 (v1.99) is installed in the MBR of /dev/mapper/pdc_cajdjcbgd and 
    looks at sector 1 of the same hard drive for core.img. core.img is at this 
    location and looks for  on this drive.

sdb2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sdb5: __________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:   mount: unknown filesystem type ''

pdc_cajdjcbgd1: ________________________________________________________________

    File system:       ext2
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files:        /grub/grub.cfg /grub/core.img

pdc_cajdjcbgd2: ________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

pdc_cajdjcbgd5: ________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

pdc_cajdjcbgd6: ________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.10
    Boot files:        /etc/fstab

pdc_cajdjcbgd7: ________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files:        

============================ Drive/Partition Info: =============================

Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb2         810,719,232   976,771,071   166,051,840   5 Extended
/dev/sdb5         925,294,592   964,898,815    39,604,224  82 Linux swap / Solaris


Drive: pdc_cajdjcbgd _____________________________________________________________________

Disk /dev/mapper/pdc_cajdjcbgd: 1000.1 GB, 1000081457152 bytes
255 heads, 63 sectors/track, 121586 cylinders, total 1953284096 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/mapper/pdc_cajdjcbgd1                256     2,148,607     2,148,352  83 Linux
/dev/mapper/pdc_cajdjcbgd2          2,148,862 1,953,283,583 1,951,134,722   5 Extended
/dev/mapper/pdc_cajdjcbgd5          2,148,864    12,109,567     9,960,704  82 Linux swap / Solaris
/dev/mapper/pdc_cajdjcbgd6         12,109,824   600,000,255   587,890,432  83 Linux
/dev/mapper/pdc_cajdjcbgd7        600,000,512 1,953,283,583 1,353,283,072  83 Linux


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/mapper/pdc_cajdjcbgd1 e0f2f483-dffd-46a8-8f88-2546632590bf   ext2       
/dev/mapper/pdc_cajdjcbgd5 fc83a968-1cbe-4feb-a810-b09eab28820f   swap       
/dev/mapper/pdc_cajdjcbgd6 6b3a28ea-c080-4dc9-8853-af38b73aba47   ext4       
/dev/mapper/pdc_cajdjcbgd7 2723b1a7-0214-47fd-8f7e-c55309fbe7f0   ext4       
/dev/sda                                                promise_fasttrack_raid_member 

========================= "ls -R /dev/mapper/" output: =========================

/dev/mapper:
control
pdc_cajdjcbgd
pdc_cajdjcbgd1
pdc_cajdjcbgd5
pdc_cajdjcbgd6
pdc_cajdjcbgd7

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)


======================== pdc_cajdjcbgd1/grub/grub.cfg: =========================

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
set root='(hd3,msdos6)'
search --no-floppy --fs-uuid --set=root 6b3a28ea-c080-4dc9-8853-af38b73aba47
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
  insmod part_msdos
  insmod ext2
  set root='(hd3,msdos1)'
  search --no-floppy --fs-uuid --set=root e0f2f483-dffd-46a8-8f88-2546632590bf
  set locale_dir=($root)/grub/locale
  set lang=en_CA
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
menuentry 'Ubuntu, with Linux 3.0.0-12-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd3,msdos1)'
    search --no-floppy --fs-uuid --set=root e0f2f483-dffd-46a8-8f88-2546632590bf
    linux    /vmlinuz-3.0.0-12-generic root=UUID=6b3a28ea-c080-4dc9-8853-af38b73aba47 ro   quiet splash vt.handoff=7
    initrd    /initrd.img-3.0.0-12-generic
}
menuentry 'Ubuntu, with Linux 3.0.0-12-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd3,msdos1)'
    search --no-floppy --fs-uuid --set=root e0f2f483-dffd-46a8-8f88-2546632590bf
    echo    'Loading Linux 3.0.0-12-generic ...'
    linux    /vmlinuz-3.0.0-12-generic root=UUID=6b3a28ea-c080-4dc9-8853-af38b73aba47 ro recovery nomodeset 
    echo    'Loading initial ramdisk ...'
    initrd    /initrd.img-3.0.0-12-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(hd3,msdos1)'
    search --no-floppy --fs-uuid --set=root e0f2f483-dffd-46a8-8f88-2546632590bf
    linux16    /memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd3,msdos1)'
    search --no-floppy --fs-uuid --set=root e0f2f483-dffd-46a8-8f88-2546632590bf
    linux16    /memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
if [ "x${timeout}" != "x-1" ]; then
  if keystatus; then
    if keystatus --shift; then
      set timeout=-1
    else
      set timeout=0
    fi
  else
    if sleep --interruptible 3 ; then
      set timeout=0
    fi
  fi
fi
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

============== pdc_cajdjcbgd1: Location of files loaded by Grub: ===============

           GiB - GB             File                                 Fragment(s)

               =                grub/core.img                                  2
               =                grub/grub.cfg                                  1
               =                initrd.img-3.0.0-12-generic                   57
               =                vmlinuz-3.0.0-12-generic                      19

========================== pdc_cajdjcbgd6/etc/fstab: ===========================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/mapper/pdc_cajdjcbgd6 /               ext4    errors=remount-ro 0       1
/dev/mapper/pdc_cajdjcbgd1 /boot           ext2    defaults        0       2
/dev/mapper/pdc_cajdjcbgd7 /home           ext4    defaults        0       2
/dev/mapper/pdc_cajdjcbgd5 none            swap    sw              0       0
--------------------------------------------------------------------------------

======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on sdb2


Unknown BootLoader on sdb5


Unknown BootLoader on pdc_cajdjcbgd2



========= Devices which don't seem to have a corresponding hard drive: =========

sdc sdd sde sdf 

=============================== StdErr Messages: ===============================

unlzma: Decoder error
hexdump: /dev/sdb2: No such file or directory
hexdump: /dev/sdb2: No such file or directory
hexdump: /dev/sdb5: No such file or directory
hexdump: /dev/sdb5: No such file or directory
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
hexdump: /dev/mapper/pdc_cajdjcbgd2: No such file or directory
hexdump: /dev/mapper/pdc_cajdjcbgd2: No such file or directory

```


hope this helps.

---

### Post by darkod on 2011-11-28
Are you running fakeraid or software raid? /dev/mapper/etc is a raid device and seems to be RAID0 made up from both your disks.

For installing with RAID the recommendation is to use the alternate install cd, not the standard desktop cd.

The recommendation is exactly for what happened to you. Grub often doesn't install correctly if using the standard cd for raid.

If you are not using raid you should remove the meta data, but it seems you are using it.

---

### Post by Omegus on 2011-11-28
It is a raid0. as for the rest not a clue what you mean. I'm in the infantry so you need to speak slower I am trying to learn this stuff.

---

### Post by darkod on 2011-11-28
OK.
1. Forget about the ubuntu cd you have for the moment.
2. Go here: [http://releases.ubuntu.com/oneiric/](http://releases.ubuntu.com/oneiric/) look carefully in all the download options and download the alternate image, 32bit or 64bit to your liking.
3. Boot the computer with the alternate cd and when it asks you if you want to activate the raid array it will detect, say Yes.
4. Then simply continue with the install. I recommend the manual method for partitioning. You might need to delete some partitions you made during this failed install. If not sure about anything, ask questions first. :)

---

### Post by Omegus on 2011-11-28
true enough. ill try this out right away and let you know the results. thanks.

---

### Post by Omegus on 2011-11-28
Ok its asking me where to install the grub do i install it to the /boot partition or do I do something else? because I tried installing it to one of the examples /dev/sda but mine says /dev/mapper .

---

### Post by Quackers on 2011-11-28
Install grub to the /dev/mapper that usually doesn't have a number at the end of it (in your case I believe it's /dev/mapper/pdc_cajdjcbgd). This is effectively the MBR of the raid array. Not to a partition.

---

### Post by Omegus on 2011-11-28
now it comes on to a black screen and freezes . I can edit what bios go in what order for booting but i dont get that other command now it was shift + F10 for options. 

when I put the primary HD first for boot i get that black screen and when i do the other I get the Grub rescue.

  I went into the config which it is DEL key on booting and i had sen my raid was set to IDE is it spose to be there or on Raid?


I'm starting to think I screwed up my computer.

---

### Post by Quackers on 2011-11-28
If you are running a raid array the bios setting should be on raid.
However, by trying to write directly to /dev/sda (installing grub) it is possible that the raid array has been damaged, though not a certainty.
Is there any mention of a degraded or failed raid array in your bios? You may need to press a key combination during boot to see the raid configuration.

If you can, set the bios back to raid and see what happens.

---

### Post by Omegus on 2011-11-29
yup that did it I set the raid bios back from IDE to Raid rebooted and BAM! working now thank guys so much. I have now learned even more about my computer. Another tool for the tool box.

---

### Post by Quackers on 2011-11-29
Aha! Nice one! :-)
Enjoy Ubuntu-ing

---

### Post by Rubi1200 on 2011-11-29
Glad you got things worked out and can enjoy Ubuntu :-)

Great support too from darkod and Quackers!

Please mark this thread Solved using the Thread Tools near the top of the page.

---

