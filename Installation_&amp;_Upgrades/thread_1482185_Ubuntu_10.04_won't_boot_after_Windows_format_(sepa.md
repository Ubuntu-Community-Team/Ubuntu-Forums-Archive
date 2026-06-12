---
title: "Ubuntu 10.04 won't boot after Windows format (separate HDD)."
date: 2010-05-13
forum: Installation &amp; Upgrades
---

### Post by Yaheed on 2010-05-13
Hey there,

First things first, I am a noob so please be gentle.

Alright so I downloaded and burnt the 64bit Ubuntu 9.10. I installed in on to a separate hard drive to my existing Windows Vista installation. I partitioned the hard drive that Ubuntu was being installed on to 300GB of the 1TB I had on there. All was fine and dandy, updated all my packages and the noticed that 10.04 had been release so I promptly started upgrading.

The upgrade got to a point where it said something about the bootloader (sorry can't remember really, was around 2am) and to pick which hard drive / partition to put it on. I figured I may as well put it on both my Windows and Ubuntu hard drives so did so. It threw an error and then continued upgrading.

All went well and auto-restarted after installation. I was presented with a command line interface (I think grub?) to choose with version of ubuntu and my windows vista installation showed up as well. Ubuntu would boot fine from it but the Windows would not, through the error message:

```
error: no such device: 760cba250c69e09b
error: no such partition
```It was almost a freshly installed copy of Vista so I just thought "Whatever" and formated the Vista hard drive and reinstalled.

Now booting from my Windows hard drive works fine, but trying to boot from my Ubuntu hard drive does not. I figured I had erased the grub bootloader so tried to reinstall it via the instructions on the [Ubuntu Documentation]("https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202") to no success.

Now I am here. I can see both hard drives when loading the 10.04 CD and booting up from there and can access them both once they mount. Any ideas on how I can get my Ubuntu booting up again? Also is it possible, when I get it working, to boot up both my OS's even though they are on separate hard drives?

Image of the two hard drives with the CD Filesystem as the third:
[IMG]http://img.loldepot.com/e751aceee3d78b230b1c.png[/IMG]

The contents of the original Ubuntu installation:
[IMG]http://img.loldepot.com/9660d58f16621332349d.png[/IMG]

Contents of my Terminal commands trying to reinstall Grub2 to what I thought was the right partition:
```
ubuntu@ubuntu:~$ sudo -i
root@ubuntu:~# sudo fdisk -l

WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1      121602   976762583+  ee  GPT
/dev/sda2   *           1           1           0    0  Empty
Partition 2 does not end on cylinder boundary.

Disk /dev/sdb: 640.1 GB, 640135028736 bytes
255 heads, 63 sectors/track, 77825 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xcf1310f1

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       77826   625128448    7  HPFS/NTFS
root@ubuntu:~# sudo blkid
/dev/loop0: TYPE="squashfs" 
/dev/sda2: UUID="7622f31c-416b-4730-af3d-62b86fbd7327" TYPE="ext4" 
/dev/sdb1: UUID="02F400FAF400F229" TYPE="ntfs" 
root@ubuntu:~# sudo mount /dev/sda2 /mnt
root@ubuntu:~# sudo grub-install --root-directory=/mnt/ /dev/sda
/usr/sbin/grub-setup: warn: This GPT partition label has no BIOS Boot Partition; embedding won't be possible!.
/usr/sbin/grub-setup: warn: Embedding is not possible.  GRUB can only be installed in this setup by using blocklists.  However, blocklists are UNRELIABLE and its use is discouraged..
/usr/sbin/grub-setup: error: if you really want blocklists, use --force.

```

---

### Post by kansasnoob on 2010-05-13
Please post the output of the Boot Info Script as described here:

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

You can run it using the Live CD.

---

### Post by darkod on 2010-05-13
The 1TB disk has a GPT partition table which doesn't play nice with grub2 all the time. But since it was working previously, that shouldn't be the problem.

Try putting grub2 on /dev/sdb and set that disk as first in hdd order in BIOS, if that will make it boot OK. After the vista reinstall you now have windows bootloader on it. In case it doesn't work, you can put generic MBR back easily.

In live mode, like you tried reinstalling grub2, modify the second command as:

sudo mount /dev/sda2 /mnt
sudo grub-install --root-directory=/mnt/ /dev/sdb

Note that vista might not boot right away, since it was reinstalled. But if you can, boot ubuntu at least and execute:

sudo update-grub

to try to update grub.

---

### Post by Yaheed on 2010-05-13
Cheers. It's quite massive so it's [pasted here]("http://privatepaste.com/beb9aa96d6").

---

### Post by Yaheed on 2010-05-13
> **darkod said:**
> The 1TB disk has a GPT partition table which doesn't play nice with grub2 all the time. But since it was working previously, that shouldn't be the problem.

Try putting grub2 on /dev/sdb and set that disk as first in hdd order in BIOS, if that will make it boot OK. After the vista reinstall you now have windows bootloader on it. In case it doesn't work, you can put generic MBR back easily.

In live mode, like you tried reinstalling grub2, modify the second command as:

sudo mount /dev/sda2 /mnt
sudo grub-install --root-directory=/mnt/ /dev/sdb

Note that vista might not boot right away, since it was reinstalled. But if you can, boot ubuntu at least and execute:

sudo update-grub

to try to update grub.

I would do all this if I knew how to unmount it first :)

---

### Post by Yaheed on 2010-05-13
Okay so I got it installed, updated Grub and restarted. No Windows Vista option on the Grub screen but there are 4 linux kernel options and1 memtest.

How do I get my Windows Vista booting back? :)

```
jarryd@Jarryd-Ubuntu:~$ sudo update-grub
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.32-22-generic
Found initrd image: /boot/initrd.img-2.6.32-22-generic
Found linux image: /boot/vmlinuz-2.6.31-21-generic
Found initrd image: /boot/initrd.img-2.6.31-21-generic
Found memtest86+ image: /boot/memtest86+.bin
done
```

---

### Post by darkod on 2010-05-13
If it's not detected, some of the boot files are missing. I noticed this in your results. On /dev/sdb1 there should be 3 boot files for windows. Except winload.exe and /bootmgr there should also be /boot/BCD. I don't know why it's missing.

If you have the vista install dvd you can try repairing the boot, instructions here:
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

Note that that would again destroy your grub2 on /dev/sdb. :) But the main thing is to get /boot/BCD in the results.txt also.

Once that is done and vista is booting fine (the computer will probably boot vista directly when /dev/sdb is first option), again go into live mode and reinstall grub2 to the MBR:

sudo mount /dev/sda2 /mnt
sudo grub-install --root-directory=/mnt/ /dev/sdb

Once you boot into the hdd ubuntu, you need to run again

sudo update-grub

This time vista should be reported as found.

---

### Post by Yaheed on 2010-05-13
Okay well partially positive results, still no success in booting Vista via Grub.

Ran through the instructions of the link, they didn't work so I let Windows repair it automatically, that worked just fine. Ran the LiveCD and installed grub on the the sdb volume again.

Did everything until restarting, loading the "Window Vista (loader) (on /dev/sdb1) option. Same error as before with the missing partition but a slightly different code.

Boot info results:
```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks at sector 543074 of 
    the same hard drive for core.img, but core.img can not be found at this 
    location.
 => Grub 2 is installed in the MBR of /dev/sdb and looks on the same drive in 
    partition #2 for /boot/grub.

sda2: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1                   1 1,953,525,167 1,953,525,167  ee GPT


GUID Partition Table detected.

Partition           Start           End          Size System
/dev/sda2         262,178   600,262,178   600,000,001 Linux or Data

Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 640.1 GB, 640135028736 bytes
255 heads, 63 sectors/track, 77825 cylinders, total 1250263728 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *          2,048 1,250,258,943 1,250,256,896   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda2        7622f31c-416b-4730-af3d-62b86fbd7327   ext4                                     
/dev/sda: PTTYPE="gpt" 
/dev/sdb1        02F400FAF400F229                       ntfs                                     
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda2        /                        ext4       (rw,errors=remount-ro)


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
search --no-floppy --fs-uuid --set 7622f31c-416b-4730-af3d-62b86fbd7327
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
search --no-floppy --fs-uuid --set 7622f31c-416b-4730-af3d-62b86fbd7327
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
    set root='(hd0,2)'
    search --no-floppy --fs-uuid --set 7622f31c-416b-4730-af3d-62b86fbd7327
    linux    /boot/vmlinuz-2.6.32-22-generic root=UUID=7622f31c-416b-4730-af3d-62b86fbd7327 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,2)'
    search --no-floppy --fs-uuid --set 7622f31c-416b-4730-af3d-62b86fbd7327
    echo    'Loading Linux 2.6.32-22-generic ...'
    linux    /boot/vmlinuz-2.6.32-22-generic root=UUID=7622f31c-416b-4730-af3d-62b86fbd7327 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.31-21-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,2)'
    search --no-floppy --fs-uuid --set 7622f31c-416b-4730-af3d-62b86fbd7327
    linux    /boot/vmlinuz-2.6.31-21-generic root=UUID=7622f31c-416b-4730-af3d-62b86fbd7327 ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.31-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,2)'
    search --no-floppy --fs-uuid --set 7622f31c-416b-4730-af3d-62b86fbd7327
    echo    'Loading Linux 2.6.31-21-generic ...'
    linux    /boot/vmlinuz-2.6.31-21-generic root=UUID=7622f31c-416b-4730-af3d-62b86fbd7327 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.31-21-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd0,2)'
    search --no-floppy --fs-uuid --set 7622f31c-416b-4730-af3d-62b86fbd7327
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd0,2)'
    search --no-floppy --fs-uuid --set 7622f31c-416b-4730-af3d-62b86fbd7327
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows Vista (loader) (on /dev/sdb1)" {
    insmod ntfs
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set 02f400faf400f229
    chainloader +1
}
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
proc            /proc           proc    defaults        0       0
# / was on /dev/sda2 during installation
UUID=7622f31c-416b-4730-af3d-62b86fbd7327 /               ext4    errors=remount-ro 0       1
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda2: Location of files loaded by Grub: ===================


    .2GB: boot/grub/core.img
  34.6GB: boot/grub/grub.cfg
   2.3GB: boot/initrd.img-2.6.31-21-generic
   3.9GB: boot/initrd.img-2.6.32-22-generic
   1.0GB: boot/vmlinuz-2.6.31-21-generic
   3.0GB: boot/vmlinuz-2.6.32-22-generic
   3.9GB: initrd.img
   2.3GB: initrd.img.old
   3.0GB: vmlinuz
   1.0GB: vmlinuz.old
```I never knew it could be so difficult to dual boot :-P

Should I be installing the grub loader on to "sdb" or "sdb1"?

Going to bed now since it's 2am for me, I need some sleep. Will respond when I get up.

---

### Post by darkod on 2010-05-13
Yes, you should have installed on /dev/sdb as you did, not /dev/sdb1. If it has a number then it's a partition, and grub2 in general goes to the MBR of the disk.

However the following is confusing:

=> Grub 2 is installed in the MBR of /dev/sda and looks at sector 543074 of 
    the same hard drive for core.img, but core.img can not be found at this 
    location.
 => Grub 2 is installed in the MBR of [COLOR=Red]/dev/sdb[/COLOR] and looks on the same drive in 
    partition [COLOR=Red]#2 [/COLOR]for /boot/grub.

Somehow somewhere the disks seems to have switched themselves. The second item says grub2 is installed on /dev/sdb as we intended but that it's looking for its files in partition 2.

/dev/sdb in the results is the vista disk with only single ntfs partition. It has no partition 2. On the contrary, the ubuntu partition with the grub2 config files inside is on the second partition on /dev/sda, or in other words /dev/sda2.

I'm not sure if it's a bug in meierfra's script, and maybe because /dev/sda has GPT on it, but I think I've seen this confusing results in other posts too.

If you can boot ubuntu, try creating updated device.map file with:

sudo grub-mkdevicemap

It should return results like:
hd0 /dev/sda
hd1 /dev/sdb

Just in case, run again after that

sudo update-grub

At the end, post the results of:

sudo fdisk -l (small L)

to see what is /dev/sda and what /dev/sdb.

---

### Post by oldfred on 2010-05-13
We are learning about GPT.

Did you create a BIOS boot partition on the GPT disk. It supposedly makes booting with grub easy as it finds that and uses it.

grub2 & GPT info
[http://grub.enbug.org/BIOS_Boot_Partition](http://grub.enbug.org/BIOS_Boot_Partition)

GPT fdisk Tutorial -srs5694 in forums
[http://ubuntuforums.org/showthread.php?t=1439794](http://ubuntuforums.org/showthread.php?t=1439794)

I would also download gdisk as it will work where fdisk does not:
[http://www.rodsbooks.com/gdisk/](http://www.rodsbooks.com/gdisk/)

---

### Post by darkod on 2010-05-13
/usr/sbin/grub-setup: warn: This GPT partition label has no BIOS Boot Partition; embedding won't be possible!.

According to this from the first post, there isn't a BIOS boot partition. But I don't know what to advise...

Is it possible to even create it now that the disk has ubuntu installed without having to destroy it.

---

### Post by Yaheed on 2010-05-13
At work now so I can't run all the commands and stuff until I get home, sorry Darko.

Would it just be worth reinstalling Ubuntu on a newly formatted partition, after I fix the boot for Windows and the MBR?

If so, what steps should I take so I don't run in to this again? :)

What type of filesytem should I set my partition as? Where should the grub boot loader go? Do I need a swap partition? Anything else I should probably know?

I really have no idea :P

Thanks for your patience and help :)

---

### Post by Yaheed on 2010-05-15
> **darkod said:**
> Yes, you should have installed on /dev/sdb as you did, not /dev/sdb1. If it has a number then it's a partition, and grub2 in general goes to the MBR of the disk.

However the following is confusing:

=> Grub 2 is installed in the MBR of /dev/sda and looks at sector 543074 of 
    the same hard drive for core.img, but core.img can not be found at this 
    location.
 => Grub 2 is installed in the MBR of [COLOR=Red]/dev/sdb[/COLOR] and looks on the same drive in 
    partition [COLOR=Red]#2 [/COLOR]for /boot/grub.

Somehow somewhere the disks seems to have switched themselves. The second item says grub2 is installed on /dev/sdb as we intended but that it's looking for its files in partition 2.

/dev/sdb in the results is the vista disk with only single ntfs partition. It has no partition 2. On the contrary, the ubuntu partition with the grub2 config files inside is on the second partition on /dev/sda, or in other words /dev/sda2.

I'm not sure if it's a bug in meierfra's script, and maybe because /dev/sda has GPT on it, but I think I've seen this confusing results in other posts too.

If you can boot ubuntu, try creating updated device.map file with:

sudo grub-mkdevicemap

It should return results like:
hd0 /dev/sda
hd1 /dev/sdb

Just in case, run again after that

sudo update-grub

At the end, post the results of:

sudo fdisk -l (small L)

to see what is /dev/sda and what /dev/sdb.


Okay I did all of the above and the grub-mkdevicemap literally returned nothing.

So I reinstall Ubuntu on and made surethat grub was going on the Ubuntu hard drive and all is working fine except booting Windows from the Grub loader. Not a big issue, I can just change my boot order or look at the previous links in this thread.

Thanks for your help :)

---

