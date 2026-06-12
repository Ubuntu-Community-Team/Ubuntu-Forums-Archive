---
title: "Unable to boot Win XP after installing Ubuntu 10.04. Please someone help!!!"
date: 2010-07-22
forum: Installation &amp; Upgrades
---

### Post by sibisiva on 2010-07-22
First of all, I am new to Ubuntu. It is a great experience. Linux rocks...:KS

I installed Ubuntu 9.10 on my second hard disk(80GB). My first hard disk(40GB) already hosts my Windows XP on the C: partition and also the IBM factory recovery image for XP on another partition. (My system is nearly 6 years old).

First I was able to boot to XP(through GRUB, which was installed by default).:)

Then I upgraded to Ubuntu 10.04 directly through internet from the Ubuntu 9.10. The grub was also automatically upgraded and it shows my XP and recovery OS as well perfectly.:|

But when i select XP or the recovery, the OS doesn't boot and only a cursor is blinking for eternity. The processor is working heavily(which i can make out from the deafening fan speed). And all left for my option is switching off directly. But booting ubuntu causes no problem.:(:(:(

Now, i want to solve this problem and without losing any valuable data that i have in that hard-disk. :confused:
Please help friends... My only hope lies with you...
Thank you in advance and anticipation...[-o<

---

### Post by lechien73 on 2010-07-22
In the immortal words of Douglas Adams - Don't Panic :)

If you have a Windows XP CD, then boot from it and go to the recovery console. Type:

```
fixboot
```

And that should repair the boot sector of your disc. These links might help you: [http://uri.tl/8](http://uri.tl/8) and [http://uri.tl/c](http://uri.tl/c)

---

### Post by kansasnoob on 2010-07-22
> **sibisiva said:**
> First of all, I am new to Ubuntu. It is a great experience. Linux rocks...:KS

I installed Ubuntu 9.10 on my second hard disk(80GB). My first hard disk(40GB) already hosts my Windows XP on the C: partition and also the IBM factory recovery image for XP on another partition. (My system is nearly 6 years old).

First I was able to boot to XP(through GRUB, which was installed by default).:)

Then I upgraded to Ubuntu 10.04 directly through internet from the Ubuntu 9.10. The grub was also automatically upgraded and it shows my XP and recovery OS as well perfectly.:|

But when i select XP or the recovery, the OS doesn't boot and only a cursor is blinking for eternity. The processor is working heavily(which i can make out from the deafening fan speed). And all left for my option is switching off directly. But booting ubuntu causes no problem.:(:(:(

Now, i want to solve this problem and without losing any valuable data that i have in that hard-disk. :confused:
Please help friends... My only hope lies with you...
Thank you in advance and anticipation...[-o<

Please post the output of the Boot Info Script as described here:

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

It's likely that you'll need to change more than one MBR!

---

### Post by sibisiva on 2010-07-23
> **kansasnoob said:**
> Please post the output of the Boot Info Script as described here:

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

It's likely that you'll need to change more than one MBR!

Here goes the results for the boot info script:
```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #9 for /grub.
 => Grub 2 is installed in the MBR of /dev/sdb and looks on the same drive in 
    partition #9 for /grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sda1 and 
                       looks at sector 1028798 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location. No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /BOOT.INI /ntldr /NTDETECT.COM

sda2: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sda2 and 
                       looks at sector 1016510 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location. No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM /COMMAND.COM

sdb1: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sdb5 and 
                       looks at sector 1016190 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location. According to the info in the boot sector, 
                       sdb5 starts at sector 63.
    Operating System:  
    Boot files/dirs:   

sdb6: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sdb6 and 
                       looks at sector 1028798 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location. According to the info in the boot sector, 
                       sdb6 starts at sector 63.
    Operating System:  
    Boot files/dirs:   

sdb7: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sdb7 and 
                       looks at sector 1020094 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location. According to the info in the boot sector, 
                       sdb7 starts at sector 63.
    Operating System:  
    Boot files/dirs:   

sdb8: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sdb8 and 
                       looks at sector 1020606 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location. According to the info in the boot sector, 
                       sdb8 starts at sector 63.
    Operating System:  
    Boot files/dirs:   

sdb9: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sdb9 and 
                       looks at sector 1015998 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location.
    Operating System:  
    Boot files/dirs:   /grub/grub.cfg /grub/core.img

sdb10: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04 LTS
    Boot files/dirs:   /etc/fstab

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 40.0 GB, 40016019456 bytes
255 heads, 63 sectors/track, 4865 cylinders, total 78156288 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xcccdcccd

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63    70,557,479    70,557,417   7 HPFS/NTFS
/dev/sda2          70,557,480    78,156,224     7,598,745  12 Compaq diagnostics


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xe423b127

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63       996,029       995,967  82 Linux swap / Solaris
/dev/sdb2             996,030   156,280,319   155,284,290   f W95 Ext d (LBA)
/dev/sdb5          32,772,663    65,545,199    32,772,537   7 HPFS/NTFS
/dev/sdb6          65,545,263    98,317,799    32,772,537   7 HPFS/NTFS
/dev/sdb7          98,317,863   131,090,399    32,772,537   7 HPFS/NTFS
/dev/sdb8         131,090,463   156,280,319    25,189,857   7 HPFS/NTFS
/dev/sdb9             996,156     1,381,589       385,434  83 Linux
/dev/sdb10          1,381,653    32,772,599    31,390,947  83 Linux


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/ramzswap0                                          swap                                     
/dev/sda1        E4808A0D8089E680                       ntfs       Ganeshiva                     
/dev/sda2        1B33-0A00                              vfat       IBM_SERVICE                   
/dev/sdb10       792ab2c1-e3ed-454d-9607-9482e4ffb350   ext4                                     
/dev/sdb1        f870c1cc-cabe-4a90-96a0-4c87c87b2f03   swap                                     
/dev/sdb5        B26836C7683689DD                       ntfs       My Pictures                   
/dev/sdb6        F87001317000F860                       ntfs       Softwares                     
/dev/sdb7        8C40176440175474                       ntfs       My Documents                  
/dev/sdb8        16E44536E445197F                       ntfs       My Music                      
/dev/sdb9        734080ca-57c7-4e5b-be5d-b6afdca4872a   ext4                                     

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (rw)
/dev/loop0       /rofs                    squashfs   (rw)
/dev/sdb10       /media/792ab2c1-e3ed-454d-9607-9482e4ffb350 ext4       (rw,nosuid,nodev,uhelper=devkit)


================================ sda1/BOOT.INI: ================================

[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /fastdetect 

================================ sda2/boot.ini: ================================

[boot loader] 
timeout=0 
default=C:\ 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(4)\WINDOWS="Microsoft Windows XP Professional" /fastdetect 
C:\ = "PC-DOS" 

============================= sdb9/grub/grub.cfg: =============================

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
set root='(hd1,10)'
search --no-floppy --fs-uuid --set 792ab2c1-e3ed-454d-9607-9482e4ffb350
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
set root='(hd1,9)'
search --no-floppy --fs-uuid --set 734080ca-57c7-4e5b-be5d-b6afdca4872a
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
    set root='(hd1,9)'
    search --no-floppy --fs-uuid --set 734080ca-57c7-4e5b-be5d-b6afdca4872a
    linux    /vmlinuz-2.6.32-23-generic root=UUID=792ab2c1-e3ed-454d-9607-9482e4ffb350 ro   quiet splash
    initrd    /initrd.img-2.6.32-23-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-23-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,9)'
    search --no-floppy --fs-uuid --set 734080ca-57c7-4e5b-be5d-b6afdca4872a
    echo    'Loading Linux 2.6.32-23-generic ...'
    linux    /vmlinuz-2.6.32-23-generic root=UUID=792ab2c1-e3ed-454d-9607-9482e4ffb350 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /initrd.img-2.6.32-23-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd1,9)'
    search --no-floppy --fs-uuid --set 734080ca-57c7-4e5b-be5d-b6afdca4872a
    linux16    /memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd1,9)'
    search --no-floppy --fs-uuid --set 734080ca-57c7-4e5b-be5d-b6afdca4872a
    linux16    /memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Professional (on /dev/sda1)" {
    insmod ntfs
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set e4808a0d8089e680
    drivemap -s (hd0) ${root}
    chainloader +1
}
menuentry "Windows NT/2000/XP (on /dev/sda2)" {
    insmod fat
    set root='(hd0,2)'
    search --no-floppy --fs-uuid --set 1b33-0a00
    drivemap -s (hd0) ${root}
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=================== sdb9: Location of files loaded by Grub: ===================


    .5GB: grub/core.img
    .5GB: grub/grub.cfg
    .5GB: initrd.img-2.6.32-23-generic
    .5GB: vmlinuz-2.6.32-23-generic

=============================== sdb10/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sdb10 during installation
UUID=792ab2c1-e3ed-454d-9607-9482e4ffb350 /               ext4    errors=remount-ro 0       1
# /boot was on /dev/sdb9 during installation
UUID=734080ca-57c7-4e5b-be5d-b6afdca4872a /boot           ext4    defaults        0       2
# swap was on /dev/sdb1 during installation
UUID=f870c1cc-cabe-4a90-96a0-4c87c87b2f03 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
```:)

---

### Post by sibisiva on 2010-07-23
> **lechien73 said:**
> In the immortal words of Douglas Adams - Don't Panic :)

If you have a Windows XP CD, then boot from it and go to the recovery console. Type:

```
fixboot
```And that should repair the boot sector of your disc. These links might help you: [http://uri.tl/8](http://uri.tl/8) and [http://uri.tl/c](http://uri.tl/c)

As you told, tried to boot with XP CD. But same problem still persists.:(
The system wont just boot with the XP CD. Again the same, cursor blinking forever.:(
But, with Ubuntu 9.10 CD it works just too happily.

Is my system totally hating Windows after getting introduced to Linux???:shock::?

Please help!!!

---

### Post by oldfred on 2010-07-23
You installed grub2 to the windows partitions boot sectors that contain essential windows boot info.

Boot sector info:  Grub 2 is installed in the boot sector of sda1
Boot sector info:  Grub 2 is installed in the boot sector of sda2

The fixboot command is the windows way. 

You need to run testdisk twice once for sda1 and once for sda2.
Fix for most, a few have other issues, better than windows fix in many cases as it also fixes other parameters:
This has instructions on using testdisk to repair the install of grub to the boot sector for windows from Ubuntu or Linux LiveCD.
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector)

---

### Post by rawlins02 on 2010-07-23
I believe I've been through a similar problem on my new Dell that came with Windoze 7. For me, the problem was likely related to Dell DataSafe local backup on Windows:

[http://kubuntuforums.net/forums/index.php?action=printpage;topic=3111662.0](http://kubuntuforums.net/forums/index.php?action=printpage;topic=3111662.0)
[http://ubuntuforums.org/showthread.php?t=1459782](http://ubuntuforums.org/showthread.php?t=1459782)

Initial test is encouraging. I uninstalled that Dell DataSafe program, then manually set partitions, while installing Ubuntu 10.04. Now, after booting to Windoze, I still get GRUB 2 boot menu and no longer get an error saying the machine can't find an OS.

---

### Post by csnather on 2010-07-23
im having same exact problem new to linux set up dual boot first go around with ubuntu after update get same blinking light i wonder if i made a mistake in update process. when i set up dual boot initially linux gave me option for some kind of shared space between windows and linux so i can access files but without xp all programs lost

---

### Post by oldfred on 2010-07-24
csnather, Welcome to the forum.

Not sure if your problem relates to this thread. If above solutions do not work, please open a new thread post the boot_script from link above and explain exactly what is wrong.

---

### Post by sibisiva on 2010-08-06
> **lechien73 said:**
> In the immortal words of Douglas Adams - Don't Panic :)

If you have a Windows XP CD, then boot from it and go to the recovery console. Type:

```
fixboot
```And that should repair the boot sector of your disc. These links might help you: [http://uri.tl/8](http://uri.tl/8) and [http://uri.tl/c](http://uri.tl/c)

As you told, i gave the fixboot and fixmbr and windows works fine!
Thank you very much!

Now how to make dual boot with ubuntu and win XP? i dont want to lose either. Please suggest a nice solution...:D

---

### Post by oldfred on 2010-08-06
When you did fixMBR you reinstalled the windows boot loader to the MBR of sda. But you have or had grub2 also installed to sdb. Try booting from sdb. Either change BIOS or use f12 (or what ever key is single boot choice) to select sdb.

If grub2 is still ok in sdb it should boot. If it does not show windows correctly, then after you boot Ubuntu run this:

sudo update-grub

---

### Post by sibisiva on 2010-08-12
Wow! Great! The system now runs perfectly to my wish!
Thanks to you all for helping me out to sort out the issue!
Thank you once again!:D:D:D:D:D:D:D:D

---

### Post by Aterruit on 2010-08-14
Hi, I recently installed ubuntu UE onto my computer. It is a ASUS G73 GX and now I cannot boot windows, or linux, without first using the SUPERGRUB Cd. Below is my informations from my results.txt PLEASE help me. Having a sweet computer is useless when you can't use it to it's full potential.

---

### Post by oldfred on 2010-08-15
Aterruit, You should start a new thread as most of us who are helping will not look at solved threads.

You have a windows type boot loader (lilo) in the MBR. Lilo like windows then jumps to the active partition (boot flag). If you want to boot windows move the boot flag back to sda3.

If you want to boot Ubuntu you have to reinstall grub2. Yours is in sda1. So from liveCD you should only have to run the red commands below.

How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)
[https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD](https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD)

Install MBR from LiveCD, Ubuntu install on sda1 and want grub2 in drive sda's MBR:
Find linux partition, change sda1 if not correct, and/or even sda if sdb wanted:
sudo fdisk -l
[COLOR=DarkRed]sudo mount /dev/sda1 /mnt
sudo grub-install --root-directory=/mnt /dev/sda[/COLOR]
If that returns any errors run:
sudo grub-install --recheck --root-directory=/mnt /dev/sda

You grub.cfg does not show windows yet. So after rebooting into Ubuntu. This should add windows:
sudo update-grub

---

### Post by Aterruit on 2010-08-15
Thanks oldfred for your advice. I will post this thread elsewhere as well. What I would like to do is dual boot between windows and linux. How would I do this?

---

### Post by Aterruit on 2010-08-15
Ok. So far I can now boot my computer after following the instructions from this link: [https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD](https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD)

But now I can only boot Ubuntu UE. How do I make it so that I can boot windows too?

---

### Post by oldfred on 2010-08-15
sudo update-grub

That should find your windows install and let you then boot it on reboot. If not you may have other issues.

---

### Post by Aterruit on 2010-08-15
I just ran that in terminal, and I'm rebooting my computer now. I will let you know what happens. Give me one minute.

---

### Post by Aterruit on 2010-08-15
I just restarted my computer. It still only boots ubuntu. Now what would you like me to do?

---

### Post by oldfred on 2010-08-15
Start your own thread and post this. As I prefer that others can also look at your problem and then you can post it solved when we fix it. 

Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the post's menu and then paste the contents between the generated [ code][ /code] tags.

---

### Post by Aterruit on 2010-08-15
I already have started a new thread. Here is the link:[http://ubuntuforums.org/showthread.php?t=1553778](http://ubuntuforums.org/showthread.php?t=1553778)

---

