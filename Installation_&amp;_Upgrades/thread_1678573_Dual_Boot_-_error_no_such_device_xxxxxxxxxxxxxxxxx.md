---
title: "Dual Boot - error: no such device: xxxxxxxxxxxxxxxxx"
date: 2011-01-30
forum: Installation &amp; Upgrades
---

### Post by Alterah on 2011-01-30
Hello,

I was recently plagued with a bad update and then Windows decided to crap out on me. So, I backed up everything, reformatted both hard drives and reinstalled. I have two hard drives, one 200GB (sdb) and one 1TB (sda). On the 200GB hard drive I installed Ubuntu 10.04LTS and on the 1TB hard drive I installed Windows XP. I installed XP first, then I installed Ubuntu. During the last step of installing Ubuntu I noticed it was going to put Grub on the 1TB hard drive, so I changed that to the 200GB hard drive. 

The problem is that when I try to boot into Windows by using Grub I get the following:
```

error: no such device: xxxxxxxxxxxxxxxxxxxxxx
error: invalid signature
```

Booting into Ubuntu works fine. Also, I can select the 1TB hard drive to boot from and Windows XP will boot up fine as well. 

Is there a way to tell grub where to find Windows XP? Thanks for any and all assistance.

---

### Post by presence1960 on 2011-01-30
Let's get a better look at your setup & boot process. Boot the Ubuntu Live CD/USB. Choose "try ubuntu without any changes", when the desktop loads come back here and do the following:

1. Download the boot info script. There is a link in my signature.
2. Once downloaded move the boot info script to the desktop.
3. Open a terminal and run the command ```
sudo bash ~/Desktop/boot_info_script*.sh
```

  This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text. 

See [here]("http://bootinfoscript.sourceforge.net/") for more info on the boot info script.

---

### Post by Alterah on 2011-01-30
Just to note, I can boot up into Ubuntu (I have to tell the BIOS to boot from the hard drive it is on). Likewise with Windows XP. 

Here are the contents of the file:

```

                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda
 => Grub 2 is installed in the MBR of /dev/sdb and looks on the same drive in 
    partition #1 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Windows XP
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda5 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.1 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb2: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb3: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
16 heads, 63 sectors/track, 1938021 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   275,799,887   275,799,825   7 HPFS/NTFS
/dev/sda2         275,799,888 1,953,521,135 1,677,721,248   f W95 Ext d (LBA)
/dev/sda5         275,799,951 1,953,521,135 1,677,721,185   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders, total 390721968 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *          2,048    39,086,079    39,084,032  83 Linux
/dev/sdb2          39,086,080    58,640,383    19,554,304  82 Linux swap / Solaris
/dev/sdb3          58,640,384   351,635,455   292,995,072  83 Linux


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        56D02B46D02B2C25                       ntfs                                     
/dev/sda2: PTTYPE="dos" 
/dev/sda5        D64476A244768551                       ntfs       Main                          
/dev/sda: PTTYPE="dos" 
/dev/sdb1        2b98fe13-cc83-4bd2-aab1-5dfdcfd33a11   ext4                                     
/dev/sdb2        e0604437-8731-43fb-be34-fa89f3901f3a   swap                                     
/dev/sdb3        819d697d-772b-4503-8edc-f0c2de2ac136   ext4                                     
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sdb1        /                        ext4       (rw,errors=remount-ro)
/dev/sdb3        /home                    ext4       (rw)
/dev/sr0         /media/X3TC              udf        (ro,nosuid,nodev,uhelper=udisks,uid=1000,gid=1000,iocharset=utf8,umask=0077)
/dev/sda5        /media/Main              fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)


================================ sda1/boot.ini: ================================

[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Windows XP Media Center Edition" /noexecute=optin /fastdetect 

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
search --no-floppy --fs-uuid --set 2b98fe13-cc83-4bd2-aab1-5dfdcfd33a11
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
search --no-floppy --fs-uuid --set 2b98fe13-cc83-4bd2-aab1-5dfdcfd33a11
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
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set 2b98fe13-cc83-4bd2-aab1-5dfdcfd33a11
    linux    /boot/vmlinuz-2.6.32-28-generic root=UUID=2b98fe13-cc83-4bd2-aab1-5dfdcfd33a11 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-28-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-28-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set 2b98fe13-cc83-4bd2-aab1-5dfdcfd33a11
    echo    'Loading Linux 2.6.32-28-generic ...'
    linux    /boot/vmlinuz-2.6.32-28-generic root=UUID=2b98fe13-cc83-4bd2-aab1-5dfdcfd33a11 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-28-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-27-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set 2b98fe13-cc83-4bd2-aab1-5dfdcfd33a11
    linux    /boot/vmlinuz-2.6.32-27-generic root=UUID=2b98fe13-cc83-4bd2-aab1-5dfdcfd33a11 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-27-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-27-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set 2b98fe13-cc83-4bd2-aab1-5dfdcfd33a11
    echo    'Loading Linux 2.6.32-27-generic ...'
    linux    /boot/vmlinuz-2.6.32-27-generic root=UUID=2b98fe13-cc83-4bd2-aab1-5dfdcfd33a11 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-27-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-24-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set 2b98fe13-cc83-4bd2-aab1-5dfdcfd33a11
    linux    /boot/vmlinuz-2.6.32-24-generic root=UUID=2b98fe13-cc83-4bd2-aab1-5dfdcfd33a11 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-24-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set 2b98fe13-cc83-4bd2-aab1-5dfdcfd33a11
    echo    'Loading Linux 2.6.32-24-generic ...'
    linux    /boot/vmlinuz-2.6.32-24-generic root=UUID=2b98fe13-cc83-4bd2-aab1-5dfdcfd33a11 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-24-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set 2b98fe13-cc83-4bd2-aab1-5dfdcfd33a11
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set 2b98fe13-cc83-4bd2-aab1-5dfdcfd33a11
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows XP Media Center Edition (on /dev/sda1)" {
    insmod ntfs
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 56d02b46d02b2c25
    drivemap -s (hd0) ${root}
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
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdb1 during installation
UUID=2b98fe13-cc83-4bd2-aab1-5dfdcfd33a11 /               ext4    errors=remount-ro 0       1
# /home was on /dev/sdb3 during installation
UUID=819d697d-772b-4503-8edc-f0c2de2ac136 /home           ext4    defaults        0       2
# swap was on /dev/sdb2 during installation
UUID=e0604437-8731-43fb-be34-fa89f3901f3a none            swap    sw              0       0

=================== sdb1: Location of files loaded by Grub: ===================


  17.3GB: boot/grub/core.img
  15.1GB: boot/grub/grub.cfg
  17.5GB: boot/initrd.img-2.6.32-24-generic
  17.5GB: boot/initrd.img-2.6.32-27-generic
  17.4GB: boot/initrd.img-2.6.32-28-generic
  17.4GB: boot/vmlinuz-2.6.32-24-generic
  17.4GB: boot/vmlinuz-2.6.32-27-generic
  17.5GB: boot/vmlinuz-2.6.32-28-generic
  17.4GB: initrd.img
  17.5GB: initrd.img.old
  17.5GB: vmlinuz
  17.4GB: vmlinuz.old

```

---

### Post by oldfred on 2011-01-30
I boot from sdc & sdb with exactly the same XP boot stanza (with my UUID of course).

The only thing I see a little unusual is the number of heads on your 1TB drive. It is normally 255 like on your 200GB drive with LBA. Did you do something special in partitioning drive?
16 heads, 63 sectors/track, 1938021 cylinders,

Sometimes with flash drives the heads are 16 or other smaller number.

Presence1960 may see something else.

---

### Post by presence1960 on 2011-01-30
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:search](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:search)

---

### Post by Alterah on 2011-01-31
Well, that didn't seem to work. It looks like I made things worse. I tried step 3 and now right before the hard drive boot, I get an error, but it switches to the Grub menu so quickly and I can't read anything else. Grub 2 gives me the following error messages:

```

Out of disk
You need to load the kernel first

```

I just reread the steps and saw under step 1 in the link:
```

and then press "Ctrl+X". This should boot your OS. **If you were not able to boot into  you OS,   you are  infected by a different problem and should not continue this howto**. 
```

---

### Post by oldfred on 2011-01-31
Did you delete the search line from the Ubuntu or the windows. Windows was the one you were having trouble with. 

You use the e on the grub menu to edit and it is a one time change. Only if things work, then you make the change permanent.

---

### Post by Alterah on 2011-01-31
At first I deleted the search line from the grub menu at boot up. Afterwards I commented out the three lines outlined in the link. Should I be able to use a live cd to uncomment out those three lines to at least be able to boot into Ubuntu?

---

### Post by oldfred on 2011-01-31
By editing the script before we know all the solutions, you removed the search line also from the Ubuntu boot lines. The set root is wrong in the Ubuntu boot but the search allows you to find the correct partition, so then Ubuntu boots.

set root='(hd1,1)'

Should be:
set root='(hd0,1)'

You should be able to edit this at the grub menu and boot. Then lets see where we are at. Does windows boot without the search line?

---

### Post by Alterah on 2011-01-31
I will try what you suggested. And no, Windows did not boot. I removed the search line, pressed Ctrl and X and nothing happened. I will keep you posted. Thanks for the assistance thus far.

---

### Post by Alterah on 2011-02-01
Your suggestion worked. I was able to boot into Ubuntu after making those changes and I undid the changes I made to the script. I rebooted and used your suggestion on Windows.

Leaving the search line alone, I changed the Windows from:

set root='(hd0,1)'
to
set root='(hd1,1)'

Windows booted up after that.

---

### Post by oldfred on 2011-02-01
If you made the changes on the grub menu as you boot, it is a one time change.

I would first try this to see if it reverses/correct the current entries.

sudo update-grub

Otherwise we will have to copy the windows entry into  40_custom and edit it there, so it is permanent.

---

