---
title: "Can I load GRUB from grub rescue prompts? if so, how?"
date: 2010-04-11
forum: Installation &amp; Upgrades
---

### Post by t3ubu on 2010-04-11
First the hard data:

Upgraded from Ubuntu 9.04 to 9.10 via upgrade manager
System is AMD 64
Have dual boot with XP on seperate hard drive

SDA1 has XP
SDC2 has ubuntu 9.10 
Grub version is still 0.97 (Grub legacy)

Then the wheelspin:

Seem to have knocked out GRUB as normal loading screen does not appear anymore. 
Worse, I think I accidently installed grub to something labelled SDC5.

Now I'm bogged:

Cannot get anything except the "grub rescue" prompt.
I'm not sure if using the LiveCD (9.10) can help. Have tried a few prompts from other threads but just ended up with mud splattered all over the place.  

I'm gathering I need to load grub, but can I do it using any grub rescue commands?

Chains, towropes, helicopters...anything to lift me out would be great.

---

### Post by dstew on 2010-04-12
Yes, you can boot from the grub-rescue prompt. The fact that you have this prompt means you are probably running a grub 1.97 command line (also known as grub 2).

Hopefully you have a fully installed Ubuntu 9.10 system somewhere. The trick is to locate it, and have grub-rescue boot it. Once the 9.10 system is booted, you can do **grub-install** to re-configure the boot loader permanently.

To find your Ubuntu system from the grub-rescue prompt you use the **ls** command. What is the output of this command (post result to the forum)?.

---

### Post by t3ubu on 2010-04-12
> **dstew said:**
> 

To find your Ubuntu system from the grub-rescue prompt you use the **ls** command. What is the output of this command (post result to the forum)?.

Excellent! so just need to build a bridge it seems...

Ok results of 'ls' at the grub rescue prompt:

(hd0) (hd01) (hd1) (hd1,1) (hd2) (hd2,1) (hd2,5)


Here's hoping further help is at hand!

Tim

---

### Post by drs305 on 2010-04-12
Here you go - how to boot from the Grub2 command line. From the Ubuntu community doc:
[https://help.ubuntu.com/community/Grub2#Using%20CLI%20to%20Boot]("https://help.ubuntu.com/community/Grub2#Using%20CLI%20to%20Boot")

Remember that Grub2 counts the partitions differently from Grub legacy. sda1 is hd0,1, sdb5 is hd1,5; etc.

---

### Post by t3ubu on 2010-04-12
> **drs305 said:**
> Here you go - how to boot from the Grub2 command line. From the Ubuntu community doc:
[https://help.ubuntu.com/community/Grub2#Using%20CLI%20to%20Boot]("https://help.ubuntu.com/community/Grub2#Using%20CLI%20to%20Boot")

Remember that Grub2 counts the partitions differently from Grub legacy. sda1 is hd0,1, sdb5 is hd1,5; etc.

Ok, also found [https://help.ubuntu.com/community/Grub2#Command%20Line%20&%20Rescue%20Mode](https://help.ubuntu.com/community/Grub2#Command%20Line%20&%20Rescue%20Mode)

Tried ls command against each petition and getting 'unknown filesystem' on every petition ie (hd0); then (hd0,1) etc on all petitions except (hd2,1) where I got 'bad filename'

also, tried:

grub rescue> boot 
error: no loaded kernel

grub rescue> set
prefix=(hd2,1)/boot/grub
root=hd2,1

grub rescue>root
(hd2,1): filesystem is ext2.

So hd2,1 is my prob- now looking for solution...

---

### Post by drs305 on 2010-04-12
It's time for the boot info script. Let's see what we are dealing with. Download and run the script, then post the results within "code" tags. You call up the tags by selecting the **#** symbol in the post's menu.

[meierfra's boot info script]("http://bootinfoscript.sourceforge.net/")

---

### Post by t3ubu on 2010-04-13
> **drs305 said:**
> It's time for the boot info script. Let's see what we are dealing with. Download and run the script, then post the results within "code" tags. You call up the tags by selecting the **#** symbol in the post's menu.

[meierfra's boot info script]("http://bootinfoscript.sourceforge.net/")

I've reached a loop in the road- no way to access the internet on the machine that requires the boot-script to be downloaded. Unless there is a way to manually load the boot info script using a terminal in a 9.04 Live CD, I'm stuck (seperate problem has also logged about firefox/internet connection not talking to each other).

More than happy to hand winch myself out of here if I can use other options/commands using abovementioned Live CD and opening a terminal...

---

### Post by drs305 on 2010-04-13
> **t3ubu said:**
> I've reached a loop in the road- no way to access the internet on the machine that requires the boot-script to be downloaded. Unless there is a way to manually load the boot info script using a terminal in a 9.04 Live CD, I'm stuck (seperate problem has also logged about firefox/internet connection not talking to each other).


You can use the procedure detailed in post 12 of the following thread to install (or reinstall depending on which Grub you have)  Grub2 on your system via the LiveCD. There are simpler ways than using "chroot" but this will remove Grub from wherever it ended up and reinstall it to the proper location. 

You will mount your Ubuntu partition. In the first post you say it's on sdc2, but Grub shows sdc1 and sdc5. You will have to find the correct install partition first - mount sdc1 and see if the Ubuntu files are there. If not, try the other partitions. 

Once you know the correct partition, mount it and install Grub 2. Do not install it to a specific partition, install it to the drive (sda, sdb, sdc, for example). It's best to install it to the first drive booted by BIOS. If this isn't the Ubuntu drive, changing BIOS to boot this drive first provides the best results.

Here is the link on how to chroot and install G2:
[http://ubuntuforums.org/showpost.php?p=9107370&postcount=12]("http://ubuntuforums.org/showpost.php?p=9107370&postcount=12")

You can also find the procedure detailed in the GRUB2 link in my signature line.

---

### Post by t3ubu on 2010-04-16
Ok, finally got myself a bootable DVD of beta2 version 10.4, so able to connect to the internet via live install process. 

Ran the boot script; results.txt file is pasted verbatim below:

#                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 1.96 is installed in the MBR of /dev/sda and looks on boot drive #3 
    in partition #1 for /boot/grub.
 => No boot loader is installed in the MBR of /dev/sdb
 => Grub 0.97 is installed in the MBR of /dev/sdc and looks on the same drive 
    in partition #1 for /grub/stage2 and /grub/menu.lst.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sdb1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat32
    Boot sector info:  According to the info in the boot sector, sdb1 starts 
                       at sector 0. But according to the info from fdisk, 
                       sdb1 starts at sector 63.
    Operating System:  
    Boot files/dirs:   

sdc1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/menu.lst /boot/grub/grub.cfg /etc/fstab 
                       /boot/grub/core.img

sdc2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdc5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sdc5 and 
                       looks at sector 80085127 of the same hard drive for 
                       core.img, core.img is at this location on /dev/sdc and 
                       looks on partition #1 for /boot/grub.

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   156,280,319   156,280,257   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63   488,392,064   488,392,002   b W95 FAT32


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 164.7 GB, 164696555520 bytes
255 heads, 63 sectors/track, 20023 cylinders, total 321672960 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdc1                  63   319,436,459   319,436,397  83 Linux
/dev/sdc2         319,436,460   321,669,494     2,233,035   5 Extended
/dev/sdc5         319,436,523   321,669,494     2,232,972  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        046CA2896CA27558                       ntfs                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        46A1-8769                              vfat                                     
/dev/sdb: PTTYPE="dos" 
/dev/sdc1        18932614-82e7-4cf4-874d-2093c2181d45   ext3                                     
/dev/sdc2: PTTYPE="dos" 
/dev/sdc5        3af7b03c-c874-476a-b617-5d2c27d501ed   swap                                     
/dev/sdc: PTTYPE="dos" 
error: /dev/sdd: No medium found

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
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Home Edition" /noexecute=optin /fastdetect 

=========================== sdc1/boot/grub/menu.lst: ===========================

default 0
timeout 20

title Ubuntu 8.10, kernel 2.6.27-7-generic
root (hd2,0)
kernel /boot/vmlinuz-2.6.27-7-generic root=UUID=18932614-82e7-4cf4-874d-2093c2181d45 ro vga=792 quiet noacpi
initrd /boot/initrd.img-2.6.27-7-generic
quiet

title Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
root (hd2,0)
kernel /boot/vmlinuz-2.6.27-7-generic root=UUID=18932614-82e7-4cf4-874d-2093c2181d45 ro  single noacpi
initrd /boot/initrd.img-2.6.27-7-generic

title Ubuntu 8.10, kernel 2.6.24-21-generic
root (hd2,0)
kernel /boot/vmlinuz-2.6.24-21-generic root=UUID=18932614-82e7-4cf4-874d-2093c2181d45 ro vga=792 quiet noacpi
initrd /boot/initrd.img-2.6.24-21-generic
quiet

title Ubuntu 8.10, kernel 2.6.24-21-generic (recovery mode)
root (hd2,0)
kernel /boot/vmlinuz-2.6.24-21-generic root=UUID=18932614-82e7-4cf4-874d-2093c2181d45 ro  single
initrd /boot/initrd.img-2.6.24-21-generic

title Ubuntu 8.10, kernel 2.6.24-19-generic (recovery mode)
root (hd2,0)
kernel /boot/vmlinuz-2.6.24-19-generic root=UUID=18932614-82e7-4cf4-874d-2093c2181d45 ro  single
initrd /boot/initrd.img-2.6.24-19-generic

title Ubuntu 8.10, kernel 2.6.24-19-generic
root (hd2,0)
kernel /boot/vmlinuz-2.6.24-19-generic root=UUID=18932614-82e7-4cf4-874d-2093c2181d45 ro vga=792 quiet noacpi
initrd /boot/initrd.img-2.6.24-19-generic
quiet

title Ubuntu 8.10, memtest86+
root (hd2,0)
kernel /boot/memtest86+.bin
quiet

title Other operating systems:
root 

title Windows NT/2000/XP (loader)
root (hd0,0)
chainloader +1
savedefault
makeactive

=========================== sdc1/boot/grub/grub.cfg: ===========================

#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by /usr/sbin/grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s /boot/grub/grubenv ]; then
  have_grubenv=true
  load_env
fi
set default="0"
if [ ${prev_saved_entry} ]; then
  saved_entry=${prev_saved_entry}
  save_env saved_entry
  prev_saved_entry=
  save_env prev_saved_entry
fi
insmod ext2
set root=(hd2,1)
search --no-floppy --fs-uuid --set 18932614-82e7-4cf4-874d-2093c2181d45
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
if [ ${recordfail} = 1 ]; then
  set timeout=-1
else
  set timeout=5
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
insmod ext2
set root=(hd2,1)
search --no-floppy --fs-uuid --set 18932614-82e7-4cf4-874d-2093c2181d45
insmod png
if background_image /boot/grub/moreblue-orbit-grub.png ; then
  set color_normal=black/black
  set color_highlight=magenta/black
else
  set menu_color_normal=white/black
  set menu_color_highlight=black/white
fi
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry "Ubuntu, Linux 2.6.31-20-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd2,1)
    search --no-floppy --fs-uuid --set 18932614-82e7-4cf4-874d-2093c2181d45
    linux    /boot/vmlinuz-2.6.31-20-generic root=UUID=18932614-82e7-4cf4-874d-2093c2181d45 ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-20-generic
}
menuentry "Ubuntu, Linux 2.6.31-20-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd2,1)
    search --no-floppy --fs-uuid --set 18932614-82e7-4cf4-874d-2093c2181d45
    linux    /boot/vmlinuz-2.6.31-20-generic root=UUID=18932614-82e7-4cf4-874d-2093c2181d45 ro single 
    initrd    /boot/initrd.img-2.6.31-20-generic
}
menuentry "Ubuntu, Linux 2.6.28-18-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd2,1)
    search --no-floppy --fs-uuid --set 18932614-82e7-4cf4-874d-2093c2181d45
    linux    /boot/vmlinuz-2.6.28-18-generic root=UUID=18932614-82e7-4cf4-874d-2093c2181d45 ro   quiet splash
    initrd    /boot/initrd.img-2.6.28-18-generic
}
menuentry "Ubuntu, Linux 2.6.28-18-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd2,1)
    search --no-floppy --fs-uuid --set 18932614-82e7-4cf4-874d-2093c2181d45
    linux    /boot/vmlinuz-2.6.28-18-generic root=UUID=18932614-82e7-4cf4-874d-2093c2181d45 ro single 
    initrd    /boot/initrd.img-2.6.28-18-generic
}
menuentry "Ubuntu, Linux 2.6.24-21-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd2,1)
    search --no-floppy --fs-uuid --set 18932614-82e7-4cf4-874d-2093c2181d45
    linux    /boot/vmlinuz-2.6.24-21-generic root=UUID=18932614-82e7-4cf4-874d-2093c2181d45 ro   quiet splash
    initrd    /boot/initrd.img-2.6.24-21-generic
}
menuentry "Ubuntu, Linux 2.6.24-21-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd2,1)
    search --no-floppy --fs-uuid --set 18932614-82e7-4cf4-874d-2093c2181d45
    linux    /boot/vmlinuz-2.6.24-21-generic root=UUID=18932614-82e7-4cf4-874d-2093c2181d45 ro single 
    initrd    /boot/initrd.img-2.6.24-21-generic
}
menuentry "Ubuntu, Linux 2.6.24-19-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd2,1)
    search --no-floppy --fs-uuid --set 18932614-82e7-4cf4-874d-2093c2181d45
    linux    /boot/vmlinuz-2.6.24-19-generic root=UUID=18932614-82e7-4cf4-874d-2093c2181d45 ro   quiet splash
    initrd    /boot/initrd.img-2.6.24-19-generic
}
menuentry "Ubuntu, Linux 2.6.24-19-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd2,1)
    search --no-floppy --fs-uuid --set 18932614-82e7-4cf4-874d-2093c2181d45
    linux    /boot/vmlinuz-2.6.24-19-generic root=UUID=18932614-82e7-4cf4-874d-2093c2181d45 ro single 
    initrd    /boot/initrd.img-2.6.24-19-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Home Edition (on /dev/sda1)" {
    insmod ntfs
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set 046ca2896ca27558
    drivemap -s (hd0) ${root}
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sdc1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdc1
UUID=18932614-82e7-4cf4-874d-2093c2181d45 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sdc5
UUID=3af7b03c-c874-476a-b617-5d2c27d501ed none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sdc1: Location of files loaded by Grub: ===================


  41.0GB: boot/grub/core.img
  41.0GB: boot/grub/grub.cfg
  41.0GB: boot/grub/menu.lst
  41.0GB: boot/initrd.img-2.6.24-19-generic
  40.9GB: boot/initrd.img-2.6.24-19-generic.bak
  40.9GB: boot/initrd.img-2.6.24-21-generic
  41.0GB: boot/initrd.img-2.6.24-21-generic.bak
  41.0GB: boot/initrd.img-2.6.28-18-generic
  41.0GB: boot/initrd.img-2.6.31-20-generic
  40.9GB: boot/vmlinuz-2.6.24-19-generic
  40.9GB: boot/vmlinuz-2.6.24-21-generic
  40.9GB: boot/vmlinuz-2.6.28-18-generic
  41.0GB: boot/vmlinuz-2.6.31-20-generic
  33.8GB: grub/stage2
  41.0GB: initrd.img
  41.0GB: initrd.img.old
  41.0GB: vmlinuz
  40.9GB: vmlinuz.old
=======Devices which don't seem to have a corresponding hard drive==============

sdd#



Hoping this points a huge arrow as to what next step should be...continued assistance will be joyfully received.

---

### Post by drs305 on 2010-04-16
t3ubu,

I am proceeding under the assumption you are still unable to boot and are getting the rescue prompt.

You have Grub legacy and Grub2 installed on your system. I recommend you uninstall both and completely reinstall Grub2. In this way, you will clean up your system and also be ready for Lucid if you choose to do an online upgrade.

These instructions are for an Ubuntu install on sdc1.


From the LiveCD, add the necessary system files to a new mount point:
 
```
sudo -i
mount /dev/sdc1 /mnt
mount --bind /dev  /mnt/dev
mount --bind /proc /mnt/proc
mount --bind /sys  /mnt/sys
mount --bind /usr/ /mnt/usr
chroot /mnt

```

Now everything you do will affect your *real* Ubuntu install on sdc1. Commands you run will act on your actual installation, not the LiveCD files.

As you proceed you will get a warning about not having a boot loader because you are going to temporarily remove all the grub files. Make sure you have a reliable Internet connection and your power won't get interrupted:

As grub-pc is installed, it will ask twice if you want to include any extra items in the default boot lines. Just accept what is already in the line, if anything.

More importantly, you will be asked where to install Grub2. Choose "sdc" by highlighting it and pressing the space bar. That should place an * next to "sdc". If desired, you can also install it to "sda" using the same procedure. It doesn't hurt anything to place G2 on both. *Do not* select an individual partition, such as sdc1. Once you have made your selection(s), press the TAB key to highlight "OK" and press ENTER to continue. 

Here are the required commands to remove and then reinstall grub-pc and grub-common.

```
sudo -i
apt-get purge grub-pc grub-common grub
apt-get install grub-pc grub-common
grub-install /dev/sdc
grub-install --recheck /dev/sdc

```

Exit by pressing CTRL-d.

Now unmount what you previously mounted:
```
umount /mnt/dev /mnt/proc /mnt/sys /mnt/usr 
umount /mnt

```

Reboot, then run:
```
sudo update-grub
```

---

### Post by t3ubu on 2010-05-15
> **drs305 said:**
> t3ubu,

I am proceeding under the assumption you are still unable to boot and are getting the rescue prompt.

You have Grub legacy and Grub2 installed on your system. I recommend you uninstall both and completely reinstall Grub2. In this way, you will clean up your system and also be ready for Lucid if you choose to do an online upgrade.

These instructions are for an Ubuntu install on sdc1.


From the LiveCD, add the necessary system files to a new mount point:
 
[CODE]sudo -i
mount /dev/sdc1 /mnt
mount --bind /dev  /mnt/dev
mount --bind /proc /mnt/proc
mount --bind /sys  /mnt/sys
mount --bind /usr/ /mnt/usr
chroot /mnt


Sorry to continue this thread; problem still not quite fixed...happy to follow instructions to the letter, but I've stalled at the first step "add the necessary system files to a new mount point..."

I'm working off liveCD and net connection...I tried opening a terminal, and inputting the above commands, and got the following response- in the terminal:

ubuntu@ubuntu:~$ sudo -i
root@ubuntu:~# mount /dev/sdc /mnt
mount: /dev/sdc already mounted or /mnt busy

If anyone can advise how I can code the above that would be great- if it's not via a terminal, where else does ubuntu-nubie here begin?

---

### Post by frantid on 2010-05-15
]you left off the "1" in sdc1

might I suggest copying and pasting?

edit:  do you know which drive is truly your bios boot drive?  If your boot drive is sda, you need to modify the commands to:

```
grub-install --root-directory=/dev/sdc1 /dev/sda
grub-install --recheck --root-directory=/dev/sdc1 /dev/sda
```

---

