---
title: "Dual-boot attempt gone south"
date: 2011-03-21
forum: Installation &amp; Upgrades
---

### Post by Tron87 on 2011-03-21
Hi, 
I just reinstalled 10.04 LTS; I also jumped on an opportunity to free up some disk space and get rid of Windows recovery area on my drive (it was hogging 16GB, so it seemed like a good idea at that time...) and a tiny partition hosting a basic linux-based system.
Installation went ok. The problem is that I no longer get the Grub menu and cannot choose which system to boot. It just goes straight to Xubuntu.
Here is a bit more info:
> 
sudo fdisk -l

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xd937cf59

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1972    15831040   83  Linux
/dev/sda3            1972        5619    29296875    7  HPFS/NTFS
/dev/sda4            5619       30402   199068673    5  Extended
/dev/sda5           30280       30402      975872   82  Linux swap / Solaris
/dev/sda6            5619       30280   198091776   83  Linux

Partition table entries are not in disk order
and
> 
sudo update-grub
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.32-30-generic
Found initrd image: /boot/initrd.img-2.6.32-30-generic
Found linux image: /boot/vmlinuz-2.6.32-28-generic
Found initrd image: /boot/initrd.img-2.6.32-28-generic
Found memtest86+ image: /boot/memtest86+.bin
done
I tried google, but all I got was a headache. Any help would be much appreciated.
PS Just noticed SDA6 line in fdisk output. I am pretty sure it should not be there, with its ID identical of sda1 and range within sda3 range. Disk Utility comes up with 4 partitions, too (16 Gb ext4, 30 Gb Ntfs and Extended 204 GB (204 GB ext4 + 1 Gb swap). Have no idea what it means, though.

---

### Post by Hakunka-Matata on 2011-03-21
Please go to the Hyperlink 'bootinfoscript' in my signature, download and run the script "boot_info_script"  

execute it according to instructions given, and then post the results between CODE TAGS (# ICON)

That will provide the information on your boot sequence necessary to fix Grub configuration

---

### Post by Tron87 on 2011-03-21
Thanks for the quick reply, here it is. 
One last thing I forgot to mention. The links to 30Gb Filesystem do not appear in the file manager and "Mount Volume" command in the Disk Utility does not seem to do anything.
```

                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #1 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.2 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe

sda4: _________________________________________________________________________

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
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048    31,664,127    31,662,080  83 Linux
/dev/sda3          31,664,128    90,257,877    58,593,750   7 HPFS/NTFS
/dev/sda4          90,259,454   488,396,799   398,137,346   5 Extended
/dev/sda5         486,445,056   488,396,799     1,951,744  82 Linux swap / Solaris
/dev/sda6          90,259,456   486,443,007   396,183,552  83 Linux


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        1970afe8-0031-47ec-afa3-25871abf971b   ext4                                     
/dev/sda3        AAD631EDD631BB01                       ntfs                                     
/dev/sda4: PTTYPE="dos" 
/dev/sda5        07a377f4-99e0-486a-acb8-4eb760c51027   swap                                     
/dev/sda6        6e902831-2988-4023-a0dc-47282054dfab   ext4                                     
/dev/sda: PTTYPE="dos" 
error: /dev/sdb: No medium found

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda1        /                        ext4       (rw,errors=remount-ro)
/dev/sda6        /home                    ext4       (rw)
/dev/sr0         /media/VMC Lite 9.4.3.16284 iso9660    (ro,nosuid,nodev,uhelper=hal,uid=1000,utf8)


=========================== sda1/boot/grub/grub.cfg: ===========================

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
search --no-floppy --fs-uuid --set 1970afe8-0031-47ec-afa3-25871abf971b
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
search --no-floppy --fs-uuid --set 1970afe8-0031-47ec-afa3-25871abf971b
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
menuentry 'Ubuntu, with Linux 2.6.32-30-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 1970afe8-0031-47ec-afa3-25871abf971b
    linux    /boot/vmlinuz-2.6.32-30-generic root=UUID=1970afe8-0031-47ec-afa3-25871abf971b ro  splash  quiet splash
    initrd    /boot/initrd.img-2.6.32-30-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-30-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 1970afe8-0031-47ec-afa3-25871abf971b
    echo    'Loading Linux 2.6.32-30-generic ...'
    linux    /boot/vmlinuz-2.6.32-30-generic root=UUID=1970afe8-0031-47ec-afa3-25871abf971b ro single  splash
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-30-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-28-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 1970afe8-0031-47ec-afa3-25871abf971b
    linux    /boot/vmlinuz-2.6.32-28-generic root=UUID=1970afe8-0031-47ec-afa3-25871abf971b ro  splash  quiet splash
    initrd    /boot/initrd.img-2.6.32-28-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-28-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 1970afe8-0031-47ec-afa3-25871abf971b
    echo    'Loading Linux 2.6.32-28-generic ...'
    linux    /boot/vmlinuz-2.6.32-28-generic root=UUID=1970afe8-0031-47ec-afa3-25871abf971b ro single  splash
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-28-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 1970afe8-0031-47ec-afa3-25871abf971b
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 1970afe8-0031-47ec-afa3-25871abf971b
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

=============================== sda1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/sda1       /               ext4    errors=remount-ro 0       1
# /home was on /dev/sda6 during installation
UUID=6e902831-2988-4023-a0dc-47282054dfab /home           ext4    defaults        0       2
# swap was on /dev/sda5 during installation
UUID=07a377f4-99e0-486a-acb8-4eb760c51027 none            swap    sw              0       0

=================== sda1: Location of files loaded by Grub: ===================


   2.3GB: boot/grub/core.img
  13.2GB: boot/grub/grub.cfg
   2.3GB: boot/initrd.img-2.6.32-28-generic
   2.4GB: boot/initrd.img-2.6.32-30-generic
   2.3GB: boot/vmlinuz-2.6.32-28-generic
   2.3GB: boot/vmlinuz-2.6.32-30-generic
   2.4GB: initrd.img
   2.3GB: initrd.img.old
   2.3GB: vmlinuz
   2.3GB: vmlinuz.old
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda4

00000000  ff ff ff ff ff ff ff ff  ff ff ff ff ff ff ff ff  |................|
*
000001b0  ff ff ff ff ff ff ff ff  ff ff ff ff ff ff 00 fe  |................|
000001c0  ff ff 82 fe ff ff 02 50  9d 17 00 c8 1d 00 00 fe  |.......P........|
000001d0  ff ff 05 fe ff ff 01 00  00 00 01 48 9d 17 00 00  |...........H....|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


=======Devices which don't seem to have a corresponding hard drive==============

sdb 

```

---

### Post by Hakunka-Matata on 2011-03-21
Do you have two physical hard drives installed in that machine.  And if you **can** boot to a LiveCD, please post the output of GParted for both (if you have two) drives.

---

### Post by Hakunka-Matata on 2011-03-21
you changed a bunch of partitions around using GParted.  When partitions are resized, or moved, or deleted and recreated their UUIDs change.  These changes must be implemented into the /etc/fstab file.  let's have a look at your /etc/fstab file, and compare the UUIDs with the current valid UUIDs that you can get several different ways.

```
sudo blkid
```  is a good way

---

### Post by Tron87 on 2011-03-21
I have only one physical hard drive, and here is a printscreen of GParted; I hope that's what you needed

---

### Post by Tron87 on 2011-03-21
And that blkid thing:
```

sudo blkid
[sudo] password for kirill: 
/dev/sda1: UUID="1970afe8-0031-47ec-afa3-25871abf971b" TYPE="ext4" 
/dev/sda3: UUID="AAD631EDD631BB01" TYPE="ntfs" 
/dev/sda5: UUID="07a377f4-99e0-486a-acb8-4eb760c51027" TYPE="swap" 
/dev/sda6: UUID="6e902831-2988-4023-a0dc-47282054dfab" TYPE="ext4" 

```

And fstab:
```

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/sda1       /               ext4    errors=remount-ro 0       1
# /home was on /dev/sda6 during installation
UUID=6e902831-2988-4023-a0dc-47282054dfab /home           ext4    defaults        0       2
# swap was on /dev/sda5 during installation
UUID=07a377f4-99e0-486a-acb8-4eb760c51027 none            swap    sw              0       0

```

I think you are right, they don't match. What is the next step?

---

### Post by Hakunka-Matata on 2011-03-21
Yes, that's all good information, thanks.

You'll have to look @ your /etc/fstab file, to see if the UUIDs of your partitions are correctly entered there.  Hopefully there will be descrepancies in that file, which the bootloader uses to learn where the / system to be mounted and started is.  

CAUTION:  make a copy and name it something like fstaboriginalbackup or such,  of the fstab file located in your /etc folder first.  you can do this with the Terminal or Nautilus. 

```
cp /etc/fstab fstab_original_backup
```from terminal also do this please

```
cat /etc/fstab
```& post the output

that will tell us if there is a need to edit /etc/fstab to reflect the current UUIDs as displayed by "blkid" post in post #7

---

### Post by Hakunka-Matata on 2011-03-21
I can see already your /etc/fstab file is not correct, the Results.txt shows for starters that sda6 is misnamed,  it'll have to be editied

When you're comfortable, we'll proceed.

---

### Post by Tron87 on 2011-03-21
Great, the back-up is on my desktop, ready when you are;
in the meanwhile I have updated Post 7 with the fstab info

---

### Post by Hakunka-Matata on 2011-03-21
OK, it's pretty simple, you have to open /etc/fstab for editing (read/write).

Let's do it with the Terminal

```
sudo gedit /etc/fstab
```

once into the file, open another terminal, run 

```
sudo blkid
```

get them adjusted so you can see both, or print out the blkid output, what ever you like.

then copy and paste the correct UUIDs from the blkid output into the /etc/fstab file.  When you get it fixed, save /etc/fstab file.  Let me have a look at your new /etc/fstab file if you don't mind before rebooting

---

### Post by Tron87 on 2011-03-21
I have pasted the UUID's, but am not sure what to enter for their <mount point>   <type>  <options>       <dump>  <pass> parameters.
The file I am working on is attached, please have a look

---

### Post by Hakunka-Matata on 2011-03-21
maybe you attached a file, but it's not showing in your post, 

after attaching, you must also, upload the file, it's to the right hand side and invisible maybe in the attachment gui

---

### Post by Hakunka-Matata on 2011-03-21
GOT it
thanks

---

### Post by Hakunka-Matata on 2011-03-21
Your fstab file looks pretty messy:  Look @ this fstab file, just as an example. 

> das@das-System-Product-Name:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
# [SIZE=3]do not leave blank lines in this file, this is for like this for readability only...[/SIZE]


[COLOR=Red]# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0



# / was on /dev/sdc8 during installation
UUID=497a14e5-d299-43c7-ae42-3e835a4fce5a /               ext4    errors=remount-ro 0       1


# swap was on /dev/sdb5 during installation
UUID=b83e0608-fd1f-4cc3-be87-622a0590da95 none            swap    sw              0       0


# swap was on /dev/sdc7 during installation
UUID=339ad7c0-32c0-489d-a013-3c36d2181d73 none            swap    sw              0       0[/COLOR]


das@das-System-Product-Name:~$ You'll notice mine does not have an entry for /home.  Are you actually using a separate /home partition?

/  means root, where you installed the OS
swap is swap, I use two swaps, on different physical hard drives,

---

### Post by Hakunka-Matata on 2011-03-21
I"VE EDITED LAST POST

and I'm going for a food break now.......    be back in a short while

---

### Post by Tron87 on 2011-03-21
I tried to make my fstab to look more like yours and highlighted lines which I am not sure about:
```

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
[COLOR=Red]/dev/sda1       /               ext4    errors=remount-ro 0       1[/COLOR]
# /home was on /dev/sda6 during installation
UUID=6e902831-2988-4023-a0dc-47282054dfab /home           ext4    defaults        0       2
# swap was on /dev/sda5 during installation
UUID=07a377f4-99e0-486a-acb8-4eb760c51027 none            swap    sw              0       0
# / will be here:
UUID=1970afe8-0031-47ec-afa3-25871abf971b /               ext4    errors=remount-ro 0     1
# This is the Windows partition
[COLOR=Red]UUID=AAD631EDD631BB01                     ????            ntfs    ?????           ?       ?[/COLOR]
#
#blkid output
#/dev/sda1: UUID="1970afe8-0031-47ec-afa3-25871abf971b" TYPE="ext4" 
#/dev/sda3: UUID="AAD631EDD631BB01" TYPE="ntfs" 
#/dev/sda5: UUID="07a377f4-99e0-486a-acb8-4eb760c51027" TYPE="swap"
#/dev/sda6: UUID="6e902831-2988-4023-a0dc-47282054dfab" TYPE="ext4" 

```

---

### Post by Hakunka-Matata on 2011-03-21
ok, hold on one, I'll attach an fstab file that has a window partiton as well.  

Meanwhile, this is a screenshot of my fstab file, no alterations for clarity, just the plain old file.

---

### Post by Hakunka-Matata on 2011-03-21
that's an example I found on the *interweb.*  I don't have window7, rather XP, so I'm not sure what the windows7 fstab entry looks like.

---

### Post by Tron87 on 2011-03-21
Could you repeat that last message? The attachment did not go through

---

### Post by Hakunka-Matata on 2011-03-21
post #18?

oh wait, I see now

---

### Post by Hakunka-Matata on 2011-03-21
> **Tron87 said:**
> Could you repeat that last message? The attachment did not go through

Yeah, I see it didn't go through,

I had just pasted a graphic in, guess that doesn't work.  

I'm going to start a new thread and ask for a good clean example of a fstab from a dual boot Ubuntu/Windows7 system.

Dutch70 just sent me a link, maybe that will contain a good picture, ..

---

### Post by Hakunka-Matata on 2011-03-21
sda1 is my WindowsXP fstab entry.

That is not a good statement, I best RETRACT it.  This is a section of the RESULTS.txt file which has extra stuff in it.  So it cannot be taken verbatim for an entry in file /etc/fstab

How's it going?

> =============================== sdc5/etc/fstab: ===============================

# Pluggable devices are handled by uDev, they are not in fstab
/dev/sda6 / ext3 defaults,noatime 1 1
proc /proc proc defaults 0 0
devpts /dev/pts devpts mode=0622 0 0
# Dynamic entries below
/dev/sda1 /mnt/sda1 ntfs-3g noauto,users,gid=users,dmask=002,fmask=113,relatime 0 0
/dev/sda2 /mnt/sda2 ext4 noauto,users,exec,relatime 0 0
/dev/sda4 /mnt/sda4 ext4 noauto,users,exec,relatime 0 0
/dev/sdb1 /mnt/sdb1 ext4 noauto,users,exec,relatime 0 0
/dev/sdb5 swap swap sw,pri=1 0 0
/dev/sdb6 /mnt/sdb6 vfat noauto,users,gid=users,dmask=002,fmask=113,relatime 0 0
/dev/sdc1 /mnt/sdc1 ext4 noauto,users,exec,relatime 0 0
/dev/sdc2 /mnt/sdc2 ext4 noauto,users,exec,relatime 0 0
/dev/sdc3 /mnt/sdc3 ext4 noauto,users,exec,relatime 0 0
/dev/sdc5 /mnt/sdc5 ext3 noauto,users,exec,relatime 0 0
/dev/sdc6 /mnt/sdc6 ext4 noauto,users,exec,relatime 0 0
/dev/sdc7 swap swap sw,pri=1 0 0
/dev/cdrom /media/cdrom udf,iso9660 noauto,users,exec,ro 0 0
/dev/sr1 /media/cdrom udf,iso9660 noauto,users,exec,ro 0 0
/dev/cdrom1 /media/cdrom1 udf,iso9660 noauto,users,exec,ro 0 0
/dev/sr0 /media/cdrom1 udf,iso9660 noauto,users,exec,ro 0 0


---

### Post by oldfred on 2011-03-21
Your Ubuntu would not be booting if fstab was totally wrong. If somewhat wrong it gives error messages and/on continue without mounting the error. If the only error is in a commented line # then it is not important.

One of the partitions you deleted was the windows boot partition. Windows 7 normally installs to two partitions - a small 100MB boot/recovery that has these two files:
/bootmgr /Boot/BCD 
Then windows is in a main partition and you will see it as the c: drive. The boot partition is normally hidden in windows. They created it for future and to allow you to encrypt the main install as the boot files cannot be encrypted.
You can use a windows repair CD to add the missing files back to the main install. You do not have to have the separate 100MB boot partition.

oldfred's Windows Vista/Win7 repair links posts #7 & #9:
[http://ubuntuforums.org/showthread.php?p=9826152](http://ubuntuforums.org/showthread.php?p=9826152)
Make sure boot flag is set for any partition you try to repair.

You need to move boot flag to sda3 as windows only repairs windows partitions with the boot flag. You can use gparted, disk utility or command line to move boot flag.

set boot flag on for sda3 (off on others)
sudo sfdisk -A3 /dev/sda

After the windows repairs then grub's os-prober will be able to see the windows partition and add it to your menu.
sudo update-grub

---

### Post by Tron87 on 2011-03-26
Ok, I made it work =)
Thank you guys, it was nice to get help in this situation.
For those who follow my steps and delete their Windows boot partition, please follow the solution suggested by Oldfred ([http://ubuntuforums.org/showthread.php?p=9826152](http://ubuntuforums.org/showthread.php?p=9826152)).
I had to boot from a live USB, so his instructions had to be adjusted. What worked for me was to:

> DISCLAIMER: I am not very knowledgeable, most of the time I make my computer do what I need by poking around and copy-pasting commands from the web into terminal. I have messed up more than one installation this way. The method I am offering here should be your last resort, because I strongly suspect that it is neither the proper nor the safe one. Backup anything worth keeping before you do this; cause I honestly don't know what can go wrong here.1) Create a live usb using YUMI [http://www.pendrivelinux.com/yumi-multiboot-usb-creator/](http://www.pendrivelinux.com/yumi-multiboot-usb-creator/) (I had another Win7 machine for it) and recovery disk from NEOSMART [http://neosmart.net/blog/2009/windows-7-system-repair-discs/](http://neosmart.net/blog/2009/windows-7-system-repair-discs/)
2) Boot it. Agree to repair system and restart.
3) Boot it again. Select Command line. Run
> chkdsk C: /r /f (may have to run /r or /f as separate entries) rerun until no errors
BootRec.exe /FixBoot  #updates PBR partition boot sector4) Select Automatic repair. This is where it gets really funny. Instead of fixing your installation of Windos7 the recovery tool fixed your USB. It actually created mootmgr.exe and Boot folder in the live USB!
5) Reboot. Your "repaired" USB acts as a boot partition, and your Windows7 comes to live.
6) One logged in, go to My Computer, open your USB drive, select "Organize" in the top left couner of your file browser, then "Folder and search options". In View tab, uncheck "Hide protected operating system files" and select "Show hidden files".
7) Boot folder and bootmgr.exe can be seen on the USB now. Copy it to C:\. Replace whatever it asks you to and merge all folders.
8) Safely remove your USB. Reboot and log into Linux. Run ```
sudo update-grub
```9) Reboot and finally log into your Win7!

Now I have no idea why it worked this way. May be I just got lucky. However I managed to reproduce this result, so may be it is actually a good solution.
Yet again, thanks oldfred and Hakunka-Matata. People like you post stuff people like I can later use; Ubuntu would not be what it is without you.

---

### Post by Hakunka-Matata on 2011-03-26
Well done Tron87;  It's so rewarding to see someone stick with the task and achieve the goal.  We all learn in the process.

yeah....

---

