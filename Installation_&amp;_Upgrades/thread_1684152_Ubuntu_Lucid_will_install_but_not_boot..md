---
title: "Ubuntu Lucid will install but not boot."
date: 2011-02-08
forum: Installation &amp; Upgrades
---

### Post by softappstudio on 2011-02-08
I have tried 7 times to install Ubuntu Lucid from LiveCD and a USB-HDD  image of that, onto a new PC with 2.5" m-SATA HDD. Installation proceeds  smoothly, but it will not boot. Early messages (too quick to follow)  suggest failure to mount /dev (?). This system will support WinXP (which  I don't want) so no hardware problem. The actual LiveCD was used to  install Ubuntu on another PC, OK. Ubuntu runs in "trial" mode on this  new PC. I have checked "      fdisk -l     " and that indicates that the  HDD is bootable. [I am a newbie].  I have tried to use grub-install but  that failed me, and its man pages seem to be written for a different OS, so  no luck there. :confused:

Fortunately, I learned on another thread (Thank you Master Roaster !) about RESULTS.txt, so I have run that, on the said PC with these results.  The 160 GB drive is the attached USB-external-HDD (with the LiveCD image, currently the boot partition), the 250 GB drive --  sda1 --is the internal m-SATA on which the new installation is supposed to run.
```

                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #1 for /boot/grub.
 => Syslinux is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.1 LTS
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

    File system:       vfat
    Boot sector type:  Fat32
    Boot sector info:  According to the info in the boot sector, sdb1 starts 
                       at sector 0. But according to the info from fdisk, 
                       sdb1 starts at sector 63.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048   482,396,159   482,394,112  83 Linux
/dev/sda2         482,398,206   488,396,799     5,998,594   5 Extended
/dev/sda5         482,398,208   488,396,799     5,998,592  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63   312,576,704   312,576,642   c W95 FAT32 (LBA)


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/loop1       72fa26f3-cf56-4098-bdd0-9ae0d4fd6060   ext3                                     
/dev/sda1        0d3f444b-744f-41d4-afe4-756907fdde7c   ext4                                     
/dev/sda2: PTTYPE="dos" 
/dev/sda5        9f562474-58f7-434a-9ebc-b97c56c98403   swap                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        A3E6-A0D3                              vfat                                     
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sdb1        /cdrom                   vfat       (rw,relatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sda1        /media/0d3f444b-744f-41d4-afe4-756907fdde7c ext4       (rw,nosuid,nodev,uhelper=udisks)
/dev/loop1       /media/72fa26f3-cf56-4098-bdd0-9ae0d4fd6060 ext3       (rw,nosuid,nodev,uhelper=udisks)


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
search --no-floppy --fs-uuid --set 0d3f444b-744f-41d4-afe4-756907fdde7c
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
search --no-floppy --fs-uuid --set 0d3f444b-744f-41d4-afe4-756907fdde7c
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
menuentry 'Ubuntu, with Linux 2.6.32-28-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 0d3f444b-744f-41d4-afe4-756907fdde7c
    linux    /boot/vmlinuz-2.6.32-28-generic root=/dev/sda1 ro   quiet splash
}
menuentry 'Ubuntu, with Linux 2.6.32-28-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 0d3f444b-744f-41d4-afe4-756907fdde7c
    echo    'Loading Linux 2.6.32-28-generic ...'
    linux    /boot/vmlinuz-2.6.32-28-generic root=/dev/sda1 ro single 
    echo    'Loading initial ramdisk ...'
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 0d3f444b-744f-41d4-afe4-756907fdde7c
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 0d3f444b-744f-41d4-afe4-756907fdde7c
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
# / was on /dev/sda1 during installation
UUID=0d3f444b-744f-41d4-afe4-756907fdde7c /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=9f562474-58f7-434a-9ebc-b97c56c98403 none            swap    sw              0       0

=================== sda1: Location of files loaded by Grub: ===================


 171.9GB: boot/grub/core.img
 137.6GB: boot/grub/grub.cfg
 172.0GB: boot/initrd.img-2.6.32-24-generic
 171.9GB: boot/vmlinuz-2.6.32-28-generic
 171.9GB: vmlinuz

```
*|~~~~~~~~~~~~~~~~~~~

All suggestions on how to fix this will be most welcome!
--Grahame

---

### Post by drs305 on 2011-02-08
Grahame,

Thank you for creating a new post and welcome to the Ubuntu forums.

The reason your system isn't booting is because the initrd file is missing from your /boot folder.

The last line of your menuentry should be the following, but it wasn't created because the file itself is missing:
> 
initrd /boot/initrd.img-2.6.32-28-generic


That explains why it won't boot, but doesn't explain what happened to the file or why it wasn't created in the first place.

You could try chrooting into your Ubuntu partition via a LiveCD, and then run the "mkinitramfs" command to generate a new initrd file.

I wrote a guide on how to chroot. Accomplish Step 1 of the "Why Chroot" section:
[http://ubuntuforums.org/showthread.php?t=1581099]("http://ubuntuforums.org/showthread.php?t=1581099")

Then run this command to generate the initrd image (you don't use "sudo" in the chroot environment):
NOTE: This will create the current kernel. Since you just installed from the CD, I'm assuming it will be the 2.6.32-28-generic kernel.
If not, we will need to use a different kernel.
You can check the kernel in use with "uname -r"

```

mkinitramfs -o /boot/initrd.img-2.6.32-28-generic
```

One thing to watch for:
Make sure it places the new file in the /boot folder (while you are still in chroot).

Once you have the initrd file in the correct location, run 
```
update-grub
```
And then check the contents of the menuentry to ensure the "initrd" line is now in the menuentry section. This command will show Grub's menuentries.
```
grep menuentry -A10 /boot/grub/grub.cfg
or
gedit /boot/grub/grub.cfg 
```

If it is, type "exit" and reboot.

---

### Post by softappstudio on 2011-02-08
Wow, thank you Oh Master Bean.  :p  So I've printed all that out and will take it upstairs and give it a try. after I make my supper. Talk about the "deep end"!  It seemed most likely to me that it was a "boot time" problem, but I did not imagine that a crucial file was somehow missing. Fingers crossed:lolflag:
--Grahame

---

### Post by drs305 on 2011-02-08
> **softappstudio said:**
> Wow, thank you Oh Master Bean.  :p  So I've printed all that out and will take it upstairs and give it a try. after I make my supper. Talk about the "deep end"!  It seemed most likely to me that it was a "boot time" problem, but I did not imagine that a crucial file was somehow missing. Fingers crossed
--Grahame

The chroot procedure may seem a bit complicated. Just take it slowly. 

Making a new initrd.img via chroot is a first for me (as it is for you) so we'll just have to see if it works or not. It certainly won't hurt anything. Good luck and let us know.

---

### Post by softappstudio on 2011-02-09
Hello there, limited progress....

I reckon that I have a "normal" installation on the HDD, /boot is in sda1. So I got into chroot as indicated for normal installation. [I also in my enthusiasm ran the apt-get update, and the long list was found OK].

chroot fails at the  mkinitramfs command, saying it cannot find /lib/modules/"kernel" (where kernel is the kernel). I didn't know which /lib it meant (the booted  sdb or the "new" sda1) so I looked in both. I found a directory  ...

"FileSystem"/lib/modules/"kernel"

But on the new drive there was only a folder in /lib/modules for the 32-24-generic version. [no idea about that]. I tried to put the "right" version there but Ubuntu won't let me (even though logged in as a primary administrator, then sudu su into root, it says I don't have enough privileges, just like the proverbial Parisian woman) so I could not do that. I tried changing the mkinitramfs command to the (older) version specification, but it insists on looking for the -28-generic version, so no luck there. :confused:

I feel we are on the right track, just some more obstacles to overcome. ;-)

--Grahame

---

### Post by drs305 on 2011-02-09
I wish I was more knowledgeable about how all this ties together. Perhaps someone more familiar with the command will chime in.

My next thought would be to try to run the command without specifying the version and seeing what it comes up with:
```
mkinitramfs -o /boot/initramfs-$(uname -r)
```

This would be run in the chroot environment, and I am supposing you have no initrd.img files currently existing in its boot. After running the command, see the version which was created (if it did) and check to see if a kernel of the same version exists there. If not, you could try to copy the kernel from the CD's /boot/directory (such as vmlinuz-2.6.32-28-generic).

---

### Post by softappstudio on 2011-02-09
Thanks for the continuation.

I did look for the actual initrd.img files and was confused by the result. There did not appear to be one on the USB-HDD which does boot, but there is one on the m-SATA HDD which won't. As you may guess .... I know nothing! :oops:

My wife is using the PC at the moment, so tomorrow I will try what you suggest. I think part of the problem may be something to do with the fact that this USB "Trial" installation has been running a lot as the default boot, so it probably has updated itself. Perhaps the "Install it" part of Ubuntu is getting confused about which kernel version to install, the one it is running under, or the one it was brought up to believe in. The USB-HDD has both 32-24-generic and 32-28-generic directories, and apparently uses the later version for itself. I am putting the installation on a micro-ATX PC (Zotac Zbox) which does not have a CD-ROM drive; my original "Live CD" often causes read I/O errors when I boot from a new USB-CD drive (no idea why, all other CDs read fine on this PC) which is aggravating, so I have been using the USB-HDD image for most of this work.

Thanks,
--Grahame

---

### Post by softappstudio on 2011-02-11
So it slowly emerged in my aging mind that I definitely had some problem with my installation source (although it ran fine itself) and that it could be pragmatic simply to start over with a completely new slate, rather than attempt to discover and correct whatever problems were being created.
So I went down to my large and ugly WinXP machine and downloaded both the day's version of 10.04.1-generic and the Windows "pendrive" installer generator which I put on a 4 GBy USB drive and took immediately upstairs to the new Zotac Zbox and installed it on the m-SATA HDD.
 
Needless to say, it all works perfectly. Ubuntu Lucid is a perfect match for this small (very small) computer, which has such low power consumption when in "Suspend" mode that I have told my wife to leave it like that 24/7, then it is an 'instant on' device, which she greatly appreciates.

Thanks for all your generous help, both on the forum and in the development team. I look forward to the day when there will not be a single Windows Registry on the premises, but I won't actually hold my breath.

--G

---

