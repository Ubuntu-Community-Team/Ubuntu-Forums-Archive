---
title: "Ubuntu don't boot"
date: 2011-03-06
forum: Installation &amp; Upgrades
---

### Post by Azyx on 2011-03-06
Have installed Ubuntu 10.04LTS on a SATA disk, but when BIOS are finnish and it should boot, the computer reboot. No information appeare on the screen.
I have made an upgrade of new kernel, and i suspect then It could be a problem with grub2.
I can boot from live-cd and I wonder how I can find out whats wrong?

If I look in GParted the /-partition are boot-flaged for the boot-disk.

But how do I find grub2 things?

One problem with the system are that my hdd get different name (sda, sdb, sdc, sdd and sde). Can grub trie to read on another drive (if my boot-disk sometimes are sda and another time sdd? 
3 of my disk are un partionated and used by fuse-zfs.

---

### Post by grahammechanical on 2011-03-06
I get the feeling that you are not telling us everythng.

sda = sata disc a. sdb = sata disc b etc.

Which drive have you installed Ubuntu on? Which drive have you allowed the installation to put Grub2 on? Are you booting from the drive with Grub2 on? Are you selecting the drive to boot from by changing the BIOS settings? Or some other way? Are you removing and replacing drives?

Grub will not load if it is not on the drive that you are booting from.

Another thing. If you want to install any kind of Microsoft operating system, then that is your choice. but if you want it to dual boot with Linux, then you should install Windows first and then Ubuntu. Linux distributions are designed to be friendly with an installed Windows OS. Microsoft does not design its operating systems to be friendly with any other operating systems.

Regards.

---

### Post by oldfred on 2011-03-06
Usually drives do not change, but if external they may. Or sometimes mulicard readers get promoted or IDE drives get promoted to sda. Ubuntu boots and mounts partitions by UUID, so drive order is not vital.

Post this to see your configuration.
Boot Info Script courtesy of forum members meierfra & Gert Hulselmans
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the post's menu and then paste the contents between the generated [ code] paste here [ /code] tags.

---

### Post by Azyx on 2011-03-07
> **grahammechanical said:**
> I get the feeling that you are not telling us everythng.
 
sda = sata disc a. sdb = sata disc b etc.
 
Which drive have you installed Ubuntu on? Which drive have you allowed the installation to put Grub2 on? Are you booting from the drive with Grub2 on? Are you selecting the drive to boot from by changing the BIOS settings? Or some other way? Are you removing and replacing drives?
 
I have installed it on a hdd with 3 partitions linux-swap, /, /home
sdxa= 2 GB linux swap 
sdxb=10GB ext4 root
sdxc=50GB ext4 /home/
 
sdx are sda or sde. grub should also be on the boot drive, but I dont know where on it. When I installed Ubuntu I only have one hdd.
 
> **grahammechanical said:**
> 
Grub will not load if it is not on the drive that you are booting from.
 
Another thing. If you want to install any kind of Microsoft operating system, then that is your choice. but if you want it to dual boot with Linux, then you should install Windows first and then Ubuntu. Linux distributions are designed to be friendly with an installed Windows OS. Microsoft does not design its operating systems to be friendly with any other operating systems.
 
Regards.
 
So you can not boot to another hdd, than there grub2 are installed? as I remember from grub, that was possible, by calling the different hdd something. Anyway, grub can see other hdd and partitions in the machine and gave them a name. Don't remember what it's called

---

### Post by Azyx on 2011-03-07
> **oldfred said:**
> Usually drives do not change, but if external they may. Or sometimes mulicard readers get promoted or IDE drives get promoted to sda. Ubuntu boots and mounts partitions by UUID, so drive order is not vital.
 
Post this to see your configuration.
Boot Info Script courtesy of forum members meierfra & Gert Hulselmans
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the post's menu and then paste the contents between the generated [ code] paste here [ /code] tags.
 
I have 3 IDE-hdd 300GB unformatted and unpartitionated by Ubuntu, but I have made a zfs, raidz with fuse-zfs. I Think it's why the disk-naming are different from different boot. (That disk who start first, get the lowerst number. 
 
What I suspect may bee the problem is that even grub2 are referred to wrong physical disk, in 'normal' grub they where called hd0,0,(first disk, first partition) hd1,0 (second disk, and frist partition) and so on, but if the system change the who is hd0, then it's refere to wrong disk. But I think maybe the script you link to may help. Will check when i coming home. 
 
I have also i BIOS used my systemdisk to the second, and even the third boot device...
 
/Cheers

---

### Post by Azyx on 2011-03-07
Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => No boot loader is installed in the MBR of /dev/sda
 => Grub 2 is installed in the MBR of /dev/sdd and looks on the same drive in 
    partition #2 for /boot/grub.

sdd1: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdd2: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.2 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdd3: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdb: _________________________________________________________________________

    File system:       zfs
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type 'zfs'

sdc: _________________________________________________________________________

    File system:       zfs
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type 'zfs'
mount: unknown filesystem type 'zfs'

sde: _________________________________________________________________________

    File system:       zfs
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type 'zfs'
mount: unknown filesystem type 'zfs'
mount: unknown filesystem type 'zfs'

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 300.1 GB, 300069052416 bytes
255 heads, 63 sectors/track, 36481 cylinders, total 586072368 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System



Drive: sdd ___________________ _____________________________________________________

Disk /dev/sdd: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdd1                  63     4,192,964     4,192,902  82 Linux swap / Solaris
/dev/sdd2    *      4,192,965    24,675,839    20,482,875  83 Linux
/dev/sdd3          24,675,840   229,472,459   204,796,620  83 Linux


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda                                                zfs                                      
/dev/sdb                                                zfs                                      
/dev/sdc                                                zfs                                      
/dev/sdd1        dfdd51a7-ad93-49a6-94b3-e9a0bec909f5   swap                                     
/dev/sdd2        da4da2ef-85e4-4ae8-929f-e74c56420647   ext4                                     
/dev/sdd3        7a89f6cb-3af4-424f-ad2f-d715e86d723e   ext4                                     
/dev/sdd                                                zfs                                      
/dev/sde                                                zfs                                      

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sdd2        /media/da4da2ef-85e4-4ae8-929f-e74c56420647 ext4       (rw,nosuid,nodev,uhelper=udisks)


=========================== sdd2/boot/grub/grub.cfg: ===========================

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
set root='(hd3,2)'
search --no-floppy --fs-uuid --set da4da2ef-85e4-4ae8-929f-e74c56420647
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
set root='(hd3,2)'
search --no-floppy --fs-uuid --set da4da2ef-85e4-4ae8-929f-e74c56420647
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
menuentry 'Ubuntu, with Linux 2.6.32-29-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd3,2)'
    search --no-floppy --fs-uuid --set da4da2ef-85e4-4ae8-929f-e74c56420647
    linux    /boot/vmlinuz-2.6.32-29-generic root=UUID=da4da2ef-85e4-4ae8-929f-e74c56420647 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-29-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-29-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd3,2)'
    search --no-floppy --fs-uuid --set da4da2ef-85e4-4ae8-929f-e74c56420647
    echo    'Loading Linux 2.6.32-29-generic ...'
    linux    /boot/vmlinuz-2.6.32-29-generic root=UUID=da4da2ef-85e4-4ae8-929f-e74c56420647 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-29-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-28-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd3,2)'
    search --no-floppy --fs-uuid --set da4da2ef-85e4-4ae8-929f-e74c56420647
    linux    /boot/vmlinuz-2.6.32-28-generic root=UUID=da4da2ef-85e4-4ae8-929f-e74c56420647 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-28-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-28-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd3,2)'
    search --no-floppy --fs-uuid --set da4da2ef-85e4-4ae8-929f-e74c56420647
    echo    'Loading Linux 2.6.32-28-generic ...'
    linux    /boot/vmlinuz-2.6.32-28-generic root=UUID=da4da2ef-85e4-4ae8-929f-e74c56420647 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-28-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-24-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd3,2)'
    search --no-floppy --fs-uuid --set da4da2ef-85e4-4ae8-929f-e74c56420647
    linux    /boot/vmlinuz-2.6.32-24-generic root=UUID=da4da2ef-85e4-4ae8-929f-e74c56420647 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-24-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd3,2)'
    search --no-floppy --fs-uuid --set da4da2ef-85e4-4ae8-929f-e74c56420647
    echo    'Loading Linux 2.6.32-24-generic ...'
    linux    /boot/vmlinuz-2.6.32-24-generic root=UUID=da4da2ef-85e4-4ae8-929f-e74c56420647 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-24-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd3,2)'
    search --no-floppy --fs-uuid --set da4da2ef-85e4-4ae8-929f-e74c56420647
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd3,2)'
    search --no-floppy --fs-uuid --set da4da2ef-85e4-4ae8-929f-e74c56420647
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

=============================== sdd2/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda2 during installation
UUID=da4da2ef-85e4-4ae8-929f-e74c56420647 /               ext4    errors=remount-ro 0       1
# /home was on /dev/sda3 during installation
UUID=7a89f6cb-3af4-424f-ad2f-d715e86d723e /home           ext4    defaults        0       2
# swap was on /dev/sda1 during installation
UUID=aa12af7e-def6-4cd6-b84a-005a091f205b none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sdd2: Location of files loaded by Grub: ===================


   4.4GB: boot/grub/core.img
   4.8GB: boot/grub/grub.cfg
   5.5GB: boot/initrd.img-2.6.32-24-generic
   5.6GB: boot/initrd.img-2.6.32-28-generic
   3.6GB: boot/initrd.img-2.6.32-29-generic
   5.4GB: boot/vmlinuz-2.6.32-24-generic
   5.4GB: boot/vmlinuz-2.6.32-28-generic
   5.5GB: boot/vmlinuz-2.6.32-29-generic
   3.6GB: initrd.img
   5.6GB: initrd.img.old
   5.5GB: vmlinuz
   5.4GB: vmlinuz.old

> **oldfred said:**
> Usually drives do not change, but if external they may. Or sometimes mulicard readers get promoted or IDE drives get promoted to sda. Ubuntu boots and mounts partitions by UUID, so drive order is not vital.

Post this to see your configuration.
Boot Info Script courtesy of forum members meierfra & Gert Hulselmans
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the post's menu and then paste the contents between the generated [ code] paste here [ /code] tags.

---

### Post by oldfred on 2011-03-07
If this was the only issue I would think it would just give a mounting error and let you proceed. Bootscript could not see any partitions on sda, and it looks like your install was to sda, but now drive is sdd.

From fstab:
# swap was on /dev/sda1 during installation
UUID=[COLOR=Red]aa12af7e-def6-4cd6-b84a-005a091f205b[/COLOR] none            swap    sw              0       0
From blkid
/dev/sdd1        [COLOR=Red]dfdd51a7-ad93-49a6-94b3-e9a0bec909f5[/COLOR]   swap

Since you only have one system, can you hold down shift key from BIOS until menu appears? If need be you can edit the grub line and try different drive numbers hd0, hd1, hd2, hd3  and sda, sdb, sdc etc but it should be booting with the search for UUID.
But perhaps it is like the boot script and does not parse the zfs partitions and fails? I do not think grub2 supports zfs.

---

### Post by Azyx on 2011-03-08
> **oldfred said:**
> 
Since you only have one system, can you hold down shift key from BIOS until menu appears? If need be you can edit the grub line and try different drive numbers hd0, hd1, hd2, hd3  and sda, sdb, sdc etc but it should be booting with the search for UUID.
But perhaps it is like the boot script and does not parse the zfs partitions and fails? I do not think grub2 supports zfs.

No, nothing happen when I press shift during boot. Just restart as before.

/Cheers

---

### Post by oldfred on 2011-03-08
Is there some reason you are running zfs. I thought is was Solaris.

Or are you testing this?
[http://www.phoronix.com/scan.php?page=article&item=kq_zfs_gold&num=1](http://www.phoronix.com/scan.php?page=article&item=kq_zfs_gold&num=1)

---

### Post by Azyx on 2011-03-08
> **oldfred said:**
> Is there some reason you are running zfs. I thought is was Solaris.

Or are you testing this?
[http://www.phoronix.com/scan.php?page=article&item=kq_zfs_gold&num=1](http://www.phoronix.com/scan.php?page=article&item=kq_zfs_gold&num=1)


It is Solaris yes, but Solaris don't run on my hardware and freebsd are mostly kde, and also have an older verson of zfs, than zfs-fuse or it's maybee fuse-zfs? 
I want a secure storage, and zfs seems to be good.

I have not have time to test so much, cos work and other stuff. 
And now this problem with no boot appeared...

---

