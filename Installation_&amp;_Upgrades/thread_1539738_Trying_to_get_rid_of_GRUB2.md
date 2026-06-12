---
title: "Trying to get rid of GRUB2"
date: 2010-07-26
forum: Installation &amp; Upgrades
---

### Post by Martini Anderson on 2010-07-26
Hello,

I am new to Ubuntu, and i have tried several times to install the dual boot so i can use Windows XP as well, so far no success. I have followed all the instruction found on Ubuntu site and forum, done all the procedures and still nothing. 

Fist I guess the problem starts when I install Ubuntu before Windows (Because i was going to re-install the Windows) so I created another partition for Ubuntu, then I kept the old Windows partition (subtracted 10gb from there for the new Ubuntu OS). Then after installing Ubuntu , I installed Windows XP SP3, there was the first mistake, the MBR overwrites and of course Ubuntu was able to boot. So, I tried to install GRUB2 to create the dual boot menu, after several tries still nothing, things got worse, now I cant get rid of the GRUB2 and stuck in there every time I turn on the computer, MBR was gone (I guess), GRUB can't be removed or modified, (tells me no kernel stuffs like that). Now I go to the Ubuntu trial from LiveCD, I open the GParted, tells me there's no partition. (Unallocated, 149 GiB, I used to have C, D, and E drives on Windows.) So I open terminal - sudo blkid
/dev/loop0: TYPE="squashfs" 
/dev/sda1: UUID="9ECC3A3CCC3A0ED1" TYPE="ntfs" 
/dev/sda3: LABEL="Entertainment" UUID="A085103FE80015ED" TYPE="ntfs" 
/dev/sda5: UUID="937edc39-3ec5-4388-9e6e-3f71a266f65a" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda6: UUID="8b3376f2-8a85-4f9e-a072-791b7a94c879" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda7: LABEL="Files" UUID="E2E0F0DA4A53C9F7" TYPE="ntfs" 

I'd still be able to see the old partitions. 

Now all i want to do is get rid of the whole thing and use Windows only.... any help??

I am sorry, I think Ubuntu is nice and fast but the problem is that cause too many troubles when you want to use dual boot.

Thanks

---

### Post by confused57 on 2010-07-26
Please post the output of the bootinfo script, using the Ubuntu live cd:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

Someone should be able to help you with the results from the script.

---

### Post by wojox on 2010-07-26
See here [Uninstalling GRUB 2]("https://help.ubuntu.com/community/Grub2#Uninstalling%20GRUB%202")

---

### Post by kansasnoob on 2010-07-26
> **confused57 said:**
> Please post the output of the bootinfo script, using the Ubuntu live cd:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

Someone should be able to help you with the results from the script.

+1!

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

---

### Post by Martini Anderson on 2010-07-26
> **confused57 said:**
> Please post the output of the bootinfo script, using the Ubuntu live cd:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

Someone should be able to help you with the results from the script.


**I guess this is it**

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #7 for /boot/grub.

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

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   /grub/grub.cfg /grub/core.img

sda6: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04 LTS
    Boot files/dirs:   /etc/fstab /boot/grub/core.img

sda7: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda7 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda3 starts 
                       at sector 63. But according to the info from fdisk, 
                       sda3 starts at sector 84389508.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63    63,906,569    63,906,507   7 HPFS/NTFS
/dev/sda2          63,907,838   312,576,704   248,668,867   5 Extended
Extended  partition  linking to another extended partition
/dev/sda5          63,907,840    65,859,583     1,951,744  83 Linux
/dev/sda6          65,861,632    84,387,839    18,526,208  83 Linux
/dev/sda7         189,406,413   312,576,704   123,170,292   7 HPFS/NTFS
/dev/sda3          84,389,508   189,406,349   105,016,842   7 HPFS/NTFS

/dev/sda2 overlaps with /dev/sda3

blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        9ECC3A3CCC3A0ED1                       ntfs                                     
/dev/sda2: PTTYPE="dos" 
/dev/sda3        A085103FE80015ED                       ntfs       Entertainment                 
/dev/sda5        937edc39-3ec5-4388-9e6e-3f71a266f65a   ext3                                     
/dev/sda6        8b3376f2-8a85-4f9e-a072-791b7a94c879   ext3                                     
/dev/sda7        E2E0F0DA4A53C9F7                       ntfs       Files                         
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)


================================ sda1/boot.ini: ================================

[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect 

============================= sda5/grub/grub.cfg: =============================

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
set root='(hd0,8)'
search --no-floppy --fs-uuid --set 8b3376f2-8a85-4f9e-a072-791b7a94c879
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
set root='(hd0,7)'
search --no-floppy --fs-uuid --set 937edc39-3ec5-4388-9e6e-3f71a266f65a
set locale_dir=($root)/grub/locale
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
menuentry 'Ubuntu, with Linux 2.6.32-23-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,7)'
    search --no-floppy --fs-uuid --set 937edc39-3ec5-4388-9e6e-3f71a266f65a
    linux    /vmlinuz-2.6.32-23-generic root=UUID=8b3376f2-8a85-4f9e-a072-791b7a94c879 ro   quiet splash
    initrd    /initrd.img-2.6.32-23-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-23-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,7)'
    search --no-floppy --fs-uuid --set 937edc39-3ec5-4388-9e6e-3f71a266f65a
    echo    'Loading Linux 2.6.32-23-generic ...'
    linux    /vmlinuz-2.6.32-23-generic root=UUID=8b3376f2-8a85-4f9e-a072-791b7a94c879 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /initrd.img-2.6.32-23-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,7)'
    search --no-floppy --fs-uuid --set 937edc39-3ec5-4388-9e6e-3f71a266f65a
    linux    /vmlinuz-2.6.32-21-generic root=UUID=8b3376f2-8a85-4f9e-a072-791b7a94c879 ro   quiet splash
    initrd    /initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,7)'
    search --no-floppy --fs-uuid --set 937edc39-3ec5-4388-9e6e-3f71a266f65a
    echo    'Loading Linux 2.6.32-21-generic ...'
    linux    /vmlinuz-2.6.32-21-generic root=UUID=8b3376f2-8a85-4f9e-a072-791b7a94c879 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd0,7)'
    search --no-floppy --fs-uuid --set 937edc39-3ec5-4388-9e6e-3f71a266f65a
    linux16    /memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd0,7)'
    search --no-floppy --fs-uuid --set 937edc39-3ec5-4388-9e6e-3f71a266f65a
    linux16    /memtest86+.bin console=ttyS0,115200n8
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

=================== sda5: Location of files loaded by Grub: ===================


  32.8GB: grub/core.img
  32.9GB: grub/grub.cfg
  32.7GB: initrd.img-2.6.32-21-generic
  32.7GB: initrd.img-2.6.32-23-generic
  32.8GB: vmlinuz-2.6.32-21-generic
  32.7GB: vmlinuz-2.6.32-23-generic

=============================== sda6/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda8 during installation
UUID=8b3376f2-8a85-4f9e-a072-791b7a94c879 /               ext3    errors=remount-ro 0       1
# /boot was on /dev/sda7 during installation
UUID=937edc39-3ec5-4388-9e6e-3f71a266f65a /boot           ext3    defaults        0       2
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sda6: Location of files loaded by Grub: ===================


  34.3GB: boot/grub/core.img
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda2

00000000  f1 13 e4 bb 4f 53 e5 bb  94 5a c5 bb 15 94 a1 bb  |....OS...Z......|
00000010  5c 20 8a bb 3c 6a 69 bb  db 96 2a bb f2 d9 cc ba  |\ ..<ji...*.....|
00000020  ce d5 84 ba 85 06 59 ba  a1 10 fe b9 ee db 0f ba  |......Y.........|
00000030  f1 03 f1 ba 40 e7 6f bb  cd f3 a8 bb 6b 75 db bb  |....@.o.....ku..|
00000040  49 85 11 bc ad 6b 36 bc  41 1c 4f bc 3d 8e 5e bc  |I....k6.A.O.=.^.|
00000050  65 13 71 bc bc 52 80 bc  d2 e9 80 bc 8e b3 7b bc  |e.q..R........{.|
00000060  f1 62 78 bc e0 64 71 bc  51 04 63 bc e9 a1 56 bc  |.bx..dq.Q.c...V.|
00000070  c6 ae 4f bc 79 78 49 bc  7d 6e 44 bc 04 38 45 bc  |..O.yxI.}nD..8E.|
00000080  f0 44 4a bc ed 0e 4e bc  da 98 51 bc 11 4d 59 bc  |.DJ...N...Q..MY.|
00000090  69 a2 66 bc 1a 0d 76 bc  93 6a 7f bc d1 d3 7d bc  |i.f...v..j....}.|
000000a0  50 fd 7a bc 95 f4 7c bc  6f 13 78 bc 06 cd 6e bc  |P.z...|.o.x...n.|
000000b0  07 f3 6d bc 30 a4 6c bc  ab bb 69 bc d3 ee 79 bc  |..m.0.l...i...y.|
000000c0  b7 38 8b bc 03 51 93 bc  a5 62 9d bc 25 ac b0 bc  |.8...Q...b..%...|
000000d0  2c 45 c0 bc 7f 1e c6 bc  be 62 ca bc a9 a2 cb bc  |,E.......b......|
000000e0  d3 21 c6 bc cc ab bd bc  89 c8 b0 bc e5 87 9a bc  |.!..............|
000000f0  71 82 79 bc 72 a5 39 bc  be 22 eb bb 5b d6 3b bb  |q.y.r.9.."..[.;.|
00000100  6b d8 dc 3a 99 f9 d0 3b  44 47 32 3c d6 79 73 3c  |k..:...;DG2<.ys<|
00000110  17 0a 98 3c 89 49 b2 3c  b4 01 c6 3c d8 f6 d5 3c  |...<.I.<...<...<|
00000120  0b d9 e6 3c 9a ef f4 3c  16 47 fe 3c 3d 3b 04 3d  |...<...<.G.<=;.=|
00000130  03 a1 0a 3d 6d bb 0f 3d  a2 96 14 3d 32 ed 1a 3d  |...=m..=...=2..=|
00000140  9c a0 20 3d cb 15 24 3d  47 bc 26 3d ae 16 28 3d  |.. =..$=G.&=..(=|
00000150  0b a1 26 3d c6 a4 23 3d  42 c3 20 3d 1a 3b 1c 3d  |..&=..#=B. =.;.=|
00000160  35 83 12 3d 03 c5 04 3d  51 fe ee 3c 45 2b d7 3c  |5..=...=Q..<E+.<|
00000170  0f 03 be 3c e3 20 a8 3c  30 33 96 3c 59 4b 83 3c  |...<. .<03.<YK.<|
00000180  39 a1 66 3c 2f 52 58 3c  50 aa 4b 3c 43 67 39 3c  |9.f</RX<P.K<Cg9<|
00000190  3c 6d 2e 3c f0 12 28 3c  d0 8a 1e 3c 6a ce 15 3c  |<m.<..(<...<j..<|
000001a0  47 45 05 3c 7d 0c d3 3b  85 3b a0 3b 66 9a 53 3b  |GE.<}..;.;.;f.S;|
000001b0  04 37 3c 3a df a1 db ba  bd eb 6b bb 71 06 00 fe  |.7<:......k.q...|
000001c0  ff ff 05 fe ff ff 01 00  00 00 01 c8 1d 00 00 00  |................|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200

---

### Post by Martini Anderson on 2010-07-26
> **wojox said:**
> See here [Uninstalling GRUB 2]("https://help.ubuntu.com/community/Grub2#Uninstalling%20GRUB%202")

I tried that.. didn't work.. that's why i am posting this.. :/

Thanks though

---

### Post by oldfred on 2010-07-27
You have some partition issues and your grub in the MBR points to a partition that does not have Ubuntu nor the rest of grub to boot.


Extended partition linking to another extended partition
/dev/sda2 overlaps with /dev/sda3

=> Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in
partition #7 for /boot/grub.
/dev/sda7 189,406,413 312,576,704 123,170,292 7 HPFS/NTFS

You will need to use testdisk and see if it will fix your partition issues.
enable the "universe" repository to download testdisk
System>Administration>Software Sources>Ubuntu Software.
[https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)
[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)
repairs including testdisk info & links
[http://members.iinet.net.au/~herman546/p21.html](http://members.iinet.net.au/~herman546/p21.html)
[https://help.ubuntu.com/community/DataRecovery#Lost%20Partition](https://help.ubuntu.com/community/DataRecovery#Lost%20Partition)

I am not sure you install is complete in sda5 or sda6, do you have a separate /boot partition? If so, that confuses the reinstall of grub to the MBR as you also have to mount that and most of the instructions do not include that.

General info:
[http://www.gnu.org/software/grub/manual/](http://www.gnu.org/software/grub/manual/)
The Grub 2 Guide (formerly Grub 2 Basics)
[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)
[https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202](https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202)
[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

---

### Post by Martini Anderson on 2010-07-27
> **oldfred said:**
> You have some partition issues and your grub in the MBR points to a partition that does not have Ubuntu nor the rest of grub to boot.


Extended partition linking to another extended partition
/dev/sda2 overlaps with /dev/sda3

=> Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in
partition #7 for /boot/grub.
/dev/sda7 189,406,413 312,576,704 123,170,292 7 HPFS/NTFS

You will need to use testdisk and see if it will fix your partition issues.
enable the "universe" repository to download testdisk
System>Administration>Software Sources>Ubuntu Software.
[https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)
[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)
repairs including testdisk info & links
[http://members.iinet.net.au/~herman546/p21.html]("http://members.iinet.net.au/%7Eherman546/p21.html")
[https://help.ubuntu.com/community/DataRecovery#Lost%20Partition](https://help.ubuntu.com/community/DataRecovery#Lost%20Partition)

I am not sure you install is complete in sda5 or sda6, do you have a separate /boot partition? If so, that confuses the reinstall of grub to the MBR as you also have to mount that and most of the instructions do not include that.

General info:
[http://www.gnu.org/software/grub/manual/](http://www.gnu.org/software/grub/manual/)
The Grub 2 Guide (formerly Grub 2 Basics)
[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)
[https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202](https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202)
[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)


**Well Test disk tells me this**
Disk /dev/sda - 160 GB / 149 GiB - CHS 19458 255 63
     Partition               Start        End    Size in sectors
* HPFS - NTFS              0   1  1  3977 254 63   63906507
P HPFS - NTFS           3978   0  1  5252 254 63   20482875
D HPFS - NTFS           5253   1  1 11789 254 63  105016842 [Entertainment]
D HPFS - NTFS          11789 254 63 18326 254 63  105016906

Structure: Ok.  Use Up/Down Arrow keys to select partition.
Use Left/Right Arrow keys to CHANGE partition characteristics:
*=Primary bootable  P=Primary  L=Logical  E=Extended  D=Deleted
Keys A: add partition, L: load backup, T: change type, P: list files,
     Enter: to continue
ubuntu@ubuntu:~$ GiB

Now i dont know what to do.

Initially when i read the Installing Ubuntu I thought that I needed to creat a boot partition, so that's why i created an 1GB partition for that, then 10 for Ubuntu OS...

I guess that looks bad, Deleted both of the partitions? I got tons of datas in there... I guess I just want to get rid of everything and just stick with Windows.. :/

Any help for that?? I will appreciate very much...

---

### Post by confused57 on 2010-07-27
I've never used Testdisk, so can't help you there, but you could try reinstalling Window's IPL to the mbr by booting a Window's installation cd(a recovery cd won't work), press R, then enter "fixmbr"(without quotes).

If you don't have a Window's install cd, then you could boot an Ubuntu live cd, enter in the terminal:
```
sudo apt-get install lilo
sudo lilo -M /dev/sda mbr
```
ignore any warnings or errors you may get.

See if this will at least get you into Windows & hopefully someone more familiar with Testdisk can help you recover your data.

---

### Post by Martini Anderson on 2010-07-27
I will try that now then reboot... and see what happens

Thanks a lot

---

