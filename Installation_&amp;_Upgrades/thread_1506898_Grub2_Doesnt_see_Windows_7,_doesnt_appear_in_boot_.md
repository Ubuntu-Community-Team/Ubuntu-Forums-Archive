---
title: "Grub2 Doesnt see Windows 7, doesnt appear in boot menu."
date: 2010-06-10
forum: Installation &amp; Upgrades
---

### Post by sbi23 on 2010-06-10
Ok, so a few days ago i wiped my entire hard drive that had xp as its only OS. I freshly installed a Windows 7 ultimate and everything went perfectly. 

I then decided to install 10.4. I split the partitions correctly (i had experience doing this already with my laptop, which has xp/10.4). Ubuntu 10.4 install went flawlessly, except for one thing. 

Now when i boot up the pc, it goes straight into 10.4. I have tried holding shift during the start up to force the boot menu, and it just shows the Ubuntu 10.4 OS as choices. Any clue what i could do to make Win7 appear in the boot menu?

---

### Post by wilee-nilee on 2010-06-10
First run ```
sudo update-grub
``` in a terminal in Ubuntu, if this doesn't add it to grub post this boot script in code tags, it will show whats going on and make it easier to identify the problem.
[noparse]```
[/noparse] at the beginning and [noparse]
```[/noparse] at the end.
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

Be sure to use the code tags as the script output is quite long and hard to read otherwise.:)

Also are you using truecrypt in W7?

---

### Post by sbi23 on 2010-06-10
Ok, so doing sudo update-grub, still didnt solve the problem.

Sol here is the boot info script:

```


                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #6 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat32
    Boot sector info:  According to the info in the boot sector, sda1 starts 
                       at sector 0. But according to the info from fdisk, 
                       sda1 starts at sector 245762370.
    Operating System:  
    Boot files/dirs:   

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda6: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda7: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *    245,762,370   286,728,119    40,965,750   b W95 FAT32
/dev/sda2         286,728,190   312,580,095    25,851,906   5 Extended
/dev/sda5         306,571,264   312,580,095     6,008,832  82 Linux swap / Solaris
/dev/sda6         286,728,192   305,627,135    18,898,944  83 Linux
/dev/sda7         305,629,184   306,569,215       940,032  82 Linux swap / Solaris
/dev/sda3                  63   245,762,369   245,762,307   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        647D-E903                              vfat       Extra                         
/dev/sda2: PTTYPE="dos" 
/dev/sda3        0F7A53E470822831                       ntfs                                     
/dev/sda5        920decdb-0467-46f8-8225-4f0ce39b97ad   swap                                     
/dev/sda6        e58a4ac8-fcb3-44a0-beb6-2ee54492a67f   ext4                                     
/dev/sda7        d06cf4b2-6ee4-4f31-835a-c643da081b83   swap                                     
/dev/sda: PTTYPE="dos" 
error: /dev/sdb: No medium found
error: /dev/sdc: No medium found
error: /dev/sdd: No medium found
error: /dev/sde: No medium found

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda6        /                        ext4       (rw,errors=remount-ro)
/dev/sda3        /media/0F7A53E470822831  fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)


=========================== sda6/boot/grub/grub.cfg: ===========================

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
set root='(hd0,6)'
search --no-floppy --fs-uuid --set e58a4ac8-fcb3-44a0-beb6-2ee54492a67f
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
set root='(hd0,6)'
search --no-floppy --fs-uuid --set e58a4ac8-fcb3-44a0-beb6-2ee54492a67f
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
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry 'Ubuntu, with Linux 2.6.32-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,6)'
    search --no-floppy --fs-uuid --set e58a4ac8-fcb3-44a0-beb6-2ee54492a67f
    linux    /boot/vmlinuz-2.6.32-22-generic root=UUID=e58a4ac8-fcb3-44a0-beb6-2ee54492a67f ro splash  quiet splash
    initrd    /boot/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,6)'
    search --no-floppy --fs-uuid --set e58a4ac8-fcb3-44a0-beb6-2ee54492a67f
    echo    'Loading Linux 2.6.32-22-generic ...'
    linux    /boot/vmlinuz-2.6.32-22-generic root=UUID=e58a4ac8-fcb3-44a0-beb6-2ee54492a67f ro single splash
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,6)'
    search --no-floppy --fs-uuid --set e58a4ac8-fcb3-44a0-beb6-2ee54492a67f
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=e58a4ac8-fcb3-44a0-beb6-2ee54492a67f ro splash  quiet splash
    initrd    /boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,6)'
    search --no-floppy --fs-uuid --set e58a4ac8-fcb3-44a0-beb6-2ee54492a67f
    echo    'Loading Linux 2.6.32-21-generic ...'
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=e58a4ac8-fcb3-44a0-beb6-2ee54492a67f ro single splash
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd0,6)'
    search --no-floppy --fs-uuid --set e58a4ac8-fcb3-44a0-beb6-2ee54492a67f
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd0,6)'
    search --no-floppy --fs-uuid --set e58a4ac8-fcb3-44a0-beb6-2ee54492a67f
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
UUID=e58a4ac8-fcb3-44a0-beb6-2ee54492a67f /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda7 during installation
UUID=d06cf4b2-6ee4-4f31-835a-c643da081b83 none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sda6: Location of files loaded by Grub: ===================


 151.5GB: boot/grub/core.img
 155.6GB: boot/grub/grub.cfg
 146.9GB: boot/initrd.img-2.6.32-21-generic
 151.9GB: boot/initrd.img-2.6.32-22-generic
 152.4GB: boot/vmlinuz-2.6.32-21-generic
 152.7GB: boot/vmlinuz-2.6.32-22-generic
 151.9GB: initrd.img
 146.9GB: initrd.img.old
 152.7GB: vmlinuz
 152.4GB: vmlinuz.old
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda2

00000000  00 b3 74 13 76 e4 be 90  dc 1b b7 f8 62 60 d0 c7  |..t.v.......b`..|
00000010  21 86 16 19 ce 73 ff d3  e9 ba a9 d6 45 fc e7 72  |!....s......E..r|
00000020  34 62 80 e4 f8 6f 49 67  8a 5e dc 8d 7f 7e 06 4b  |4b...oIg.^...~.K|
00000030  51 3f d7 50 1e a6 f8 b6  f8 2d ba 95 d6 7f 90 d9  |Q?.P.....-......|
00000040  1b 60 37 c9 fe 8f 0d 21  17 c3 18 7a 1b ab 97 94  |.`7....!...z....|
00000050  3b 45 76 cd a7 ae b0 5a  bf ba c6 e1 19 8d 4e 86  |;Ev....Z......N.|
00000060  a0 69 db 0a cc ce fd 74  9d be 5f f8 76 a0 d5 be  |.i.....t.._.v...|
00000070  5e e6 6d bc 65 15 4e 81  7d 95 b1 19 a3 58 8c 71  |^.m.e.N.}....X.q|
00000080  1e 33 1d 82 dd 82 9a 3d  40 6f 81 ca 75 eb fb e6  |.3.....=@o..u...|
00000090  fa 37 91 e7 34 81 b4 07  f8 1c c8 c4 fb d5 f6 3f  |.7..4..........?|
000000a0  f0 3f c8 8f 18 04 10 41  9d 7c 07 d3 e5 ff 5d 7b  |.?.....A.|....]{|
000000b0  eb 72 51 05 e5 e7 cc 00  31 87 33 13 e8 76 62 25  |.rQ.....1.3..vb%|
000000c0  3b 1f cc 72 2a 48 15 d4  a2 3f 77 af bb 2f 6e 16  |;..r*H...?w../n.|
000000d0  da 42 77 f8 62 84 71 b5  d5 e3 fe a0 19 46 7f c0  |.Bw.b.q......F..|
000000e0  83 5f dc e5 71 4f 23 ef  86 e2 77 f9 a9 db f8 a0  |._..qO#...w.....|
000000f0  01 d4 e3 f9 06 be ef ce  e2 ab bb f6 66 14 cd 7a  |............f..z|
00000100  fc 37 5b c0 67 0f 72 7e  03 92 8f 22 53 a1 a2 a2  |.7[.g.r~..."S...|
00000110  b6 74 ff e0 33 99 90 a3  16 ff bc b2 8b 5f e9 3b  |.t..3........_.;|
00000120  e5 7a 48 16 41 df 1e c3  8f 6a ae 3e 2d 97 ce 6b  |.zH.A....j.>-..k|
00000130  75 52 72 cd c1 b5 90 8c  76 d7 8d 96 cb dc f5 fc  |uRr.....v.......|
00000140  21 b4 1c a3 38 b7 ad b1  bf 09 8f 1e 2c 6f 31 f6  |!...8.......,o1.|
00000150  57 50 0a ef 7d 81 72 a0  62 00 10 ea 76 b7 2b 01  |WP..}.r.b...v.+.|
00000160  a6 3e cd c4 5f 6d 5d bd  af 2e ff fa ba c9 6c 60  |.>.._m].......l`|
00000170  23 e5 89 f1 b4 ea 69 c3  aa 9b 21 41 4a e2 f3 85  |#.....i...!AJ...|
00000180  53 b6 aa fd 42 b2 e9 d2  3f 21 bc 96 ee 72 59 bf  |S...B...?!...rY.|
00000190  92 97 1f 90 be d1 12 9b  31 d0 d4 37 8b 31 b5 7e  |........1..7.1.~|
000001a0  1d 8f bf 83 da d8 72 e0  1f 53 a8 ea d2 30 d3 61  |......r..S...0.a|
000001b0  a7 8b 94 f8 db d9 66 f8  83 ef 59 d9 d5 a3 00 fe  |......f...Y.....|
000001c0  ff ff 82 fe ff ff 02 c8  2e 01 00 b0 5b 00 00 fe  |............[...|
000001d0  ff ff 05 fe ff ff 01 00  00 00 01 60 20 01 00 00  |...........` ...|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


=======Devices which don't seem to have a corresponding hard drive==============

sdb sdc sdd sde 



```
Also, i dont know what truecrypt in Windows 7 is, so im assuming im not using it?

---

### Post by darkod on 2010-06-10
sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    [COLOR=Red]Boot files/dirs:   /Windows/System32/winload.exe[/COLOR]

You're missing two win7 boot files. Maybe you had the small boot partition and you deleted it.

Boot with your win7 dvd and follow the instructions here to repair the boot files:
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

Run just the /fixboot command or you will need to reinstall grub2 to the MBR again.

If you don't have win7 dvd, download repair cd image here:
[http://neosmart.net/blog/2009/windows-7-system-repair-discs/](http://neosmart.net/blog/2009/windows-7-system-repair-discs/)

---

### Post by sbi23 on 2010-06-11
So i downloaded the Win7 recovery disc and ran the cd. I did as the guide said, (bootrec.exe /fixboot) and it told me it was done successfully.

So then i rebooted without the disk, and the same thing occurred as before. It just boots straight into 10.4. I even tried updating the grub again, and nothing has changed.

Anything else i can try?

---

### Post by wilee-nilee on 2010-06-11
There is another experienced user on line that will probably stop by soon to take a look, they may want to see the script again. So just to confirm you just ran the BootRec.exe /FixBoot command?

---

### Post by sbi23 on 2010-06-11
yeah i ran the Win7 Repair Disc, just like the guide said, and ran:

bootrec.exe /fixboot

and DID NOT run "bootrec.exe /fixmbr" like you said not to.

And upon rebooting, the same thing occurrs as when i first had this problem. (It just boots straight into 10.4)

So i tried sudo update-grub, just to see if that would work now, and it still didnt detect the Win7 OS. I also tried Startup-manager, and it does not appear there also.

---

### Post by wilee-nilee on 2010-06-11
> **sbi23 said:**
> yeah i ran the Win7 Repair Disc, just like the guide said, and ran:

bootrec.exe /fixboot

and DID NOT run "bootrec.exe /fixmbr" like you said not to.

And upon rebooting, the same thing occurrs as when i first had this problem. (It just boots straight into 10.4)

So i tried sudo update-grub, just to see if that would work now, and it still didnt detect the Win7 OS. I also tried Startup-manager, and it does not appear there also.

I think your in good shape, this just needs either darkod or the other person on line, or somebody who is familiar with reloading the missing boot files, I think I know what it is but, when there are others who do know, I always refer to them, and when I answer you it is like a free bump, so your on the main pages for all to see.;)

---

### Post by oldfred on 2010-06-11
We are looking at getting windows to repair by adding these two files to the boot list. /bootmgr /Boot/BCD 

Boot files/dirs:   /Windows/System32/winload.exe

If you installed windows to a new or reformated drive it creates a hidden partition of 100MB that is the boot and recovery partition. Since your boot flag is on sda1 that maybe was the boot partition but it still is missing the two files that are normally in it. If you cannot repair the sda1 boot partition you can move the  boot flag to the sda3 partition and repair it. 

I would run the full set of repairs and see if that works. If not move boot flag to sda3 and rerun repairs. Once windows boots on its own then you will then have to reinstall grub, boot Ubuntu and run the sudo update-grub to add it to the menu.

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
[http://neosmart.net/wiki/display/EBCD/Recovering+the+Vista+Bootloader+from+the+DVD](http://neosmart.net/wiki/display/EBCD/Recovering+the+Vista+Bootloader+from+the+DVD)

How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)
kansasnoob on grub or grub2 reinstall
[http://ubuntuforums.org/showpost.php?p=9338226&postcount=41](http://ubuntuforums.org/showpost.php?p=9338226&postcount=41)

sudo mkdir /mnt/sda6
sudo mount /dev/sda6 /mnt
sudo grub-install --root-directory=/mnt /dev/sda
sudo grub-install --recheck --root-directory=/mnt /dev/sda

---

### Post by dandnsmith on 2010-06-11
I don't know if I'm mis-reading things, but that grub.cfg posted near the start of this thread doesn't show any entry to boot Windows.
When I look at my installation, I have an entry for each Windows partition - even where there isn't a real installation. I would expect the OS prober to find any installation (when grub is updated as well?)

---

### Post by darkod on 2010-06-11
Run the script again to see the current status.

Maybe it wasn't repaired properly because the boot flag was on /dev/sda1. Didn't notice that at first until oldfred mentioned it. In my defense, it was already 4AM here. :)

---

### Post by oldfred on 2010-06-11
You have no defense Darko, we have seen you on line 24 hrs a day ( or so it seems:p).

wilee-nilee had the OP run the sudo update-grub which would find windows if it is findable. Old grub would only find working windows and then not even all the time. The grub2 osprober finds windows that sometimes does not even work, but if it is missing whatever it is looking for, it will not show the windows install.

---

### Post by simonrose on 2011-05-07
Hi all,

I have a similar problem to this issue. Today I tried to install the latest ubuntu 11.04

After several attempts and failers due to the installer crashing and then not being able to install the bootloader I gave up and have reinstalled 10.04

The problem now is that my windows xp drive is no longer shown in grub and running update-grub doesn't show it. I know my windows drive exists because i can mount it and view my files.

i can't figure out what the problem is. Any one have any suggestions??

here is the output from boot info script:

```


                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #1 for /boot/grub.
 => Grub 2 is installed in the MBR of /dev/sdb and looks on the same drive in 
    partition #1 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM /boot/grub/core.img

sdb1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 300.1 GB, 300069052416 bytes
255 heads, 63 sectors/track, 36481 cylinders, total 586072368 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   586,067,264   586,067,202   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1               2,048   476,325,887   476,323,840  83 Linux
/dev/sdb2         476,327,934   488,396,799    12,068,866   5 Extended
/dev/sdb5         476,327,936   488,396,799    12,068,864  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        68A0A98FA0A963F2                       ntfs                                     
/dev/sda                                                promise_fasttrack_raid_member                               
/dev/sdb1        4aa91a2b-aa43-45eb-8bc5-7f6cb4445494   ext4                                     
/dev/sdb2: PTTYPE="dos" 
/dev/sdb5        d421bbf9-e22a-4d1e-9f77-e503cd0f6b75   swap                                     
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sdb1        /                        ext4       (rw,errors=remount-ro)
/dev/sda1        /media/68A0A98FA0A963F2  fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)


================================ sda1/boot.ini: ================================

[boot loader]

timeout=30

default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /fastdetect /NoExecute=OptIn


=================== sda1: Location of files loaded by Grub: ===================


    ??GB: boot/grub/core.img

=========================== sdb1/boot/grub/grub.cfg: ===========================

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
set root='(hd1,1)'
search --no-floppy --fs-uuid --set 4aa91a2b-aa43-45eb-8bc5-7f6cb4445494
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
set root='(hd1,1)'
search --no-floppy --fs-uuid --set 4aa91a2b-aa43-45eb-8bc5-7f6cb4445494
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
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry 'Ubuntu, with Linux 2.6.32-21-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd1,1)'
	search --no-floppy --fs-uuid --set 4aa91a2b-aa43-45eb-8bc5-7f6cb4445494
	linux	/boot/vmlinuz-2.6.32-21-generic root=UUID=4aa91a2b-aa43-45eb-8bc5-7f6cb4445494 ro   quiet splash acpi=off
	initrd	/boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd1,1)'
	search --no-floppy --fs-uuid --set 4aa91a2b-aa43-45eb-8bc5-7f6cb4445494
	echo	'Loading Linux 2.6.32-21-generic ...'
	linux	/boot/vmlinuz-2.6.32-21-generic root=UUID=4aa91a2b-aa43-45eb-8bc5-7f6cb4445494 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod ext2
	set root='(hd1,1)'
	search --no-floppy --fs-uuid --set 4aa91a2b-aa43-45eb-8bc5-7f6cb4445494
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod ext2
	set root='(hd1,1)'
	search --no-floppy --fs-uuid --set 4aa91a2b-aa43-45eb-8bc5-7f6cb4445494
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
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

=============================== sdb1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdb1 during installation
UUID=4aa91a2b-aa43-45eb-8bc5-7f6cb4445494 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdb5 during installation
UUID=d421bbf9-e22a-4d1e-9f77-e503cd0f6b75 none            swap    sw              0       0

=================== sdb1: Location of files loaded by Grub: ===================


 107.5GB: boot/grub/core.img
  51.7GB: boot/grub/grub.cfg
 107.5GB: boot/initrd.img-2.6.32-21-generic
 107.5GB: boot/vmlinuz-2.6.32-21-generic
 107.5GB: initrd.img
 107.5GB: vmlinuz
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sdb2

00000000  10 01 01 10 21 21 00 00  e0 0a 00 00 25 05 00 11  |....!!......%...|
00000010  bc 1c 00 00 c0 1c 00 00  01 00 04 00 00 00 00 00  |................|
00000020  f7 00 94 02 10 01 01 10  e9 21 00 00 d2 0a 00 00  |.........!......|
00000030  10 01 01 10 ee 21 00 00  e0 0a 00 00 25 05 00 11  |.....!......%...|
00000040  bc 1c 00 00 c0 1c 00 00  01 00 04 00 00 00 00 00  |................|
00000050  f7 00 96 02 10 01 01 10  e9 21 00 00 d2 0a 00 00  |.........!......|
00000060  10 01 01 10 f3 21 00 00  e0 0a 00 00 25 05 00 11  |.....!......%...|
00000070  bc 1c 00 00 c0 1c 00 00  01 00 04 00 00 00 00 00  |................|
00000080  f7 00 98 02 10 01 01 10  72 0d 00 00 d2 0a 00 00  |........r.......|
00000090  10 01 01 10 50 12 00 00  e0 0a 00 00 25 05 00 11  |....P.......%...|
000000a0  bc 1c 00 00 c0 1c 00 00  01 00 04 00 00 00 00 00  |................|
000000b0  f7 00 9a 02 10 01 01 10  72 0d 00 00 d2 0a 00 00  |........r.......|
000000c0  10 01 01 10 9b 12 00 00  e0 0a 00 00 25 05 00 11  |............%...|
000000d0  bc 1c 00 00 c0 1c 00 00  01 00 04 00 00 00 00 00  |................|
000000e0  f7 00 9c 02 10 01 01 10  72 0d 00 00 d2 0a 00 00  |........r.......|
000000f0  10 01 01 10 18 0e 00 00  e0 0a 00 00 25 05 00 11  |............%...|
00000100  bc 1c 00 00 c0 1c 00 00  01 00 04 00 00 00 00 00  |................|
00000110  f7 00 9e 02 10 01 01 10  72 0d 00 00 d2 0a 00 00  |........r.......|
00000120  10 01 01 10 f8 21 00 00  e0 0a 00 00 25 05 00 11  |.....!......%...|
00000130  bc 1c 00 00 c0 1c 00 00  01 00 04 00 00 00 00 00  |................|
00000140  f7 00 a0 02 10 01 01 10  72 0d 00 00 d2 0a 00 00  |........r.......|
00000150  10 01 01 10 fd 21 00 00  e0 0a 00 00 25 05 00 11  |.....!......%...|
00000160  bc 1c 00 00 c0 1c 00 00  01 00 04 00 00 00 00 00  |................|
00000170  f7 00 a2 02 10 01 01 10  72 0d 00 00 d2 0a 00 00  |........r.......|
00000180  10 01 01 10 02 22 00 00  e0 0a 00 00 25 05 00 11  |....."......%...|
00000190  bc 1c 00 00 c0 1c 00 00  01 00 04 00 00 00 00 00  |................|
000001a0  f7 00 a4 02 10 01 01 10  72 0d 00 00 d2 0a 00 00  |........r.......|
000001b0  10 01 01 10 07 22 00 00  e0 0a 00 00 25 05 00 fe  |....."......%...|
000001c0  ff ff 82 fe ff ff 02 00  00 00 00 28 b8 00 00 00  |...........(....|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200




```

---

### Post by coffeecat on 2011-05-07
Your problem is down to grub code getting written to the boot sector of your Windows partition smehow:

> **simonrose said:**
> 
```


sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM [COLOR=Red]/boot/grub/core.img[/COLOR]

```

That is preventing the os-prober from detecting the presence of a bootable Windows. In addition, if you were to create a custom Windows entry by means of the /etc/grub.d/40_custom file, Windows booting would probably fail anyway. You need to repair the Windows partition boot sector.

Have a look here:

[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector)

If you have a Windows XP installation CD (a Microsoft one - not an OEM recovery disc) the simplest way is to run fixboot from the repair console. Don't run fixmbr because that will write Windows code to the mbr and you would have to re-install grub again. If you don't have a Windows XP disc, that link gives you directions for repairing the Windows boot sector using testdisk. Please note: I have not tried testdisk for this purpose myself, but I've seen this link posted elsewhere and have no reason to suspect that it doesn't work.

---

### Post by oldfred on 2011-05-07
@simonrose

You seem to have installed part of grub into the windows partition, creating confusion on whether it is windows or grub.

Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM[COLOR=Red] /boot/grub/core.img[/COLOR]

Delete the above folder and rerun sudo update-grub.

Never mind. I see coffeecat beat me to it.


A few housekeeping issues. I like to have each systems boot loader in the same drive as the system and set BIOS to boot grub/ubuntu drive since it lets you choose. If your BIOS lets you directly boot sdb then I would also install windows boot loader to sda. 

Grub does not use a boot flag and if you can boot you do not need one, but some BIOS have to have a boot flag on a primary partition. If BIOS gives errors on booting sdb, it may be the missing boot flag.

---

### Post by coffeecat on 2011-05-07
> **oldfred said:**
> 
Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM[COLOR=Red] /boot/grub/core.img[/COLOR]

Delete the above folder and rerun sudo update-grub.

Never mind. I see coffeecat beat me to it.

In fact, maybe I didn't. :) I was wondering about suggesting that the OP simply delete /boot/grub/core.img because that's all that seems to be wrong in the Windows partition and would make running testdisk or the Windows disc unnecessary. Do you think that will be enough?

---

### Post by simonrose on 2011-05-07
Thanks!

I've got an original WinXP disc so I'll give the fixboot option a go...

---

### Post by simonrose on 2011-05-07
Thanks both for your responses...

I have tried them all but still have not got the windows drive into grub.

/boot/grub/core.img has been removed

I rebooted and went into recovery console but when I ran FIXBOOT I got this error:
"FIXBOOT cannot find the system drive, or the drive specified is not valid"

I also tried the testdisk option but on the sixth screen where I should have seen "BackupBS" I didn't and the website suggests using a WINXP disc at that point.

Any other ideas? The fixboot error isn't a good one right?

---

### Post by oldfred on 2011-05-07
Do you still have the boot flag (active partition in windows) on the sda1 partition? That is normally the way windows knows a NTFS partition is the boot partition. Then it should be able to find it to repair.

You kept the other three boot files that windows has to have?
  /boot.ini /ntldr /NTDETECT.COM

---

### Post by simonrose on 2011-05-07
> **oldfred said:**
> Do you still have the boot flag (active partition in windows) on the sda1 partition? That is normally the way windows knows a NTFS partition is the boot partition. Then it should be able to find it to repair

I don't really know what you mean..

> 
You kept the other three boot files that windows has to have?
  /boot.ini /ntldr /NTDETECT.COM

Correct. I ran the boot info script again and they all still exist.

---

### Post by oldfred on 2011-05-07
In boot script listing or sudo fdisk -lu listing of partitions you will see a little * on the boot partition.

This is from mine:

   Device [COLOR=Red]Boot[/COLOR]      Start         End      Blocks   Id  System 
/dev/sda1   [COLOR=Red]*[/COLOR]          63   115330634    57665286    7  HPFS/NTFS

You had it and it should still be there, but then I would expect windows to repair your sda1 partition.

---

### Post by Quackers on 2011-05-07
Are you using a raid array? I noticed this
```
blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        68A0A98FA0A963F2                       ntfs                                     
/dev/sda                                                [COLOR="Red"]promise_fasttrack_raid_member[/COLOR]                               
/dev/sdb1        4aa91a2b-aa43-45eb-8bc5-7f6cb4445494   ext4                                     
/dev/sdb2: PTTYPE="dos" 
/dev/sdb5        d421bbf9-e22a-4d1e-9f77-e503cd0f6b75   swap                                     
/dev/sdb: PTTYPE="dos" 
```

---

### Post by simonrose on 2011-05-08
@oldfred

I do have a boot asterisk against sda1 but not against sdb. I tried the fixboot option again after removing the grub folder from my windows drive just in case that worked but it didn't


@Quackers

I don't think I have a raid setup. I think that driver was installed by my motherboard driver disc. I don't remember setting my hdd to be in a raid.

---

### Post by simonrose on 2011-05-08
Anyone have any other suggestions?

---

### Post by oldfred on 2011-05-08
If you are sure you are not running RAID, RAID leaves settings on hard drives that interfer with standard installs. Double check BIOS settings, you may need IDE or Compatibility mode, but with win7 & Ubuntu large & AHCI should work. (BIOS sometimes use slightly different names).

Presence1960 on remove old raid setting from HD
[http://ubuntuforums.org/showthread.php?t=1325650](http://ubuntuforums.org/showthread.php?t=1325650)
sudo dmraid -E -r /dev/sda
sudo dmraid -E -r /dev/sdb
Also check BIOS for raid settings
More discusion:
[http://wwww.ubuntuforums.org/showthread.php?p=9274738#post9274738](http://wwww.ubuntuforums.org/showthread.php?p=9274738#post9274738)

---

### Post by simonrose on 2011-05-08
> **oldfred said:**
> 

Presence1960 on remove old raid setting from HD
[http://ubuntuforums.org/showthread.php?t=1325650](http://ubuntuforums.org/showthread.php?t=1325650)
sudo dmraid -E -r /dev/sda
sudo dmraid -E -r /dev/sdb


Thanks @oldfred this fixed it!

Ran the raid removal code and it removed it from sda (nothing on sdb). Ran update-grub and there was windows.

Not sure I fully understand what happened but thanks very much for your help

In case I think about installing 11.04 again is there anything I need to know about grub2 and the installer that might prevent this from happening again? As the installation process seems to have started this mess...

---

### Post by oldfred on 2011-05-08
Glad that worked & thank Quackers as I missed the promise RAID controller before.

I always create partitions in advance and use manual install, now called Something Else. I want to know what is installed where and determine sizes and additional partitions myself. But I know have so many partitions I have to keep notes as I have installed to the wrong partition.

With manual install you also get the option on where to install grub2's boot loader.

For two or more drives this is a good set of instructions. Herman has lots of detail. I still think it is Maverick screens but Natty is not a lot different and the procedures are the same.

Installing Ubuntu in Hard Disk Two (or more) internal or external
[http://members.iinet.net.au/~herman546/p24.html](http://members.iinet.net.au/~herman546/p24.html)

[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)

Ubuntu Install steps - then choose guide, close to what you want.
[http://members.iinet.net/~herman546/index.html](http://members.iinet.net/~herman546/index.html)
Installs with good screenshots/examples:
[http://members.iinet.net.au/~herman546/p22.html](http://members.iinet.net.au/~herman546/p22.html)
Install with separate /home from aysiu
[http://www.psychocats.net/ubuntu/installseparatehome](http://www.psychocats.net/ubuntu/installseparatehome)

---

