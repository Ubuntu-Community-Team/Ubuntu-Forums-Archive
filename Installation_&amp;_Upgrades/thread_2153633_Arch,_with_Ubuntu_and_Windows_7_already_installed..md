---
title: "Arch, with Ubuntu and Windows 7 already installed."
date: 2013-06-11
forum: Installation &amp; Upgrades
---

### Post by s33k3rgr on 2013-06-11
I want to install Arch and my pc already have Ubuntu and Windows 7 installed. I don't want to erase any partition or mess up the Grub menu @boot. I just want to install Arch and update Grub menu to include Arch.

My two hard drives are 1TB(Windows) and 300 GB(Ubuntu).

I provide some info about my hard drive setup (screenshots from gparted - see attachments).

What do u recommend to do ? Which empty space should i use and what must i avoid in order to not mess my Grub menu ??

---

### Post by oldfred on 2013-06-11
I have not installed Arch. But do you have your Windows boot loader in the MBR of your Windows drive and grub2 in the MBR of the Ubuntu drive?
If Arch gives the choice do not install its grub2 to any MBR, but install to its partition more as a throw away just ot have a grub.cfg. Then run sudo update-grub in Ubuntu and it will read the grub.cfg or grub configuration file from Arch and add a boot stanza to let you boot Arch from Ubuntu's grub menu.

If just testing Arch, just shrink either Windows using Windows disk tools or Ubuntu with gparted from a liveCD to make a 25GB / (root) partition.

---

### Post by bfmetcalf on 2013-06-11
You can also install arch to a USB stick pretty easily, just follow the beginners guide and it should work fine.  Then run the update-grub with the usb-stick in place and it should add it to Ubuntu's grub line fine.

---

### Post by fantab on 2013-06-12
You have to create a new partition on /dev/sdb (which is a Ubuntu drive) by creating some space from /dev/sda1, then you can install ARCH on it. 
Just don't install GRUB Bootloader when Arch asks you to. After installing Arch without Bootloader you have to boot back into Ubuntu and run:

```
sudo update-grub
```

---

### Post by s33k3rgr on 2013-06-12
Do i need to partition before the arch installation or during it? Can i do it through gparted in ubuntu?

---

### Post by gigenieks on 2013-06-12
[Beginners Guide:]("https://wiki.archlinux.org/index.php/Beginners'_Guide")
> 
Absolute beginners are encouraged to use a graphical partitioning tool. GParted is a good example, and is provided as a "live" CD. It is also included on live CDs of most Linux distributions such as Ubuntu and Linux Mint. A drive should first be partitioned and the partitions should be formatted with a file system before rebooting.


Note: I'm also going to install ArchLinux. Probably today. Doing preparations.. My setup will be similar to yours (Win8 + Ubuntu + Arch). Gonna post later with results.

---

### Post by fantab on 2013-06-12
> **s33k3rgr said:**
> Do i need to partition before the arch installation or during it? Can i do it through gparted in ubuntu?

Create Partition before you install ARCH. You can use your Ubuntu LiveDVD/USB to use Gparted. Or Create [GPARTED LiveCD/USB]("http://gparted.sourceforge.net/livecd.php").

Do NOT use Gparted from installed Ubuntu because the partition you are going to resize has Ubuntu installed on it and its a very very bad idea to work on partitions that are in use/mounted.

---

### Post by s33k3rgr on 2013-06-13
I get the following sequence of messages during my first boot.

```

early console in decompress_kernel

Decompressing Linux... Parsing ELF... done
Booting the kernel.
:: running early hook [udev]
:: running hook [udev]
:: Triggering uevents...
:: performing fsck on '/dev/sda5'
fsck: fsck.swap: not found
fsck: error 2 while executing fsck.swap for /dev/sda5
ERROR: fsck failed on 'dev/sda5'
:: mounting '/dev/sda5' on real root
mount: unknown filesystem type 'swap'
You are now being dropped into an emergency shell.
sh: can't access tty; job control turned off
[rootfs /]# 

```

My partition table is the following : 

[img]http://i41.tinypic.com/mjp8g1.png[/img]

I'll try to explain further what i did. I got two hard drives on my system .   **_sda_** and **_sdb_** . sda disk is 1TB and had **_windows 7_** installed in all of its capacity (prior the arch installation). The other hard drive sdb is 270GB and had **_Ubuntu_** installed .  sdb has **_Grub_** installed also. 

I decided to install Arch and go triple boot . I followed roughly [this installation](http://www.muktware.com/5451/how-install-arch-linux) without the part where the guy installs grub. I chose that after installing arch i will go to Ubuntu and update my grub with ```
sudo update-grub
``` and so did i. Grub updated succesfully and i got one addition to the menu of Grub (Arch on /dev/sda5). Also i want to report that i used gpartedlive Usb to make my arch partitions. 

After booting to Arch i was getting the above message which is difficult to decrypt but i know that is something subtle. I just can't get my head around it.

---

### Post by fantab on 2013-06-14
Did you reinstall Arch after creating SWAP?
Have you reinstalled ARCH?

Post the output of:
```
sudo parted -l
```

Post the output of **[BootInfo Script?]("http://bootinfoscript.sourceforge.net/")** Or if you have 'Boot-Repair' already installed then post the output of 'BootInfo Summary'.

However, my suggestion is use [**ARCH Wiki**]("https://wiki.archlinux.org/index.php/Beginners%27_Guide") to Re-install Arch. Its simple and quite informative. Like I have mentioned earlier, I have installed Arch without installing GRUB and boot it with Ubuntu-Grub, and I have no issues. I suspect that you may have missed a step during Arch Install. Are you sure you generated /etc/fstab? 

Run:
```
sudo blkid
```

and compare the UUID's in /etc/fstab with the UUID's which are shown by the above command. (Mount Arch Partition from Ubuntu and open /etc/fstab to look at its contents to compare).
Post the output of sudo blkid and the contents of Arch- /etc/fstab, if you have any doubts.

Good Luck...

---

### Post by s33k3rgr on 2013-06-14
To answer your first question, yes i have reinstalled Arch but first  i deleted all the partitions in the extended part of the sda 
disk and repartitioned with the same logic. So i reinstalled Arch.


The output of ```
sudo parted -l
```  is below :

```

Model: ATA SAMSUNG HD103SJ (scsi)
Disk /dev/sda: 1000GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos


Number  Start   End     Size    Type      File system     Flags
 1      1049kB  106MB   105MB   primary   ntfs            boot
 2      106MB   838GB   838GB   primary   ntfs
 3      838GB   1000GB  162GB   extended
 5      838GB   855GB   16.5GB  logical   ext4
 6      855GB   858GB   3492MB  logical   linux-swap(v1)
 7      858GB   1000GB  142GB   logical   ext4




Model: ATA ST3320418AS (scsi)
Disk /dev/sdb: 320GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos


Number  Start   End    Size    Type      File system     Flags
 1      1049kB  311GB  311GB   primary   ext4            boot
 2      311GB   320GB  8587MB  extended
 5      311GB   320GB  8587MB  logical   linux-swap(v1)

```


Here is the loooong output of the _bootinfoscript_ :

```

   Boot Info Script 0.61      [1 April 2012]




============================= Boot Info Summary: ===============================


 => Windows is installed in the MBR of /dev/sda.
 => Grub2 (v1.99) is installed in the MBR of /dev/sdb and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (,msdos1)/boot/grub on this drive.


sda1: __________________________________________________________________________


    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /Boot/BCD


sda2: __________________________________________________________________________


    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files:        /Windows/System32/winload.exe


sda3: __________________________________________________________________________


    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info: 


sda5: __________________________________________________________________________


    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Arch Linux ()
    Boot files:        /etc/fstab


sda6: __________________________________________________________________________


    File system:       swap
    Boot sector type:  -
    Boot sector info: 


sda7: __________________________________________________________________________


    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  
    Boot files:        


sdb1: __________________________________________________________________________


    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Ubuntu 12.04.2 LTS
    Boot files:        /boot/grub/grub.cfg /etc/fstab 
                       /boot/extlinux/extlinux.conf /boot/grub/core.img


sdb2: __________________________________________________________________________


    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info: 


sdb5: __________________________________________________________________________


    File system:       swap
    Boot sector type:  -
    Boot sector info: 


============================ Drive/Partition Info: =============================


Drive: sda _____________________________________________________________________


Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes


Partition  Boot  Start Sector    End Sector  # of Sectors  Id System


/dev/sda1    *          2,048       206,847       204,800   7 NTFS / exFAT / HPFS
/dev/sda2             206,848 1,637,087,231 1,636,880,384   7 NTFS / exFAT / HPFS
/dev/sda3       1,637,087,232 1,953,523,711   316,436,480   5 Extended
/dev/sda5       1,637,089,280 1,669,365,759    32,276,480  83 Linux
/dev/sda6       1,669,367,808 1,676,187,647     6,819,840  82 Linux swap / Solaris
/dev/sda7       1,676,189,696 1,953,523,711   277,334,016  83 Linux




Drive: sdb _____________________________________________________________________


Disk /dev/sdb: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes


Partition  Boot  Start Sector    End Sector  # of Sectors  Id System


/dev/sdb1    *          2,048   608,368,639   608,366,592  83 Linux
/dev/sdb2         608,370,686   625,141,759    16,771,074   5 Extended
/dev/sdb5         608,370,688   625,141,759    16,771,072  82 Linux swap / Solaris




"blkid" output: ________________________________________________________________


Device           UUID                                   TYPE       LABEL


/dev/sda1        12923898923881F1                       ntfs       System Reserved
/dev/sda2        3AF04536F044FA21                       ntfs       
/dev/sda5        0e2597fd-b847-4da2-8b58-73fd216ad1f8   ext4       
/dev/sda6        798fd669-f356-4594-a516-dfc75ebf9dcb   swap       
/dev/sda7        2d3b4dd4-0b86-4171-a618-ec0846bc83be   ext4       
/dev/sdb1        761353a7-7c9d-46c2-8bfb-301ea1637546   ext4       
/dev/sdb5        908e0cfd-b0ab-46bb-8ec9-62d5c962442e   swap       


================================ Mount points: =================================


Device           Mount_Point              Type       Options


/dev/sda5        /media/0e2597fd-b847-4da2-8b58-73fd216ad1f8 ext4       (rw,nosuid,nodev,uhelper=udisks)
/dev/sda7        /media/2d3b4dd4-0b86-4171-a618-ec0846bc83be ext4       (rw,nosuid,nodev,uhelper=udisks)
/dev/sdb1        /                        ext4       (rw,errors=remount-ro)




=============================== sda5/etc/fstab: ================================


--------------------------------------------------------------------------------
# 
# /etc/fstab: static file system information
#
# <file system>    <dir>    <type>    <options>    <dump>    <pass>
# /dev/sda5
UUID=0e2597fd-b847-4da2-8b58-73fd216ad1f8    /             ext4          rw,relatime,data=ordered    0 1


# /dev/sda7
UUID=2d3b4dd4-0b86-4171-a618-ec0846bc83be    /home         ext4          rw,relatime,data=ordered    0 2


# /dev/sda6
UUID=798fd669-f356-4594-a516-dfc75ebf9dcb    none          swap          defaults      0 0


--------------------------------------------------------------------------------


=================== sda5: Location of files loaded by Grub: ====================


           GiB - GB             File                                 Fragment(s)


 780.872230530 = 838.455173120  boot/initramfs-linux-fallback.img              1
 788.821151733 = 846.990262272  boot/initramfs-linux.img                       1
 788.753322601 = 846.917431296  boot/vmlinuz-linux                             1


=========================== sdb1/boot/grub/grub.cfg: ===========================


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
set root='(hd1,msdos1)'
search --no-floppy --fs-uuid --set=root 761353a7-7c9d-46c2-8bfb-301ea1637546
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
  insmod part_msdos
  insmod ext2
  set root='(hd1,msdos1)'
  search --no-floppy --fs-uuid --set=root 761353a7-7c9d-46c2-8bfb-301ea1637546
  set locale_dir=($root)/boot/grub/locale
  set lang=en_US
  insmod gettext
fi
terminal_output gfxterm
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
function gfxmode {
    set gfxpayload="${1}"
    if [ "${1}" = "keep" ]; then
        set vt_handoff=vt.handoff=7
    else
        set vt_handoff=
    fi
}
if [ "${recordfail}" != 1 ]; then
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
if [ "${linux_gfx_mode}" != "text" ]; then load_video; fi
menuentry 'Ubuntu, with Linux 3.2.0-45-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    gfxmode $linux_gfx_mode
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos1)'
    search --no-floppy --fs-uuid --set=root 761353a7-7c9d-46c2-8bfb-301ea1637546
    linux    /boot/vmlinuz-3.2.0-45-generic-pae root=UUID=761353a7-7c9d-46c2-8bfb-301ea1637546 ro   quiet splash $vt_handoff
    initrd    /boot/initrd.img-3.2.0-45-generic-pae
}
menuentry 'Ubuntu, with Linux 3.2.0-45-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos1)'
    search --no-floppy --fs-uuid --set=root 761353a7-7c9d-46c2-8bfb-301ea1637546
    echo    'Loading Linux 3.2.0-45-generic-pae ...'
    linux    /boot/vmlinuz-3.2.0-45-generic-pae root=UUID=761353a7-7c9d-46c2-8bfb-301ea1637546 ro recovery nomodeset 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-3.2.0-45-generic-pae
}
submenu "Previous Linux versions" {
menuentry 'Ubuntu, with Linux 3.2.0-40-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    gfxmode $linux_gfx_mode
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos1)'
    search --no-floppy --fs-uuid --set=root 761353a7-7c9d-46c2-8bfb-301ea1637546
    linux    /boot/vmlinuz-3.2.0-40-generic-pae root=UUID=761353a7-7c9d-46c2-8bfb-301ea1637546 ro   quiet splash $vt_handoff
    initrd    /boot/initrd.img-3.2.0-40-generic-pae
}
menuentry 'Ubuntu, with Linux 3.2.0-40-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos1)'
    search --no-floppy --fs-uuid --set=root 761353a7-7c9d-46c2-8bfb-301ea1637546
    echo    'Loading Linux 3.2.0-40-generic-pae ...'
    linux    /boot/vmlinuz-3.2.0-40-generic-pae root=UUID=761353a7-7c9d-46c2-8bfb-301ea1637546 ro recovery nomodeset 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-3.2.0-40-generic-pae
}
menuentry 'Ubuntu, with Linux 3.2.0-39-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    gfxmode $linux_gfx_mode
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos1)'
    search --no-floppy --fs-uuid --set=root 761353a7-7c9d-46c2-8bfb-301ea1637546
    linux    /boot/vmlinuz-3.2.0-39-generic-pae root=UUID=761353a7-7c9d-46c2-8bfb-301ea1637546 ro   quiet splash $vt_handoff
    initrd    /boot/initrd.img-3.2.0-39-generic-pae
}
menuentry 'Ubuntu, with Linux 3.2.0-39-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos1)'
    search --no-floppy --fs-uuid --set=root 761353a7-7c9d-46c2-8bfb-301ea1637546
    echo    'Loading Linux 3.2.0-39-generic-pae ...'
    linux    /boot/vmlinuz-3.2.0-39-generic-pae root=UUID=761353a7-7c9d-46c2-8bfb-301ea1637546 ro recovery nomodeset 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-3.2.0-39-generic-pae
}
menuentry 'Ubuntu, with Linux 3.2.0-37-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    gfxmode $linux_gfx_mode
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos1)'
    search --no-floppy --fs-uuid --set=root 761353a7-7c9d-46c2-8bfb-301ea1637546
    linux    /boot/vmlinuz-3.2.0-37-generic-pae root=UUID=761353a7-7c9d-46c2-8bfb-301ea1637546 ro   quiet splash $vt_handoff
    initrd    /boot/initrd.img-3.2.0-37-generic-pae
}
menuentry 'Ubuntu, with Linux 3.2.0-37-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos1)'
    search --no-floppy --fs-uuid --set=root 761353a7-7c9d-46c2-8bfb-301ea1637546
    echo    'Loading Linux 3.2.0-37-generic-pae ...'
    linux    /boot/vmlinuz-3.2.0-37-generic-pae root=UUID=761353a7-7c9d-46c2-8bfb-301ea1637546 ro recovery nomodeset 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-3.2.0-37-generic-pae
}
menuentry 'Ubuntu, with Linux 3.2.0-36-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    gfxmode $linux_gfx_mode
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos1)'
    search --no-floppy --fs-uuid --set=root 761353a7-7c9d-46c2-8bfb-301ea1637546
    linux    /boot/vmlinuz-3.2.0-36-generic-pae root=UUID=761353a7-7c9d-46c2-8bfb-301ea1637546 ro   quiet splash $vt_handoff
    initrd    /boot/initrd.img-3.2.0-36-generic-pae
}
menuentry 'Ubuntu, with Linux 3.2.0-36-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos1)'
    search --no-floppy --fs-uuid --set=root 761353a7-7c9d-46c2-8bfb-301ea1637546
    echo    'Loading Linux 3.2.0-36-generic-pae ...'
    linux    /boot/vmlinuz-3.2.0-36-generic-pae root=UUID=761353a7-7c9d-46c2-8bfb-301ea1637546 ro recovery nomodeset 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-3.2.0-36-generic-pae
}
menuentry 'Ubuntu, with Linux 3.2.0-35-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    gfxmode $linux_gfx_mode
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos1)'
    search --no-floppy --fs-uuid --set=root 761353a7-7c9d-46c2-8bfb-301ea1637546
    linux    /boot/vmlinuz-3.2.0-35-generic-pae root=UUID=761353a7-7c9d-46c2-8bfb-301ea1637546 ro   quiet splash $vt_handoff
    initrd    /boot/initrd.img-3.2.0-35-generic-pae
}
menuentry 'Ubuntu, with Linux 3.2.0-35-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos1)'
    search --no-floppy --fs-uuid --set=root 761353a7-7c9d-46c2-8bfb-301ea1637546
    echo    'Loading Linux 3.2.0-35-generic-pae ...'
    linux    /boot/vmlinuz-3.2.0-35-generic-pae root=UUID=761353a7-7c9d-46c2-8bfb-301ea1637546 ro recovery nomodeset 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-3.2.0-35-generic-pae
}
menuentry 'Ubuntu, with Linux 3.0.0-29-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    gfxmode $linux_gfx_mode
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos1)'
    search --no-floppy --fs-uuid --set=root 761353a7-7c9d-46c2-8bfb-301ea1637546
    linux    /boot/vmlinuz-3.0.0-29-generic-pae root=UUID=761353a7-7c9d-46c2-8bfb-301ea1637546 ro   quiet splash $vt_handoff
    initrd    /boot/initrd.img-3.0.0-29-generic-pae
}
menuentry 'Ubuntu, with Linux 3.0.0-29-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos1)'
    search --no-floppy --fs-uuid --set=root 761353a7-7c9d-46c2-8bfb-301ea1637546
    echo    'Loading Linux 3.0.0-29-generic-pae ...'
    linux    /boot/vmlinuz-3.0.0-29-generic-pae root=UUID=761353a7-7c9d-46c2-8bfb-301ea1637546 ro recovery nomodeset 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-3.0.0-29-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.38-11-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    gfxmode $linux_gfx_mode
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos1)'
    search --no-floppy --fs-uuid --set=root 761353a7-7c9d-46c2-8bfb-301ea1637546
    linux    /boot/vmlinuz-2.6.38-11-generic-pae root=UUID=761353a7-7c9d-46c2-8bfb-301ea1637546 ro   quiet splash $vt_handoff
    initrd    /boot/initrd.img-2.6.38-11-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.38-11-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos1)'
    search --no-floppy --fs-uuid --set=root 761353a7-7c9d-46c2-8bfb-301ea1637546
    echo    'Loading Linux 2.6.38-11-generic-pae ...'
    linux    /boot/vmlinuz-2.6.38-11-generic-pae root=UUID=761353a7-7c9d-46c2-8bfb-301ea1637546 ro recovery nomodeset 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.38-11-generic-pae
}
}
### END /etc/grub.d/10_linux ###


### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###


### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos1)'
    search --no-floppy --fs-uuid --set=root 761353a7-7c9d-46c2-8bfb-301ea1637546
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos1)'
    search --no-floppy --fs-uuid --set=root 761353a7-7c9d-46c2-8bfb-301ea1637546
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###


### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set=root 12923898923881F1
    chainloader +1
}
menuentry "Arch (on /dev/sda5)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set=root 0e2597fd-b847-4da2-8b58-73fd216ad1f8
    linux /boot/vmlinuz-linux root=/dev/sda5
    initrd /boot/initramfs-linux.img
}
### END /etc/grub.d/30_os-prober ###


### BEGIN /etc/grub.d/30_uefi-firmware ###
### END /etc/grub.d/30_uefi-firmware ###


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


=============================== sdb1/etc/fstab: ================================


--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/sda1       /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=908e0cfd-b0ab-46bb-8ec9-62d5c962442e none            swap    sw              0       0
--------------------------------------------------------------------------------


====================== sdb1/boot/extlinux/extlinux.conf: =======================


--------------------------------------------------------------------------------
## /boot/extlinux/extlinux.conf
##
## IMPORTANT WARNING
##
## The configuration of this file is generated automatically.
## Do not edit this file manually, use: extlinux-update




default l0
prompt 1
timeout 50


include themes/debian/theme.cfg
--------------------------------------------------------------------------------


=================== sdb1: Location of files loaded by Grub: ====================


           GiB - GB             File                                 Fragment(s)


 136.153617859 = 146.193833984  boot/grub/core.img                             1
 139.696758270 = 149.998252032  boot/grub/grub.cfg                             1
  33.680664062 = 36.164337664   boot/initrd.img-2.6.38-11-generic-pae          2
 185.881027222 = 199.588233216  boot/initrd.img-3.0.0-29-generic-pae           1
 196.701667786 = 211.206807552  boot/initrd.img-3.2.0-35-generic-pae           2
 142.428234100 = 152.931151872  boot/initrd.img-3.2.0-36-generic-pae           1
 233.606384277 = 250.832945152  boot/initrd.img-3.2.0-37-generic-pae           2
 243.634876251 = 261.600956416  boot/initrd.img-3.2.0-39-generic-pae           2
  91.397224426 = 98.137022464   boot/initrd.img-3.2.0-40-generic-pae           2
  83.785449982 = 89.963941888   boot/initrd.img-3.2.0-45-generic-pae           2
 136.864688873 = 146.957340672  boot/vmlinuz-2.6.38-11-generic-pae             2
  69.837486267 = 74.987429888   boot/vmlinuz-3.0.0-29-generic-pae              2
 172.240028381 = 184.941322240  boot/vmlinuz-3.2.0-35-generic-pae              1
 140.431434631 = 150.787104768  boot/vmlinuz-3.2.0-36-generic-pae              1
 140.931434631 = 151.323975680  boot/vmlinuz-3.2.0-37-generic-pae              2
 230.622840881 = 247.629389824  boot/vmlinuz-3.2.0-39-generic-pae              1
 243.372844696 = 261.319602176  boot/vmlinuz-3.2.0-40-generic-pae              1
  12.529094696 = 13.453012992   boot/vmlinuz-3.2.0-45-generic-pae              2
  83.785449982 = 89.963941888   initrd.img                                     2
  91.397224426 = 98.137022464   initrd.img.old                                 2
  12.529094696 = 13.453012992   vmlinuz                                        2
 243.372844696 = 261.319602176  vmlinuz.old                                    1


================= sdb1: Location of files loaded by Syslinux: ==================


           GiB - GB             File                                 Fragment(s)


  16.136688232 = 17.326637056   boot/extlinux/chain.c32                        1
  16.136165619 = 17.326075904   boot/extlinux/extlinux.conf                    1


============== sdb1: Version of COM32(R) files used by Syslinux: ===============


 boot/extlinux/chain.c32            :  COM32R module (v4.xx)


======================== Unknown MBRs/Boot Sectors/etc: ========================


Unknown BootLoader on sdb2


00000000  28 8b 84 06 d5 fc 02 0f  94 d8 6c 2a 33 53 f7 c5  |(.........l*3S..|
00000010  6c 7a 01 78 a4 6a 25 2b  d5 7f 2e 2e 91 bb bf 6f  |lz.x.j%+.......o|
00000020  67 85 6a cb d5 cb fb 9e  e4 f4 f7 84 71 13 80 61  |g.j.........q..a|
00000030  73 e4 96 fb c5 29 81 57  41 85 93 7c c0 3c 5f ff  |s....).WA..|.<_.|
00000040  30 a5 c4 2c 64 46 c9 57  bb 35 6f e1 1f 53 54 10  |0..,dF.W.5o..ST.|
00000050  ad c0 78 1b 9f d0 7c 9f  fe db 3e b6 f7 93 b6 91  |..x...|...>.....|
00000060  53 74 f7 a4 ff 72 cb d1  76 34 42 44 92 5f e5 0f  |St...r..v4BD._..|
00000070  a0 71 7a 80 56 bc 4a 2e  6d 4d 3e fb 5f 53 16 b9  |.qz.V.J.mM>._S..|
00000080  34 c4 74 c3 54 03 31 a9  d3 fd db 01 4d 05 4f b6  |4.t.T.1.....M.O.|
00000090  34 63 de 06 1f 8f 00 34  4a 54 af ca 40 e8 ef 5a  |4c.....4JT..@..Z|
000000a0  4a 35 aa 9b c5 f8 35 06  54 0c 3f 1f 55 4a cb 87  |J5....5.T.?.UJ..|
000000b0  f1 8c bf 18 17 5e 7e 3f  d4 0d b8 14 d9 02 e1 5b  |.....^~?.......[|
000000c0  0c 24 7f 55 0f d5 de 8e  ab fd 7f e2 f9 c4 04 c1  |.$.U............|
000000d0  00 49 2f 90 7e ab e2 20  97 01 8b 41 8c 84 2b e1  |.I/.~.. ...A..+.|
000000e0  d7 c7 fa 07 95 7b a3 d4  89 79 4f ff 14 f9 40 d0  |.....{...yO...@.|
000000f0  0a 60 a0 2a 09 80 f0 14  0e 07 07 14 8f 41 8e aa  |.`.*.........A..|
00000100  a3 f5 42 32 9d 1d c6 8e  84 20 60 84 10 44 a0 65  |..B2..... `..D.e|
00000110  7b e1 de cf c1 dd 11 4b  ac e6 36 19 17 78 1e 02  |{......K..6..x..|
00000120  04 55 62 50 96 a3 fa 3c  56 3b f7 c9 60 05 aa 04  |.UbP...<V;..`...|
00000130  18 07 a2 9a c9 e0 53 0b  05 10 2c 12 36 1c 19 58  |......S...,.6..X|
00000140  41 07 80 ff 24 18 bc 19  5f 95 84 01 2c bc 78 24  |A...$..._...,.x$|
00000150  09 03 f5 65 de 12 15 73  c0 73 ea 22 95 ce 2a 65  |...e...s.s."..*e|
00000160  40 81 c7 d1 fa aa a8 03  c0 35 4f b3 47 f4 7f 90  |@........5O.G...|
00000170  0b 8a c4 b0 84 0f 07 ff  98 42 f8 3c 37 fe 22 52  |.........B.<7."R|
00000180  00 3e e9 c3 04 60 79 04  c2 a2 97 09 40 cd 78 8b  |.>...`y.....@.x.|
00000190  61 df 17 73 ce d7 1a 4c  9f e7 b4 0e 04 36 69 c0  |a..s...L.....6i.|
000001a0  63 1b 2e 1e 7a 81 a9 25  58 18 58 10 b6 b8 19 de  |c...z..%X.X.....|
000001b0  4a 89 72 07 a6 48 4a d9  5b 72 a4 94 f0 91 00 fe  |J.r..HJ.[r......|
000001c0  ff ff 82 fe ff ff 02 00  00 00 00 e8 ff 00 00 00  |................|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200




=============================== StdErr Messages: ===============================


xz: (stdin): Compressed data is corrupt




```


Here is the output of _sudo blkid_:

```

/dev/sda1: LABEL="System Reserved" UUID="12923898923881F1" TYPE="ntfs" 
/dev/sda2: UUID="3AF04536F044FA21" TYPE="ntfs" 
/dev/sda5: UUID="0e2597fd-b847-4da2-8b58-73fd216ad1f8" TYPE="ext4" 
/dev/sda6: UUID="798fd669-f356-4594-a516-dfc75ebf9dcb" TYPE="swap" 
/dev/sda7: UUID="2d3b4dd4-0b86-4171-a618-ec0846bc83be" TYPE="ext4" 
/dev/sdb1: UUID="761353a7-7c9d-46c2-8bfb-301ea1637546" TYPE="ext4" 
/dev/sdb5: UUID="908e0cfd-b0ab-46bb-8ec9-62d5c962442e" TYPE="swap"

```


and finally the contents of _fstab_ in _sda5_:

```

# 
# /etc/fstab: static file system information
#
# <file system>    <dir>    <type>    <options>    <dump>    <pass>
# /dev/sda5
UUID=0e2597fd-b847-4da2-8b58-73fd216ad1f8    /             ext4          rw,relatime,data=ordered    0 1


# /dev/sda7
UUID=2d3b4dd4-0b86-4171-a618-ec0846bc83be    /home         ext4          rw,relatime,data=ordered    0 2


# /dev/sda6
UUID=798fd669-f356-4594-a516-dfc75ebf9dcb    none          swap          defaults      0 0



```

---

### Post by s33k3rgr on 2013-06-14
I solved it with the help from some guy in arch forums.I had to replace root=/dev/sda5 with root=UUID=0e2597fd-b847-4da2-8b58-73fd216ad1f8 on my Grub configuration file manually.

---

