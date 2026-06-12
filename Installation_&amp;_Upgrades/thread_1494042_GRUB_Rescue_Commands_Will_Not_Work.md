---
title: "GRUB Rescue Commands Will Not Work"
date: 2010-05-26
forum: Installation &amp; Upgrades
---

### Post by SpikeLS6 on 2010-05-26
I too have the  "GRUB_puts_" file missing error on the 9.10 to 10.04 LTS Upgrade.

I run a dual boot with WIN 7 on SDA1 and Ubuntu on SDA2. My screen boots up to a GRUB Rescue screen, but none of the commands for the GRUB 2 enhancement do anything. I ran the ls
      set prefix=
      set root=
      ls /boot
but it will not recognize the "insmod" command.

I also tried to boot a specific kernel manually, but it never finds the file I input.

I booted from an old 9.04 CD and did:
sudo fdisk -l
sudo mkdir /media/sdb1
sudo mount /dev/sdb1 /media/sdb1
then tried to install grub with:
sudo grub-install --root-directory=/media/sdb1 /dev/sdb1
    as per the Forums thread #1014708. That did nothing either.

What can I try next?

Thank you.

Spike

---

### Post by darkod on 2010-05-26
The 9.04 cd has grub1 on it, and you can't use it to reinstall grub2.

On the other hand, if you upgraded from 9.04 to 9.10 too, without upgrading grub separately, you might be still using grub1. But grub1 is restored with different commands anyway.

---

### Post by SpikeLS6 on 2010-05-26
Are the original Grub commands in the HELP; Get Help with Ubuntu Directory?

Spike

---

### Post by oldfred on 2010-05-26
grub puts error - reinstall grub worked
Different drive
[http://ubuntuforums.org/showthread.php?t=1467514](http://ubuntuforums.org/showthread.php?t=1467514)
Chroot & install grub2
[http://www.webupd8.org/2010/05/fix-symbol-grubputs-not-found-when.html](http://www.webupd8.org/2010/05/fix-symbol-grubputs-not-found-when.html)

---

### Post by SpikeLS6 on 2010-05-26
Thanks OldFred. I already tried the first thread you mentioned. I had upgraded to the 64-bit kernel in 9.10, but apparently did not upgrade the Grub to the newer 1.97, because those commands will not work.

I'll try working with the WebUpd8 article next and see what happens.

Thank you.

Spike

---

### Post by SpikeLS6 on 2010-05-26
I went through all the Terminal commands from the WebUpd8 link you provided. It tells me I already have the most current Grub installed. After rebooting, I still come to the same "Grub_puts_" with flashing cursor as before. My grub.cfg file does show the new Upgrade to the 2.3.32-22-generic-pae version, and also has the WIN 7 line at the bottom of the list. I just can not figure out how to get to one of those to start Ubuntu from the Sdb1 drive where Linux resides.

Anything else I might try?

Thank you.

Spike

---

### Post by oldfred on 2010-05-26
Are you booting the drive grub installed to?

Lets see where everything is at:

Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Be sure to highlight and use code tags (# in edit panel) to make it easier to read when you post the results.txt.

---

### Post by SpikeLS6 on 2010-05-27
I tried the sudo bash boot_info_script055.sh file in the beginning of the Boot Script I download from Sourceforge.net, but I get "No such file or directory" as a result. I tried a cd to get into my /Michael folder on the sdb1 drive, but it will not let me out of the Live CD area.

What command on the Boot Script do I need to input?

Spike

---

### Post by darkod on 2010-05-27
It depends where the script is located after download. It might be on the desktop, or in the Downloads folder (in Places). To avoid confusion I always recommend to move it to the desktop regardless where it downloaded. Then you can run it with:

sudo bash ~/Desktop/boot_info_script*.sh

If it's in Downloads just replace Desktop with Downloads, it's up to you. Be careful, linux is case sensitive, type exactly. Desktop is not the same as desktop.

---

### Post by SpikeLS6 on 2010-05-27
Uh, oh. I downloaded it onto my Desktop PC. I have problems getting the Wireless to work with the CD. I guess I best work on getting Wi-Fi to work before I go any further. Stand-by, please.

Spike

---

### Post by SpikeLS6 on 2010-05-27
This is the Results.txt that came up from running the script: I am not sure how the # in Edit mode work; what do you mean?

                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks for 
    (UUID=294a6cee-7977-4187-b5e2-c083bac672a9)/boot/grub.
 => Grub 2 is installed in the MBR of /dev/sdb and looks on the same drive in 
    partition #1 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot/BCD

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe

sdb1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  Grub
    Boot sector info:  Grub 0.97 is installed in the boot sector of sdb1 and 
                       looks at sector 78399 of the same hard drive for the 
                       stage2 file. A stage2 file is at this location on 
                       /dev/sdb. Stage2 looks on partition #1 for 
                       /boot/grub/menu.lst.
    Operating System:  Ubuntu 10.04 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x018b0c8f

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048       206,847       204,800   7 HPFS/NTFS
/dev/sda2             206,848   488,394,751   488,187,904   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xc6c7c6c7

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63   964,687,184   964,687,122  83 Linux
/dev/sdb2         964,687,185   976,768,064    12,080,880   5 Extended
/dev/sdb5         964,687,248   976,768,064    12,080,817  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        788C95AA8C956402                       ntfs       System Reserved               
/dev/sda2        F84C98E84C98A2C4                       ntfs                                     
/dev/sdb1        294a6cee-7977-4187-b5e2-c083bac672a9   ext4                                     
/dev/sdb5        3c92c42f-2c7a-408b-b9e2-1cff55201f50   swap                                     

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

rootfs           /                        rootfs     (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)


=========================== sdb1/boot/grub/grub.cfg: ===========================

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
set root='(hd1,1)'
search --no-floppy --fs-uuid --set 294a6cee-7977-4187-b5e2-c083bac672a9
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
set root='(hd1,1)'
search --no-floppy --fs-uuid --set 294a6cee-7977-4187-b5e2-c083bac672a9
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
menuentry 'Ubuntu, with Linux 2.6.32-22-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set 294a6cee-7977-4187-b5e2-c083bac672a9
    linux    /boot/vmlinuz-2.6.32-22-generic-pae root=UUID=294a6cee-7977-4187-b5e2-c083bac672a9 ro  splash  quiet splash
    initrd    /boot/initrd.img-2.6.32-22-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.32-22-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set 294a6cee-7977-4187-b5e2-c083bac672a9
    echo    'Loading Linux 2.6.32-22-generic-pae ...'
    linux    /boot/vmlinuz-2.6.32-22-generic-pae root=UUID=294a6cee-7977-4187-b5e2-c083bac672a9 ro single  splash
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-22-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.31-21-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set 294a6cee-7977-4187-b5e2-c083bac672a9
    linux    /boot/vmlinuz-2.6.31-21-generic-pae root=UUID=294a6cee-7977-4187-b5e2-c083bac672a9 ro  splash  quiet splash
    initrd    /boot/initrd.img-2.6.31-21-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.31-21-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set 294a6cee-7977-4187-b5e2-c083bac672a9
    echo    'Loading Linux 2.6.31-21-generic-pae ...'
    linux    /boot/vmlinuz-2.6.31-21-generic-pae root=UUID=294a6cee-7977-4187-b5e2-c083bac672a9 ro single  splash
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.31-21-generic-pae
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set 294a6cee-7977-4187-b5e2-c083bac672a9
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set 294a6cee-7977-4187-b5e2-c083bac672a9
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" {
    insmod ntfs
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 788c95aa8c956402
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sdb1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sdb1 during installation
UUID=294a6cee-7977-4187-b5e2-c083bac672a9 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdb5 during installation
UUID=3c92c42f-2c7a-408b-b9e2-1cff55201f50 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sdb1: Location of files loaded by Grub: ===================


    .0GB: boot/grub/core.img
    .0GB: boot/grub/grub.cfg
    .0GB: boot/grub/stage2
   4.3GB: boot/initrd.img-2.6.31-21-generic-pae
   4.3GB: boot/initrd.img-2.6.32-22-generic-pae
   2.0GB: boot/vmlinuz-2.6.31-21-generic-pae
   3.6GB: boot/vmlinuz-2.6.32-22-generic-pae
   4.3GB: initrd.img
   4.3GB: initrd.img.old
   3.6GB: vmlinuz
   2.0GB: vmlinuz.old

---

### Post by darkod on 2010-05-27
There is nothing wrong I can see. :( You have some grub1 installed on the /dev/sdb1 partition, but it shouldn't interfere with grub2 from the MBR. And you do have grub2 on MBR of both disks.
It's better to boot from the 500GB as first option in BIOS. But it should work either way.

Another thing I noticed is that you are actually running the -generic-pae kernels, not -generic.

I am not familiar with that and have no idea whether this could be a reason for this error.

---

### Post by kansasnoob on 2010-05-27
**If you have internet with the Live CD** (any Ubuntu Live CD, version doesn't matter) try this (please copy-n-paste commands):

Note: I really need to see the full terminal output so please copy-n-paste it back here :)

```
sudo mount /dev/sdb1 /mnt && sudo mount --bind /dev /mnt/dev && sudo mount --bind /proc /mnt/proc && sudo mount --bind /sys /mnt/sys && sudo mount --bind /dev/pts /mnt/dev/pts && sudo cp /etc/resolv.conf /mnt/etc/resolv.conf && sudo chroot /mnt
```

```
dpkg-divert --local --rename --add /sbin/initctl
```

```
ln -s /bin/true /sbin/initctl
```

```
grub-install -v && aptitude show grub|head -2 && aptitude show grub-pc|head -2 && aptitude show grub-common|head -2 && aptitude show os-prober|head -2
```

```
apt-get update
```

```
apt-get install --reinstall grub-pc
```

```
grub-mkconfig -o /boot/grub/grub.cfg
```

```
grub-install /dev/sda
```

```
grub-install /dev/sdb
```

Note: if either of those last two "grub-install" commands produces errors then also run:

```
grub-install --recheck /dev/sdX
```

Of course you must replace the X with the proper drive designation letter.

Then please copy-n-paste the full terminal output back here, and next exit the chroot and unmount:

```
exit
```

```
sudo umount /mnt/dev/pts && sudo umount /mnt/sys && sudo umount /mnt/proc && sudo umount /mnt/dev && sudo umount /mnt
```

---

### Post by mr clark25 on 2010-05-27
i would chroot into the system from a live cd and then run grub-update. you can do this with:

```

sudo bash
mkdir -p /mnt/temp/boot
mount /dev/sda5 /mnt/temp/
mount -o bind /proc /mnt/temp/proc
mount -o bind /dev /mnt/temp/dev
mount -o bind /dev/pts /mnt/temp/dev/pts
mount -o bind /sys /mnt/temp/sys
chroot /mnt/temp
grub-install --recheck /dev/sda
update-grub
exit

```replace "sda5" with your partition that you have ubuntu installed on. the last 3 commands will reinstall grub on "sda". if these produce any error codes, please post them here.

EDIT: sorry kansasnoob. i didnt see that you had already posted. it took me a while to dig up the commands. looks like you beat me to it ;)__[URL="http://ubuntuforums.org/member.php?u=554595"]
[/URL]

---

### Post by SpikeLS6 on 2010-05-27
Kansasnoob, what Terminal Output from what Command do you need?

Spike

---

### Post by SpikeLS6 on 2010-05-27
By the way, the -pae is the 64-bit kernel for the 32-bit application. It allows me to take advantage of the whole 4 Gig of RAM in the laptop without having to lose everything by installing the regular 64-bit software, at least that is how it was explained to me. The laptop does load to the Ubuntu desktop twice as fast as the 2 Gig RAM Desktop PC I use with about the same speed AMD 64 processor.

Terminal Output after running the entire protocol  provided by Kansanoob:

To run a command as administrator (user "root"), use "sudo <command>".
See "man sudo_root" for details.

ubuntu@ubuntu:~$ chroot /home/michael
chroot: cannot change root directory to /home/michael: No such file or directory
ubuntu@ubuntu:~$ sudo mount /dev/sdb1 /mnt && sudo mount --bind /dev /mnt/dev && sudo mount --bind /proc /mnt/proc && sudo mount --bind /sys /mnt/sys && sudo mount --bind /dev/pts /mnt/dev/pts && sudo cp /etc/resolv.conf /mnt/etc/resolv.conf && sudo chroot /mnt
root@ubuntu:/# dpkg-divert --local --rename --add /sbin/initctl
Adding `local diversion of /sbin/initctl to /sbin/initctl.distrib'
root@ubuntu:/# ln -s /bin/true /sbin/initctl
root@ubuntu:/# grub-install -v && aptitude show grub|head -2 && aptitude show grub-pc|head -2 && aptitude show grub-common|head -2 && aptitude show os-prober|head -2
grub-install (GNU GRUB 1.98-1ubuntu6)
Package: grub
State: not installed
Package: grub-pc
State: installed
Package: grub-common
State: installed
Package: os-prober
State: installed
root@ubuntu:/# apt-get update
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid Release.gpg
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/main Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/universe Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/multiverse Translation-en_US
Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates Release.gpg [189B]
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates/main Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates/universe Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates/multiverse Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid Release 
Get:2 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates Release [38.5kB]    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/main Packages                         
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/multiverse Sources
Get:3 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/main Packages [173kB]
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security Release.gpg
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/main Translation-en_US
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/restricted Translation-en_US
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/universe Translation-en_US
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/multiverse Translation-en_US
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security Release  
Get:4 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/restricted Packages [2,102B]
Get:5 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/main Sources [66.5kB]
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/main Packages                  
Get:6 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/restricted Sources [737B]   
Get:7 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/universe Packages [31.0kB]
Get:8 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/universe Sources [8,389B]    
Get:9 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/multiverse Packages [632B]    
Get:10 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/multiverse Sources [14B]     
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/restricted Packages            
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/restricted Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/universe Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/multiverse Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/multiverse Sources
Fetched 321kB in 3s (83.1kB/s)
Reading package lists... Done
root@ubuntu:/# apt-get install --reinstall grub-pc
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 1 reinstalled, 0 to remove and 22 not upgraded.
Need to get 0B/607kB of archives.
After this operation, 0B of additional disk space will be used.
Do you want to continue [Y/n]? Y
Preconfiguring packages ...
(Reading database ... 156165 files and directories currently installed.)
Preparing to replace grub-pc 1.98-1ubuntu6 (using .../grub-pc_1.98-1ubuntu6_i386.deb) ...
Unpacking replacement grub-pc ...
Processing triggers for man-db ...
Setting up grub-pc (1.98-1ubuntu6) ...
Installation finished. No error reported.
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.32-22-generic-pae
Found initrd image: /boot/initrd.img-2.6.32-22-generic-pae
Found linux image: /boot/vmlinuz-2.6.31-21-generic-pae
Found initrd image: /boot/initrd.img-2.6.31-21-generic-pae
Found memtest86+ image: /boot/memtest86+.bin
ls: cannot access /media/disk: No such file or directory
ls: cannot access /media/disk: No such file or directory
ls: cannot access /media/disk: No such file or directory
ls: cannot access /media/disk: No such file or directory
ls: cannot access /media/disk: No such file or directory
ls: cannot access /media/disk: No such file or directory
Found Windows 7 (loader) on /dev/sda1
done

root@ubuntu:/# grub-mkconfig -o /boot/grub/grub.cfg
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.32-22-generic-pae
Found initrd image: /boot/initrd.img-2.6.32-22-generic-pae
Found linux image: /boot/vmlinuz-2.6.31-21-generic-pae
Found initrd image: /boot/initrd.img-2.6.31-21-generic-pae
Found memtest86+ image: /boot/memtest86+.bin
ls: cannot access /media/disk: No such file or directory
ls: cannot access /media/disk: No such file or directory
ls: cannot access /media/disk: No such file or directory
ls: cannot access /media/disk: No such file or directory
ls: cannot access /media/disk: No such file or directory
ls: cannot access /media/disk: No such file or directory
Found Windows 7 (loader) on /dev/sda1
done
root@ubuntu:/# grub-install /dev/sda
Installation finished. No error reported.
root@ubuntu:/# grub-install /dev/sdb
Installation finished. No error reported.
root@ubuntu:/# 

Spike   WHOA!!! Maybe this it moot!
I just tried to reboot the laptop and Ubuntu came right up! Then I rebooted and WIN 7 on the other drive came up. I sent an amateur radio email through Paclink in WIN 7, so it works. Now I need to get the Upgraded ubuntu set up with email, Pidgin, etc.

Thank you very much for all your help. I did not understand everything you had me do, but it worked. I'll make print outs of the files you provided for future reference, and mark this issue Solved. By the way, where is the Solved moniker and how do I get it posted?

Thanks again. Without your help I would still be floundering in the wrong places.

Spike

---

### Post by kansasnoob on 2010-05-27
As far as what we did this link somewhat explains my mount and chroot procedure:

[http://ubuntuforums.org/showpost.php?p=8068512&postcount=10](http://ubuntuforums.org/showpost.php?p=8068512&postcount=10)

The rest of it comes down to figuring out what version of grub is installed (I had some clues from the output of the Boot Info Script) and forcing a reinstall and reconfiguration of grub 2.

Sometimes problems just happen during installation or updates/upgrades. But trying to recover any "grub" mbr need not be so complicated. I've been toying with this for weeks:

[http://ubuntuforums.org/showpost.php?p=9338226&postcount=41](http://ubuntuforums.org/showpost.php?p=9338226&postcount=41)

Once I have it polished up I'll submit it as "How to restore any Ubuntu or Windows MBR with any Ubuntu Live CD"! Or something that will fit in the title bar :)

I think 90% of our current grub problems are either due to this bug (which I reported):

[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/576724](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/576724)

Or this absolute nonsense of "you must use the proper Live CD to recover the proper version of grub".

Things need to be less complicated!

---

### Post by prateekswapnil on 2010-05-27
Hi I have up with the same problem.I use WUBI to run ubuntu.I updated from ubuntu 9.10 to ubuntu 10.04 lts. Restarted after the updates and on restart computer hangs in grub rescue.Used the live cd (Ubuntu 8.10) and typed the first command mentioned by kansasnoob,it gives the error
mount:special device /dev/sbd1 does not exist
Any help to fix this error and get ubuntu running would be really helpfull

---

### Post by prateekswapnil on 2010-05-27
Also for now I cannot boot into windows...

---

### Post by oldfred on 2010-05-27
prateekswapnil - This is why you should have your own thread. Your problem is different than that in this thread. 

You also are running the wubi version which does not and should not have grub in the MBR. You need to reinstall windows to the MBR as both windows and Ubuntu's wubi use the windows boot loader first then you choose windows or Ubuntu.

---

### Post by darkod on 2010-05-27
> **prateekswapnil said:**
> Hi I have up with the same problem.I use WUBI to run ubuntu.I updated from ubuntu 9.10 to ubuntu 10.04 lts. Restarted after the updates and on restart computer hangs in grub rescue.Used the live cd (Ubuntu 8.10) and typed the first command mentioned by kansasnoob,it gives the error
mount:special device /dev/sbd1 does not exist
Any help to fix this error and get ubuntu running would be really helpfull

You probably need to do this fix to your windows partition:
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector)

And don't try the procedures to reinstall grub, when running wubi you DON'T have grub on your disk.

@kansas
I don't know if you noticed, another thing that needs urgent attention: when running wubi and doing the upgrade to 10.04, the window you mentioned in your bug report asking where to install grub2, actually installs it on all disks and partitions you select, the real ones. Even though wubi is in a way virtual, inside windows. I have seen results.txt with grub2 on all partitions and the MBR while the user had wubi and did the upgrade.
I'm only using ubuntu for 6 months but I didn't like wubi from day one. Too much confusion about what you actually have and misleading for lots of people. IMHO, they should take it offline, right now, especially with this bug putting grub2 on all partitions during the upgrade (if selected when asked, and most users do select all of them).

---

### Post by darkod on 2010-05-27
> **oldfred said:**
> 
You also are running the wubi version which does not and should not have grub in the MBR. 

Yeap, he should not have, but now he does. See my previous post here. :(

This wubi is becoming more hassle than it's worth. :)

---

