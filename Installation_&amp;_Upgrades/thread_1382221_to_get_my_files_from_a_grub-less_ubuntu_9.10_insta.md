---
title: "to get my files from a grub-less ubuntu 9.10 installation"
date: 2010-01-15
forum: Installation &amp; Upgrades
---

### Post by .volatile. on 2010-01-15
I made a plain ubuntu installation, my first one, from CD.
I then reinstalled my windows system not knowing of the right order of installation.
The grub was lost, I made several attempts to recover it but not succeeded.
 
While working with ubuntu that I like much, before the reinstallation of windows, I copied files to the desktop from my windows desktop.
 
Now I would like to get those files back but the files are restricted and the owner of the files/directories is unchangeable.
 
Is there a solution for this?
Thank you.

---

### Post by darkod on 2010-01-15
You can't copy them even if you boot with ubuntu cd, Try Ubuntu option, and in Places open the ubuntu partition?

PS. Also, I'm not sure why grub2 reinstall didn't work for you. Are you willing to try again?

---

### Post by alwayshere on 2010-01-15
photorec will do what you want .I used it to recover all my music i deleted by mistake.

heres a link that may help

[http://www.cgsecurity.org/wiki/PhotoRec_Step_By_Step]("http://www.cgsecurity.org/wiki/PhotoRec_Step_By_Step")

to install photorec

sudo apt-get install testdisk



to open photorec type "photorec"

---

### Post by Leppie on 2010-01-15
yes, try to re-install grub2 again. it's not an impossible mission... ;)

---

### Post by .volatile. on 2010-01-16
Thank you for the answers.
I will try photorec.
 
But first may describe my "grub" situation a little.
I used actively the Live CD this is where I installed my ubuntu.
I tried Auto Super Grub Disk recently and it did not work either but may have mixed things up.
 
My harddisk is partitioned into approx. 8 partitions.
C: was the windows boot.
D: is where XP is installed.
 
When I follow the instructions of this site and list the drives (fdisk -l), I get the following thing:
 
sda1 is a 255 byte * boot unit
sda2 is where I found the linux boot partition files
sda8 is where I found the root
and there is sda9 a Linux SWAP partition
 
unfortunately, sda2 has a file system written W95 (LBA)
and when I get to install grub in the terminal, it says the file system has to be changed, I do not know, how.
 
I think if I succeed to recover the files with photorec, I will reinstall ubuntu with the working windows system and it will be fine.
 
Thank you.

---

### Post by .volatile. on 2010-01-16
Id rather restore my grub, since photorec restores files with new names.

With "sudo grub" I cannot reach the grub prompt in the terminal, to start with.

---

### Post by Leppie on 2010-01-16
are you booting off the livecd now?

---

### Post by .volatile. on 2010-01-16
I managed to install grub on /dev/sda1

now no grub no windows install

it says
GNU GRUB version 1.97 beta 4
Minimal BASH-like line editing is supplied....

with the following prompt:
sh:grub>

what is next?

---

### Post by .volatile. on 2010-01-16
If I redo the whole process of grub-recovery,
I get the following line for sudo update-grub2 :
grub-probe: error: cannot find a device for /.

Any help?

---

### Post by Leppie on 2010-01-16
which grub recovery process did you follow?

could you [download and run meierfra's script]("http://sourceforge.net/projects/bootinfoscript/") and post the generated RESULTS.txt?

---

### Post by kansasnoob on 2010-01-16
> **Leppie said:**
> which grub recovery process did you follow?

could you [download and run meierfra's script]("http://sourceforge.net/projects/bootinfoscript/") and post the generated RESULTS.txt?

+1! louieb did an excellent job of explaining how to run the script:

[http://ubuntuforums.org/showthread.php?t=1291280](http://ubuntuforums.org/showthread.php?t=1291280)

---

### Post by .volatile. on 2010-01-17
I followed this one:
 
[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)
 
using the Live CD for Windows XP
 
certainly now I cannot boot XP either

---

### Post by kansasnoob on 2010-01-17
> **.volatile. said:**
> I followed this one:
 
[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)
 
using the Live CD for Windows XP
 
certainly now I cannot boot XP either

Well we need to see the results of the Boot Info Script:

[http://ubuntuforums.org/showthread.php?t=1291280](http://ubuntuforums.org/showthread.php?t=1291280)

You said:

> I managed to install grub on /dev/sda1

Which is usually the wrong thing to do! It's seldom wise to install grub to a partition!

If you want to try and get that booting give us the info we need to help you please!

---

### Post by .volatile. on 2010-01-17
tomorrow I will post it

---

### Post by kansasnoob on 2010-01-18
I'll check back this PM.

---

### Post by .volatile. on 2010-01-18
============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda
sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Grub 1.97
    Boot sector info:  Grub 1.97 is installed in the boot sector of sda1 and 
                       looks at sector 2619851 of the same hard drive for 
                       core.img, core.img is at this location on /dev/sda and 
                       looks on partition #1 for /grub. No errors found in 
                       the Boot Parameter Block.
    Boot file info:     Grub in the file /ubninit looks at sector 39 of the 
                       same hard drive for the stage2 file, but no stage2 
                       files can be found at this location.
    Operating System:  
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM /grub/core.img

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda5 starts 
                       at sector 63.
    Operating System:  Windows XP
    Boot files/dirs:   

sda6: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda6 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sda7: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda7 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sda8: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  Grub 1.97
    Boot sector info:  Grub 1.97 is installed in the boot sector of sda8 and 
                       looks at sector 69700583 of the same hard drive for 
                       core.img, core.img is at this location on /dev/sda and 
                       looks on partition #8 for /boot/grub.
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /grub/core.img 
                       /boot/grub/core.img

sda9: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda10: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda10 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 82.0 GB, 81964302336 bytes
255 heads, 63 sectors/track, 9964 cylinders, total 160086528 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x1dda1dd9

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63     4,096,574     4,096,512   7 HPFS/NTFS
/dev/sda2           4,096,575   160,055,594   155,959,020   f W95 Ext d (LBA)
/dev/sda5           4,096,638    34,877,114    30,780,477   7 HPFS/NTFS
/dev/sda6          34,877,178    55,359,989    20,482,812   7 HPFS/NTFS
/dev/sda7          55,360,053    65,545,199    10,185,147   7 HPFS/NTFS
/dev/sda8          65,545,263    86,734,934    21,189,672  83 Linux
/dev/sda9          86,734,998    87,779,159     1,044,162  82 Linux swap / Solaris
/dev/sda10         87,779,223   160,055,594    72,276,372   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

/dev/loop0: TYPE="squashfs" 
/dev/ramzswap0: TYPE="swap" 
/dev/sda10: UUID="4CDC5576DC555B72" LABEL="iWORK" TYPE="ntfs" 
/dev/sda1: UUID="520C96BC0C969B15" LABEL="base" TYPE="ntfs" 
/dev/sda5: UUID="D2D03EF1D03EDC03" LABEL="XP" TYPE="ntfs" 
/dev/sda6: UUID="087CFEDF7CFEC70A" LABEL="TRANS-L" TYPE="ntfs" 
/dev/sda7: UUID="049865E59865D5A8" LABEL="PROGs" TYPE="ntfs" 
/dev/sda8: UUID="b0eb733c-283e-45ba-9abd-f45d1d1838df" TYPE="ext4" 
/dev/sda9: UUID="92c4be46-1693-460a-95c4-03052aa2537c" TYPE="swap" 

=============================== "mount" output: ===============================

aufs on / type aufs (rw)
none on /proc type proc (rw,noexec,nosuid,nodev)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
udev on /dev type tmpfs (rw,mode=0755)
/dev/sr1 on /cdrom type iso9660 (rw)
/dev/loop0 on /rofs type squashfs (rw)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
none on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/ubuntu/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=ubuntu)


================================ sda1/boot.ini: ================================

[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(2)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(2)\WINDOWS="Microsoft Windows XP Professional" /fastdetect 

=================== sda1: Location of files loaded by Grub: ===================


    .0GB: grub/core.img
    .0GB: grub/stage2

=========================== sda8/boot/grub/grub.cfg: ===========================

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
set root=(hd0,9)
search --no-floppy --fs-uuid --set b0eb733c-283e-45ba-9abd-f45d1d1838df
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
    set root=(hd0,9)
    search --no-floppy --fs-uuid --set b0eb733c-283e-45ba-9abd-f45d1d1838df
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=b0eb733c-283e-45ba-9abd-f45d1d1838df ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd0,9)
    search --no-floppy --fs-uuid --set b0eb733c-283e-45ba-9abd-f45d1d1838df
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=b0eb733c-283e-45ba-9abd-f45d1d1838df ro single 
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
menuentry "Windows NT/2000/XP (loader) (on /dev/sda1)" {
    insmod ntfs
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set 520c96bc0c969b15
    drivemap -s (hd0) ${root}
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sda8/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda9 during installation
UUID=b0eb733c-283e-45ba-9abd-f45d1d1838df /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda10 during installation
UUID=92c4be46-1693-460a-95c4-03052aa2537c none            swap    sw              0       0
/dev/scd1       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sda8: Location of files loaded by Grub: ===================


  33.5GB: boot/grub/core.img
  33.5GB: boot/grub/grub.cfg
  33.5GB: boot/initrd.img-2.6.31-14-generic
  33.5GB: boot/vmlinuz-2.6.31-14-generic
  33.5GB: grub/core.img
  33.5GB: initrd.img
  33.5GB: vmlinuz

---

### Post by .volatile. on 2010-01-18
thanks for your time

I also have a suggestion for the Live CD:
the opening image that resembles a turning compact disk should
have the light arranged on it in a different way.
Now it looks as if the lightsource turns with the disk or a piece of dirt
keeps on reappearing in the same location of the disk.

The light should light up and fade away in the same location at regular
revolution. If this is what it symbolizes.

Where can I tell about this?

---

### Post by kansasnoob on 2010-01-18
I'm looking at this now but I'm a bit on the tired side so please be patient.

---

### Post by kansasnoob on 2010-01-19
Wow!

Did I already say WOW?

It appears that you just keep throwing commands hoping something sticks and some did:

> Windows is installed in the MBR of /dev/sda
sda1: __________________________________________________ _______________________
File system: ntfs
Boot sector type: Grub 1.97
Boot sector info: Grub 1.97 is installed in the boot sector of sda1 and
looks at sector 2619851 of the same hard drive for
core.img, core.img is at this location on /dev/sda and
looks on partition #1 for /grub. No errors found in
the Boot Parameter Block.
Boot file info: Grub in the file /ubninit looks at sector 39 of the
same hard drive for the stage2 file, but no stage2
files can be found at this location.
Operating System:
Boot files/dirs: /boot.ini /ntldr /NTDETECT.COM /grub/core.img

And:

> sda8: __________________________________________________ _______________________

File system: ext4
Boot sector type: Grub 1.97
Boot sector info: Grub 1.97 is installed in the boot sector of sda8 and
looks at sector 69700583 of the same hard drive for
core.img, core.img is at this location on /dev/sda and
looks on partition #8 for /boot/grub.
Operating System: Ubuntu 9.10
Boot files/dirs: /boot/grub/grub.cfg /etc/fstab /grub/core.img
/boot/grub/core.img

In the next post I'll show you how to get Ubuntu booting!

---

### Post by kansasnoob on 2010-01-19
I expect you to copy-n-paste the commands that follow!

I also expect you to copy-n-paste all of the results from the terminal here.

I'm sorry if I seem gruff but you've made a phenomenal mess of things!

So boot your Live CD choosing to "try without changes" and then in Terminal:

```
sudo mount /dev/sda8 /mnt && sudo mount --bind /dev /mnt/dev && sudo mount --bind /proc /mnt/proc && sudo mount --bind /dev/pts /mnt/dev/pts && sudo cp /etc/resolv.conf /mnt/etc/resolv.conf && sudo chroot /mnt
```

You'll see the command prompt chnage from $ to #.

```
mv /boot/grub /boot/grub_backup
```

```
mkdir /boot/grub
```

```
apt-get --purge remove grub-pc grub-common
```

```
apt-get install grub-pc
```

```
grub-install /dev/sda
```

```
update-grub
```

Wait! Wait until it says "done". It will not find Windows, that's OK! Then:

```
exit
```

```
sudo umount /mnt/dev/pts && sudo umount /mnt/dev && sudo umount /mnt/proc && sudo umount /mnt
```

Then reboot and hopefully you can boot into Ubuntu.

Once booted into Ubuntu go to terminal and run:

```
sudo update-grub
```

Wait until it says done and see if it finds Windows.

Then we'll go from there.

---

### Post by .volatile. on 2010-01-20
Thank you.
Tomorrow I try it and let you know the results.
It seems promising.

---

### Post by .volatile. on 2010-01-21
What I have done until reboot:

To run a command as administrator (user "root"), use "sudo <command>".
See "man sudo_root" for details.

ubuntu@ubuntu:~$ sudo mount /dev/sda8 /mnt && sudo mount --bind /dev /mnt/dev && sudo mount --bind /proc /mnt/proc && sudo mount --bind /dev/pts /mnt/dev/pts && sudo cp /etc/resolv.conf /mnt/etc/resolv.conf && sudo chroot /mnt
root@ubuntu:/# mv /boot/grub /boot/grub_backup
root@ubuntu:/# mkdir /boot/grub
root@ubuntu:/# apt-get --purge remove grub-pc grub-common
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  grub-common* grub-pc*
0 upgraded, 0 newly installed, 2 to remove and 158 not upgraded.
After this operation, 4,170kB disk space will be freed.
Do you want to continue [Y/n]? Y
(Reading database ... 119427 files and directories currently installed.)
Removing grub-pc ...
Purging configuration files for grub-pc ...
Removing grub-common ...
Purging configuration files for grub-common ...
Processing triggers for man-db ...
Processing triggers for sreadahead ...
sreadahead will be reprofiled on next reboot
Processing triggers for install-info ...
root@ubuntu:/# apt-get install grub-pc
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  grub-common
Suggested packages:
  multiboot-doc grub-emu desktop-base
The following NEW packages will be installed:
  grub-common grub-pc
0 upgraded, 2 newly installed, 0 to remove and 158 not upgraded.
Need to get 1,428kB of archives.
After this operation, 4,170kB of additional disk space will be used.
Do you want to continue [Y/n]? Y
Get:1 [http://hu.archive.ubuntu.com](http://hu.archive.ubuntu.com) karmic-updates/main grub-common 1.97~beta4-1ubuntu4.1 [994kB]
Get:2 [http://hu.archive.ubuntu.com](http://hu.archive.ubuntu.com) karmic-updates/main grub-pc 1.97~beta4-1ubuntu4.1 [434kB]
Fetched 1,428kB in 1s (1,039kB/s)   
Preconfiguring packages ...
Selecting previously deselected package grub-common.
(Reading database ... 119204 files and directories currently installed.)
Unpacking grub-common (from .../grub-common_1.97~beta4-1ubuntu4.1_i386.deb) ...
Selecting previously deselected package grub-pc.
Unpacking grub-pc (from .../grub-pc_1.97~beta4-1ubuntu4.1_i386.deb) ...
Processing triggers for man-db ...
Processing triggers for install-info ...
Processing triggers for sreadahead ...
Setting up grub-common (1.97~beta4-1ubuntu4.1) ...

Setting up grub-pc (1.97~beta4-1ubuntu4.1) ...

Creating config file /etc/default/grub with new version

root@ubuntu:/# grub-install /dev/sda
Installation finished. No error reported.
This is the contents of the device map /boot/grub/device.map.
Check if this is correct or not. If any of the lines is incorrect,
fix it and re-run the script `grub-install'.

(fd0)    /dev/fd0
(hd0)    /dev/sda
root@ubuntu:/# update-grub
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.31-14-generic
Found initrd image: /boot/initrd.img-2.6.31-14-generic
Found memtest86+ image: /boot/memtest86+.bin
Cannot find list of partitions!
done
root@ubuntu:/# ^C
root@ubuntu:/# exit
exit
ubuntu@ubuntu:~$ sudo umount /mnt/dev/pts && sudo umount /mnt/dev && sudo umount /mnt/proc && sudo umount /mnt
ubuntu@ubuntu:~$

---

### Post by .volatile. on 2010-01-21
Pop-up windows during install grub-pc command:

Configuring grub-pc &#9500;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9488;
 &#9474; The following Linux command line was extracted from /etc/default/grub or  &#9474; 
 &#9474; the `kopt' parameter in GRUB Legacy's menu.lst.  Please verify that it    &#9474; 
 &#9474; is correct, and modify it if necessary.                                   &#9474; 
 &#9474;                                                                           &#9474; 
 &#9474; Linux command line: 
OK

&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9508; Configuring grub-pc &#9500;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9488;
  &#9474; The following string will be used as Linux parameters for the default   &#9474; 
  &#9474; menu entry but not for the recovery mode.                               &#9474; 
  &#9474;                                                                         &#9474; 
  &#9474; Linux default command line:                                             &#9474; 
  &#9474;                                                                         &#9474; 
  &#9474; quiet splash___________________________________________________________ &#9474; 
  &#9474;                                                                         &#9474; 
  &#9474;                                 <Ok>  

Configuring grub-pc &#9500;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9488;
 &#9474;                                                                           &#9474; 
 &#9474; The grub-pc package is being upgraded.  This menu allows you to select    &#9474; 
 &#9474; which devices you'd like grub-install to be automatically run for, if     &#9474; 
 &#9474; any.                                                                      &#9474; 
 &#9474;                                                                           &#9474; 
 &#9474; It is recommended that you do this in most situations, to prevent the     &#9474; 
 &#9474; installed GRUB from getting out of sync with other components such as     &#9474; 
 &#9474; grub.cfg or with newer Linux images it will have to load.                 &#9474; 
 &#9474;                                                                           &#9474; 
 &#9474; If you're unsure which drive is designated as boot drive by your BIOS,    &#9474; 
 &#9474; it is often a good idea to install GRUB to all of them.                   &#9474; 
 &#9474;                                                                           &#9474; 
 &#9474; Note: It is possible to install GRUB to partition boot records as well.   &#9474; 
 &#9474; However, this forces GRUB to use the blocklist mechanism, which makes it  &#9474; 
 &#9474; less reliable, and therefore is not recommended.                          &#9474; 
 &#9474;                                                                           &#9474; 
 &#9474;                                  <Ok>     

grub install devices:
/dev/sda
OK

---

### Post by .volatile. on 2010-01-21
It did find it, thank you:

ubuntu@HOME:~$ sudo update-grub
[sudo] password for ubuntu: 
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.31-14-generic
Found initrd image: /boot/initrd.img-2.6.31-14-generic
Found memtest86+ image: /boot/memtest86+.bin
Found Microsoft Windows XP Professional on /dev/sda1
done
ubuntu@HOME:~$ 

Is there anything else left to be done?
Thank you very much

---

### Post by .volatile. on 2010-01-21
Ubuntu wokrs fine and the grub lists Windows as well in the fifth last place

When I choose Windows in the grub, it returns me the same results I received for Ubuntu earlier:

GNU GRUB version 1.97 beta 4
Minimal BASH-like line editing is supplied....

with the following prompt:
sh:grub>

Windows partitions are mountable.

---

### Post by kansasnoob on 2010-01-21
> **.volatile. said:**
> Ubuntu wokrs fine and the grub lists Windows as well in the fifth last place

When I choose Windows in the grub, it returns me the same results I received for Ubuntu earlier:

GNU GRUB version 1.97 beta 4
Minimal BASH-like line editing is supplied....

with the following prompt:
sh:grub>

Windows partitions are mountable.

OK we'll work this out. I should say I'm not incredibly surprised that you can't boot Windows yet because there did appear to be some grub files in the Windows partition (sda1) that's why we don't install grub to a partition, but rather the mbr of the drive:

```
File system: ntfs
Boot sector type: Grub 1.97
Boot sector info: Grub 1.97 is installed in the boot sector of sda1 and
looks at sector 2619851 of the same hard drive for
core.img, core.img is at this location on /dev/sda and
looks on partition #1 for /grub. No errors found in
the Boot Parameter Block.
Boot file info: Grub in the file /ubninit looks at sector 39 of the
same hard drive for the stage2 file, but no stage2
files can be found at this location.
Operating System:
Boot files/dirs: /boot.ini /ntldr /NTDETECT.COM /grub/core.img
```

Just as a point of comparison this is mine:

```

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM
```

So we have some repair work to do there but the first thing we need is a fresh output of the Boot Info Script since we've changed some things:

[http://ubuntuforums.org/showthread.php?t=1291280](http://ubuntuforums.org/showthread.php?t=1291280)

I should also note that I must run some errands so I might be out for a couple of hours, and it might take the wisdom of someone like meierfra to help get Win XP straightened out, but a fresh output of the Boot Info Script is the first step.

I might then have you temporarily install a generic Windows mbr to the drive using Lilo just to see if Windows will boot with that, and then we'll restore the Grub2 mbr **properly**, but I'd appreciate some patience here.

I guess it can't hurt to tell you the procedure I'm talking about. To restore a Win mbr (using the Live CD):

```
sudo apt-get install lilo
```

Ignore the warning and just press enter.

```
sudo lilo -M /dev/sda mbr
```

Note: that actually can be done from your installed Ubuntu but then I like to follow that with:

```
sudo apt-get remove lilo
```

Just to be sure that Lilo doesn't mess with the Grub2 config later on.

Then to properly restore grub2, knowing that your Ubuntu is on sda8 (using the Live CD):

```
sudo mount /dev/sda8 /mnt && sudo mount --bind /dev /mnt/dev &&sudo mount --bind /proc /mnt/proc && sudo chroot /mnt
```

```
grub-install /dev/sda
```

Should that return any errors:

```
grub-install --recheck /dev/sda
```

```
exit
```

```
sudo umount /mnt/dev && sudo umount /mnt/proc && sudo umount /mnt
```

Just don't try anything reckless.

---

### Post by kansasnoob on 2010-01-21
Just getting ready to run some errands but noticed meirfra is around so thought I'd bump this in hopes that he'd see this and we might get a real expert opinion and maybe some great suggestions.

---

### Post by meierfra. on 2010-01-21
You just need to fix the boot sector of your the Windows XP partition.  You can do  that with "fixboot" from you XP CD, but in my experiences, testdisk works best in cases like this:



```
sudo apt-get install testdisk
sudo testdisk /dev/sda
```

Choose "proceed" on the first screen, then
"intel"
"advanced",
Select the Windows partition (although it should be selected already) and choose
"boot"
"BackupBS"
Type "Y" to confirm
  
then press "q" a few times to quit  testdisk, reboot and see whether you can boot into Windows.

---

### Post by .volatile. on 2010-01-23
So can I ignore the requests of kansasnoob and proceed according to meierfra.? Is testdisk enough to fix the windows boot?
 
Thank you.

---

### Post by kansasnoob on 2010-01-23
> **.volatile. said:**
> So can I ignore the requests of kansasnoob and proceed according to meierfra.? Is testdisk enough to fix the windows boot?
 
Thank you.

By all means, meierfra knows 100 times more than I do about boot issues. That's why I bumped this. I was hoping he'd see it.

---

### Post by meierfra. on 2010-01-23
> Is testdisk enough to fix the windows boot?
Yes.

---

### Post by .volatile. on 2010-01-23
Thank you very much, really, both of you.
Now everything is in order, both of my OS work fine and my files were saved.
I owe you my very best wishes, thank you!!! :)

---

### Post by meierfra. on 2010-01-23
> Now everything is in order, 
Great. Have fun with XP and Ubuntu.

---

