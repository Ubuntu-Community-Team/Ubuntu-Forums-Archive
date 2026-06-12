---
title: "Ubuntu wont load"
date: 2011-08-31
forum: Installation &amp; Upgrades
---

### Post by angus1964 on 2011-08-31
I have installed ubuntu on a laptop alongside windows 7, the installation went fine but when i boot up i get the option for either, windows loads ok, ubuntu loads ask for login then goes to a blue (windows) page and goes no further, Can anyone offer any advise?

---

### Post by Sef on 2011-08-31
1) How did you install the dual boot?

2) Use a live CD/USB and then go to the terminal and copy and paste this command: 

```
sudo fdisk -l
```

copy and paste the results here. That will show us the partitions.

3) How did the Live CD/USB work? Any problems?

---

### Post by angus1964 on 2011-09-01
Thanks for quick reply, i was able to run ubuntu in recovery mode with no problems so i assume the partitions are ok. I ran the updates but still found the same problem.

---

### Post by Hakunka-Matata on 2011-09-01
Welcome to the forum:

It's good you get a boot menu, and you're able to run the recovery kernel, but without more information it's hard to suggest anything.  Open a Terminal window (**Applications>Terminal),** type in the ```
sudo fdisk -l
``` command as [COLOR=Red]Sef[/COLOR] requested, and post results between code tags, (click # icon).  After that download and run boot_info_script program listed in my signature.  Post the ENTIRE contents of the RESULTS.txt file between code tags as well, that will allow people to see what is happening during your computers boot process.

---

### Post by angus1964 on 2011-09-02
I ran the fdisk command and got the following.

#
  Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1          13      102400   de  Dell Utility
Partition 1 does not end on cylinder boundary.
/dev/sda2   *          13        1926    15360000    7  HPFS/NTFS
/dev/sda3            1926       48459   373782651+   7  HPFS/NTFS
/dev/sda4           48460       60802    99138561    5  Extended
/dev/sda5           48460       60313    95211520   83  Linux
/dev/sda6           60313       60802     3926016   82  Linux swap / Solaris
#

Have done several searches but unable to fin results.txt.

---

### Post by Hakunka-Matata on 2011-09-02
> **angus1964 said:**
> I ran the fdisk command and got the following.

#
  Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1          13      102400   de  Dell Utility
Partition 1 does not end on cylinder boundary.
/dev/sda2   *          13        1926    15360000    7  HPFS/NTFS
/dev/sda3            1926       48459   373782651+   7  HPFS/NTFS
/dev/sda4           48460       60802    99138561    5  Extended
/dev/sda5           48460       60313    95211520   83  Linux
/dev/sda6           60313       60802     3926016   82  Linux swap / Solaris
#

Have done several searches but unable to fin results.txt.

Good, 
RESULTS.txt file should be in the same directory that the boot_info_script.sh is.  Maybe /Home/"yourusername"/Dowloads
Did boot_info_script run OK?

---

### Post by angus1964 on 2011-09-02
Thank you for you quick reply, i hadn't fully understood your post( trying to do things inbetween looking after two young kids), have now read it and understood i will run it later and post the results, linux in failsafe mode runs incredibly slow so it may take me a while.

Many Thanks

---

### Post by Hakunka-Matata on 2011-09-02
Can you run off your liveCD?  That should work quite fast?

---

### Post by angus1964 on 2011-09-02
even the live cd takes ages to load and is still pretty slow when loaded

---

### Post by angus1964 on 2011-09-02
Ran t     Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (,msdos5)/boot/grub on this drive.

sda1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  Dell Utility: FAT16
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /DELLBIO.BIN /DELLRMK.BIN /COMMAND.COM

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
    Boot files:        /bootmgr /Boot/BCD /Windows/System32/winload.exe

sda4: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.04
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda6: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1               2,048       206,847       204,800  de Dell Utility
/dev/sda2    *        206,848    30,926,847    30,720,000   7 NTFS / exFAT / HPFS
/dev/sda3          30,926,848   778,492,150   747,565,303   7 NTFS / exFAT / HPFS
/dev/sda4         778,493,950   976,771,071   198,277,122   5 Extended
/dev/sda5         778,493,952   968,916,991   190,423,040  83 Linux
/dev/sda6         968,919,040   976,771,071     7,852,032  82 Linux swap / Solaris


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/sda1        3030-3030                              vfat       DELLUTILITY
/dev/sda2        CC70378A703779F2                       ntfs       Recovery
/dev/sda3        AC7C4EC27C4E86D4                       ntfs       OS
/dev/sda5        9113ff04-ab64-4ac9-9fa0-74ad45a3ac8c   ext4       
/dev/sda6        3ad2b8ac-6d5f-44bb-94df-b21e3566f5a9   swap       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sda3        /media/OS                fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sda5        /                        ext4       (rw,errors=remount-ro,commit=0)


=========================== sda5/boot/grub/grub.cfg: ===========================
he boot script info and got the following.
#

Hope this helps.

#

---

### Post by Hakunka-Matata on 2011-09-02
angus1964:  Good, you ran boot_info_script.  Please repost the RESULTS.txt file in it's entirety and enclosed in code tags (click on the # icon).

```
gedit RESULTS.txt
# highlight the entire file, CTRL+A, or right button Select All.
# copy it
# paste into reply
# highlight the entire pasted in file again
# then click on the # icon, code tags
# preview and post it.
```I'm posting one from here so you see how it looks.
```

                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (,msdos6)/boot/grub on this drive.
 => Grub2 (v1.99) is installed in the MBR of /dev/sdb and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (,msdos2)/boot/grub on this drive.
 => Grub2 (v1.99) is installed in the MBR of /dev/sdc and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (,msdos5)/boot/grub on this drive.

sda1: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.3 LTS
    Boot files:        /boot/grub/menu.lst /boot/grub/grub.cfg /etc/fstab 
                       /boot/grub/core.img

sda2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sda3: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Puppy Linux Linux 2.6.30.5 
                       [i686 arch]
    Boot files:        /etc/fstab

sda4: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda6: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.04
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda7: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files:        

sdb1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files:        /boot.ini /ntldr /NTDETECT.COM

sdb2: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.04
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb3: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdc1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files:        /boot.ini /ntldr /NTDETECT.COM

sdc2: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  FAT16
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdc3: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdc5: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.04
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdc6: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdc4: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files:        

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1                  63    40,965,749    40,965,687  83 Linux
/dev/sda2          40,965,750    57,341,951    16,376,202   7 NTFS / exFAT / HPFS
/dev/sda3         122,881,185   204,796,619    81,915,435  83 Linux
/dev/sda4         286,730,238   488,396,799   201,666,562   5 Extended
/dev/sda5         484,096,000   488,396,799     4,300,800  82 Linux swap / Solaris
/dev/sda6         286,730,240   327,690,239    40,960,000  83 Linux
/dev/sda7         368,654,336   484,093,951   115,439,616  83 Linux


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1    *             63    53,229,567    53,229,505   7 NTFS / exFAT / HPFS
/dev/sdb2          77,819,904   154,255,359    76,435,456  83 Linux
/dev/sdb3         154,255,360   156,301,311     2,045,952  82 Linux swap / Solaris


Drive: sdc _____________________________________________________________________

Disk /dev/sdc: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdc1    *             63   102,398,309   102,398,247   7 NTFS / exFAT / HPFS
/dev/sdc2         102,398,310   201,680,009    99,281,700  83 Linux
/dev/sdc3         304,080,894   488,396,799   184,315,906   5 Extended
/dev/sdc5         304,080,896   334,800,895    30,720,000  83 Linux
/dev/sdc6         484,202,496   488,396,799     4,194,304  82 Linux swap / Solaris
/dev/sdc4         201,680,010   304,078,319   102,398,310  83 Linux


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/sda1        01e2ae96-7804-4da9-a8b6-52b9f62a48af   ext4       10.04 lucid-32
/dev/sda2        21AFF7904D67E9DA                       ntfs       
/dev/sda3        4556b6fd-c494-4200-9d85-3e4c96ea9609   ext4       Puppy 4.3.1
/dev/sda5        ad9eb714-de6b-4ab3-b23e-8af75adf7202   swap       
/dev/sda6        497a14e5-d299-43c7-ae42-3e835a4fce5a   ext4       11.04 natty-32
/dev/sda7        a9f5d94a-6571-4016-a267-1b425da6382f   ext4       sda7_home_data
/dev/sdb1        C0B4A5D4B4A5CD6A                       ntfs       
/dev/sdb2        a62cccf7-ad57-46e2-954a-a487373ecf28   ext4       
/dev/sdb3        a3d8acd6-6614-4730-85de-c4ae54803b99   swap       
/dev/sdc1        5A14174B14172A11                       ntfs       WinXP
/dev/sdc2        0fb28b1f-044f-43ff-a1b5-1b36cd43feeb   ext4       10.10 mav-32
/dev/sdc4        b951593b-2ef3-4f1e-971e-6b1e4db61aa6   ext4       sdc4_home_data
/dev/sdc5        e7709c08-7686-4c02-a4df-c04e7537b17b   ext4       11.04 natty-32
/dev/sdc6        9752b8ed-c51a-494c-8c09-a73346e79166   swap       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sda6        /                        ext4       (rw,errors=remount-ro,commit=0)
/dev/sda7        /home                    ext4       (rw,nosuid,nodev,commit=0)


=========================== sda1/boot/grub/menu.lst: ===========================

--------------------------------------------------------------------------------
sudo nano /boot/grub/menu.lst

that's how this file was created, just testing
--------------------------------------------------------------------------------

=========================== sda1/boot/grub/grub.cfg: ===========================

--------------------------------------------------------------------------------
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
set root='(hd0,1)'
search --no-floppy --fs-uuid --set 01e2ae96-7804-4da9-a8b6-52b9f62a48af
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
set root='(hd0,1)'
search --no-floppy --fs-uuid --set 01e2ae96-7804-4da9-a8b6-52b9f62a48af
set locale_dir=($root)/boot/grub/locale
set lang=en
insmod gettext
if [ ${recordfail} = 1 ]; then
  set timeout=-1
else
  set timeout=3
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry 'Ubuntu, with Linux 2.6.32-33-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 01e2ae96-7804-4da9-a8b6-52b9f62a48af
    linux    /boot/vmlinuz-2.6.32-33-generic root=UUID=01e2ae96-7804-4da9-a8b6-52b9f62a48af ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-33-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-33-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 01e2ae96-7804-4da9-a8b6-52b9f62a48af
    echo    'Loading Linux 2.6.32-33-generic ...'
    linux    /boot/vmlinuz-2.6.32-33-generic root=UUID=01e2ae96-7804-4da9-a8b6-52b9f62a48af ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-33-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-30-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 01e2ae96-7804-4da9-a8b6-52b9f62a48af
    linux    /boot/vmlinuz-2.6.32-30-generic root=UUID=01e2ae96-7804-4da9-a8b6-52b9f62a48af ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-30-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-30-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 01e2ae96-7804-4da9-a8b6-52b9f62a48af
    echo    'Loading Linux 2.6.32-30-generic ...'
    linux    /boot/vmlinuz-2.6.32-30-generic root=UUID=01e2ae96-7804-4da9-a8b6-52b9f62a48af ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-30-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 01e2ae96-7804-4da9-a8b6-52b9f62a48af
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 01e2ae96-7804-4da9-a8b6-52b9f62a48af
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "unknown Linux distribution (on /dev/sda3)" {
    insmod ext2
    set root='(hd0,3)'
    search --no-floppy --fs-uuid --set 4556b6fd-c494-4200-9d85-3e4c96ea9609
    linux /boot/vmlinuz root=/dev/sda3
}
menuentry "unknown Linux distribution (on /dev/sda3)" {
    insmod ext2
    set root='(hd0,3)'
    search --no-floppy --fs-uuid --set 4556b6fd-c494-4200-9d85-3e4c96ea9609
    linux /boot/vmlinuz root=/dev/sda3
}
menuentry "Ubuntu, with Linux 2.6.38-11-generic (on /dev/sda6)" {
    insmod ext2
    set root='(hd0,6)'
    search --no-floppy --fs-uuid --set 497a14e5-d299-43c7-ae42-3e835a4fce5a
    linux /boot/vmlinuz-2.6.38-11-generic root=UUID=497a14e5-d299-43c7-ae42-3e835a4fce5a ro quiet splash vt.handoff=7
    initrd /boot/initrd.img-2.6.38-11-generic
}
menuentry "Ubuntu, with Linux 2.6.38-11-generic (recovery mode) (on /dev/sda6)" {
    insmod ext2
    set root='(hd0,6)'
    search --no-floppy --fs-uuid --set 497a14e5-d299-43c7-ae42-3e835a4fce5a
    linux /boot/vmlinuz-2.6.38-11-generic root=UUID=497a14e5-d299-43c7-ae42-3e835a4fce5a ro single
    initrd /boot/initrd.img-2.6.38-11-generic
}
menuentry "Ubuntu, with Linux 2.6.38-10-generic (on /dev/sda6)" {
    insmod ext2
    set root='(hd0,6)'
    search --no-floppy --fs-uuid --set 497a14e5-d299-43c7-ae42-3e835a4fce5a
    linux /boot/vmlinuz-2.6.38-10-generic root=UUID=497a14e5-d299-43c7-ae42-3e835a4fce5a ro quiet splash vt.handoff=7
    initrd /boot/initrd.img-2.6.38-10-generic
}
menuentry "Ubuntu, with Linux 2.6.38-10-generic (recovery mode) (on /dev/sda6)" {
    insmod ext2
    set root='(hd0,6)'
    search --no-floppy --fs-uuid --set 497a14e5-d299-43c7-ae42-3e835a4fce5a
    linux /boot/vmlinuz-2.6.38-10-generic root=UUID=497a14e5-d299-43c7-ae42-3e835a4fce5a ro single
    initrd /boot/initrd.img-2.6.38-10-generic
}
menuentry "Microsoft Windows XP Professional (on /dev/sdb1)" {
    insmod ntfs
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set C0B4A5D4B4A5CD6A
    drivemap -s (hd0) ${root}
    chainloader +1
}
menuentry "Ubuntu, with Linux 2.6.38-10-generic (on /dev/sdb2)" {
    insmod ext2
    set root='(hd1,2)'
    search --no-floppy --fs-uuid --set a62cccf7-ad57-46e2-954a-a487373ecf28
    linux /boot/vmlinuz-2.6.38-10-generic root=UUID=a62cccf7-ad57-46e2-954a-a487373ecf28 ro quiet splash vt.handoff=7
    initrd /boot/initrd.img-2.6.38-10-generic
}
menuentry "Ubuntu, with Linux 2.6.38-10-generic (recovery mode) (on /dev/sdb2)" {
    insmod ext2
    set root='(hd1,2)'
    search --no-floppy --fs-uuid --set a62cccf7-ad57-46e2-954a-a487373ecf28
    linux /boot/vmlinuz-2.6.38-10-generic root=UUID=a62cccf7-ad57-46e2-954a-a487373ecf28 ro single
    initrd /boot/initrd.img-2.6.38-10-generic
}
menuentry "Ubuntu, with Linux 2.6.38-8-generic (on /dev/sdb2)" {
    insmod ext2
    set root='(hd1,2)'
    search --no-floppy --fs-uuid --set a62cccf7-ad57-46e2-954a-a487373ecf28
    linux /boot/vmlinuz-2.6.38-8-generic root=UUID=a62cccf7-ad57-46e2-954a-a487373ecf28 ro quiet splash vt.handoff=7
    initrd /boot/initrd.img-2.6.38-8-generic
}
menuentry "Ubuntu, with Linux 2.6.38-8-generic (recovery mode) (on /dev/sdb2)" {
    insmod ext2
    set root='(hd1,2)'
    search --no-floppy --fs-uuid --set a62cccf7-ad57-46e2-954a-a487373ecf28
    linux /boot/vmlinuz-2.6.38-8-generic root=UUID=a62cccf7-ad57-46e2-954a-a487373ecf28 ro single
    initrd /boot/initrd.img-2.6.38-8-generic
}
menuentry "Microsoft Windows XP Professional (on /dev/sdc1)" {
    insmod ntfs
    set root='(hd2,1)'
    search --no-floppy --fs-uuid --set 5A14174B14172A11
    drivemap -s (hd0) ${root}
    chainloader +1
}
menuentry "Ubuntu, with Linux 2.6.35-30-generic (on /dev/sdc2)" {
    insmod ext2
    set root='(hd2,2)'
    search --no-floppy --fs-uuid --set 0fb28b1f-044f-43ff-a1b5-1b36cd43feeb
    linux /boot/vmlinuz-2.6.35-30-generic root=UUID=0fb28b1f-044f-43ff-a1b5-1b36cd43feeb ro quiet splash
    initrd /boot/initrd.img-2.6.35-30-generic
}
menuentry "Ubuntu, with Linux 2.6.35-30-generic (recovery mode) (on /dev/sdc2)" {
    insmod ext2
    set root='(hd2,2)'
    search --no-floppy --fs-uuid --set 0fb28b1f-044f-43ff-a1b5-1b36cd43feeb
    linux /boot/vmlinuz-2.6.35-30-generic root=UUID=0fb28b1f-044f-43ff-a1b5-1b36cd43feeb ro single
    initrd /boot/initrd.img-2.6.35-30-generic
}
menuentry "Ubuntu, with Linux 2.6.35-28-generic (on /dev/sdc2)" {
    insmod ext2
    set root='(hd2,2)'
    search --no-floppy --fs-uuid --set 0fb28b1f-044f-43ff-a1b5-1b36cd43feeb
    linux /boot/vmlinuz-2.6.35-28-generic root=UUID=0fb28b1f-044f-43ff-a1b5-1b36cd43feeb ro quiet splash
    initrd /boot/initrd.img-2.6.35-28-generic
}
menuentry "Ubuntu, with Linux 2.6.35-28-generic (recovery mode) (on /dev/sdc2)" {
    insmod ext2
    set root='(hd2,2)'
    search --no-floppy --fs-uuid --set 0fb28b1f-044f-43ff-a1b5-1b36cd43feeb
    linux /boot/vmlinuz-2.6.35-28-generic root=UUID=0fb28b1f-044f-43ff-a1b5-1b36cd43feeb ro single
    initrd /boot/initrd.img-2.6.35-28-generic
}
menuentry "Ubuntu, with Linux 2.6.35-23-generic (on /dev/sdc2)" {
    insmod ext2
    set root='(hd2,2)'
    search --no-floppy --fs-uuid --set 0fb28b1f-044f-43ff-a1b5-1b36cd43feeb
    linux /boot/vmlinuz-2.6.35-23-generic root=UUID=0fb28b1f-044f-43ff-a1b5-1b36cd43feeb ro quiet splash
    initrd /boot/initrd.img-2.6.35-23-generic
}
menuentry "Ubuntu, with Linux 2.6.35-23-generic (recovery mode) (on /dev/sdc2)" {
    insmod ext2
    set root='(hd2,2)'
    search --no-floppy --fs-uuid --set 0fb28b1f-044f-43ff-a1b5-1b36cd43feeb
    linux /boot/vmlinuz-2.6.35-23-generic root=UUID=0fb28b1f-044f-43ff-a1b5-1b36cd43feeb ro single
    initrd /boot/initrd.img-2.6.35-23-generic
}
menuentry "Ubuntu, with Linux 2.6.38-11-generic (on /dev/sdc5)" {
    insmod ext2
    set root='(hd2,5)'
    search --no-floppy --fs-uuid --set e7709c08-7686-4c02-a4df-c04e7537b17b
    linux /boot/vmlinuz-2.6.38-11-generic root=UUID=e7709c08-7686-4c02-a4df-c04e7537b17b ro quiet splash vt.handoff=7
    initrd /boot/initrd.img-2.6.38-11-generic
}
menuentry "Ubuntu, with Linux 2.6.38-11-generic (recovery mode) (on /dev/sdc5)" {
    insmod ext2
    set root='(hd2,5)'
    search --no-floppy --fs-uuid --set e7709c08-7686-4c02-a4df-c04e7537b17b
    linux /boot/vmlinuz-2.6.38-11-generic root=UUID=e7709c08-7686-4c02-a4df-c04e7537b17b ro single
    initrd /boot/initrd.img-2.6.38-11-generic
}
menuentry "Ubuntu, with Linux 2.6.38-8-generic (on /dev/sdc5)" {
    insmod ext2
    set root='(hd2,5)'
    search --no-floppy --fs-uuid --set e7709c08-7686-4c02-a4df-c04e7537b17b
    linux /boot/vmlinuz-2.6.38-8-generic root=UUID=e7709c08-7686-4c02-a4df-c04e7537b17b ro quiet splash vt.handoff=7
    initrd /boot/initrd.img-2.6.38-8-generic
}
menuentry "Ubuntu, with Linux 2.6.38-8-generic (recovery mode) (on /dev/sdc5)" {
    insmod ext2
    set root='(hd2,5)'
    search --no-floppy --fs-uuid --set e7709c08-7686-4c02-a4df-c04e7537b17b
    linux /boot/vmlinuz-2.6.38-8-generic root=UUID=e7709c08-7686-4c02-a4df-c04e7537b17b ro single
    initrd /boot/initrd.img-2.6.38-8-generic
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###
--------------------------------------------------------------------------------

=============================== sda1/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system>                 <mount point>   <type>  <options>           <dump>  <pass>
proc                            /proc           proc    nodev,noexec,nosuid     0       0
# / was on /dev/sdc1 during installation
UUID=01e2ae96-7804-4da9-a8b6-52b9f62a48af     /               ext4    errors=remount-ro     0       1
# swap was on /dev/sdc6 during installation
UUID=383a9e8e-3f83-4d37-a13f-eace58ddb2fc     none            swap    sw                     0       0
# swap was on /dev/sdb3 80GB drive
UUID=a3d8acd6-6614-4730-85de-c4ae54803b99     none            swap    sw                     0       0


--------------------------------------------------------------------------------

=================== sda1: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

  16.298884869 = 17.500794368   boot/grub/core.img                             1
  16.125167370 = 17.314266624   boot/grub/grub.cfg                             2
  16.222136974 = 17.418386944   boot/grub/menu.lst                             1
   8.116923809 = 8.715480576    boot/initrd.img-2.6.32-30-generic              2
  10.087111950 = 10.830953984   boot/initrd.img-2.6.32-33-generic              2
  16.445300579 = 17.658007040   boot/vmlinuz-2.6.32-30-generic                 1
  16.385970592 = 17.594301952   boot/vmlinuz-2.6.32-33-generic                 1
  10.087111950 = 10.830953984   initrd.img                                     2
   8.116923809 = 8.715480576    initrd.img.old                                 2
  16.385970592 = 17.594301952   vmlinuz                                        1
  16.445300579 = 17.658007040   vmlinuz.old                                    1

=============================== sda3/etc/fstab: ================================

--------------------------------------------------------------------------------
/dev/sdb3     /            ext4     defaults               0 1
none          /proc        proc     defaults               0 0
none          /sys         sysfs    defaults               0 0
none          /dev/pts     devpts   gid=2,mode=620         0 0
/dev/fd0      /mnt/floppy  auto     noauto,rw              0 0
--------------------------------------------------------------------------------

=================== sda3: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

  58.900890827 = 63.244349952   boot/vmlinuz                                   1

=========================== sda6/boot/grub/grub.cfg: ===========================

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
set root='(/dev/sda,msdos6)'
search --no-floppy --fs-uuid --set=root 497a14e5-d299-43c7-ae42-3e835a4fce5a
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos6)'
search --no-floppy --fs-uuid --set=root 497a14e5-d299-43c7-ae42-3e835a4fce5a
set locale_dir=($root)/boot/grub/locale
set lang=en_US
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
menuentry 'Ubuntu, with Linux 2.6.38-11-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos6)'
    search --no-floppy --fs-uuid --set=root 497a14e5-d299-43c7-ae42-3e835a4fce5a
    linux    /boot/vmlinuz-2.6.38-11-generic root=UUID=497a14e5-d299-43c7-ae42-3e835a4fce5a ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-2.6.38-11-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-11-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos6)'
    search --no-floppy --fs-uuid --set=root 497a14e5-d299-43c7-ae42-3e835a4fce5a
    echo    'Loading Linux 2.6.38-11-generic ...'
    linux    /boot/vmlinuz-2.6.38-11-generic root=UUID=497a14e5-d299-43c7-ae42-3e835a4fce5a ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.38-11-generic
}
submenu "Previous Linux versions" {
menuentry 'Ubuntu, with Linux 2.6.38-10-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos6)'
    search --no-floppy --fs-uuid --set=root 497a14e5-d299-43c7-ae42-3e835a4fce5a
    linux    /boot/vmlinuz-2.6.38-10-generic root=UUID=497a14e5-d299-43c7-ae42-3e835a4fce5a ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-2.6.38-10-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-10-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos6)'
    search --no-floppy --fs-uuid --set=root 497a14e5-d299-43c7-ae42-3e835a4fce5a
    echo    'Loading Linux 2.6.38-10-generic ...'
    linux    /boot/vmlinuz-2.6.38-10-generic root=UUID=497a14e5-d299-43c7-ae42-3e835a4fce5a ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.38-10-generic
}
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos6)'
    search --no-floppy --fs-uuid --set=root 497a14e5-d299-43c7-ae42-3e835a4fce5a
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos6)'
    search --no-floppy --fs-uuid --set=root 497a14e5-d299-43c7-ae42-3e835a4fce5a
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Ubuntu, with Linux 2.6.32-33-generic (on /dev/sda1)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos1)'
    search --no-floppy --fs-uuid --set=root 01e2ae96-7804-4da9-a8b6-52b9f62a48af
    linux /boot/vmlinuz-2.6.32-33-generic root=UUID=01e2ae96-7804-4da9-a8b6-52b9f62a48af ro quiet splash
    initrd /boot/initrd.img-2.6.32-33-generic
}
menuentry "Ubuntu, with Linux 2.6.32-33-generic (recovery mode) (on /dev/sda1)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos1)'
    search --no-floppy --fs-uuid --set=root 01e2ae96-7804-4da9-a8b6-52b9f62a48af
    linux /boot/vmlinuz-2.6.32-33-generic root=UUID=01e2ae96-7804-4da9-a8b6-52b9f62a48af ro single
    initrd /boot/initrd.img-2.6.32-33-generic
}
menuentry "Ubuntu, with Linux 2.6.32-30-generic (on /dev/sda1)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos1)'
    search --no-floppy --fs-uuid --set=root 01e2ae96-7804-4da9-a8b6-52b9f62a48af
    linux /boot/vmlinuz-2.6.32-30-generic root=UUID=01e2ae96-7804-4da9-a8b6-52b9f62a48af ro quiet splash
    initrd /boot/initrd.img-2.6.32-30-generic
}
menuentry "Ubuntu, with Linux 2.6.32-30-generic (recovery mode) (on /dev/sda1)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos1)'
    search --no-floppy --fs-uuid --set=root 01e2ae96-7804-4da9-a8b6-52b9f62a48af
    linux /boot/vmlinuz-2.6.32-30-generic root=UUID=01e2ae96-7804-4da9-a8b6-52b9f62a48af ro single
    initrd /boot/initrd.img-2.6.32-30-generic
}
menuentry "unknown Linux distribution (on /dev/sda3)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos3)'
    search --no-floppy --fs-uuid --set=root 4556b6fd-c494-4200-9d85-3e4c96ea9609
    linux /boot/vmlinuz root=/dev/sda3
}
menuentry "unknown Linux distribution (on /dev/sda3)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos3)'
    search --no-floppy --fs-uuid --set=root 4556b6fd-c494-4200-9d85-3e4c96ea9609
    linux /boot/vmlinuz root=/dev/sda3
}
menuentry "Microsoft Windows XP Professional (on /dev/sdb1)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(/dev/sdb,msdos1)'
    search --no-floppy --fs-uuid --set=root C0B4A5D4B4A5CD6A
    drivemap -s (hd0) ${root}
    chainloader +1
}
menuentry "Ubuntu, with Linux 2.6.38-10-generic (on /dev/sdb2)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sdb,msdos2)'
    search --no-floppy --fs-uuid --set=root a62cccf7-ad57-46e2-954a-a487373ecf28
    linux /boot/vmlinuz-2.6.38-10-generic root=UUID=a62cccf7-ad57-46e2-954a-a487373ecf28 ro quiet splash vt.handoff=7
    initrd /boot/initrd.img-2.6.38-10-generic
}
menuentry "Ubuntu, with Linux 2.6.38-10-generic (recovery mode) (on /dev/sdb2)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sdb,msdos2)'
    search --no-floppy --fs-uuid --set=root a62cccf7-ad57-46e2-954a-a487373ecf28
    linux /boot/vmlinuz-2.6.38-10-generic root=UUID=a62cccf7-ad57-46e2-954a-a487373ecf28 ro single
    initrd /boot/initrd.img-2.6.38-10-generic
}
menuentry "Ubuntu, with Linux 2.6.38-8-generic (on /dev/sdb2)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sdb,msdos2)'
    search --no-floppy --fs-uuid --set=root a62cccf7-ad57-46e2-954a-a487373ecf28
    linux /boot/vmlinuz-2.6.38-8-generic root=UUID=a62cccf7-ad57-46e2-954a-a487373ecf28 ro quiet splash vt.handoff=7
    initrd /boot/initrd.img-2.6.38-8-generic
}
menuentry "Ubuntu, with Linux 2.6.38-8-generic (recovery mode) (on /dev/sdb2)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sdb,msdos2)'
    search --no-floppy --fs-uuid --set=root a62cccf7-ad57-46e2-954a-a487373ecf28
    linux /boot/vmlinuz-2.6.38-8-generic root=UUID=a62cccf7-ad57-46e2-954a-a487373ecf28 ro single
    initrd /boot/initrd.img-2.6.38-8-generic
}
menuentry "Microsoft Windows XP Professional (on /dev/sdc1)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(/dev/sdc,msdos1)'
    search --no-floppy --fs-uuid --set=root 5A14174B14172A11
    drivemap -s (hd0) ${root}
    chainloader +1
}
menuentry "Ubuntu, with Linux 2.6.35-30-generic (on /dev/sdc2)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sdc,msdos2)'
    search --no-floppy --fs-uuid --set=root 0fb28b1f-044f-43ff-a1b5-1b36cd43feeb
    linux /boot/vmlinuz-2.6.35-30-generic root=UUID=0fb28b1f-044f-43ff-a1b5-1b36cd43feeb ro quiet splash
    initrd /boot/initrd.img-2.6.35-30-generic
}
menuentry "Ubuntu, with Linux 2.6.35-30-generic (recovery mode) (on /dev/sdc2)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sdc,msdos2)'
    search --no-floppy --fs-uuid --set=root 0fb28b1f-044f-43ff-a1b5-1b36cd43feeb
    linux /boot/vmlinuz-2.6.35-30-generic root=UUID=0fb28b1f-044f-43ff-a1b5-1b36cd43feeb ro single
    initrd /boot/initrd.img-2.6.35-30-generic
}
menuentry "Ubuntu, with Linux 2.6.35-28-generic (on /dev/sdc2)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sdc,msdos2)'
    search --no-floppy --fs-uuid --set=root 0fb28b1f-044f-43ff-a1b5-1b36cd43feeb
    linux /boot/vmlinuz-2.6.35-28-generic root=UUID=0fb28b1f-044f-43ff-a1b5-1b36cd43feeb ro quiet splash
    initrd /boot/initrd.img-2.6.35-28-generic
}
menuentry "Ubuntu, with Linux 2.6.35-28-generic (recovery mode) (on /dev/sdc2)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sdc,msdos2)'
    search --no-floppy --fs-uuid --set=root 0fb28b1f-044f-43ff-a1b5-1b36cd43feeb
    linux /boot/vmlinuz-2.6.35-28-generic root=UUID=0fb28b1f-044f-43ff-a1b5-1b36cd43feeb ro single
    initrd /boot/initrd.img-2.6.35-28-generic
}
menuentry "Ubuntu, with Linux 2.6.35-23-generic (on /dev/sdc2)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sdc,msdos2)'
    search --no-floppy --fs-uuid --set=root 0fb28b1f-044f-43ff-a1b5-1b36cd43feeb
    linux /boot/vmlinuz-2.6.35-23-generic root=UUID=0fb28b1f-044f-43ff-a1b5-1b36cd43feeb ro quiet splash
    initrd /boot/initrd.img-2.6.35-23-generic
}
menuentry "Ubuntu, with Linux 2.6.35-23-generic (recovery mode) (on /dev/sdc2)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sdc,msdos2)'
    search --no-floppy --fs-uuid --set=root 0fb28b1f-044f-43ff-a1b5-1b36cd43feeb
    linux /boot/vmlinuz-2.6.35-23-generic root=UUID=0fb28b1f-044f-43ff-a1b5-1b36cd43feeb ro single
    initrd /boot/initrd.img-2.6.35-23-generic
}
menuentry "Ubuntu, with Linux 2.6.38-11-generic (on /dev/sdc5)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sdc,msdos5)'
    search --no-floppy --fs-uuid --set=root e7709c08-7686-4c02-a4df-c04e7537b17b
    linux /boot/vmlinuz-2.6.38-11-generic root=UUID=e7709c08-7686-4c02-a4df-c04e7537b17b ro quiet splash vt.handoff=7
    initrd /boot/initrd.img-2.6.38-11-generic
}
menuentry "Ubuntu, with Linux 2.6.38-11-generic (recovery mode) (on /dev/sdc5)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sdc,msdos5)'
    search --no-floppy --fs-uuid --set=root e7709c08-7686-4c02-a4df-c04e7537b17b
    linux /boot/vmlinuz-2.6.38-11-generic root=UUID=e7709c08-7686-4c02-a4df-c04e7537b17b ro single
    initrd /boot/initrd.img-2.6.38-11-generic
}
menuentry "Ubuntu, with Linux 2.6.38-10-generic (on /dev/sdc5)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sdc,msdos5)'
    search --no-floppy --fs-uuid --set=root e7709c08-7686-4c02-a4df-c04e7537b17b
    linux /boot/vmlinuz-2.6.38-10-generic root=UUID=e7709c08-7686-4c02-a4df-c04e7537b17b ro quiet splash vt.handoff=7
    initrd /boot/initrd.img-2.6.38-10-generic
}
menuentry "Ubuntu, with Linux 2.6.38-10-generic (recovery mode) (on /dev/sdc5)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sdc,msdos5)'
    search --no-floppy --fs-uuid --set=root e7709c08-7686-4c02-a4df-c04e7537b17b
    linux /boot/vmlinuz-2.6.38-10-generic root=UUID=e7709c08-7686-4c02-a4df-c04e7537b17b ro single
    initrd /boot/initrd.img-2.6.38-10-generic
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

=============================== sda6/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system>                 <mount point>    <type>  <options>       <dump>  <pass>
proc                            /proc            proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda6 during installation
UUID=497a14e5-d299-43c7-ae42-3e835a4fce5a     /                ext4    errors=remount-ro     0       1
# swap was on /dev/sdc6 during installation
UUID=9752b8ed-c51a-494c-8c09-a73346e79166     none             swap    sw                  0       0
# swap was on /dev/sda5 during installation
UUID=ad9eb714-de6b-4ab3-b23e-8af75adf7202     none             swap    sw                   0       0
# swap was on /dev/sdb3 during installation
UUID=a3d8acd6-6614-4730-85de-c4ae54803b99     none             swap    sw                   0       0
# mount the /homeData partition /dev/sda7
UUID=a9f5d94a-6571-4016-a267-1b425da6382f    /home     ext4     nodev,nosuid            0       2
# mount the /sdc4_home_data partition /dev/sdc4
# UUID=b951593b-2ef3-4f1e-971e-6b1e4db61aa6    /home/das/sdb4_home_data_das     ext4     nodev,nosuid            0       2
--------------------------------------------------------------------------------

=================== sda6: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

 146.852870941 = 157.682069504  boot/grub/core.img                             1
 154.899448395 = 166.322016256  boot/grub/grub.cfg                             1
 138.767536163 = 149.000507392  boot/initrd.img-2.6.38-10-generic              2
 149.603004456 = 160.635002880  boot/initrd.img-2.6.38-11-generic              2
 137.555973053 = 147.699601408  boot/vmlinuz-2.6.38-10-generic                 2
 147.798160553 = 158.697066496  boot/vmlinuz-2.6.38-11-generic                 2
 149.603004456 = 160.635002880  initrd.img                                     2
 138.767536163 = 149.000507392  initrd.img.old                                 2
 147.798160553 = 158.697066496  vmlinuz                                        2
 137.555973053 = 147.699601408  vmlinuz.old                                    2

================================ sdb1/boot.ini: ================================

--------------------------------------------------------------------------------
[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /fastdetect /NoExecute=OptIn 
--------------------------------------------------------------------------------

=========================== sdb2/boot/grub/grub.cfg: ===========================

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
set root='(/dev/sdb,msdos2)'
search --no-floppy --fs-uuid --set=root a62cccf7-ad57-46e2-954a-a487373ecf28
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(/dev/sdb,msdos2)'
search --no-floppy --fs-uuid --set=root a62cccf7-ad57-46e2-954a-a487373ecf28
set locale_dir=($root)/boot/grub/locale
set lang=en_US
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
menuentry 'Ubuntu, with Linux 2.6.38-10-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sdb,msdos2)'
    search --no-floppy --fs-uuid --set=root a62cccf7-ad57-46e2-954a-a487373ecf28
    linux    /boot/vmlinuz-2.6.38-10-generic root=UUID=a62cccf7-ad57-46e2-954a-a487373ecf28 ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-2.6.38-10-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-10-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sdb,msdos2)'
    search --no-floppy --fs-uuid --set=root a62cccf7-ad57-46e2-954a-a487373ecf28
    echo    'Loading Linux 2.6.38-10-generic ...'
    linux    /boot/vmlinuz-2.6.38-10-generic root=UUID=a62cccf7-ad57-46e2-954a-a487373ecf28 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.38-10-generic
}
submenu "Previous Linux versions" {
menuentry 'Ubuntu, with Linux 2.6.38-8-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sdb,msdos2)'
    search --no-floppy --fs-uuid --set=root a62cccf7-ad57-46e2-954a-a487373ecf28
    linux    /boot/vmlinuz-2.6.38-8-generic root=UUID=a62cccf7-ad57-46e2-954a-a487373ecf28 ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-2.6.38-8-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-8-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sdb,msdos2)'
    search --no-floppy --fs-uuid --set=root a62cccf7-ad57-46e2-954a-a487373ecf28
    echo    'Loading Linux 2.6.38-8-generic ...'
    linux    /boot/vmlinuz-2.6.38-8-generic root=UUID=a62cccf7-ad57-46e2-954a-a487373ecf28 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.38-8-generic
}
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sdb,msdos2)'
    search --no-floppy --fs-uuid --set=root a62cccf7-ad57-46e2-954a-a487373ecf28
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sdb,msdos2)'
    search --no-floppy --fs-uuid --set=root a62cccf7-ad57-46e2-954a-a487373ecf28
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Ubuntu, with Linux 2.6.32-33-generic (on /dev/sda1)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos1)'
    search --no-floppy --fs-uuid --set=root 01e2ae96-7804-4da9-a8b6-52b9f62a48af
    linux /boot/vmlinuz-2.6.32-33-generic root=UUID=01e2ae96-7804-4da9-a8b6-52b9f62a48af ro quiet splash
    initrd /boot/initrd.img-2.6.32-33-generic
}
menuentry "Ubuntu, with Linux 2.6.32-33-generic (recovery mode) (on /dev/sda1)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos1)'
    search --no-floppy --fs-uuid --set=root 01e2ae96-7804-4da9-a8b6-52b9f62a48af
    linux /boot/vmlinuz-2.6.32-33-generic root=UUID=01e2ae96-7804-4da9-a8b6-52b9f62a48af ro single
    initrd /boot/initrd.img-2.6.32-33-generic
}
menuentry "Ubuntu, with Linux 2.6.32-30-generic (on /dev/sda1)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos1)'
    search --no-floppy --fs-uuid --set=root 01e2ae96-7804-4da9-a8b6-52b9f62a48af
    linux /boot/vmlinuz-2.6.32-30-generic root=UUID=01e2ae96-7804-4da9-a8b6-52b9f62a48af ro quiet splash
    initrd /boot/initrd.img-2.6.32-30-generic
}
menuentry "Ubuntu, with Linux 2.6.32-30-generic (recovery mode) (on /dev/sda1)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos1)'
    search --no-floppy --fs-uuid --set=root 01e2ae96-7804-4da9-a8b6-52b9f62a48af
    linux /boot/vmlinuz-2.6.32-30-generic root=UUID=01e2ae96-7804-4da9-a8b6-52b9f62a48af ro single
    initrd /boot/initrd.img-2.6.32-30-generic
}
menuentry "Puppy Linux 4.3.1 Linux distribution (on /dev/sda3)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos3)'
    search --no-floppy --fs-uuid --set=root 4556b6fd-c494-4200-9d85-3e4c96ea9609
    linux /boot/vmlinuz root=/dev/sda3
}
menuentry "Puppy Linux 4.3.1 recovery Linux distribution (on /dev/sda3)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos3)'
    search --no-floppy --fs-uuid --set=root 4556b6fd-c494-4200-9d85-3e4c96ea9609
    linux /boot/vmlinuz root=/dev/sda3
}
menuentry "Ubuntu, with Linux 2.6.38-11-generic (on /dev/sda6)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos6)'
    search --no-floppy --fs-uuid --set=root 497a14e5-d299-43c7-ae42-3e835a4fce5a
    linux /boot/vmlinuz-2.6.38-11-generic root=UUID=497a14e5-d299-43c7-ae42-3e835a4fce5a ro quiet splash vt.handoff=7
    initrd /boot/initrd.img-2.6.38-11-generic
}
menuentry "Ubuntu, with Linux 2.6.38-11-generic (recovery mode) (on /dev/sda6)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos6)'
    search --no-floppy --fs-uuid --set=root 497a14e5-d299-43c7-ae42-3e835a4fce5a
    linux /boot/vmlinuz-2.6.38-11-generic root=UUID=497a14e5-d299-43c7-ae42-3e835a4fce5a ro single
    initrd /boot/initrd.img-2.6.38-11-generic
}
menuentry "Ubuntu, with Linux 2.6.38-10-generic (on /dev/sda6)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos6)'
    search --no-floppy --fs-uuid --set=root 497a14e5-d299-43c7-ae42-3e835a4fce5a
    linux /boot/vmlinuz-2.6.38-10-generic root=UUID=497a14e5-d299-43c7-ae42-3e835a4fce5a ro quiet splash vt.handoff=7
    initrd /boot/initrd.img-2.6.38-10-generic
}
menuentry "Ubuntu, with Linux 2.6.38-10-generic (recovery mode) (on /dev/sda6)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos6)'
    search --no-floppy --fs-uuid --set=root 497a14e5-d299-43c7-ae42-3e835a4fce5a
    linux /boot/vmlinuz-2.6.38-10-generic root=UUID=497a14e5-d299-43c7-ae42-3e835a4fce5a ro single
    initrd /boot/initrd.img-2.6.38-10-generic
}
menuentry "Microsoft Windows XP Professional (on /dev/sdb1)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(/dev/sdb,msdos1)'
    search --no-floppy --fs-uuid --set=root C0B4A5D4B4A5CD6A
    drivemap -s (hd0) ${root}
    chainloader +1
}
menuentry "Microsoft Windows XP Professional (on /dev/sdc1)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(/dev/sdc,msdos1)'
    search --no-floppy --fs-uuid --set=root 5A14174B14172A11
    drivemap -s (hd0) ${root}
    chainloader +1
}
menuentry "Ubuntu, with Linux 2.6.35-30-generic (on /dev/sdc2)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sdc,msdos2)'
    search --no-floppy --fs-uuid --set=root 0fb28b1f-044f-43ff-a1b5-1b36cd43feeb
    linux /boot/vmlinuz-2.6.35-30-generic root=UUID=0fb28b1f-044f-43ff-a1b5-1b36cd43feeb ro quiet splash
    initrd /boot/initrd.img-2.6.35-30-generic
}
menuentry "Ubuntu, with Linux 2.6.35-30-generic (recovery mode) (on /dev/sdc2)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sdc,msdos2)'
    search --no-floppy --fs-uuid --set=root 0fb28b1f-044f-43ff-a1b5-1b36cd43feeb
    linux /boot/vmlinuz-2.6.35-30-generic root=UUID=0fb28b1f-044f-43ff-a1b5-1b36cd43feeb ro single
    initrd /boot/initrd.img-2.6.35-30-generic
}
menuentry "Ubuntu, with Linux 2.6.35-28-generic (on /dev/sdc2)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sdc,msdos2)'
    search --no-floppy --fs-uuid --set=root 0fb28b1f-044f-43ff-a1b5-1b36cd43feeb
    linux /boot/vmlinuz-2.6.35-28-generic root=UUID=0fb28b1f-044f-43ff-a1b5-1b36cd43feeb ro quiet splash
    initrd /boot/initrd.img-2.6.35-28-generic
}
menuentry "Ubuntu, with Linux 2.6.35-28-generic (recovery mode) (on /dev/sdc2)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sdc,msdos2)'
    search --no-floppy --fs-uuid --set=root 0fb28b1f-044f-43ff-a1b5-1b36cd43feeb
    linux /boot/vmlinuz-2.6.35-28-generic root=UUID=0fb28b1f-044f-43ff-a1b5-1b36cd43feeb ro single
    initrd /boot/initrd.img-2.6.35-28-generic
}
menuentry "Ubuntu, with Linux 2.6.35-23-generic (on /dev/sdc2)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sdc,msdos2)'
    search --no-floppy --fs-uuid --set=root 0fb28b1f-044f-43ff-a1b5-1b36cd43feeb
    linux /boot/vmlinuz-2.6.35-23-generic root=UUID=0fb28b1f-044f-43ff-a1b5-1b36cd43feeb ro quiet splash
    initrd /boot/initrd.img-2.6.35-23-generic
}
menuentry "Ubuntu, with Linux 2.6.35-23-generic (recovery mode) (on /dev/sdc2)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sdc,msdos2)'
    search --no-floppy --fs-uuid --set=root 0fb28b1f-044f-43ff-a1b5-1b36cd43feeb
    linux /boot/vmlinuz-2.6.35-23-generic root=UUID=0fb28b1f-044f-43ff-a1b5-1b36cd43feeb ro single
    initrd /boot/initrd.img-2.6.35-23-generic
}
menuentry "Ubuntu, with Linux 2.6.38-11-generic (on /dev/sdc5)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sdc,msdos5)'
    search --no-floppy --fs-uuid --set=root e7709c08-7686-4c02-a4df-c04e7537b17b
    linux /boot/vmlinuz-2.6.38-11-generic root=UUID=e7709c08-7686-4c02-a4df-c04e7537b17b ro quiet splash vt.handoff=7
    initrd /boot/initrd.img-2.6.38-11-generic
}
menuentry "Ubuntu, with Linux 2.6.38-11-generic (recovery mode) (on /dev/sdc5)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sdc,msdos5)'
    search --no-floppy --fs-uuid --set=root e7709c08-7686-4c02-a4df-c04e7537b17b
    linux /boot/vmlinuz-2.6.38-11-generic root=UUID=e7709c08-7686-4c02-a4df-c04e7537b17b ro single
    initrd /boot/initrd.img-2.6.38-11-generic
}
menuentry "Ubuntu, with Linux 2.6.38-10-generic (on /dev/sdc5)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sdc,msdos5)'
    search --no-floppy --fs-uuid --set=root e7709c08-7686-4c02-a4df-c04e7537b17b
    linux /boot/vmlinuz-2.6.38-10-generic root=UUID=e7709c08-7686-4c02-a4df-c04e7537b17b ro quiet splash vt.handoff=7
    initrd /boot/initrd.img-2.6.38-10-generic
}
menuentry "Ubuntu, with Linux 2.6.38-10-generic (recovery mode) (on /dev/sdc5)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sdc,msdos5)'
    search --no-floppy --fs-uuid --set=root e7709c08-7686-4c02-a4df-c04e7537b17b
    linux /boot/vmlinuz-2.6.38-10-generic root=UUID=e7709c08-7686-4c02-a4df-c04e7537b17b ro single
    initrd /boot/initrd.img-2.6.38-10-generic
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

=============================== sdb2/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda2 during installation
UUID=a62cccf7-ad57-46e2-954a-a487373ecf28 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda3 during installation
UUID=c03410b4-67c6-48ca-8132-0dd5f8ec4de9 none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sdb2: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

  59.253223419 = 63.622664192   boot/grub/core.img                             1
  39.556816101 = 42.473807872   boot/grub/grub.cfg                             1
  38.486583710 = 41.324654592   boot/initrd.img-2.6.38-10-generic              2
  37.861545563 = 40.653524992   boot/initrd.img-2.6.38-8-generic               2
  37.674137115 = 40.452296704   boot/vmlinuz-2.6.38-10-generic                 1
  59.331546783 = 63.706763264   boot/vmlinuz-2.6.38-8-generic                  1
  38.486583710 = 41.324654592   initrd.img                                     2
  37.861545563 = 40.653524992   initrd.img.old                                 2
  37.674137115 = 40.452296704   vmlinuz                                        1
  59.331546783 = 63.706763264   vmlinuz.old                                    1

================================ sdc1/boot.ini: ================================

--------------------------------------------------------------------------------
[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /fastdetect /NoExecute=OptIn 
--------------------------------------------------------------------------------

=========================== sdc2/boot/grub/grub.cfg: ===========================

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
}

insmod part_msdos
insmod ext2
set root='(hd2,msdos2)'
search --no-floppy --fs-uuid --set 0fb28b1f-044f-43ff-a1b5-1b36cd43feeb
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd2,msdos2)'
search --no-floppy --fs-uuid --set 0fb28b1f-044f-43ff-a1b5-1b36cd43feeb
set locale_dir=($root)/boot/grub/locale
set lang=en
insmod gettext
if [ "${recordfail}" = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
play 480 440 1
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry 'Ubuntu, with Linux 2.6.35-30-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd2,msdos2)'
    search --no-floppy --fs-uuid --set 0fb28b1f-044f-43ff-a1b5-1b36cd43feeb
    linux    /boot/vmlinuz-2.6.35-30-generic root=UUID=0fb28b1f-044f-43ff-a1b5-1b36cd43feeb ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-30-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-30-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd2,msdos2)'
    search --no-floppy --fs-uuid --set 0fb28b1f-044f-43ff-a1b5-1b36cd43feeb
    echo    'Loading Linux 2.6.35-30-generic ...'
    linux    /boot/vmlinuz-2.6.35-30-generic root=UUID=0fb28b1f-044f-43ff-a1b5-1b36cd43feeb ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-30-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-28-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd2,msdos2)'
    search --no-floppy --fs-uuid --set 0fb28b1f-044f-43ff-a1b5-1b36cd43feeb
    linux    /boot/vmlinuz-2.6.35-28-generic root=UUID=0fb28b1f-044f-43ff-a1b5-1b36cd43feeb ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-28-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-28-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd2,msdos2)'
    search --no-floppy --fs-uuid --set 0fb28b1f-044f-43ff-a1b5-1b36cd43feeb
    echo    'Loading Linux 2.6.35-28-generic ...'
    linux    /boot/vmlinuz-2.6.35-28-generic root=UUID=0fb28b1f-044f-43ff-a1b5-1b36cd43feeb ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-28-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-23-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd2,msdos2)'
    search --no-floppy --fs-uuid --set 0fb28b1f-044f-43ff-a1b5-1b36cd43feeb
    linux    /boot/vmlinuz-2.6.35-23-generic root=UUID=0fb28b1f-044f-43ff-a1b5-1b36cd43feeb ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-23-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-23-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd2,msdos2)'
    search --no-floppy --fs-uuid --set 0fb28b1f-044f-43ff-a1b5-1b36cd43feeb
    echo    'Loading Linux 2.6.35-23-generic ...'
    linux    /boot/vmlinuz-2.6.35-23-generic root=UUID=0fb28b1f-044f-43ff-a1b5-1b36cd43feeb ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-23-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(hd2,msdos2)'
    search --no-floppy --fs-uuid --set 0fb28b1f-044f-43ff-a1b5-1b36cd43feeb
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd2,msdos2)'
    search --no-floppy --fs-uuid --set 0fb28b1f-044f-43ff-a1b5-1b36cd43feeb
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Ubuntu, with Linux 2.6.32-33-generic (on /dev/sda1)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 01e2ae96-7804-4da9-a8b6-52b9f62a48af
    linux /boot/vmlinuz-2.6.32-33-generic root=UUID=01e2ae96-7804-4da9-a8b6-52b9f62a48af ro quiet splash
    initrd /boot/initrd.img-2.6.32-33-generic
}
menuentry "Ubuntu, with Linux 2.6.32-33-generic (recovery mode) (on /dev/sda1)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 01e2ae96-7804-4da9-a8b6-52b9f62a48af
    linux /boot/vmlinuz-2.6.32-33-generic root=UUID=01e2ae96-7804-4da9-a8b6-52b9f62a48af ro single
    initrd /boot/initrd.img-2.6.32-33-generic
}
menuentry "Ubuntu, with Linux 2.6.32-30-generic (on /dev/sda1)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 01e2ae96-7804-4da9-a8b6-52b9f62a48af
    linux /boot/vmlinuz-2.6.32-30-generic root=UUID=01e2ae96-7804-4da9-a8b6-52b9f62a48af ro quiet splash
    initrd /boot/initrd.img-2.6.32-30-generic
}
menuentry "Ubuntu, with Linux 2.6.32-30-generic (recovery mode) (on /dev/sda1)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 01e2ae96-7804-4da9-a8b6-52b9f62a48af
    linux /boot/vmlinuz-2.6.32-30-generic root=UUID=01e2ae96-7804-4da9-a8b6-52b9f62a48af ro single
    initrd /boot/initrd.img-2.6.32-30-generic
}
menuentry "unknown Linux distribution (on /dev/sda3)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos3)'
    search --no-floppy --fs-uuid --set 4556b6fd-c494-4200-9d85-3e4c96ea9609
    linux /boot/vmlinuz root=/dev/sda3
}
menuentry "unknown Linux distribution (on /dev/sda3)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos3)'
    search --no-floppy --fs-uuid --set 4556b6fd-c494-4200-9d85-3e4c96ea9609
    linux /boot/vmlinuz root=/dev/sda3
}
menuentry "Ubuntu, with Linux 2.6.38-11-generic (on /dev/sda6)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set 497a14e5-d299-43c7-ae42-3e835a4fce5a
    linux /boot/vmlinuz-2.6.38-11-generic root=UUID=497a14e5-d299-43c7-ae42-3e835a4fce5a ro quiet splash vt.handoff=7
    initrd /boot/initrd.img-2.6.38-11-generic
}
menuentry "Ubuntu, with Linux 2.6.38-11-generic (recovery mode) (on /dev/sda6)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set 497a14e5-d299-43c7-ae42-3e835a4fce5a
    linux /boot/vmlinuz-2.6.38-11-generic root=UUID=497a14e5-d299-43c7-ae42-3e835a4fce5a ro single
    initrd /boot/initrd.img-2.6.38-11-generic
}
menuentry "Ubuntu, with Linux 2.6.38-10-generic (on /dev/sda6)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set 497a14e5-d299-43c7-ae42-3e835a4fce5a
    linux /boot/vmlinuz-2.6.38-10-generic root=UUID=497a14e5-d299-43c7-ae42-3e835a4fce5a ro quiet splash vt.handoff=7
    initrd /boot/initrd.img-2.6.38-10-generic
}
menuentry "Ubuntu, with Linux 2.6.38-10-generic (recovery mode) (on /dev/sda6)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set 497a14e5-d299-43c7-ae42-3e835a4fce5a
    linux /boot/vmlinuz-2.6.38-10-generic root=UUID=497a14e5-d299-43c7-ae42-3e835a4fce5a ro single
    initrd /boot/initrd.img-2.6.38-10-generic
}
menuentry "Microsoft Windows XP Professional (on /dev/sdb1)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd1,msdos1)'
    search --no-floppy --fs-uuid --set C0B4A5D4B4A5CD6A
    drivemap -s (hd0) ${root}
    chainloader +1
}
menuentry "Ubuntu, with Linux 2.6.38-10-generic (on /dev/sdb2)" {
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos2)'
    search --no-floppy --fs-uuid --set a62cccf7-ad57-46e2-954a-a487373ecf28
    linux /boot/vmlinuz-2.6.38-10-generic root=UUID=a62cccf7-ad57-46e2-954a-a487373ecf28 ro quiet splash vt.handoff=7
    initrd /boot/initrd.img-2.6.38-10-generic
}
menuentry "Ubuntu, with Linux 2.6.38-10-generic (recovery mode) (on /dev/sdb2)" {
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos2)'
    search --no-floppy --fs-uuid --set a62cccf7-ad57-46e2-954a-a487373ecf28
    linux /boot/vmlinuz-2.6.38-10-generic root=UUID=a62cccf7-ad57-46e2-954a-a487373ecf28 ro single
    initrd /boot/initrd.img-2.6.38-10-generic
}
menuentry "Ubuntu, with Linux 2.6.38-8-generic (on /dev/sdb2)" {
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos2)'
    search --no-floppy --fs-uuid --set a62cccf7-ad57-46e2-954a-a487373ecf28
    linux /boot/vmlinuz-2.6.38-8-generic root=UUID=a62cccf7-ad57-46e2-954a-a487373ecf28 ro quiet splash vt.handoff=7
    initrd /boot/initrd.img-2.6.38-8-generic
}
menuentry "Ubuntu, with Linux 2.6.38-8-generic (recovery mode) (on /dev/sdb2)" {
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos2)'
    search --no-floppy --fs-uuid --set a62cccf7-ad57-46e2-954a-a487373ecf28
    linux /boot/vmlinuz-2.6.38-8-generic root=UUID=a62cccf7-ad57-46e2-954a-a487373ecf28 ro single
    initrd /boot/initrd.img-2.6.38-8-generic
}
menuentry "Microsoft Windows XP Professional (on /dev/sdc1)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd2,msdos1)'
    search --no-floppy --fs-uuid --set 5A14174B14172A11
    drivemap -s (hd0) ${root}
    chainloader +1
}
menuentry "Ubuntu, with Linux 2.6.38-11-generic (on /dev/sdc5)" {
    insmod part_msdos
    insmod ext2
    set root='(hd2,msdos5)'
    search --no-floppy --fs-uuid --set e7709c08-7686-4c02-a4df-c04e7537b17b
    linux /boot/vmlinuz-2.6.38-11-generic root=UUID=e7709c08-7686-4c02-a4df-c04e7537b17b ro quiet splash vt.handoff=7
    initrd /boot/initrd.img-2.6.38-11-generic
}
menuentry "Ubuntu, with Linux 2.6.38-11-generic (recovery mode) (on /dev/sdc5)" {
    insmod part_msdos
    insmod ext2
    set root='(hd2,msdos5)'
    search --no-floppy --fs-uuid --set e7709c08-7686-4c02-a4df-c04e7537b17b
    linux /boot/vmlinuz-2.6.38-11-generic root=UUID=e7709c08-7686-4c02-a4df-c04e7537b17b ro single
    initrd /boot/initrd.img-2.6.38-11-generic
}
menuentry "Ubuntu, with Linux 2.6.38-8-generic (on /dev/sdc5)" {
    insmod part_msdos
    insmod ext2
    set root='(hd2,msdos5)'
    search --no-floppy --fs-uuid --set e7709c08-7686-4c02-a4df-c04e7537b17b
    linux /boot/vmlinuz-2.6.38-8-generic root=UUID=e7709c08-7686-4c02-a4df-c04e7537b17b ro quiet splash vt.handoff=7
    initrd /boot/initrd.img-2.6.38-8-generic
}
menuentry "Ubuntu, with Linux 2.6.38-8-generic (recovery mode) (on /dev/sdc5)" {
    insmod part_msdos
    insmod ext2
    set root='(hd2,msdos5)'
    search --no-floppy --fs-uuid --set e7709c08-7686-4c02-a4df-c04e7537b17b
    linux /boot/vmlinuz-2.6.38-8-generic root=UUID=e7709c08-7686-4c02-a4df-c04e7537b17b ro single
    initrd /boot/initrd.img-2.6.38-8-generic
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

=============================== sdc2/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda2 during installation
UUID=0fb28b1f-044f-43ff-a1b5-1b36cd43feeb /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdc6 during installation
# UUID=383a9e8e-3f83-4d37-a13f-eace58ddb2fc none            swap    sw              0       0
# (identifier)  (location, eg sda5)
UUID=a9f5d94a-6571-4016-a267-1b425da6382f   /home    ext4          nodev,nosuid       0       2 
# swap was on /dev/sda7 during installation
UUID=ad9eb714-de6b-4ab3-b23e-8af75adf7202 none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sdc2: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

  81.004481316 = 86.977899520   boot/grub/core.img                             1
  61.018771172 = 65.518406656   boot/grub/grub.cfg                             2
  51.069506645 = 54.835465216   boot/initrd.img-2.6.35-23-generic              2
  52.122759819 = 55.966387200   boot/initrd.img-2.6.35-28-generic              2
  52.163256645 = 56.009870336   boot/initrd.img-2.6.35-30-generic              2
  81.091170311 = 87.070981120   boot/vmlinuz-2.6.35-23-generic                 1
  81.214323997 = 87.203216384   boot/vmlinuz-2.6.35-28-generic                 1
  81.218329430 = 87.207517184   boot/vmlinuz-2.6.35-30-generic                 1
  52.163256645 = 56.009870336   initrd.img                                     2
  52.122759819 = 55.966387200   initrd.img.old                                 2
  81.218329430 = 87.207517184   vmlinuz                                        1
  81.214323997 = 87.203216384   vmlinuz.old                                    1

=========================== sdc5/boot/grub/grub.cfg: ===========================

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
set root='(/dev/sdc,msdos5)'
search --no-floppy --fs-uuid --set=root e7709c08-7686-4c02-a4df-c04e7537b17b
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(/dev/sdc,msdos5)'
search --no-floppy --fs-uuid --set=root e7709c08-7686-4c02-a4df-c04e7537b17b
set locale_dir=($root)/boot/grub/locale
set lang=en_US
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
menuentry 'Ubuntu, with Linux 2.6.38-11-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sdc,msdos5)'
    search --no-floppy --fs-uuid --set=root e7709c08-7686-4c02-a4df-c04e7537b17b
    linux    /boot/vmlinuz-2.6.38-11-generic root=UUID=e7709c08-7686-4c02-a4df-c04e7537b17b ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-2.6.38-11-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-11-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sdc,msdos5)'
    search --no-floppy --fs-uuid --set=root e7709c08-7686-4c02-a4df-c04e7537b17b
    echo    'Loading Linux 2.6.38-11-generic ...'
    linux    /boot/vmlinuz-2.6.38-11-generic root=UUID=e7709c08-7686-4c02-a4df-c04e7537b17b ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.38-11-generic
}
submenu "Previous Linux versions" {
menuentry 'Ubuntu, with Linux 2.6.38-10-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sdc,msdos5)'
    search --no-floppy --fs-uuid --set=root e7709c08-7686-4c02-a4df-c04e7537b17b
    linux    /boot/vmlinuz-2.6.38-10-generic root=UUID=e7709c08-7686-4c02-a4df-c04e7537b17b ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-2.6.38-10-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-10-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sdc,msdos5)'
    search --no-floppy --fs-uuid --set=root e7709c08-7686-4c02-a4df-c04e7537b17b
    echo    'Loading Linux 2.6.38-10-generic ...'
    linux    /boot/vmlinuz-2.6.38-10-generic root=UUID=e7709c08-7686-4c02-a4df-c04e7537b17b ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.38-10-generic
}
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sdc,msdos5)'
    search --no-floppy --fs-uuid --set=root e7709c08-7686-4c02-a4df-c04e7537b17b
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sdc,msdos5)'
    search --no-floppy --fs-uuid --set=root e7709c08-7686-4c02-a4df-c04e7537b17b
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Ubuntu, with Linux 2.6.32-33-generic (on /dev/sda1)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos1)'
    search --no-floppy --fs-uuid --set=root 01e2ae96-7804-4da9-a8b6-52b9f62a48af
    linux /boot/vmlinuz-2.6.32-33-generic root=UUID=01e2ae96-7804-4da9-a8b6-52b9f62a48af ro quiet splash
    initrd /boot/initrd.img-2.6.32-33-generic
}
menuentry "Ubuntu, with Linux 2.6.32-33-generic (recovery mode) (on /dev/sda1)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos1)'
    search --no-floppy --fs-uuid --set=root 01e2ae96-7804-4da9-a8b6-52b9f62a48af
    linux /boot/vmlinuz-2.6.32-33-generic root=UUID=01e2ae96-7804-4da9-a8b6-52b9f62a48af ro single
    initrd /boot/initrd.img-2.6.32-33-generic
}
menuentry "Ubuntu, with Linux 2.6.32-30-generic (on /dev/sda1)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos1)'
    search --no-floppy --fs-uuid --set=root 01e2ae96-7804-4da9-a8b6-52b9f62a48af
    linux /boot/vmlinuz-2.6.32-30-generic root=UUID=01e2ae96-7804-4da9-a8b6-52b9f62a48af ro quiet splash
    initrd /boot/initrd.img-2.6.32-30-generic
}
menuentry "Ubuntu, with Linux 2.6.32-30-generic (recovery mode) (on /dev/sda1)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos1)'
    search --no-floppy --fs-uuid --set=root 01e2ae96-7804-4da9-a8b6-52b9f62a48af
    linux /boot/vmlinuz-2.6.32-30-generic root=UUID=01e2ae96-7804-4da9-a8b6-52b9f62a48af ro single
    initrd /boot/initrd.img-2.6.32-30-generic
}
menuentry "unknown Linux distribution (on /dev/sda3)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos3)'
    search --no-floppy --fs-uuid --set=root 4556b6fd-c494-4200-9d85-3e4c96ea9609
    linux /boot/vmlinuz root=/dev/sda3
}
menuentry "unknown Linux distribution (on /dev/sda3)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos3)'
    search --no-floppy --fs-uuid --set=root 4556b6fd-c494-4200-9d85-3e4c96ea9609
    linux /boot/vmlinuz root=/dev/sda3
}
menuentry "Ubuntu, with Linux 2.6.38-11-generic (on /dev/sda6)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos6)'
    search --no-floppy --fs-uuid --set=root 497a14e5-d299-43c7-ae42-3e835a4fce5a
    linux /boot/vmlinuz-2.6.38-11-generic root=UUID=497a14e5-d299-43c7-ae42-3e835a4fce5a ro quiet splash vt.handoff=7
    initrd /boot/initrd.img-2.6.38-11-generic
}
menuentry "Ubuntu, with Linux 2.6.38-11-generic (recovery mode) (on /dev/sda6)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos6)'
    search --no-floppy --fs-uuid --set=root 497a14e5-d299-43c7-ae42-3e835a4fce5a
    linux /boot/vmlinuz-2.6.38-11-generic root=UUID=497a14e5-d299-43c7-ae42-3e835a4fce5a ro single
    initrd /boot/initrd.img-2.6.38-11-generic
}
menuentry "Ubuntu, with Linux 2.6.38-10-generic (on /dev/sda6)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos6)'
    search --no-floppy --fs-uuid --set=root 497a14e5-d299-43c7-ae42-3e835a4fce5a
    linux /boot/vmlinuz-2.6.38-10-generic root=UUID=497a14e5-d299-43c7-ae42-3e835a4fce5a ro quiet splash vt.handoff=7
    initrd /boot/initrd.img-2.6.38-10-generic
}
menuentry "Ubuntu, with Linux 2.6.38-10-generic (recovery mode) (on /dev/sda6)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos6)'
    search --no-floppy --fs-uuid --set=root 497a14e5-d299-43c7-ae42-3e835a4fce5a
    linux /boot/vmlinuz-2.6.38-10-generic root=UUID=497a14e5-d299-43c7-ae42-3e835a4fce5a ro single
    initrd /boot/initrd.img-2.6.38-10-generic
}
menuentry "Microsoft Windows XP Professional (on /dev/sdb1)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(/dev/sdb,msdos1)'
    search --no-floppy --fs-uuid --set=root C0B4A5D4B4A5CD6A
    drivemap -s (hd0) ${root}
    chainloader +1
}
menuentry "Ubuntu, with Linux 2.6.38-10-generic (on /dev/sdb2)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sdb,msdos2)'
    search --no-floppy --fs-uuid --set=root a62cccf7-ad57-46e2-954a-a487373ecf28
    linux /boot/vmlinuz-2.6.38-10-generic root=UUID=a62cccf7-ad57-46e2-954a-a487373ecf28 ro quiet splash vt.handoff=7
    initrd /boot/initrd.img-2.6.38-10-generic
}
menuentry "Ubuntu, with Linux 2.6.38-10-generic (recovery mode) (on /dev/sdb2)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sdb,msdos2)'
    search --no-floppy --fs-uuid --set=root a62cccf7-ad57-46e2-954a-a487373ecf28
    linux /boot/vmlinuz-2.6.38-10-generic root=UUID=a62cccf7-ad57-46e2-954a-a487373ecf28 ro single
    initrd /boot/initrd.img-2.6.38-10-generic
}
menuentry "Ubuntu, with Linux 2.6.38-8-generic (on /dev/sdb2)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sdb,msdos2)'
    search --no-floppy --fs-uuid --set=root a62cccf7-ad57-46e2-954a-a487373ecf28
    linux /boot/vmlinuz-2.6.38-8-generic root=UUID=a62cccf7-ad57-46e2-954a-a487373ecf28 ro quiet splash vt.handoff=7
    initrd /boot/initrd.img-2.6.38-8-generic
}
menuentry "Ubuntu, with Linux 2.6.38-8-generic (recovery mode) (on /dev/sdb2)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sdb,msdos2)'
    search --no-floppy --fs-uuid --set=root a62cccf7-ad57-46e2-954a-a487373ecf28
    linux /boot/vmlinuz-2.6.38-8-generic root=UUID=a62cccf7-ad57-46e2-954a-a487373ecf28 ro single
    initrd /boot/initrd.img-2.6.38-8-generic
}
menuentry "Microsoft Windows XP Professional (on /dev/sdc1)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(/dev/sdc,msdos1)'
    search --no-floppy --fs-uuid --set=root 5A14174B14172A11
    drivemap -s (hd0) ${root}
    chainloader +1
}
menuentry "Ubuntu, with Linux 2.6.35-30-generic (on /dev/sdc2)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sdc,msdos2)'
    search --no-floppy --fs-uuid --set=root 0fb28b1f-044f-43ff-a1b5-1b36cd43feeb
    linux /boot/vmlinuz-2.6.35-30-generic root=UUID=0fb28b1f-044f-43ff-a1b5-1b36cd43feeb ro quiet splash
    initrd /boot/initrd.img-2.6.35-30-generic
}
menuentry "Ubuntu, with Linux 2.6.35-30-generic (recovery mode) (on /dev/sdc2)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sdc,msdos2)'
    search --no-floppy --fs-uuid --set=root 0fb28b1f-044f-43ff-a1b5-1b36cd43feeb
    linux /boot/vmlinuz-2.6.35-30-generic root=UUID=0fb28b1f-044f-43ff-a1b5-1b36cd43feeb ro single
    initrd /boot/initrd.img-2.6.35-30-generic
}
menuentry "Ubuntu, with Linux 2.6.35-28-generic (on /dev/sdc2)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sdc,msdos2)'
    search --no-floppy --fs-uuid --set=root 0fb28b1f-044f-43ff-a1b5-1b36cd43feeb
    linux /boot/vmlinuz-2.6.35-28-generic root=UUID=0fb28b1f-044f-43ff-a1b5-1b36cd43feeb ro quiet splash
    initrd /boot/initrd.img-2.6.35-28-generic
}
menuentry "Ubuntu, with Linux 2.6.35-28-generic (recovery mode) (on /dev/sdc2)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sdc,msdos2)'
    search --no-floppy --fs-uuid --set=root 0fb28b1f-044f-43ff-a1b5-1b36cd43feeb
    linux /boot/vmlinuz-2.6.35-28-generic root=UUID=0fb28b1f-044f-43ff-a1b5-1b36cd43feeb ro single
    initrd /boot/initrd.img-2.6.35-28-generic
}
menuentry "Ubuntu, with Linux 2.6.35-23-generic (on /dev/sdc2)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sdc,msdos2)'
    search --no-floppy --fs-uuid --set=root 0fb28b1f-044f-43ff-a1b5-1b36cd43feeb
    linux /boot/vmlinuz-2.6.35-23-generic root=UUID=0fb28b1f-044f-43ff-a1b5-1b36cd43feeb ro quiet splash
    initrd /boot/initrd.img-2.6.35-23-generic
}
menuentry "Ubuntu, with Linux 2.6.35-23-generic (recovery mode) (on /dev/sdc2)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sdc,msdos2)'
    search --no-floppy --fs-uuid --set=root 0fb28b1f-044f-43ff-a1b5-1b36cd43feeb
    linux /boot/vmlinuz-2.6.35-23-generic root=UUID=0fb28b1f-044f-43ff-a1b5-1b36cd43feeb ro single
    initrd /boot/initrd.img-2.6.35-23-generic
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

=============================== sdc5/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdc5 during installation
UUID=e7709c08-7686-4c02-a4df-c04e7537b17b /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=ad9eb714-de6b-4ab3-b23e-8af75adf7202 none            swap    sw              0       0
# swap was on /dev/sdb3 during installation
UUID=a3d8acd6-6614-4730-85de-c4ae54803b99 none            swap    sw              0       0
# swap was on /dev/sdc6 during installation
UUID=9752b8ed-c51a-494c-8c09-a73346e79166 none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sdc5: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

 155.200618744 = 166.645395456  boot/grub/core.img                             1
 157.728507996 = 169.359695872  boot/grub/grub.cfg                             1
 146.378345490 = 157.172551680  boot/initrd.img-2.6.38-10-generic              2
 157.766853333 = 169.400868864  boot/initrd.img-2.6.38-11-generic              1
 146.227848053 = 157.010956288  boot/vmlinuz-2.6.38-10-generic                 2
 145.930973053 = 156.692189184  boot/vmlinuz-2.6.38-11-generic                 2
 146.378345490 = 157.172551680  initrd.img                                     2
 157.766853333 = 169.400868864  initrd.img.old                                 1
 146.227848053 = 157.010956288  vmlinuz                                        2
 145.930973053 = 156.692189184  vmlinuz.old                                    2

=============================== StdErr Messages: ===============================

unlzma: Decoder error
unlzma: Decoder error
unlzma: Decoder error
```

---

### Post by angus1964 on 2011-09-02
Apologies for not posting full report, new to linux, learning fast.

```
                 Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (,msdos5)/boot/grub on this drive.

sda1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  Dell Utility: FAT16
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /DELLBIO.BIN /DELLRMK.BIN /COMMAND.COM

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
    Boot files:        /bootmgr /Boot/BCD /Windows/System32/winload.exe

sda4: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.04
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda6: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1               2,048       206,847       204,800  de Dell Utility
/dev/sda2    *        206,848    30,926,847    30,720,000   7 NTFS / exFAT / HPFS
/dev/sda3          30,926,848   778,492,150   747,565,303   7 NTFS / exFAT / HPFS
/dev/sda4         778,493,950   976,771,071   198,277,122   5 Extended
/dev/sda5         778,493,952   968,916,991   190,423,040  83 Linux
/dev/sda6         968,919,040   976,771,071     7,852,032  82 Linux swap / Solaris


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/sda1        3030-3030                              vfat       DELLUTILITY
/dev/sda2        CC70378A703779F2                       ntfs       Recovery
/dev/sda3        AC7C4EC27C4E86D4                       ntfs       OS
/dev/sda5        9113ff04-ab64-4ac9-9fa0-74ad45a3ac8c   ext4       
/dev/sda6        3ad2b8ac-6d5f-44bb-94df-b21e3566f5a9   swap       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sda3        /media/OS                fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sda5        /                        ext4       (rw,errors=remount-ro,commit=0)


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
  insmod vbe
  insmod vga
  insmod video_bochs
  insmod video_cirrus
}

insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos5)'
search --no-floppy --fs-uuid --set=root 9113ff04-ab64-4ac9-9fa0-74ad45a3ac8c
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos5)'
search --no-floppy --fs-uuid --set=root 9113ff04-ab64-4ac9-9fa0-74ad45a3ac8c
set locale_dir=($root)/boot/grub/locale
set lang=en_GB
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
menuentry 'Ubuntu, with Linux 2.6.38-11-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos5)'
    search --no-floppy --fs-uuid --set=root 9113ff04-ab64-4ac9-9fa0-74ad45a3ac8c
    linux    /boot/vmlinuz-2.6.38-11-generic-pae root=UUID=9113ff04-ab64-4ac9-9fa0-74ad45a3ac8c ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-2.6.38-11-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.38-11-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos5)'
    search --no-floppy --fs-uuid --set=root 9113ff04-ab64-4ac9-9fa0-74ad45a3ac8c
    echo    'Loading Linux 2.6.38-11-generic-pae ...'
    linux    /boot/vmlinuz-2.6.38-11-generic-pae root=UUID=9113ff04-ab64-4ac9-9fa0-74ad45a3ac8c ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.38-11-generic-pae
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos5)'
    search --no-floppy --fs-uuid --set=root 9113ff04-ab64-4ac9-9fa0-74ad45a3ac8c
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos5)'
    search --no-floppy --fs-uuid --set=root 9113ff04-ab64-4ac9-9fa0-74ad45a3ac8c
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda2)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(/dev/sda,msdos2)'
    search --no-floppy --fs-uuid --set=root CC70378A703779F2
    chainloader +1
}
menuentry "Windows 7 (loader) (on /dev/sda3)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(/dev/sda,msdos3)'
    search --no-floppy --fs-uuid --set=root AC7C4EC27C4E86D4
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
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda5 during installation
UUID=9113ff04-ab64-4ac9-9fa0-74ad45a3ac8c /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=3ad2b8ac-6d5f-44bb-94df-b21e3566f5a9 none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sda5: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

 385.372230530 = 413.790281728  boot/grub/core.img                             1
 441.358837128 = 473.905442816  boot/grub/grub.cfg                             1
 372.285156250 = 399.738142720  boot/initrd.img-2.6.38-11-generic-pae          2
 404.641056061 = 434.480025600  boot/vmlinuz-2.6.38-11-generic-pae             2
 372.285156250 = 399.738142720  initrd.img                                     2
 404.641056061 = 434.480025600  vmlinuz                                        2

=============================== StdErr Messages: ===============================

unlzma: Decoder error




```

---

### Post by Hakunka-Matata on 2011-09-02
Thanks, that looks good.

I don't see anything wrong with RESULTS.txt - but I'm still an apprentice figuring them................
The location on disk of the boot/grub/grub files is deep into the disk, ~400 GB, that may be causing problems but I don't know how to fix, it.  I'll see if I can get someone else to look at it.

>  
385.372230530 = 413.790281728  boot/grub/core.img    

---

### Post by angus1964 on 2011-09-02
Thanks for that, good to know the setup is basically sound. i have noticed quite a few postings on this forum with similar problems, the general consensus is a conflict with the graphics card, that would make some sense. Will have to do some research for a solution.

---

### Post by Hakunka-Matata on 2011-09-02
Yes, this thread is a sticky on the subject: [http://ubuntuforums.org/showthread.php?t=1743535](http://ubuntuforums.org/showthread.php?t=1743535)

When you get to the grub boot menu, try hitting F6, might give you options

---

### Post by oldfred on 2011-09-02
I also think you have a video issue not a boot issue. Boot script looks normal and you get to grub menu, so that is good.

Hakunka-Matata  	 		posted the first link I usually give.

Another link:
How to set NOMODESET and other kernel boot options in grub2 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

The nomodeset works with some video issues, there are other settings for specific video cards/brands. What Video do you have.

#To see video:
sudo lshw | grep -A 11 display

---

### Post by angus1964 on 2011-09-02
I have an ATI Mobility Radeon HD 4250. I will try your recommendations hopefully tomorrow, if it is resolved i will mark the thread.

---

### Post by angus1964 on 2011-09-03
Thanks very much oldfred that cured it.

Many thanks to all who posted.

---

