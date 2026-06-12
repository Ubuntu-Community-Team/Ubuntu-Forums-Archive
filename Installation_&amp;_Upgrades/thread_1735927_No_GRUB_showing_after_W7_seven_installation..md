---
title: "No GRUB showing after W7 seven installation."
date: 2011-04-21
forum: Installation &amp; Upgrades
---

### Post by silentrock on 2011-04-21
Hello everybody i will give you a detailed explanation of my current situation and relevant events so you can get the idea.
 
I've been an Ubuntu user for around a year now,i used to dual boot Ubuntu with Windows Vista until around 6 months ago when Vista stopped working and i cleared that whole partition but today i decided that it was time to bring Windows back into my life so i installed Windows 7 in the the old Vista's partition but for my surprise when i rebooted the PC GRUB wasn't showing anymore,just the windows boot loader.
 
I know that my other partitions (Ubuntu and swap) are still there i just checked them,but the problem is that GRUB wont show up to select between OS.
 
Anyway to install GRUB from Windows?
I don't want to install it through a LiveCD and all that,i would like to to it through Windows if possible.
 
Thanks for your time.
 
~Silent

---

### Post by Quackers on 2011-04-21
As far as I'm aware it must be done from a live cd.
It's easy enough though - just 2 commands.
From a live cd desktop open up a terminal and copy/paste the following commands in, one at a time, pressing enter after each line.
I am using /dev/sda5 as the example Ubuntu root partition, yours may be different. You can check by opening gparted from the live desktop. It will also be different if you have a separate Linux boot partition, or if you have more than one hard drive.
```
sudo mount /dev/sda5 /mnt
sudo grub-install --root-directory=/mnt /dev/sda
```

---

### Post by silentrock on 2011-04-21
Thanks for the quick response :p
Oh wait,i happen to have a Backtrack LiveUSB maybe that would help me.

---

### Post by Quackers on 2011-04-21
No problem. Good luck :-)
When done, if you reboot you should have Ubuntu booting directly. You will then need to run ```
sudo update-grub
``` in the terminal so that the Windows Loader is then picked up.

---

### Post by nakinaw on 2011-04-22
This is exactly what I was looking for, and its insane to me that while I was taking the time to register and search and all that jazz, you guys were acutally having this conversation.  
 
My question is this though, how do I check my partitions through Windows?  I had a dual boot with Vista and Ubuntu, and I had to reformat Vista.  I now have the same problem with grub not loading.  I made sure during the reformatting process that I kept the Linux partitions, but I would like to check to make sure they are still there.  
 
nakinaw

---

### Post by wilee-nilee on 2011-04-22
> **silentrock said:**
> Thanks for the quick response :p
Oh wait,i happen to have a Backtrack LiveUSB maybe that would help me.

Backtrack is grub-legacy use a cd equal to the install ie the same one.

@nakinaw, start a new thread all your own and do this, from a booted live Ubuntu cd or thumbdrive lets see the bootscript read out; in my signature just click on it and follow the instructions. Come back to the thread and click on the **(#)** in the reply panel this makes code tags paste all the text in between.

---

### Post by garvinrick4 on 2011-04-22
> My question is this though, how do I check my partitions through  Windows?  I had a dual boot with Vista and Ubuntu, and I had to reformat  Vista.  I now have the same problem with grub not loading.  I made sure  during the reformatting process that I kept the Linux partitions, but I  would like to check to make sure they are still there.  The code in a Live Cd or a linux install is:
sudo fdisk -l (lower case L)
then replace your sda# with your own in Quackers code and run in a terminal and you
will get grub back:

EDIT: Nakinaw you are most likely better off giving wilee-nilee his boot script and that will make sure you get it right. Who knows what your system looks
like after uninstalling a Windows product. 

** wilee-nilee was typing same time as you or would have kept out of thread, boot script is called for.**

---

### Post by silentrock on 2011-04-22
Is it highly necessary to use an Ubuntu LiveCD with the same distro i've got to install Gurb?
Cause it would be a blast if i could just download Puppy Linux and Install GRUB from there...Is it possible?

---

### Post by Quackers on 2011-04-22
As Wilee-nilee said earlier, it depends on what version of grub you are using. It's no good using a live cd that will install grub legacy if you need grub2.

---

### Post by silentrock on 2011-04-22
Hey i am running from Xubuntu 9.10 which should have the same GRUB version than Ubunut 10.04 and this is what i get:

```
ubuntu@ubuntu:~$ sudo grub-install --root-directory=/mnt /dev/sda
grub-probe: error: Cannot find a GRUB drive for /dev/sda2.  Check your device.map.

Auto-detection of a filesystem module failed.
Please specify the module with the option `--modules' explicitly.

```

This is my second attempt.on the first it kinda got stuck at the process so i restarted up the PC....any help? 
:/

---

### Post by silentrock on 2011-04-22
Wait the problem is because i had to run ```
sudo apt-get install grub
``` which i did on the first attempt but forgot to repeat and now that i run ```
 sudo grub-install --root-directory=/mnt  /dev/sda
``` 
i get this output 

```
ubuntu@ubuntu:~$ sudo grub-install --root-directory=/mnt /dev/sda
/dev/sda does not have any corresponding BIOS drive.

```

---

### Post by wilee-nilee on 2011-04-22
Do this; from a booted live Ubuntu cd or thumbdrive lets see the bootscript read out; in my signature just click on it and follow the instructions. Come back to the thread and click on the **(#)** in the reply panel this makes code tags paste all the text in between.

ret a iso of the installed ubuntu and burn it to a cd or load a usb flash drive.

---

### Post by silentrock on 2011-04-22
Here is the output of the script: THanks in advance.
Both partitions seem tu be well.

Note:/sdb1 is the LiveUSB which im botting Xubuntu from...just saying LOL


```
   Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda
 => Syslinux is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /menu.lst /boot.ini /bootmgr /boot/bcd 
                       /Windows/System32/winload.exe /grldr

sda2: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.1 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab

sda3: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda4: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Unknown
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 400.1 GB, 400088457216 bytes
255 heads, 63 sectors/track, 48641 cylinders, total 781422768 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x1549f232

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048   558,669,823   558,667,776   7 HPFS/NTFS
/dev/sda2         558,669,824   763,467,775   204,797,952  83 Linux
/dev/sda3         763,469,280   771,555,216     8,085,937  82 Linux swap / Solaris
/dev/sda4         771,569,820   781,417,664     9,847,845   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 7743 MB, 7743995904 bytes
80 heads, 16 sectors/track, 11816 cylinders, total 15124992 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xc3072e18

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *          8,064    15,124,991    15,116,928   b W95 FAT32


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        39E8312968242FCF                       ntfs       Lastra                        
/dev/sda2        7e17c99c-d902-454c-bb5a-0de792d909d9   ext4                                     
/dev/sda3        4c225650-9dfd-4e37-ad58-532852c42fa0   swap                                     
/dev/sda4        0294DF047781692D                       ntfs       BT                            
/dev/sdb1        CC5B-4546                              vfat                                     

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sdb1        /cdrom                   vfat       (rw)
/dev/loop0       /rofs                    squashfs   (rw)
/dev/sda2        /mnt                     ext4       (rw)


================================ sda1/menu.lst: ================================

timeout 0 
default 0 
title grub2 
find --set-root /boot/grub/core.img 
kernel /boot/grub/core.img 
boot
================================ sda1/boot.ini: ================================

[boot loader] 
timeout=0 
default=c:\grldr.mbr 
[operating systems] 
C:\grldr.mbr="Grub4Dos"
=================== sda1: Location of files loaded by Grub: ===================


    !!GB: menu.lst

=========================== sda2/boot/grub/grub.cfg: ===========================

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
set root='(hd0,2)'
search --no-floppy --fs-uuid --set 7e17c99c-d902-454c-bb5a-0de792d909d9
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
set root='(hd0,2)'
search --no-floppy --fs-uuid --set 7e17c99c-d902-454c-bb5a-0de792d909d9
set locale_dir=($root)/boot/grub/locale
set lang=en
insmod gettext
if [ ${recordfail} = 1 ]; then
  set timeout=-1
else
  set timeout=15
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry 'Ubuntu, with Linux 2.6.32-26-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,2)'
    search --no-floppy --fs-uuid --set 7e17c99c-d902-454c-bb5a-0de792d909d9
    linux    /boot/vmlinuz-2.6.32-26-generic root=UUID=7e17c99c-d902-454c-bb5a-0de792d909d9 ro  quiet vga=769  quiet splash
    initrd    /boot/initrd.img-2.6.32-26-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-26-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,2)'
    search --no-floppy --fs-uuid --set 7e17c99c-d902-454c-bb5a-0de792d909d9
    echo    'Loading Linux 2.6.32-26-generic ...'
    linux    /boot/vmlinuz-2.6.32-26-generic root=UUID=7e17c99c-d902-454c-bb5a-0de792d909d9 ro single  quiet vga=769
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-26-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-25-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,2)'
    search --no-floppy --fs-uuid --set 7e17c99c-d902-454c-bb5a-0de792d909d9
    linux    /boot/vmlinuz-2.6.32-25-generic root=UUID=7e17c99c-d902-454c-bb5a-0de792d909d9 ro  quiet vga=769  quiet splash
    initrd    /boot/initrd.img-2.6.32-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-25-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,2)'
    search --no-floppy --fs-uuid --set 7e17c99c-d902-454c-bb5a-0de792d909d9
    echo    'Loading Linux 2.6.32-25-generic ...'
    linux    /boot/vmlinuz-2.6.32-25-generic root=UUID=7e17c99c-d902-454c-bb5a-0de792d909d9 ro single  quiet vga=769
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-23-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,2)'
    search --no-floppy --fs-uuid --set 7e17c99c-d902-454c-bb5a-0de792d909d9
    linux    /boot/vmlinuz-2.6.32-23-generic root=UUID=7e17c99c-d902-454c-bb5a-0de792d909d9 ro  quiet vga=769  quiet splash
    initrd    /boot/initrd.img-2.6.32-23-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-23-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,2)'
    search --no-floppy --fs-uuid --set 7e17c99c-d902-454c-bb5a-0de792d909d9
    echo    'Loading Linux 2.6.32-23-generic ...'
    linux    /boot/vmlinuz-2.6.32-23-generic root=UUID=7e17c99c-d902-454c-bb5a-0de792d909d9 ro single  quiet vga=769
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-23-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,2)'
    search --no-floppy --fs-uuid --set 7e17c99c-d902-454c-bb5a-0de792d909d9
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=7e17c99c-d902-454c-bb5a-0de792d909d9 ro  quiet vga=769  quiet splash
    initrd    /boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,2)'
    search --no-floppy --fs-uuid --set 7e17c99c-d902-454c-bb5a-0de792d909d9
    echo    'Loading Linux 2.6.32-21-generic ...'
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=7e17c99c-d902-454c-bb5a-0de792d909d9 ro single  quiet vga=769
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd0,2)'
    search --no-floppy --fs-uuid --set 7e17c99c-d902-454c-bb5a-0de792d909d9
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd0,2)'
    search --no-floppy --fs-uuid --set 7e17c99c-d902-454c-bb5a-0de792d909d9
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sda2/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/sda2       /               ext4    errors=remount-ro 0       1
/dev/sda3       none            swap    sw              0       0

=================== sda2: Location of files loaded by Grub: ===================


 366.2GB: boot/grub/grub.cfg
 378.6GB: boot/initrd.img-2.6.32-21-generic
 378.6GB: boot/initrd.img-2.6.32-23-generic
 379.0GB: boot/initrd.img-2.6.32-25-generic
 380.5GB: boot/initrd.img-2.6.32-26-generic
 378.5GB: boot/vmlinuz-2.6.32-21-generic
 378.6GB: boot/vmlinuz-2.6.32-23-generic
 378.9GB: boot/vmlinuz-2.6.32-25-generic
 378.6GB: boot/vmlinuz-2.6.32-26-generic
 380.5GB: initrd.img
 379.0GB: initrd.img.old
 378.6GB: vmlinuz
 378.9GB: vmlinuz.old
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sdb1

00000000  eb 58 90 53 59 53 4c 49  4e 55 58 00 02 08 ea 0c  |.X.SYSLINUX.....|
00000010  02 00 00 00 00 f8 00 00  3f 00 ff 00 80 1f 00 00  |........?.......|
00000020  80 aa e6 00 8b 39 00 00  00 00 00 00 02 00 00 00  |.....9..........|
00000030  01 00 06 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000040  80 00 29 46 45 5b cc 4e  4f 20 4e 41 4d 45 20 20  |..)FE[.NO NAME  |
00000050  20 20 46 41 54 33 32 20  20 20 fa fc 31 c9 8e d1  |  FAT32   ..1...|
00000060  bc 76 7b 52 06 57 1e 56  8e c1 b1 26 bf 78 7b f3  |.v{R.W.V...&.x{.|
00000070  a5 8e d9 bb 78 00 0f b4  37 0f a0 56 20 d2 78 1b  |....x...7..V .x.|
00000080  31 c0 b1 06 89 3f 89 47  02 f3 64 a5 8a 0e 18 7c  |1....?.G..d....||
00000090  88 4d bc 50 50 50 50 cd  13 eb 5c 8b 55 aa 8b 75  |.M.PPPP...\.U..u|
000000a0  a8 c1 ee 04 01 f2 81 fa  b7 07 73 2b f6 45 b4 7f  |..........s+.E..|
000000b0  75 25 38 4d b8 74 20 66  3d 21 47 50 54 75 10 80  |u%8M.t f=!GPTu..|
000000c0  7d b8 ed 75 0a 66 ff 75  ec 66 ff 75 e8 eb 0f 51  |}..u.f.u.f.u...Q|
000000d0  51 66 ff 75 bc eb 07 51  51 66 ff 36 1c 7c b4 08  |Qf.u...QQf.6.|..|
000000e0  cd 13 72 13 20 e4 75 0f  c1 ea 08 42 89 16 1a 7c  |..r. .u....B...||
000000f0  83 e1 3f 89 0e 18 7c fb  bb aa 55 b4 41 8a 16 74  |..?...|...U.A..t|
00000100  7b cd 13 72 10 81 fb 55  aa 75 0a f6 c1 01 74 05  |{..r...U.u....t.|
00000110  c6 06 45 7d 00 66 b8 48  89 15 00 66 ba 00 00 00  |..E}.f.H...f....|
00000120  00 bb 00 7e e8 10 00 66  81 3e 24 7e d4 ff 73 72  |...~...f.>$~..sr|
00000130  75 76 ea 38 7e 00 00 66  03 06 60 7b 66 13 16 64  |uv.8~..f..`{f..d|
00000140  7b b9 10 00 eb 2b 66 52  66 50 06 53 6a 01 6a 10  |{....+fRfP.Sj.j.|
00000150  89 e6 66 60 b4 42 e8 7f  00 66 61 8d 64 10 72 01  |..f`.B...fa.d.r.|
00000160  c3 66 60 31 c0 e8 70 00  66 61 e2 da c6 06 45 7d  |.f`1..p.fa....E}|
00000170  2b 66 60 66 0f b7 36 18  7c 66 0f b7 3e 1a 7c 66  |+f`f..6.|f..>.|f|
00000180  f7 f6 31 c9 87 ca 66 f7  f7 66 3d ff 03 00 00 77  |..1...f..f=....w|
00000190  17 c0 e4 06 41 08 e1 88  c5 88 d6 b8 01 02 e8 37  |....A..........7|
000001a0  00 66 61 72 01 c3 e2 c9  31 f6 8e d6 bc 68 7b 8e  |.far....1....h{.|
000001b0  de 66 8f 06 78 00 be df  7d e8 09 00 31 c0 cd 16  |.f..x...}...1...|
000001c0  cd 19 f4 eb fd 66 60 ac  20 c0 74 09 b4 0e bb 07  |.....f`. .t.....|
000001d0  00 cd 10 eb f2 66 61 c3  8a 16 74 7b cd 13 c3 42  |.....fa...t{...B|
000001e0  6f 6f 74 20 65 72 72 6f  72 0d 0a 00 00 00 00 00  |oot error.......|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


=======Devices which don't seem to have a corresponding hard drive==============

sdc sdd sde sdf sdg 
  
```

---

### Post by garvinrick4 on 2011-04-22
1.You got way to much going on in sda1, need to reinstall windows boot from Windows Recovery disk.
Do that first: Directions in this link: Just two commands.
[Grub/XP/Vista Bootloader - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=1014708") 
2.  Missing files in sda2.You need to purge all in sda2 just purge grub grub-common grub-pc all three items as instructed here and reinstall grub-common and grub-pc.  as instructed here below. 
[HOWTO: Purge and Reinstall Grub 2 from the Live CD - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=1581099")

**Just follow instructions and will be okay. Looks like you have been trying a lot of things.

---

### Post by silentrock on 2011-04-22
Yeah i tried using Grub4dos and Wingrub but not worked...Thanks gonna try that and psot results ;) Thanks.

---

### Post by silentrock on 2011-04-23
Wow Thanks everybody everything went smoothly and i reinstalled Grub2 successfully with the help of this two guides:

For reinstalling Windows MBR: [http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

For purging and reinstalling GRUB2: [http://ubuntuforums.org/showthread.php?t=1581099](http://ubuntuforums.org/showthread.php?t=1581099)


Thanks Quackers,Wilee-nille and  garvinrick4

---

### Post by Quackers on 2011-04-23
Aha! That's good :-)
Happy Ubuntu-ing!

---

