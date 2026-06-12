---
title: "please help me with grub !!!"
date: 2010-02-14
forum: Installation &amp; Upgrades
---

### Post by pirlo89 on 2010-02-14
Hi, i have two internal sata hard drives. one with ubuntu 9.10, on the other one i have installed windows 7. And now my ubuntu wont work. 

i have followed this link >> [http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351) , but when i type ```
find /boot/grub/stage1
```it says : ```
Error 15: File not found

```I have tried many things but none of them worked, please help :(
[I][COLOR=Red]
**Remark : When i booted into the live cd and typed the first command into the terminal it said that i dont have grub, so i installed grub in the live cd session.**[/COLOR][/I]

---

### Post by darkod on 2010-02-14
Boot the live desktop, download the script in my signature, move it on desktop for example and run it in terminal with:
sudo bash ~/Desktop/boot_info_script*.sh

It will create results.txt file with your boot info. Copy the content here and put it inside CODE tags for easier reading. With the text selected hit the # button in the toolbar when writing the post.
After I see the exact situation, I can give exact commands.
Just for information, the ones you tried to use are for grub1 which is used in 9.04 and before, not in 9.10. Lets hope nothing was messed up.

---

### Post by pirlo89 on 2010-02-14
> **darkod said:**
> Boot the live desktop, download the script in my signature, move it on desktop for example and run it in terminal with:
sudo bash ~/Desktop/boot_info_script*.sh

It will create results.txt file with your boot info. Copy the content here and put it inside CODE tags for easier reading. With the text selected hit the # button in the toolbar when writing the post.
After I see the exact situation, I can give exact commands.
Just for information, the ones you tried to use are for grub1 which is used in 9.04 and before, not in 9.10. Lets hope nothing was messed up.


[COLOR=Blue]_** Here are the results**_[/COLOR]

 ```
                    Boot Info Script 0.54 of  February 14th, 2010                         

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #1 for /boot/grub.
 => Windows is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe /grldr

sdb2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x1549f232

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   613,072,529   613,072,467  83 Linux
/dev/sda2         613,072,530   625,137,344    12,064,815   5 Extended
/dev/sda5         613,072,593   625,137,344    12,064,752  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x5918d8e0

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63   299,805,029   299,804,967   7 HPFS/NTFS
/dev/sdb2         299,805,030   312,576,704    12,771,675   5 Extended
/dev/sdb5         299,805,093   312,576,704    12,771,612   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        508e5b53-dab1-4ede-81a2-83d673f16538   ext4                                     
/dev/sda5        f393a9d2-c3b2-4b0a-a72d-2101ae288904   swap                                     
/dev/sdb1        3156ACA426FECA4A                       ntfs                                     
/dev/sdb5        7DF6016A1BDC1D7C                       ntfs                                     

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (rw)
/dev/loop0       /rofs                    squashfs   (rw)
/dev/sda1        /media/508e5b53-dab1-4ede-81a2-83d673f16538 ext4       (rw,nosuid,nodev,uhelper=devkit)


=========================== sda1/boot/grub/grub.cfg: ===========================

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
menuentry "Ubuntu, Linux 2.6.31-19-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    linux    /boot/vmlinuz-2.6.31-19-generic root=/dev/sdb1 ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-19-generic
}
menuentry "Ubuntu, Linux 2.6.31-19-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    linux    /boot/vmlinuz-2.6.31-19-generic root=/dev/sdb1 ro single 
    initrd    /boot/initrd.img-2.6.31-19-generic
}
menuentry "Ubuntu, Linux 2.6.31-17-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    linux    /boot/vmlinuz-2.6.31-17-generic root=/dev/sdb1 ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-17-generic
}
menuentry "Ubuntu, Linux 2.6.31-17-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    linux    /boot/vmlinuz-2.6.31-17-generic root=/dev/sdb1 ro single 
    initrd    /boot/initrd.img-2.6.31-17-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    linux    /boot/vmlinuz-2.6.31-14-generic root=/dev/sdb1 ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    linux    /boot/vmlinuz-2.6.31-14-generic root=/dev/sdb1 ro single 
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
menuentry "Ubuntu, Linux 2.6.31-17-generic (on /dev/sda1)" {
    insmod ext2
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set 0a1e3282-e275-4c1a-acbd-37889da91e9d
    linux /boot/vmlinuz-2.6.31-17-generic root=UUID=0a1e3282-e275-4c1a-acbd-37889da91e9d ro quiet splash
    initrd /boot/initrd.img-2.6.31-17-generic
}
menuentry "Ubuntu, Linux 2.6.31-17-generic (recovery mode) (on /dev/sda1)" {
    insmod ext2
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set 0a1e3282-e275-4c1a-acbd-37889da91e9d
    linux /boot/vmlinuz-2.6.31-17-generic root=UUID=0a1e3282-e275-4c1a-acbd-37889da91e9d ro single
    initrd /boot/initrd.img-2.6.31-17-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (on /dev/sda1)" {
    insmod ext2
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set 0a1e3282-e275-4c1a-acbd-37889da91e9d
    linux /boot/vmlinuz-2.6.31-14-generic root=UUID=0a1e3282-e275-4c1a-acbd-37889da91e9d ro quiet splash
    initrd /boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode) (on /dev/sda1)" {
    insmod ext2
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set 0a1e3282-e275-4c1a-acbd-37889da91e9d
    linux /boot/vmlinuz-2.6.31-14-generic root=UUID=0a1e3282-e275-4c1a-acbd-37889da91e9d ro single
    initrd /boot/initrd.img-2.6.31-14-generic
}
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
proc            /proc           proc    defaults        0       0
# / was on /dev/sda1 during installation
UUID=508e5b53-dab1-4ede-81a2-83d673f16538 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=f393a9d2-c3b2-4b0a-a72d-2101ae288904 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda1: Location of files loaded by Grub: ===================


  40.3GB: boot/grub/core.img
 182.4GB: boot/grub/grub.cfg
    .7GB: boot/initrd.img-2.6.31-14-generic
   2.9GB: boot/initrd.img-2.6.31-17-generic
   3.4GB: boot/initrd.img-2.6.31-19-generic
    .5GB: boot/vmlinuz-2.6.31-14-generic
    .9GB: boot/vmlinuz-2.6.31-17-generic
   2.9GB: boot/vmlinuz-2.6.31-19-generic
   3.4GB: initrd.img
   2.9GB: initrd.img.old
   2.9GB: vmlinuz
    .9GB: vmlinuz.old
=======Devices which don't seem to have a corresponding hard drive==============

sdc sdd sde sdf 
```

---

### Post by pirlo89 on 2010-02-14
***[COLOR=Blue]Good news  :???:[/COLOR]***  [COLOR=Blue]***?***[/COLOR]

---

### Post by SoFl W on 2010-02-14
Grub error 15.  Had it myself.
[https://wiki.ubuntu.com/Grub2#Err15](https://wiki.ubuntu.com/Grub2#Err15)

---

### Post by darkod on 2010-02-14
No wonder it can't boot up, it's looking at the wrong partition. I have no idea how you managed to do this.

First, boot the ubuntu live desktop, open /dev/sdb1 and delete the /grldr file. You don't need it there, that's the windows partition. When I say /dev/sdb1 you will have to find it in Places according to its size, click on it to mount it, and only then you can open it.

Then open /dev/sda1 and in /boot/grub folder move the file grub.cfg into /home/username folder.

Then in terminal execute these commands one by one,exactly as written. You can also post the result here to see it.

sudo -i
mount /dev/sda1 /mnt
mount --bind /proc /mnt/proc
mount --bind /dev /mnt/dev
mount --bind /sys /mnt/sys
chroot /mnt
update-grub
umount /mnt/sys
umount /mnt/dev
umount /mnt/proc
exit

After that close terminal and reboot. If all went well, you should be able to boot both ubuntu and windows.

---

### Post by darkod on 2010-02-14
> **SoFl W said:**
> Grub error 15.  Had it myself.
[https://wiki.ubuntu.com/Grub2#Err15](https://wiki.ubuntu.com/Grub2#Err15)

I believe the error 15 was only reported after the OP searched for /boot/grub/stage1 which is not there because he has grub2. So that's not really the issue here.

---

### Post by pirlo89 on 2010-02-14
woooooooooooooooooooooooooooow :p, im so happy right now.

Thanks guys, i have followed the link that **("**SoFl W**")**[COLOR=Blue][COLOR=Black]have posted. and it worked.

When i restarted the computer, there were some commands running. I read something like "checking for FileSystem errors", then it opened my ubuntu.

Now i have a question to ("[/COLOR][/COLOR]darkod[COLOR=Blue][COLOR=Black]") : you seem like linux guru O:), would you mind if i run that file again at your signature and post the output so you could check if everything went fine ?
[/COLOR][/COLOR]

---

### Post by darkod on 2010-02-14
> **pirlo89 said:**
> woooooooooooooooooooooooooooow :p, im so happy right now.

Thanks guys, i have followed the link that **("**SoFl W**")**[COLOR=Blue][COLOR=Black]have posted. and it worked.

When i restarted the computer, there were some commands running. I read something like "checking for FileSystem errors", then it opened my ubuntu.

Now i have a question to ("[/COLOR][/COLOR]darkod[COLOR=Blue][COLOR=Black]") : you seem like linux guru O:), would you mind if i run that file again at your signature and post the output so you could check if everything went fine ?
[/COLOR][/COLOR]

Those are the same commands I wrote. :) I'm far from a guru, but I'm learning fast. I'm quite new to ubuntu too actually. :)
Yes, you can run it and post it.

---

### Post by pirlo89 on 2010-02-14
There you go...


```
                    Boot Info Script 0.54 of  February 14th, 2010                         

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #1 for /boot/grub.
 => Windows is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe /grldr

sdb2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x1549f232

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   613,072,529   613,072,467  83 Linux
/dev/sda2         613,072,530   625,137,344    12,064,815   5 Extended
/dev/sda5         613,072,593   625,137,344    12,064,752  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x5918d8e0

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63   299,805,029   299,804,967   7 HPFS/NTFS
/dev/sdb2         299,805,030   312,576,704    12,771,675   5 Extended
/dev/sdb5         299,805,093   312,576,704    12,771,612   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        508e5b53-dab1-4ede-81a2-83d673f16538   ext4                                     
/dev/sda5        f393a9d2-c3b2-4b0a-a72d-2101ae288904   swap                                     
/dev/sdb1        3156ACA426FECA4A                       ntfs                                     
/dev/sdb5        7DF6016A1BDC1D7C                       ntfs                                     

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda1        /                        ext4       (rw,errors=remount-ro)


=========================== sda1/boot/grub/grub.cfg: ===========================

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
set root=(hd0,1)
search --no-floppy --fs-uuid --set 508e5b53-dab1-4ede-81a2-83d673f16538
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
menuentry "Ubuntu, Linux 2.6.31-19-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set 508e5b53-dab1-4ede-81a2-83d673f16538
    linux    /boot/vmlinuz-2.6.31-19-generic root=UUID=508e5b53-dab1-4ede-81a2-83d673f16538 ro   dpkg-reconfigure grub-pc
    initrd    /boot/initrd.img-2.6.31-19-generic
}
menuentry "Ubuntu, Linux 2.6.31-19-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set 508e5b53-dab1-4ede-81a2-83d673f16538
    linux    /boot/vmlinuz-2.6.31-19-generic root=UUID=508e5b53-dab1-4ede-81a2-83d673f16538 ro single 
    initrd    /boot/initrd.img-2.6.31-19-generic
}
menuentry "Ubuntu, Linux 2.6.31-17-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set 508e5b53-dab1-4ede-81a2-83d673f16538
    linux    /boot/vmlinuz-2.6.31-17-generic root=UUID=508e5b53-dab1-4ede-81a2-83d673f16538 ro   dpkg-reconfigure grub-pc
    initrd    /boot/initrd.img-2.6.31-17-generic
}
menuentry "Ubuntu, Linux 2.6.31-17-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set 508e5b53-dab1-4ede-81a2-83d673f16538
    linux    /boot/vmlinuz-2.6.31-17-generic root=UUID=508e5b53-dab1-4ede-81a2-83d673f16538 ro single 
    initrd    /boot/initrd.img-2.6.31-17-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set 508e5b53-dab1-4ede-81a2-83d673f16538
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=508e5b53-dab1-4ede-81a2-83d673f16538 ro   dpkg-reconfigure grub-pc
    initrd    /boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set 508e5b53-dab1-4ede-81a2-83d673f16538
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=508e5b53-dab1-4ede-81a2-83d673f16538 ro single 
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
    chainloader +1
}
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
proc            /proc           proc    defaults        0       0
# / was on /dev/sda1 during installation
UUID=508e5b53-dab1-4ede-81a2-83d673f16538 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=f393a9d2-c3b2-4b0a-a72d-2101ae288904 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda1: Location of files loaded by Grub: ===================


   1.9GB: boot/grub/core.img
   1.9GB: boot/grub/grub.cfg
    .7GB: boot/initrd.img-2.6.31-14-generic
   2.9GB: boot/initrd.img-2.6.31-17-generic
   3.4GB: boot/initrd.img-2.6.31-19-generic
    .5GB: boot/vmlinuz-2.6.31-14-generic
    .9GB: boot/vmlinuz-2.6.31-17-generic
   2.9GB: boot/vmlinuz-2.6.31-19-generic
   3.4GB: initrd.img
   2.9GB: initrd.img.old
   2.9GB: vmlinuz
    .9GB: vmlinuz.old
=======Devices which don't seem to have a corresponding hard drive==============

sdc sdd sde sdf 
```

---

### Post by darkod on 2010-02-14
Looking fine. :) Enjoy it now.

---

### Post by pirlo89 on 2010-02-14
> **darkod said:**
> Looking fine. :) Enjoy it now.

Thank you, i will ;).

---

