---
title: "Dualboot does not work"
date: 2010-08-28
forum: Installation &amp; Upgrades
---

### Post by x_master222 on 2010-08-28
I had on my notebook Windows 7 and Win Vista. I deleted partition with Vista and installed Ubuntu, but now when I turn on my notebook Ubuntu starts automatically, there is no option to choose Ubuntu or Windows 7. Why ? What should I do ? .. there is still that partition with Windows 7 I did not delete it.

Thanks for help

---

### Post by Kyrie1337 on 2010-08-28
Try to make the partition with linux install CD.

---

### Post by x_master222 on 2010-08-28
what partition ? And how ? :)

---

### Post by Kyrie1337 on 2010-08-28
Go to your ubuntu installer. After you deleted partition you want. Press install side-by-side and choose at start up. there you go

~Kyrie

---

### Post by oldfred on 2010-08-28
Was Vista installed first? If so when you deleted Vista you deleted the boot files for 7 also as windows combines the boot files into the active (boot flag) partition. You can probably repair with the windows CD.

To see exactly what your system has installed where.

Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the post's menu and then paste the contents between the generated [ code][ /code] tags.

---

### Post by x_master222 on 2010-08-28
Yes,  Vista was installed as a first. 

And here is the result of that script:

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #5 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.1 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda6: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda7: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda3 starts 
                       at sector 0. But according to the info from fdisk, 
                       sda3 starts at sector 151219845.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe

sda4: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048     3,074,047     3,072,000  27 Hidden HPFS/NTFS
/dev/sda2           3,076,094   151,218,175   148,142,082   5 Extended
/dev/sda5           3,076,096    51,902,463    48,826,368  83 Linux
/dev/sda6          51,904,512   140,795,903    88,891,392  83 Linux
/dev/sda7         140,797,952   151,218,175    10,420,224  82 Linux swap / Solaris
/dev/sda3         151,219,845   246,774,464    95,554,620   7 HPFS/NTFS
/dev/sda4         246,786,048   488,394,751   241,608,704   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda: PTTYPE="dos" 
/dev/sda1        74C43105C430CB5E                       ntfs       WinRE                         
/dev/sda2: PTTYPE="dos" 
/dev/sda3        01CA5572F5A93420                       ntfs                                     
/dev/sda4        329A36639A36242F                       ntfs       Data                          
/dev/sda5        790ddd1d-4d75-4de6-8895-c0cc2d850bf9   ext4                                     
/dev/sda6        af1acdd9-f896-4aad-b3f7-7009f329a2a7   ext4                                     
/dev/sda7        4e17859e-b9d2-4473-aa7c-8bb663772c41   swap                                     

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda5        /                        ext4       (rw,errors=remount-ro)
/dev/sda6        /home                    ext4       (rw)
/dev/sda3        /media/01CA5572F5A93420  fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sda4        /media/Data              fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)


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
search --no-floppy --fs-uuid --set 790ddd1d-4d75-4de6-8895-c0cc2d850bf9
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
search --no-floppy --fs-uuid --set 790ddd1d-4d75-4de6-8895-c0cc2d850bf9
set locale_dir=($root)/boot/grub/locale
set lang=sk
insmod gettext
if [ ${recordfail} = 1 ]; then
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
menuentry 'Ubuntu, with Linux 2.6.32-24-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 790ddd1d-4d75-4de6-8895-c0cc2d850bf9
    linux    /boot/vmlinuz-2.6.32-24-generic-pae root=UUID=790ddd1d-4d75-4de6-8895-c0cc2d850bf9 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-24-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.32-24-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 790ddd1d-4d75-4de6-8895-c0cc2d850bf9
    echo    'Loading Linux 2.6.32-24-generic-pae ...'
    linux    /boot/vmlinuz-2.6.32-24-generic-pae root=UUID=790ddd1d-4d75-4de6-8895-c0cc2d850bf9 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-24-generic-pae
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 790ddd1d-4d75-4de6-8895-c0cc2d850bf9
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 790ddd1d-4d75-4de6-8895-c0cc2d850bf9
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
if [ ${timeout} != -1 ]; then
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

=============================== sda5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda5 during installation
UUID=790ddd1d-4d75-4de6-8895-c0cc2d850bf9 /               ext4    errors=remount-ro 0       1
# /home was on /dev/sda6 during installation
UUID=af1acdd9-f896-4aad-b3f7-7009f329a2a7 /home           ext4    defaults        0       2
# swap was on /dev/sda7 during installation
UUID=4e17859e-b9d2-4473-aa7c-8bb663772c41 none            swap    sw              0       0

=================== sda5: Location of files loaded by Grub: ===================


  10.3GB: boot/grub/core.img
  14.9GB: boot/grub/grub.cfg
  10.3GB: boot/initrd.img-2.6.32-24-generic-pae
  10.3GB: boot/vmlinuz-2.6.32-24-generic-pae
  10.3GB: initrd.img
  10.3GB: vmlinuz
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda2

00000000  8b 55 ec 89 51 2c 8b 45  08 8b 48 2c 89 4d ec c7  |.U..Q,.E..H,.M..|
00000010  45 f0 27 00 00 00 8b 55  ec 3b 55 f0 1b c0 f7 d8  |E.'....U.;U.....|
00000020  8b 4d 08 89 41 28 8b 55  08 8b 42 08 89 45 fc 8b  |.M..A(.U..B..E..|
00000030  4d 08 8b 51 28 89 55 ec  8b 45 fc 3b 45 ec 75 05  |M..Q(.U..E.;E.u.|
00000040  e9 af 00 00 00 8b 4d 08  8b 51 14 89 55 ec c7 45  |......M..Q..U..E|
00000050  f0 84 02 00 00 8b 45 ec  03 45 f0 8b 4d 08 89 41  |......E..E..M..A|
00000060  30 8b 55 08 8b 42 2c 89  45 ec c7 45 f0 02 00 00  |0.U..B,.E..E....|
00000070  00 8b 55 ec 8b 4d f0 d3  e2 8b 45 08 89 50 20 8b  |..U..M....E..P .|
00000080  4d 08 8b 51 20 89 55 ec  8b 45 08 8b 48 30 89 4d  |M..Q .U..E..H0.M|
00000090  f0 8b 55 ec 03 55 f0 8b  45 08 89 50 34 8d 4d ec  |..U..U..E..P4.M.|
000000a0  51 8b 55 08 8b 42 34 50  8b 4d 08 51 e8 8f f4 01  |Q.U..B4P.M.Q....|
000000b0  00 89 45 f4 83 7d f4 00  7d 0e 8b 55 08 8b 45 f4  |..E..}..}..U..E.|
000000c0  89 42 14 e9 20 c4 01 00  8b 4d 08 8b 55 ec 89 51  |.B.. ....M..U..Q|
000000d0  38 8b 45 08 8b 48 38 89  4d ec 8b 55 08 8b 42 70  |8.E..H8.M..U..Bp|
000000e0  89 45 f0 8b 4d ec 33 4d  f0 8b 55 08 89 4a 30 e9  |.E..M.3M..U..J0.|
000000f0  aa 00 00 00 8b 45 08 8b  48 2c 89 4d ec c7 45 f0  |.....E..H,.M..E.|
00000100  02 00 00 00 8b 55 ec 8b  4d f0 d3 e2 8b 45 08 89  |.....U..M....E..|
00000110  50 3c 8b 4d 08 8b 51 14  89 55 ec c7 45 f0 74 24  |P<.M..Q..U..E.t$|
00000120  00 00 8b 45 ec 03 45 f0  8b 4d 08 89 41 40 8b 55  |...E..E..M..A@.U|
00000130  08 8b 42 3c 89 45 ec 8b  4d 08 8b 51 40 89 55 f0  |..B<.E..M..Q@.U.|
00000140  8b 45 ec 03 45 f0 8b 4d  08 89 41 2c 8d 55 ec 52  |.E..E..M..A,.U.R|
00000150  8b 45 08 8b 48 2c 51 8b  55 08 52 e8 20 f5 01 00  |.E..H,Q.U.R. ...|
00000160  89 45 f4 83 7d f4 00 7d  0e 8b 45 08 8b 4d f4 89  |.E..}..}..E..M..|
00000170  48 14 e9 71 c3 01 00 8b  55 08 8b 45 ec 89 42 28  |H..q....U..E..B(|
00000180  8b 4d 08 8b 51 28 89 55  ec 8b 45 08 8b 48 74 89  |.M..Q(.U..E..Ht.|
00000190  4d f0 8b 55 ec 33 55 f0  8b 45 08 89 50 30 8d 4d  |M..U.3U..E..P0.M|
000001a0  ec 51 8b 55 08 0f b7 42  04 83 c0 41 50 8b 4d 08  |.Q.U...B...AP.M.|
000001b0  51 e8 1a 04 02 00 89 45  f4 83 7d f4 00 7d 00 79  |Q......E..}..}.y|
000001c0  3b bf 83 fe ff ff 02 00  00 00 00 08 e9 02 00 fe  |;...............|
000001d0  ff ff 05 fe ff ff 02 08  e9 02 00 68 4c 05 00 00  |...........hL...|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200

```

---

### Post by oldfred on 2010-08-28
You need to move the boot flag to sda3 and repair your install.
You can use gparted, right click on partition & manage flags, Disk Utility, or command line:
set boot flag on for sda3 (off on others)
sudo sfdisk -A3 /dev/sda

Then you need to use a win7 repairCD to fix windows. Do not run fixMBR or you will have to reinstall grub. Or you can do it to test it boots ok directly with windows then reinstall grub. After fixing it in Ubuntu run sudo update-grub to find your windows.

You have this:
Boot files/dirs:   /Windows/System32/winload.exe
and should have this:
 /bootmgr /Boot/BCD  /Windows/System32/winload.exe

How to use the Bootrec.exe tool in the Windows Recovery Environment to troubleshoot and repair startup issues in Windows
[http://support.microsoft.com/kb/927392](http://support.microsoft.com/kb/927392)
[http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html](http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html)
[http://windows7ultimate.windowsreinstall.com/repairwin7startup/indexthumbs.ht](http://windows7ultimate.windowsreinstall.com/repairwin7startup/indexthumbs.ht)

Above links summarized, see links if more detail desired
You will need to boot with your Vista/Windows 7 installation disk or repair disk. Hit Enter at the language selection prompt then hit "R" to get to the repair section. You can then select the automatic boot repair tool, but it often will not do any good. Then select the command prompt (console) and type in the following commands:
BootRec.exe /fixmbr   #updates MBR master boot record  do not run if you still want grub
chkdsk C: /r /f (may have to run /r or /f as separate entries) rerun until no errors
BootRec.exe /FixBoot  #updates PBR partition boot sector
BootRec.exe /ScanOs
BootRec.exe /RebuildBcd

How to fix Vista/Window 7 when the boot files are missing - rebuild BCD with bcdedit
[http://ubuntuforums.org/showpost.php?p=5726832&postcount=4](http://ubuntuforums.org/showpost.php?p=5726832&postcount=4)
Some advanced BCD rebuild, Vista:
[http://ubuntuforums.org/showthread.php?t=1426103](http://ubuntuforums.org/showthread.php?t=1426103)

If your PC did not come with a complete Vista or Win7 installation CD, you can download a Recovery Disc at the following links:
Windows Vista/7 Recovery Disc - for repairs only
[http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/](http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/)
[http://neosmart.net/blog/2009/windows-7-system-repair-discs/](http://neosmart.net/blog/2009/windows-7-system-repair-discs/)
Vista will not repair XP (they create the boot sectors differently) but can run chkdsk.
[http://support.microsoft.com/kb/927392](http://support.microsoft.com/kb/927392)

---

### Post by x_master222 on 2010-08-28
I did that commands: 
BootRec.exe /fixmbr   #updates MBR master boot record  do not run if you still want grub
chkdsk C: /r /f (may have to run /r or /f as separate entries) rerun until no errors
BootRec.exe /FixBoot  #updates PBR partition boot sector
BootRec.exe /ScanOs
BootRec.exe /RebuildBcd

but now, when I restart notebook, nothing starts, just a black screen comes

---

### Post by oldfred on 2010-08-28
If you put the windows boot loader into the MBR you are directly booting the windows install. Did  all the windows repairs say they worked? Do you have boot flag on sda3?

Try rerunning boot script from liveCD to see if windows looks correct now.

The repair should have fixed it but the boot sector was still XP.
Boot sector type:  Windows XP

---

### Post by x_master222 on 2010-08-28
now, again just Ubuntu runs automatically when I turn notebook on, here is the result of the script:

```
                                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #5 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.1 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda6: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda7: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  According to the info in the boot sector, sda3 starts 
                       at sector 0. But according to the info from fdisk, 
                       sda3 starts at sector 151219845.
    Operating System:  Windows 7
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe

sda4: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1               2,048     3,074,047     3,072,000  27 Hidden HPFS/NTFS
/dev/sda2           3,076,094   151,218,175   148,142,082   5 Extended
/dev/sda5           3,076,096    51,902,463    48,826,368  83 Linux
/dev/sda6          51,904,512   140,795,903    88,891,392  83 Linux
/dev/sda7         140,797,952   151,218,175    10,420,224  82 Linux swap / Solaris
/dev/sda3    *    151,219,845   246,774,464    95,554,620   7 HPFS/NTFS
/dev/sda4         246,786,048   488,394,751   241,608,704   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda: PTTYPE="dos" 
/dev/sda1        74C43105C430CB5E                       ntfs       WinRE                         
/dev/sda2: PTTYPE="dos" 
/dev/sda3        01CA5572F5A93420                       ntfs                                     
/dev/sda4        329A36639A36242F                       ntfs       Data                          
/dev/sda5        790ddd1d-4d75-4de6-8895-c0cc2d850bf9   ext4                                     
/dev/sda6        af1acdd9-f896-4aad-b3f7-7009f329a2a7   ext4                                     
/dev/sda7        4e17859e-b9d2-4473-aa7c-8bb663772c41   swap                                     

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda5        /                        ext4       (rw,errors=remount-ro)
/dev/sda6        /home                    ext4       (rw)
/dev/sda3        /media/01CA5572F5A93420  fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)


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
search --no-floppy --fs-uuid --set 790ddd1d-4d75-4de6-8895-c0cc2d850bf9
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
search --no-floppy --fs-uuid --set 790ddd1d-4d75-4de6-8895-c0cc2d850bf9
set locale_dir=($root)/boot/grub/locale
set lang=sk
insmod gettext
if [ ${recordfail} = 1 ]; then
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
menuentry 'Ubuntu, with Linux 2.6.32-24-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 790ddd1d-4d75-4de6-8895-c0cc2d850bf9
    linux    /boot/vmlinuz-2.6.32-24-generic-pae root=UUID=790ddd1d-4d75-4de6-8895-c0cc2d850bf9 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-24-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.32-24-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 790ddd1d-4d75-4de6-8895-c0cc2d850bf9
    echo    'Loading Linux 2.6.32-24-generic-pae ...'
    linux    /boot/vmlinuz-2.6.32-24-generic-pae root=UUID=790ddd1d-4d75-4de6-8895-c0cc2d850bf9 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-24-generic-pae
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 790ddd1d-4d75-4de6-8895-c0cc2d850bf9
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 790ddd1d-4d75-4de6-8895-c0cc2d850bf9
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
if [ ${timeout} != -1 ]; then
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

=============================== sda5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda5 during installation
UUID=790ddd1d-4d75-4de6-8895-c0cc2d850bf9 /               ext4    errors=remount-ro 0       1
# /home was on /dev/sda6 during installation
UUID=af1acdd9-f896-4aad-b3f7-7009f329a2a7 /home           ext4    defaults        0       2
# swap was on /dev/sda7 during installation
UUID=4e17859e-b9d2-4473-aa7c-8bb663772c41 none            swap    sw              0       0

=================== sda5: Location of files loaded by Grub: ===================


  10.3GB: boot/grub/core.img
  14.9GB: boot/grub/grub.cfg
  10.3GB: boot/initrd.img-2.6.32-24-generic-pae
  10.3GB: boot/vmlinuz-2.6.32-24-generic-pae
  10.3GB: initrd.img
  10.3GB: vmlinuz
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda2

00000000  8b 55 ec 89 51 2c 8b 45  08 8b 48 2c 89 4d ec c7  |.U..Q,.E..H,.M..|
00000010  45 f0 27 00 00 00 8b 55  ec 3b 55 f0 1b c0 f7 d8  |E.'....U.;U.....|
00000020  8b 4d 08 89 41 28 8b 55  08 8b 42 08 89 45 fc 8b  |.M..A(.U..B..E..|
00000030  4d 08 8b 51 28 89 55 ec  8b 45 fc 3b 45 ec 75 05  |M..Q(.U..E.;E.u.|
00000040  e9 af 00 00 00 8b 4d 08  8b 51 14 89 55 ec c7 45  |......M..Q..U..E|
00000050  f0 84 02 00 00 8b 45 ec  03 45 f0 8b 4d 08 89 41  |......E..E..M..A|
00000060  30 8b 55 08 8b 42 2c 89  45 ec c7 45 f0 02 00 00  |0.U..B,.E..E....|
00000070  00 8b 55 ec 8b 4d f0 d3  e2 8b 45 08 89 50 20 8b  |..U..M....E..P .|
00000080  4d 08 8b 51 20 89 55 ec  8b 45 08 8b 48 30 89 4d  |M..Q .U..E..H0.M|
00000090  f0 8b 55 ec 03 55 f0 8b  45 08 89 50 34 8d 4d ec  |..U..U..E..P4.M.|
000000a0  51 8b 55 08 8b 42 34 50  8b 4d 08 51 e8 8f f4 01  |Q.U..B4P.M.Q....|
000000b0  00 89 45 f4 83 7d f4 00  7d 0e 8b 55 08 8b 45 f4  |..E..}..}..U..E.|
000000c0  89 42 14 e9 20 c4 01 00  8b 4d 08 8b 55 ec 89 51  |.B.. ....M..U..Q|
000000d0  38 8b 45 08 8b 48 38 89  4d ec 8b 55 08 8b 42 70  |8.E..H8.M..U..Bp|
000000e0  89 45 f0 8b 4d ec 33 4d  f0 8b 55 08 89 4a 30 e9  |.E..M.3M..U..J0.|
000000f0  aa 00 00 00 8b 45 08 8b  48 2c 89 4d ec c7 45 f0  |.....E..H,.M..E.|
00000100  02 00 00 00 8b 55 ec 8b  4d f0 d3 e2 8b 45 08 89  |.....U..M....E..|
00000110  50 3c 8b 4d 08 8b 51 14  89 55 ec c7 45 f0 74 24  |P<.M..Q..U..E.t$|
00000120  00 00 8b 45 ec 03 45 f0  8b 4d 08 89 41 40 8b 55  |...E..E..M..A@.U|
00000130  08 8b 42 3c 89 45 ec 8b  4d 08 8b 51 40 89 55 f0  |..B<.E..M..Q@.U.|
00000140  8b 45 ec 03 45 f0 8b 4d  08 89 41 2c 8d 55 ec 52  |.E..E..M..A,.U.R|
00000150  8b 45 08 8b 48 2c 51 8b  55 08 52 e8 20 f5 01 00  |.E..H,Q.U.R. ...|
00000160  89 45 f4 83 7d f4 00 7d  0e 8b 45 08 8b 4d f4 89  |.E..}..}..E..M..|
00000170  48 14 e9 71 c3 01 00 8b  55 08 8b 45 ec 89 42 28  |H..q....U..E..B(|
00000180  8b 4d 08 8b 51 28 89 55  ec 8b 45 08 8b 48 74 89  |.M..Q(.U..E..Ht.|
00000190  4d f0 8b 55 ec 33 55 f0  8b 45 08 89 50 30 8d 4d  |M..U.3U..E..P0.M|
000001a0  ec 51 8b 55 08 0f b7 42  04 83 c0 41 50 8b 4d 08  |.Q.U...B...AP.M.|
000001b0  51 e8 1a 04 02 00 89 45  f4 83 7d f4 00 7d 00 79  |Q......E..}..}.y|
000001c0  3b bf 83 fe ff ff 02 00  00 00 00 08 e9 02 00 fe  |;...............|
000001d0  ff ff 05 fe ff ff 02 08  e9 02 00 68 4c 05 00 00  |...........hL...|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


```

---

### Post by x_master222 on 2010-08-29
now, I runned the command sudo update-grub from Ubuntu and when I turn notebook on there is a choice to choose between Ubuntu and Windows 7, but when I choose Windows 7 it does not start, just a black screen.

What to do now ?

---

### Post by oldfred on 2010-08-29
There still seems to be some issue with your boot sector in the windows partition that must be confusing windows.

    Boot sector info:  According to the info in the boot sector, sda3 starts 
                       at sector 0. But according to the info from fdisk, 
                       sda3 starts at sector 151219845.

I thought the fixboot command would have fixed this. You might try that again but I am not hopeful. You want it to fully rebuild the boot sector. Did chkdsk report any errors, you often have to rerun until there are no errors and before reruning fixboot.

Other windows/System boot repair tools may work better like EasyBCD or Supergrub. ( I do not recommend using EasyBCD for booting although some like it but it may also repair issues).

[http://support.microsoft.com/kb/927392](http://support.microsoft.com/kb/927392)

[http://www.supergrubdisk.org/wiki/SuperGrubDiskDocumentation](http://www.supergrubdisk.org/wiki/SuperGrubDiskDocumentation)
[http://neosmart.net/wiki/display/EBCD/EasyBCD+Documentation+Home](http://neosmart.net/wiki/display/EBCD/EasyBCD+Documentation+Home)

---

