---
title: "Keep getting error 17 when installing from live disk"
date: 2010-02-22
forum: Installation &amp; Upgrades
---

### Post by elite0083 on 2010-02-22
I recently had an Ubuntu 9.10 disk sent to me so that i could install it, when i am installing it it does all the steps properly and then asks if i want to restart, but when i do all i get is Grub loading Error 17.

---

### Post by presence1960 on 2010-02-22
Let's get a better look at your setup & boot process. Boot the Ubuntu Live CD/USB. Choose "try ubuntu without any changes", when the desktop loads come back here and do the following:

1. Download the boot info script. There is a link in my signature.
2. Once downloaded move the boot info script to the desktop.
3. Open a terminal and run the command ```
sudo bash ~/Desktop/boot_info_script*.sh
```

  This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text. 

See [here]("http://bootinfoscript.sourceforge.net/") for more info on the boot info script.

Above link is to meierfra's Sourceforge web page.

---

### Post by elite0083 on 2010-02-24
Ok I followed your instructions and this is what it gave me. hopefully you can figure something out.

                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks for 
    (UUID=d7c6285e-a46e-41e7-aad9-1d6c7bcb1960)/boot/grub.
 => Windows is installed in the MBR of /dev/sdb
 => Grub 0.97 is installed in the MBR of /dev/sdh and looks on the same drive 
    in partition #2 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot/BCD /grldr

sdh1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdh2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdh5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xddaff46c

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   625,137,344   625,137,282   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x28ba76b1

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63   625,137,344   625,137,282   7 HPFS/NTFS


Drive: sdh ___________________ _____________________________________________________

Disk /dev/sdh: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x799b4238

Partition  Boot         Start           End          Size  Id System

/dev/sdh1                  63   957,104,504   957,104,442  83 Linux
/dev/sdh2         957,104,505   976,768,064    19,663,560   5 Extended
/dev/sdh5         957,104,568   976,768,064    19,663,497  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        3EB10BD21BC7B47F                       ntfs                                     
/dev/sdb1        6B76BB13309965EA                       ntfs                                     
/dev/sdh1        d7c6285e-a46e-41e7-aad9-1d6c7bcb1960   ext4                                     
/dev/sdh5        626bff8e-de37-45f7-a4b2-99bf7d5d7050   swap                                     

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr1         /cdrom                   iso9660    (rw)
/dev/loop0       /rofs                    squashfs   (rw)
/dev/sr0         /media/Devil May Cry 4   udf        (ro,nosuid,nodev,uhelper=devkit,uid=999,gid=999,iocharset=utf8,umask=0077)
/dev/sdh1        /media/d7c6285e-a46e-41e7-aad9-1d6c7bcb1960 ext4       (rw,nosuid,nodev,uhelper=devkit)


=========================== sdh1/boot/grub/grub.cfg: ===========================

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
search --no-floppy --fs-uuid --set d7c6285e-a46e-41e7-aad9-1d6c7bcb1960
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
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/white
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry "Ubuntu, Linux 2.6.31-14-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd2,1)
    search --no-floppy --fs-uuid --set d7c6285e-a46e-41e7-aad9-1d6c7bcb1960
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=d7c6285e-a46e-41e7-aad9-1d6c7bcb1960 ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd2,1)
    search --no-floppy --fs-uuid --set d7c6285e-a46e-41e7-aad9-1d6c7bcb1960
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=d7c6285e-a46e-41e7-aad9-1d6c7bcb1960 ro single 
    initrd    /boot/initrd.img-2.6.31-14-generic
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
menuentry "Windows 7 (loader) (on /dev/sdb1)" {
    insmod ntfs
    set root=(hd1,1)
    search --no-floppy --fs-uuid --set 6b76bb13309965ea
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sdh1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sdg1 during installation
UUID=d7c6285e-a46e-41e7-aad9-1d6c7bcb1960 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdg5 during installation
UUID=626bff8e-de37-45f7-a4b2-99bf7d5d7050 none            swap    sw              0       0
/dev/scd1       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/scd0       /media/cdrom1   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sdh1: Location of files loaded by Grub: ===================


    .8GB: boot/grub/core.img
    .8GB: boot/grub/grub.cfg
    .8GB: boot/initrd.img-2.6.31-14-generic
    .6GB: boot/vmlinuz-2.6.31-14-generic
    .8GB: initrd.img
    .6GB: vmlinuz
=======Devices which don't seem to have a corresponding hard drive==============

sdc sdd sde sdf

---

### Post by darkod on 2010-02-24
Very strange, your disks are named sda, sdb and sdh. Usually it will have sdc, sdd, etc until it gets to sdh. Did you have some usb drives or similar plugged in previously?

Anyway, boot the live desktop and install grub2 to the MBR of /dev/sdh where your ubuntu is.

sudo mount /dev/sdh1 /mnt
sudo grub-install --root-directory=/mnt/ /dev/sdh

In BIOS set the 500GB as first hdd option to boot from. It should work OK after that.

Also your win7 boot files are split, I don't think you can boot win7 like that.

---

### Post by elite0083 on 2010-02-24
I have two internals and one external I am trying to save it to my external and you can have two win7 because mine works fine, I tried what you told me and have been getting this error message.

ubuntu@ubuntu:~$ sudo mount /dev/sdh1 /mnt
mount: special device /dev/sdh1 does not exist
ubuntu@ubuntu:~$ sudo grub-install --root-directory=/mnt/ /dev/sdh
grub-probe: error: cannot find a device for /mnt//boot/grub.

thanks in advanced 
:confused: still confused,
elite

---

### Post by darkod on 2010-02-24
Like I said, the disk shouldn't really be /dev/sdh. It seems it figured that out and changed the name. :)
Boot the live desktop and post the result of

sudo fdisk -l

and wait a bit, I'll post you back commands as soon as I see the current situation. You can run them right away from the live desktop.

PS. If the 500GB is external it needs to be plugged in of course.

---

### Post by elite0083 on 2010-02-25
the external is plugged in, this time when i ran it though it said it was g for some reason. I followed your instructions and this is what it gave me.

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xddaff46c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       38913   312568641    7  HPFS/NTFS

Disk /dev/sdb: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x28ba76b1

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       38913   312568641    7  HPFS/NTFS

Disk /dev/sdg: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x799b4238

   Device Boot      Start         End      Blocks   Id  System
/dev/sdg1               1       59577   478552221   83  Linux
/dev/sdg2           59578       60801     9831780    5  Extended
/dev/sdg5           59578       60801     9831748+  82  Linux swap / Sol

---

### Post by darkod on 2010-02-25
In that case the commands would be:

sudo mount /dev/sdg1 /mnt
sudo grub-install --root-directory=/mnt/ /dev/sdg

You first mount the Linux parttion, in this case /dev/sdg1 and then you install grub2 on the MBR of the same drive, /dev/sdg (no number, just /dev/sdg).

If the next time you try it uses different letter again, just adjust the commands for that moment.

And I think you are getting error 17 because you are booting wrong grub. You also have grub2 on the MBR of /dev/sda which it seems is no longer connected to existing ubuntu partition. It just remained there. Because you have windows on both sda and sdb, just reinstall generic mbr on /dev/sda with:

sudo apt-get install lilo
sudo lilo -M /dev/sda mbr

Ignore the warnings it will show. That will write generic mbr on /dev/sda.

---

### Post by elite0083 on 2010-02-25
The first thing you told me to do still isn't working even though I am telling it sdc its still trying to go to g this is the error message I am getting.

ubuntu@ubuntu:~$ sudo grub-install --root-directory=/mnt/ /dev/sdc
error: cannot open `/dev/sdg' while attempting to get disk size
error: cannot open `/dev/sdg' while attempting to get disk size
grub-probe: error: Cannot find a GRUB drive for /dev/sdc1.  Check your device.map.

Auto-detection of a filesystem module failed.
Please specify the module with the option `--modules' explicitly.

the second one worked however

---

### Post by darkod on 2010-02-25
If the device.map is wrong you can create a current one with:

sudo grub-mkdevicemap

---

### Post by elite0083 on 2010-02-26
i tried the command that you gave me, but it still isn't working the first time I did it i just put it exactly like you had it, but then i figured i would have to specify so I put /sdg at the end so it knew what drive to run off of. Every time i try to run it from the external and it doesn't work i press ctrl alt del to restart it and it restarts, but the only problem is it freezes on the bios screen what could be the problem there?

---

### Post by darkod on 2010-02-26
> **elite0083 said:**
> i tried the command that you gave me, but it still isn't working and i added /sdg at the end should i just try to reinstall or something?

It should work. Because the letter seems to change, you need to boot into live desktop, and run:

sudo fdisk -l

that will show you the name of the 500GB disk as you already saw. Do not reboot or anything, just continue with those two commands using the correct letter for that moment:

sudo mount /dev/sdX1 /mnt
sudo grub-install --root-directory=/mnt/ /dev/sdX

You can try reinstalling if you want but there is no reason for that. And during the reinstall you will also have to watch out and put grub2 on the ext hdd MBR, in the last screen before clicking Install you need to click on Advanced and tell it to install on the ext hdd disk. The name of the ext hdd disk can be seen in step 4 of the installer, when it asks you where to install.

---

### Post by elite0083 on 2010-02-27
Ok I did everything exactly the same, but for some reason this time it worked I am now using Ubuntu thank you how do I mark this thread as solved?

---

### Post by darkod on 2010-02-27
> **elite0083 said:**
> Ok I did everything exactly the same, but for some reason this time it worked I am now using Ubuntu thank you how do I mark this thread as solved?

Excellent, enjoy it now. You can mark it as solved in Thread Tools, above the first post on any page of the thread.

---

### Post by elite0083 on 2010-02-28
OK I spoke to soon it only worked the one time and after that it keeps saying that it can't read ext4 so i don't know what to do it makes it to where the white ubuntu thing comes up and then it keeps saying error can't read ext4

---

### Post by duleep on 2010-07-05
i had the same type of problem in grub 2 re-installation 
> 
[B]root@ubuntu:~# mount /dev/sda7 /mnt
root@ubuntu:~# mount --bind /dev /mnt/dev
root@ubuntu:~# mount --bind /proc /mnt/proc
root@ubuntu:~# grub-install /dev/sda
/usr/sbin/grub-probe: error: cannot find a device for /boot/grub (is /dev mounted?).
No path or device is specified.
Try `/usr/sbin/grub-probe --help' for more information.
Auto-detection of a filesystem module failed.
Please specify the module with the option `--modules' explicitly.
[/B]so i don't know what to do next plz help

---

