---
title: "Adding space to the system drive"
date: 2011-08-22
forum: Installation &amp; Upgrades
---

### Post by YasinG on 2011-08-22
hi guys, when i first installed ubuntu i cut up 20 gb from one of my drives and put ubuntu in it, because i still had xp. Now i want to add extra space. can i do that ?
please be over explanatory since i'm not that good with it yet.
Thanks in advance

---

### Post by lmarmisa on 2011-08-22
I suppose you are not running Ubuntu with Wubi.

The procedure for resizing your system partition requires an Ubuntu Live CD / USB and the use of the tool Gparted. But, the exact steps to follow depends on the partitions of your hard drive.

Please, open a terminal and post the output of this command:

```

sudo fdisk -l

```

---

### Post by YasinG on 2011-08-22
Here it is:

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x77777777

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4844    38909398+   7  HPFS/NTFS
/dev/sda2            4845       30400   205278539+   f  W95 Ext'd (LBA)
/dev/sda5            4845       14990    81496554+   7  HPFS/NTFS
/dev/sda6           17623       30400   102639253+   7  HPFS/NTFS
/dev/sda7           14990       15245     2048000   82  Linux swap / Solaris
/dev/sda8           15246       17622    19092480   83  Linux

Partition table entries are not in disk order

ps: what is wubi?

---

### Post by rcayea on 2011-08-22
I have before been in your same situation. I don't know if it will work for you, but I just downloaded EASEUS Partition Manager (it is free) and I expanded my linux partition that way. Then it told me to reboot and when it rebooted, the computer partitioned the space and I was on my way.

---

### Post by lmarmisa on 2011-08-23
Wubi is an special version of Ubuntu. The system and swap partitions of Wubi are not physical but they are files of Windows. Anyway, do not worry about Wubi because you are not running it. 

You have defined several NTFS partitions in your hard drive. I see 3 partitions with 38,5 GB, 81.5 GB and 102 GB.

I would appreciate if you could explain what type of information (XP, personal files, etc) is stored in each partition.

---

### Post by YasinG on 2011-08-30
Sorry for replying so late, I have been incredibly busy.
The 38.5 GB drive contains the XP files wich I don't need.
The 81.5 GB drive contains personal files, it was 100 GB before i cut 20 for UBUNTU 
The last drive has personal information too.
I want to move UBUNTU on the 38.5 GB drive.
Thanks in advance.

---

### Post by Iantos on 2011-08-30
download easus partition manager, install it in xp partition...and then open it and you will be able to see all your partitions there, resize, decrease and move whatever partition as you wish.

---

### Post by fdrake on 2011-08-30
i have never tried EASEUS Partition Manager, but there is always a chance that you will encounter errors with grub after the resizing. also keeping files all in different partitions is a better and safer thing to do in case of crashes or corruptions. Why do not create a folder in win partition and store there your data from UBUNTU. in this case you will be able to share the data easily between the systems. You can mount the win folder in ubuntu like you do with partitions automatically in fstab too.

---

### Post by YasinG on 2011-08-30
Ok here's the update. I had my friend make me a live cd on my flash drive and started Gparted and copied the UBUNTU drive into the 38.5 drive.
Now in the black screen i get my normal ubuntu generic and ubuntu generic (recovery mode) and two memory tests, i don't really understand why but they have always been there since i installed UBUNTU, plus a new choice: Previous versions, when i press enter on that i get another screen where there is two Ubuntus like this:

Ubuntu generic <some numbers like the ones on the previous screen but 10 instead of eleven >
Ubuntu generic <some numbers like the ones on the previous screen but 10 instead of eleven > ( recovery mode)

Ubuntu generic <some numbers like the ones on the previous screen but 10 instead of eleven >
Ubuntu generic <some numbers like the ones on the previous screen but 10 instead of eleven > recovery mode)

I didn't repeat myself that's how they are shown , two identical Ubuntus.
My question is what are those ? are they the copy that i made ? and why there is two when i only copied one? notice there is another one thats in the previous screen, the old one.
And can i delete the one that's in the 20 GB now or i should keep it in case ?
Thanks for your answers everyone, i deeply appreciate this.
Yasin

---

### Post by YesWeCan on 2011-08-30
Hi. Your system won't boot if you delete the original Ubuntu so don't do that yet.

Did you do a copy & paste in GParted? Pretty slick feature, I think. But if you did it this way there are a few things you need to do to make things work. If you did not do it this way then ignore the following instructions. This also assumes you are using Grub2. If not, don't do this.

You should boot from live CD (same version as the installed) to do this:

1) The UUID for the new Ubuntu partition will be the same as the old one and this will confuse the boot and filesystem mounting process.
[COLOR=Navy]sudo blkid[/COLOR]
will show you the UUIDs for all partitions. If your new one (sda1 I guess?) is the same as the old one sda8 then you'll need to change it.
[COLOR=Navy]sudo tune2fs -U random /dev/sda1[/COLOR]
then run
[COLOR=Navy]sudo blkid[/COLOR]
and see the new, unique UUID for sda1. You'll need this for the next step.

2) The fstab file in the new Ubuntu will have the wrong UUID for its root (/) entry. So you need to edit it and change the UUID to the new one for sda1:
[COLOR=Navy]sudo mount /dev/sda1 /mnt
sudo gedit /mnt/etc/fstab
[/COLOR]
3) You need to reinstall Grub so that it works using files in your new Ubuntu:
[COLOR=Navy]sudo grub-install --root-directory=/mnt /dev/sda[/COLOR]

Now you can reboot into the first Ubuntu on the menu.
Check this is the new Ubuntu by looking at which partition / is mounted on. It should be sda1
[COLOR=Navy]mount[/COLOR]

If all that checks out, you can go ahead and delete the old Ubuntu in sda8. If any of that is not clear enough just ask.

---

### Post by YasinG on 2011-08-30
hi YesWeCan, I did a copy & paste in Gparted, but i have no idea what grub2 is and whether or not i'm using it. is there a way to find that out ?
By the way the UUID for my sda1 is the same as the UUID for my sda8, which is the old one.

---

### Post by YesWeCan on 2011-08-30
Yes. From live CD, assuming your new Ubuntu partition is sda1 (tell me what it is if it isn't)
[COLOR=Navy]sudo mount /dev/sda1 /mnt
ls /mnt/boot/grub[/COLOR]
and if there is a file named grub.cfg and if there is not a file named menu.lst you have Grub2.
BTW which version of ubuntu are you using?

---

### Post by YesWeCan on 2011-08-30
> **YasinG said:**
> By the way the UUID for my sda1 is the same as the UUID for my sda8, which is the old one.
Indeed. sda1 needs to be given a new UUID of its own to avoid confusion with sda8, as per my previous post. When GParted does a copy and paste it does not do this.

---

### Post by YesWeCan on 2011-08-30
BTW you might be wondering why I don't just say to delete sda8 right now so there is no UUID conflict. That would work. But I am cautious and I think it better to make sure the new Ubuntu is working properly *before* you delete the old one.

---

### Post by YasinG on 2011-08-30
I'm running Ubuntu 11.04, i don't know the name of it but it's something complicated and russain-like.
so i typed in terminal 
[COLOR=Navy]sudo mount /dev/sda1 /mnt
ls /mnt/boot/grub
[COLOR=Black]and it gave me the no such file message[/COLOR].
[/COLOR]

---

### Post by YesWeCan on 2011-08-30
What does [COLOR=Navy]ls /mnt[/COLOR] show?

---

### Post by YasinG on 2011-08-30
Sorry I didn't boot from the live cd, that's why it wouldn't show.
You were right, grub.cfg is there and no menu.lst, so i'm using grub. Shall I execute the rest of the steps in your first post ?

---

### Post by YesWeCan on 2011-08-30
Go ahead. I have to go now but I'll check back tomorrow.

---

### Post by YasinG on 2011-08-30
I still says it's mounted on sda8
/dev/sda8 on / type ext4 (rw,errors=remount-ro,user_xattr,commit=0)
proc on /proc type proc (rw,noexec,nosuid,nodev)
...

---

### Post by YesWeCan on 2011-08-30
Ok, it may be the new ubuntu is further down the boot menu list. Yes, that may be right because we havent updated grub yet.

try that.

if that doesnt work, boot sda8 again and run
sudo update-grub
sudo grub-install /dev/sda

then reboot and select the new ubuntu at the end of the menu
check using mount that sda1 is on /
if so, again do
sudo update-grub
sudo grub-install /dev/sda

then reboot and the first menu entry should take you to sda1

---

### Post by YasinG on 2011-08-30
This is what i get after the last step in your first post:

[COLOR=Blue]ubuntu@ubuntu:~$ sudo grub-install --root-directory=/mnt /dev/sda
/usr/sbin/grub-setup: warn: Sector 32 is already in use by FlexNet;  avoiding it.  This software may cause boot or other problems in future.   Please ask its authors not to store data in the boot track.
Installation finished. No error reported.[/COLOR]

I'll reboot now and check.

---

### Post by YesWeCan on 2011-08-30
That warning is a long story to explain right now. Its due to residue from a Windows app.

---

### Post by YasinG on 2011-08-30
Ok, never mind about the warning.
I did this step:

[COLOR=Red]if that doesnt work, boot sda8 again and run
sudo update-grub
sudo grub-install /dev/sda

then reboot and select the new ubuntu at the end of the menu
check using mount that sda1 is on /[/COLOR]
and the same thing happened:

[COLOR=Blue]/dev/sda8 on / type ext4 (rw,errors=remount-ro,user_xattr,commit=0)
proc on /proc type proc (rw,noexec,nosuid,nodev)[/COLOR]

There is something new though. In the boot menu, there is about three Ubuntus. But each one has the <> brackets beside it stating on which partition it's mounted, i chose the one with sda1, but it still shows the previous message. Could it be i'm writing the mount command wrongly ? I just type [COLOR=Blue]mount[/COLOR] right ?

---

### Post by YesWeCan on 2011-08-30
you edited the fstab in sda1 and gave / the new UUID for sda1?

if it still has the sda8 uuid then it will mount the root partition in sda8.

---

### Post by YasinG on 2011-08-30
Yes i did. Here is the fstab file:
[COLOR=Blue]
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda8 during installation
UUID=88118626-5482-45ab-8f03-c2d131752aa9 /               ext4    errors=remount-ro,user_xattr 0       1
# swap was on /dev/sda7 during installation
UUID=978c7491-f17e-4adf-9882-32a1ef3c3071 none            swap    sw              0       0
[/COLOR]
And this is the UUID of the sda1:

[COLOR=Blue]/dev/sda1: UUID="88118626-5482-45ab-8f03-c2d131752aa9" TYPE="ext4" [/COLOR]

IT's the same.

---

### Post by YesWeCan on 2011-08-30
That fstab file looks good.
The sda8 uuid is different, right?
Im am going to have to go. I'll check back tomorrow. it would be helpful for others who may want to assist if you post the bootinfoscript output.

---

### Post by YasinG on 2011-08-30
Yes it's different.
Here is the bootinfoscript output:
```

                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (,msdos8)/boot/grub on this drive.
 => Syslinux MBR (3.61-4.03) is installed in the MBR of /dev/sdb.

sda1: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.04
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:   According to the info in the boot sector, sda5 starts 
                       at sector 63.
    Operating System:  
    Boot files:        

sda6: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:   According to the info in the boot sector, sda6 starts 
                       at sector 63.
    Operating System:  
    Boot files:        

sda7: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda8: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.04
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  SYSLINUX 4.02 debian-20101016 ...........>...r>........G8....0...~.k...~...f...M.f.f....f..8~....>2}
    Boot sector info:   Syslinux looks at sector 3420256 of /dev/sdb1 for its 
                       second stage. SYSLINUX is installed in the  directory. 
                       The integrity check of the ADV area failed. No errors 
                       found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /syslinux/syslinux.cfg /ldlinux.sys

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *             63    77,818,859    77,818,797  83 Linux
/dev/sda2          77,818,921   488,375,999   410,557,079   f W95 Extended (LBA)
/dev/sda5          77,818,923   240,812,031   162,993,109   7 NTFS / exFAT / HPFS
/dev/sda6         283,097,493   488,375,999   205,278,507   7 NTFS / exFAT / HPFS
/dev/sda7         240,814,080   244,910,079     4,096,000  82 Linux swap / Solaris
/dev/sda8         244,912,128   283,097,087    38,184,960  83 Linux


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 7873 MB, 7873757184 bytes
255 heads, 63 sectors/track, 957 cylinders, total 15378432 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1    *             63    15,378,431    15,378,369   b W95 FAT32


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        88118626-5482-45ab-8f03-c2d131752aa9   ext4       
/dev/sda5        249096089095E11A                       ntfs       Mein
/dev/sda6        AE0804BB08048515                       ntfs       Sweet
/dev/sda7        978c7491-f17e-4adf-9882-32a1ef3c3071   swap       
/dev/sda8        93efeb51-de8e-4240-8163-0c812b73a9a6   ext4       
/dev/sdb1        4446-0923                              vfat       YASIN

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sdb1        /cdrom                   vfat       (ro,noatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)


=========================== sda1/boot/grub/grub.cfg: ===========================

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
set root='(/dev/sda,msdos8)'
search --no-floppy --fs-uuid --set=root 93efeb51-de8e-4240-8163-0c812b73a9a6
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos8)'
search --no-floppy --fs-uuid --set=root 93efeb51-de8e-4240-8163-0c812b73a9a6
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
    set root='(/dev/sda,msdos8)'
    search --no-floppy --fs-uuid --set=root 93efeb51-de8e-4240-8163-0c812b73a9a6
    linux    /boot/vmlinuz-2.6.38-11-generic root=UUID=93efeb51-de8e-4240-8163-0c812b73a9a6 ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-2.6.38-11-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-11-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos8)'
    search --no-floppy --fs-uuid --set=root 93efeb51-de8e-4240-8163-0c812b73a9a6
    echo    'Loading Linux 2.6.38-11-generic ...'
    linux    /boot/vmlinuz-2.6.38-11-generic root=UUID=93efeb51-de8e-4240-8163-0c812b73a9a6 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.38-11-generic
}
submenu "Previous Linux versions" {
menuentry 'Ubuntu, with Linux 2.6.38-10-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos8)'
    search --no-floppy --fs-uuid --set=root 93efeb51-de8e-4240-8163-0c812b73a9a6
    linux    /boot/vmlinuz-2.6.38-10-generic root=UUID=93efeb51-de8e-4240-8163-0c812b73a9a6 ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-2.6.38-10-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-10-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos8)'
    search --no-floppy --fs-uuid --set=root 93efeb51-de8e-4240-8163-0c812b73a9a6
    echo    'Loading Linux 2.6.38-10-generic ...'
    linux    /boot/vmlinuz-2.6.38-10-generic root=UUID=93efeb51-de8e-4240-8163-0c812b73a9a6 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.38-10-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-8-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos8)'
    search --no-floppy --fs-uuid --set=root 93efeb51-de8e-4240-8163-0c812b73a9a6
    linux    /boot/vmlinuz-2.6.38-8-generic root=UUID=93efeb51-de8e-4240-8163-0c812b73a9a6 ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-2.6.38-8-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-8-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos8)'
    search --no-floppy --fs-uuid --set=root 93efeb51-de8e-4240-8163-0c812b73a9a6
    echo    'Loading Linux 2.6.38-8-generic ...'
    linux    /boot/vmlinuz-2.6.38-8-generic root=UUID=93efeb51-de8e-4240-8163-0c812b73a9a6 ro single 
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
    set root='(/dev/sda,msdos8)'
    search --no-floppy --fs-uuid --set=root 93efeb51-de8e-4240-8163-0c812b73a9a6
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos8)'
    search --no-floppy --fs-uuid --set=root 93efeb51-de8e-4240-8163-0c812b73a9a6
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Professional (on /dev/sda1)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(/dev/sda,msdos1)'
    search --no-floppy --fs-uuid --set=root EE98EC2198EBE5D5
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
--------------------------------------------------------------------------------

=============================== sda1/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda8 during installation
UUID=88118626-5482-45ab-8f03-c2d131752aa9 /               ext4    errors=remount-ro,user_xattr 0       1
# swap was on /dev/sda7 during installation
UUID=978c7491-f17e-4adf-9882-32a1ef3c3071 none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sda1: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

   6.164390087 = 6.618963456    boot/grub/core.img                             1
   8.862544537 = 9.516084736    boot/grub/grub.cfg                             1
  11.507232189 = 12.355796480   boot/initrd.img-2.6.38-10-generic              2
  14.960967541 = 16.064216576   boot/initrd.img-2.6.38-11-generic              2
   7.835967541 = 8.413806080    boot/initrd.img-2.6.38-8-generic               2
  10.816745281 = 11.614391808   boot/vmlinuz-2.6.38-10-generic                 1
   2.680026531 = 2.877656576    boot/vmlinuz-2.6.38-11-generic                 1
   6.236121655 = 6.695984640    boot/vmlinuz-2.6.38-8-generic                  1
  14.960967541 = 16.064216576   initrd.img                                     2
  11.507232189 = 12.355796480   initrd.img.old                                 2
   2.680026531 = 2.877656576    vmlinuz                                        1
  10.816745281 = 11.614391808   vmlinuz.old                                    1

=========================== sda8/boot/grub/grub.cfg: ===========================

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
set root='(/dev/sda,msdos8)'
search --no-floppy --fs-uuid --set=root 93efeb51-de8e-4240-8163-0c812b73a9a6
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos8)'
search --no-floppy --fs-uuid --set=root 93efeb51-de8e-4240-8163-0c812b73a9a6
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
    set root='(/dev/sda,msdos8)'
    search --no-floppy --fs-uuid --set=root 93efeb51-de8e-4240-8163-0c812b73a9a6
    linux    /boot/vmlinuz-2.6.38-11-generic root=UUID=93efeb51-de8e-4240-8163-0c812b73a9a6 ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-2.6.38-11-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-11-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos8)'
    search --no-floppy --fs-uuid --set=root 93efeb51-de8e-4240-8163-0c812b73a9a6
    echo    'Loading Linux 2.6.38-11-generic ...'
    linux    /boot/vmlinuz-2.6.38-11-generic root=UUID=93efeb51-de8e-4240-8163-0c812b73a9a6 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.38-11-generic
}
submenu "Previous Linux versions" {
menuentry 'Ubuntu, with Linux 2.6.38-10-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos8)'
    search --no-floppy --fs-uuid --set=root 93efeb51-de8e-4240-8163-0c812b73a9a6
    linux    /boot/vmlinuz-2.6.38-10-generic root=UUID=93efeb51-de8e-4240-8163-0c812b73a9a6 ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-2.6.38-10-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-10-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos8)'
    search --no-floppy --fs-uuid --set=root 93efeb51-de8e-4240-8163-0c812b73a9a6
    echo    'Loading Linux 2.6.38-10-generic ...'
    linux    /boot/vmlinuz-2.6.38-10-generic root=UUID=93efeb51-de8e-4240-8163-0c812b73a9a6 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.38-10-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-8-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos8)'
    search --no-floppy --fs-uuid --set=root 93efeb51-de8e-4240-8163-0c812b73a9a6
    linux    /boot/vmlinuz-2.6.38-8-generic root=UUID=93efeb51-de8e-4240-8163-0c812b73a9a6 ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-2.6.38-8-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-8-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos8)'
    search --no-floppy --fs-uuid --set=root 93efeb51-de8e-4240-8163-0c812b73a9a6
    echo    'Loading Linux 2.6.38-8-generic ...'
    linux    /boot/vmlinuz-2.6.38-8-generic root=UUID=93efeb51-de8e-4240-8163-0c812b73a9a6 ro single 
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
    set root='(/dev/sda,msdos8)'
    search --no-floppy --fs-uuid --set=root 93efeb51-de8e-4240-8163-0c812b73a9a6
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos8)'
    search --no-floppy --fs-uuid --set=root 93efeb51-de8e-4240-8163-0c812b73a9a6
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Ubuntu, with Linux 2.6.38-11-generic (on /dev/sda1)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos1)'
    search --no-floppy --fs-uuid --set=root 88118626-5482-45ab-8f03-c2d131752aa9
    linux /boot/vmlinuz-2.6.38-11-generic root=UUID=93efeb51-de8e-4240-8163-0c812b73a9a6 ro quiet splash vt.handoff=7
    initrd /boot/initrd.img-2.6.38-11-generic
}
menuentry "Ubuntu, with Linux 2.6.38-11-generic (recovery mode) (on /dev/sda1)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos1)'
    search --no-floppy --fs-uuid --set=root 88118626-5482-45ab-8f03-c2d131752aa9
    linux /boot/vmlinuz-2.6.38-11-generic root=UUID=93efeb51-de8e-4240-8163-0c812b73a9a6 ro single
    initrd /boot/initrd.img-2.6.38-11-generic
}
menuentry "Ubuntu, with Linux 2.6.38-10-generic (on /dev/sda1)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos1)'
    search --no-floppy --fs-uuid --set=root 88118626-5482-45ab-8f03-c2d131752aa9
    linux /boot/vmlinuz-2.6.38-10-generic root=UUID=93efeb51-de8e-4240-8163-0c812b73a9a6 ro quiet splash vt.handoff=7
    initrd /boot/initrd.img-2.6.38-10-generic
}
menuentry "Ubuntu, with Linux 2.6.38-10-generic (recovery mode) (on /dev/sda1)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos1)'
    search --no-floppy --fs-uuid --set=root 88118626-5482-45ab-8f03-c2d131752aa9
    linux /boot/vmlinuz-2.6.38-10-generic root=UUID=93efeb51-de8e-4240-8163-0c812b73a9a6 ro single
    initrd /boot/initrd.img-2.6.38-10-generic
}
menuentry "Ubuntu, with Linux 2.6.38-8-generic (on /dev/sda1)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos1)'
    search --no-floppy --fs-uuid --set=root 88118626-5482-45ab-8f03-c2d131752aa9
    linux /boot/vmlinuz-2.6.38-8-generic root=UUID=93efeb51-de8e-4240-8163-0c812b73a9a6 ro quiet splash vt.handoff=7
    initrd /boot/initrd.img-2.6.38-8-generic
}
menuentry "Ubuntu, with Linux 2.6.38-8-generic (recovery mode) (on /dev/sda1)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos1)'
    search --no-floppy --fs-uuid --set=root 88118626-5482-45ab-8f03-c2d131752aa9
    linux /boot/vmlinuz-2.6.38-8-generic root=UUID=93efeb51-de8e-4240-8163-0c812b73a9a6 ro single
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

=============================== sda8/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda8 during installation
UUID=93efeb51-de8e-4240-8163-0c812b73a9a6 /               ext4    errors=remount-ro,user_xattr 0       1
# swap was on /dev/sda7 during installation
UUID=978c7491-f17e-4adf-9882-32a1ef3c3071 none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sda8: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

 123.027122498 = 132.099366912  boot/grub/core.img                             1
 131.488670349 = 141.184884736  boot/grub/grub.cfg                             1
 128.290405273 = 137.750773760  boot/initrd.img-2.6.38-10-generic              2
 131.744140625 = 141.459193856  boot/initrd.img-2.6.38-11-generic              2
 124.619140625 = 133.808783360  boot/initrd.img-2.6.38-8-generic               2
 127.599918365 = 137.009369088  boot/vmlinuz-2.6.38-10-generic                 1
 119.463199615 = 128.272633856  boot/vmlinuz-2.6.38-11-generic                 1
 123.019294739 = 132.090961920  boot/vmlinuz-2.6.38-8-generic                  1
 131.744140625 = 141.459193856  initrd.img                                     2
 128.290405273 = 137.750773760  initrd.img.old                                 2
 119.463199615 = 128.272633856  vmlinuz                                        1
 127.599918365 = 137.009369088  vmlinuz.old                                    1

========================= sdb1/syslinux/syslinux.cfg: ==========================

--------------------------------------------------------------------------------
# D-I config version 2.0
include menu.cfg
default vesamenu.c32
prompt 0
timeout 50
ui gfxboot bootlogo
--------------------------------------------------------------------------------

================= sdb1: Location of files loaded by Syslinux: ==================

           GiB - GB             File                                 Fragment(s)

            ?? = ??             ldlinux.sys                                    1
            ?? = ??             syslinux/gfxboot.c32                           1
            ?? = ??             syslinux/syslinux.cfg                          1
            ?? = ??             syslinux/vesamenu.c32                          1

============== sdb1: Version of COM32(R) files used by Syslinux: ===============

 syslinux/gfxboot.c32               :  COM32R module (v4.xx)
 syslinux/vesamenu.c32              :  COM32R module (v4.xx)

=============================== StdErr Messages: ===============================

unlzma: Decoder error
/home/ubuntu/Desktop/boot_info_script.sh: line 1579: [: 2.73495e+09: integer expression expected


```

---

### Post by YesWeCan on 2011-08-31
Ok, the grub.cfg file in sd8:/boot/grub has the wrong UUID for root of sda1:
```
### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Ubuntu, with Linux 2.6.38-11-generic (on /dev/sda1)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos1)'
    search --no-floppy --fs-uuid --set=root 88118626-5482-45ab-8f03-c2d131752aa9
    linux /boot/vmlinuz-2.6.38-11-generic root=UUID=[COLOR="Red"]93efeb51-de8e-4240-8163-0c812b73a9a6[/COLOR] ro quiet splash vt.handoff=7
    initrd /boot/initrd.img-2.6.38-11-generic
}
```
Should be
```
### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Ubuntu, with Linux 2.6.38-11-generic (on /dev/sda1)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos1)'
    search --no-floppy --fs-uuid --set=root 88118626-5482-45ab-8f03-c2d131752aa9
    linux /boot/vmlinuz-2.6.38-11-generic root=UUID=[COLOR="Green"]88118626-5482-45ab-8f03-c2d131752aa9[/COLOR] ro quiet splash vt.handoff=7
    initrd /boot/initrd.img-2.6.38-11-generic
}
```

Edit this file and change the UUID; this will change the first menu entry for sda1. Reboot and select this menu entry. This should get you in to sda1 and then you need to do
sudo update-grub
sudo grub-install /dev/sda

If that doesn't work...the belt and braces chroot method will: see 12.1.4 here [https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

---

### Post by YasinG on 2011-09-01
You are right, I can't imagine how you found that out !
Any way, grub.cfg is a read only file i can't change it.

---

### Post by dino99 on 2011-09-01
update /etc/fstab with the good uuid (sudo gedit /etc/fstab)

sudo grub-mkconfig
sudo update-grub

---

### Post by YesWeCan on 2011-09-01
You can do:
sudo gedit /boot/grub/grub.cfg


I'm not sure whether this is a bug in update-grub or not. After you fix grub.cfg it will boot into sda1 and then if you run update-grub there it will change something so that when you go back to sda8 and run update-grub it will get it right. But I don't see why the location of the Ubuntu boot files should be affected by what the state of the Grub files is.

---

### Post by YasinG on 2011-09-01
Dino Thats what i did the first time, i updated the fstab file two times, it still wouldn't ubdate the grub file as you see.
I'll do that YesWeCan

---

### Post by YasinG on 2011-09-01
It worked. Now there is finally an entry on the menu that directs me to sda1, it's not the first one though. I guess that's what grub updating is right? or should i change the UUID in the first entry in the grub file? The one you marked in red was one further down the list.

---

### Post by YesWeCan on 2011-09-01
Right. I think the one I marked is the first entry after the memtest ones. So select it and give it a while to boot and hopefully when you run mount it will be sda1 at /.
Then you run
sudo update-grub
sudo grub-install /dev/sda

And now when you reboot everything should go through sda1 and the sda1 Ubuntu should be the first on the list.

The rule is that the Ubuntu, and its variants, that you are running when you do update-grub becomes the first on the menu. All other OSs get listed at the end after memtest.


BTW: When you see the grub menu you can highlight an entry and then press "e" to bring up an editor for that entry. You then see the whole line that's been grabbed from grub.cfg and you can edit it on the spot and then boot it. This is an alternative to editing the grub.cfg file.

---

### Post by YasinG on 2011-09-01
I thought so, and it did. Thanks a lot for all your work with me.
Now i have few questions if you don't mind.
How do i delete the old Ubuntu?
How do i get rid of the many entries in the boot menu? or what are they good for if i can't delete them ?
I noticed  a small partition named linux swap when i was in Gparted or when i checked for UUIDs, what is that?
Thanks again.
Yasin

---

### Post by YesWeCan on 2011-09-01
Good stuff. You are welcome.
To remove a partition you can either run Disk Utility or GParted and use a nice GUI, or you can do it from the command line:
[COLOR="Navy"]sudo parted /dev/sda rm[/COLOR]
and it will ask you for the number of the partition

I prefer using a GUI because I feel more sure about what I am deleting. Make sure your cloned Ubuntu is all present and correct before you delete the old one.

Each time you run update-grub a scan is made of all your drives and any OS detected is an entry in the boot menu. So after you have deleted the old Ubuntu you need to run this again to remove its entries.

The swap space is like an emergency RAM supply. If Ubuntu runs out of RAM then it stops functioning properly. Some disk space is set aside as a sort of very slow, simulated RAM in case of short-term shortages. This space is also used when laptops hibernate: they copy the real RAM contents into the swap for restoration later. Windows uses a more modern form of swap by using a file in the actual root filesystem so no special partition is needed. Linux can also do it this way but for some reason Ubuntu still defaults to installing a swap partition. As a rule, you should set aside the same amount of swap as RAM, but unless you are going to hibernate or do really memory intensive stuff, 4GB of swap is plenty.

BTW Ubuntu may auto-mount any swap spaces it sees. This can cause confusion when you try to resize or delete a swap partition and you cannot because it is "in use". To see which swap partitions are active:
swapon -s
to deactivate a swap partition
swapoff /dev/sdxy
to reactivate a swap partition
swapon /dev/sdxy

---

### Post by YasinG on 2011-09-01
Thanks a lot man ( is it ?), i really appreciate you being so patient with me.
Yasin

---

### Post by YesWeCan on 2011-09-01
> **YasinG said:**
> man ( is it ?),
Penguin.


Don't forget to mark this as solved in [COLOR="Red"]Thread Tools[/COLOR] when you are ready.

---

### Post by YasinG on 2011-09-01
Done. Thanks again, I'm pretty sure you will be answering more of my upcoming questions so, see you later.

---

