---
title: "Bricked Acer 1410 help request"
date: 2011-01-02
forum: Installation &amp; Upgrades
---

### Post by artisan on 2011-01-02
Acer netbook 1410
windows 7 on the original partition.
With an install of Linux mint (borked) on a second partition.
Trying to put on a clean install of ubuntu onto the netbook.


During the install of [www.ubuntu.com/netbook](www.ubuntu.com/netbook) the MBR and grub menus have been damaged.
All that is presented is:
error no such disk
grub rescue


Using a live USB 
Gparted runs but cannot see ANY drives/partitions.

Running fdsik from terminal on live USB gets:
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 3944 MB, 3944742912 bytes
255 heads, 63 sectors/track, 479 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000a3cbf

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1         479     3847536   83  Linux

Unable to read /dev/sdb
ubuntu@ubuntu:~$ 


This has been a couple of days now.
Help?
Please.
Any suggestions ?

I have spent a full day with google trawling through forums and useless posts about booting from live cds dvds.
There is no windows rescue cd. There is NO cd drive.
Everything has to run through a USB.
And as I say. Gpartedd is seeing nothing all Gparted can do is look for a drive.

---

### Post by Quackers on 2011-01-02
Please boot from the Ubuntu Live cd/usb and select "try ubuntu" then when the desktop is loaded make sure you have an internet connection and go to the site below and download the boot script to your DESKTOP and then open up a terminal (Applications > Accessories > terminal) and run
```

sudo bash ~/Desktop/boot_info_script*.sh
```

This will produce a results.txt file on your desktop. Please copy the contents of that file and paste them in your next post between CODE tags. For CODE tags click on New Reply (not quick reply)and then click on the # symbol in the toolbar.
This will give a full overview of your current system.
Thanks.

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

---

### Post by artisan on 2011-01-02
Thank you.
Sorry but. On the netbook version maybe the download should go into a file such as Documents as the desktop does not show any txt files. 


As for your offer of help....

```
0_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sdb5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda5 during installation
UUID=010be3ea-4659-4b98-8e3a-eaeb652498e3 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=faf5dd47-797d-49b6-8912-8f3ae6bb281d none            swap    sw              0       0

=================== sdb5: Location of files loaded by Grub: ===================


 208.7GB: boot/grub/core.img
 157.3GB: boot/grub/grub.cfg
 208.7GB: boot/initrd.img-2.6.32-21-generic
 208.8GB: boot/initrd.img-2.6.32-26-generic
 208.7GB: boot/vmlinuz-2.6.32-21-generic
 208.7GB: boot/vmlinuz-2.6.32-26-generic
 208.8GB: initrd.img
 208.7GB: initrd.img.old
 208.7GB: vmlinuz
 208.7GB: vmlinuz.old
```

---

### Post by artisan on 2011-01-02
Sorry that does not appear to be the complete file

Maybe?
```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Syslinux is installed in the MBR of /dev/sda
 => Grub 2 is installed in the MBR of /dev/sdb and looks on the same drive in 
    partition #7 for (,msdos7)/boot/grub.

sda1: _________________________________________________________________________

    File system:       ext2
    Boot sector type:  Fat32
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /BOOTMGR /BOOT/BCD

sdb2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot/BCD

sdb3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe

sdb4: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.1 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 3944 MB, 3944742912 bytes
255 heads, 63 sectors/track, 479 cylinders, total 7704576 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63     7,695,134     7,695,072  83 Linux


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1               2,048    25,167,871    25,165,824  27 Hidden HPFS/NTFS
/dev/sdb2    *     25,167,872    25,372,671       204,800   7 HPFS/NTFS
/dev/sdb3          25,372,672   152,566,175   127,193,504   7 HPFS/NTFS
/dev/sdb4         152,567,806   488,396,799   335,828,994   5 Extended
/dev/sdb5         294,232,064   480,409,599   186,177,536  83 Linux
/dev/sdb6         480,411,648   488,396,799     7,985,152  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        f6a4eb89-9dc1-412e-bd6e-c18d710be241   ext2                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        C2AEA495AEA4840F                       ntfs       PQSERVICE                     
/dev/sdb2        5E82A60782A5E42D                       ntfs       SYSTEM RESERVED               
/dev/sdb3        F22A4BFD2A4BBCFB                       ntfs       Acer                          
/dev/sdb4: PTTYPE="dos" 
/dev/sdb5        010be3ea-4659-4b98-8e3a-eaeb652498e3   ext4                                     
/dev/sdb6        faf5dd47-797d-49b6-8912-8f3ae6bb281d   swap                                     
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sda1        /cdrom                   ext2       (ro,noatime,errors=continue)
/dev/loop0       /rofs                    squashfs   (ro,noatime)


=========================== sdb5/boot/grub/grub.cfg: ===========================

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
set root='(hd0,5)'
search --no-floppy --fs-uuid --set 010be3ea-4659-4b98-8e3a-eaeb652498e3
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
set root='(hd0,5)'
search --no-floppy --fs-uuid --set 010be3ea-4659-4b98-8e3a-eaeb652498e3
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
menuentry 'Ubuntu, with Linux 2.6.32-26-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 010be3ea-4659-4b98-8e3a-eaeb652498e3
    linux    /boot/vmlinuz-2.6.32-26-generic root=UUID=010be3ea-4659-4b98-8e3a-eaeb652498e3 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-26-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-26-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 010be3ea-4659-4b98-8e3a-eaeb652498e3
    echo    'Loading Linux 2.6.32-26-generic ...'
    linux    /boot/vmlinuz-2.6.32-26-generic root=UUID=010be3ea-4659-4b98-8e3a-eaeb652498e3 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-26-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 010be3ea-4659-4b98-8e3a-eaeb652498e3
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=010be3ea-4659-4b98-8e3a-eaeb652498e3 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 010be3ea-4659-4b98-8e3a-eaeb652498e3
    echo    'Loading Linux 2.6.32-21-generic ...'
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=010be3ea-4659-4b98-8e3a-eaeb652498e3 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 010be3ea-4659-4b98-8e3a-eaeb652498e3
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 010be3ea-4659-4b98-8e3a-eaeb652498e3
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows Vista (loader) (on /dev/sda1)" {
    insmod ntfs
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set c2aea495aea4840f
    chainloader +1
}
menuentry "Windows 7 (loader) (on /dev/sda2)" {
    insmod ntfs
    set root='(hd0,2)'
    search --no-floppy --fs-uuid --set 5e82a60782a5e42d
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sdb5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda5 during installation
UUID=010be3ea-4659-4b98-8e3a-eaeb652498e3 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=faf5dd47-797d-49b6-8912-8f3ae6bb281d none            swap    sw              0       0

=================== sdb5: Location of files loaded by Grub: ===================


 208.7GB: boot/grub/core.img
 157.3GB: boot/grub/grub.cfg
 208.7GB: boot/initrd.img-2.6.32-21-generic
 208.8GB: boot/initrd.img-2.6.32-26-generic
 208.7GB: boot/vmlinuz-2.6.32-21-generic
 208.7GB: boot/vmlinuz-2.6.32-26-generic
 208.8GB: initrd.img
 208.7GB: initrd.img.old
 208.7GB: vmlinuz
 208.7GB: vmlinuz.old
```

---

### Post by Quackers on 2011-01-02
You're right :-)
Your partition table seems to stop at sdb6 - even though grub is looking for its boot files in sdb7.

"Acer netbook 1410
windows 7 on the original partition.
With an install of Linux mint (borked) on a second partition."

Windows 7 actually occupies 3 partitions ( to some degree )
Your fourth partition is an extended partition which appears to hold just sdb5 (Ubuntu 10.04) and sdb6 (swap).

---

### Post by artisan on 2011-01-02
I have been trying to save the windows partition.
The rest I do NOT care about.
This is my girlfriends netbook.
Linux does not format everything the same as windows. So She needs Windows for work.
Being a net book there is no cd drive and no recovery cd.

Everything is "Insert recovery CD"

---

### Post by Quackers on 2011-01-02
Try this
From the Live cd/usb desktop open up a terminal and copy/paste these lines in one at a time, pressing enter after each line.
```
sudo mount /dev/sdb5 /mnt
sudo grub-install --root-directory=/mnt /dev/sdb
```
Then reboot, when Ubuntu 10.04 should boot directly. If it does, open a terminal and run ```
sudo update-grub
``` and watch as grub.cfg is run, to see if the Windows Loader is found. If it is, reboot and try the Windows Loader entry to boot Windows.

---

### Post by artisan on 2011-01-02
That gets.

The boot splash screen for Ubuntu easy peasy.

Then.There is a white terminal in the top left hand corner.

There is a command line prompt. But when anything is typed it locks up.

---

### Post by artisan on 2011-01-02
Had to do a hard restart.
The whole thing was locked up.


Windows loader is there. 

Am trying to boot windows
But the whole things has gone back to setup.

That is fine so far.
As long as she can use windows today! She has work to do before she goes back after the holidays.
She will still be talking to me.

There is a back up of all here work on a external HD.
So that is covered.

Am just sitting through what I HOPE is windows set up.

I have never been so happy to see windows.
Or at least the startup (so far)

---

### Post by Quackers on 2011-01-02
That should be booting Ubuntu 10.04. I'm afraid there may be something wrong with that.
If you just want Windows back (and it is undamaged) you can install Lilo from the Ubuntu live cd/usb, which should make Windows bootable.
You should have made a Windows repair cd when Windows was booting, it only takes a minute. Or, at the very least, complain to Acer about the lack of one.

In a terminal, making sure you are connected to the internet, run
```
sudo apt-get install lilo
sudo lilo -M /dev/sdb mbr
```
You can ignore the errors flagged during installation.
On rebooting Windows should boot directly.

---

### Post by Quackers on 2011-01-02
That sounds like you are re-installing Windows! That means that you could have used the wrong Windows Loader!
Please see above.

---

### Post by artisan on 2011-01-02
> **Quackers said:**
> That should be booting Ubuntu 10.04. I'm afraid there may be something wrong with that.
Not a problem with me right now.

She is at least talking to me. And I do not mean the computer.

> If you just want Windows back (and it is undamaged) you can install Lilo from the Ubuntu live cd/usb, which should make Windows bootable.
I would be happy with trying the original idea.
The Linux netbook. But there are priorities. Windows does come first to some people.
When the grub menu shows. Windows is at the bottom under a couple of others I did not catch.
Right now Windows can be booted.


> You should have made a Windows repair cd when Windows was booting, it only takes a minute. Or, at the very least, complain to Acer about the lack of one.
Acer?
What a cluster *&^% they were.
Nothing on their website and the netbook is one year old, same owner. The Acer site will not issue anything because it says the product key has already been used.
Right now having a two week email conversation with a desk jockey over the holiday holds NO appeal. Sorry.

> 
In a terminal, making sure you are connected to the internet, run
```
sudo apt-get install lilo
sudo lilo -M /dev/sdb mbr
```
You can ignore the errors flagged during installation.
On rebooting Windows should boot directly.
Ah.
Sorry I jumped the gun.

---

### Post by Quackers on 2011-01-02
That's up to you sir :-) you paid them.

---

### Post by artisan on 2011-01-02
Well.
Having to do a full factory install.

I already take back the comment about happy to see windows.

During reinstall, Acer offer a backup option for reinstall. They want to use TWO dvds for 7.7 GB of data.  On a netbook with NO optical drive!


See my bitch in the cafe.
How can they sell a p...

I will stop there.




You have made my girlfriend happy.
She says thank you.

Once all the JUNK has finished downloading and all the updates rebooted and McKaffy anti virus free 60 day trials have all been dealt with I may need a little more help on cleaning up the whole grub thing.

This is what I would (politely) like to ask for help with.
Windows. Does not have to be main OS.
With dual boot into something like ubuntu.


Girlfiend actually likes ubuntu. Just that easy peasy did not last.
Easypeasy does not seem to sit to well on an Acer 1410.

So would like to try the netbook version of Ubuntu.
Would you be willing to help?

If not. That is fine. 
Thank you very much for your help so far.

---

### Post by Quackers on 2011-01-02
I don't know how long I'll be around, but if I'm here it's not a problem.
The first thing to check after all the updates are done and backups replaced is to check the Windows disk management console (enter disk management msc in Start search box then click on it above). The first consideration is how many primary partitions has Windows used during the installation? 4 is the maximum allowed on the MBR partition system. If you have 4 primary partitions you must delete one before installing another OS. If you have 3 or less, no problem.

As you have at this point re-installed Windows (probably using the whole disc) grub is now a thing of the past :wink: until you install another Linux OS.

---

### Post by artisan on 2011-01-02
Well I can safely say.
That all did not work...
Windows did reinstall.
But at reboot.
With the USB drive in the screen gets to
boot: 
Without the USB the computer just goes into a loop.
Trying to boot but not getting past a black screen.
Then it switches itself off and then back on again.

---

### Post by Quackers on 2011-01-02
Well, that's not good.
If the recovery partition doesn't work and you have no recovery dvd's nor repair disc, you are going to struggle.
Why would you re-install Windows and then reboot with the usb stick in, when bios is set to boot from that? Forgot?
ANyway, you could try the Ubuntu live cd/usb and re-run the boot script and see what got installed where, if anything did.

---

### Post by artisan on 2011-01-02
Sorry but...

this is the latest report.


```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #5 for (,msdos5)/boot/grub.
 => Syslinux is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /BOOTMGR /BOOT/BCD

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot/BCD

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe

sda4: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.1 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: _________________________________________________________________________

    File system:       ext2
    Boot sector type:  Fat32
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

/dev/sda1               2,048    25,167,871    25,165,824  27 Hidden HPFS/NTFS
/dev/sda2    *     25,167,872    25,372,671       204,800   7 HPFS/NTFS
/dev/sda3          25,372,672   152,566,175   127,193,504   7 HPFS/NTFS
/dev/sda4         152,567,806   488,396,799   335,828,994   5 Extended
/dev/sda5         294,232,064   480,409,599   186,177,536  83 Linux
/dev/sda6         480,411,648   488,396,799     7,985,152  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 3944 MB, 3944742912 bytes
255 heads, 63 sectors/track, 479 cylinders, total 7704576 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63     7,695,134     7,695,072  83 Linux


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        C2AEA495AEA4840F                       ntfs       PQSERVICE                     
/dev/sda2        5E82A60782A5E42D                       ntfs       SYSTEM RESERVED               
/dev/sda3        F22A4BFD2A4BBCFB                       ntfs       Acer                          
/dev/sda4: PTTYPE="dos" 
/dev/sda5        010be3ea-4659-4b98-8e3a-eaeb652498e3   ext4                                     
/dev/sda6        faf5dd47-797d-49b6-8912-8f3ae6bb281d   swap                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        f6a4eb89-9dc1-412e-bd6e-c18d710be241   ext2                                     
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sdb1        /cdrom                   ext2       (ro,noatime,errors=continue)
/dev/loop0       /rofs                    squashfs   (ro,noatime)


=========================== sda5/boot/grub/grub.cfg: ===========================

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
set root='(hd0,5)'
search --no-floppy --fs-uuid --set 010be3ea-4659-4b98-8e3a-eaeb652498e3
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
set root='(hd0,5)'
search --no-floppy --fs-uuid --set 010be3ea-4659-4b98-8e3a-eaeb652498e3
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
menuentry 'Ubuntu, with Linux 2.6.32-26-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 010be3ea-4659-4b98-8e3a-eaeb652498e3
    linux    /boot/vmlinuz-2.6.32-26-generic root=UUID=010be3ea-4659-4b98-8e3a-eaeb652498e3 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-26-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-26-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 010be3ea-4659-4b98-8e3a-eaeb652498e3
    echo    'Loading Linux 2.6.32-26-generic ...'
    linux    /boot/vmlinuz-2.6.32-26-generic root=UUID=010be3ea-4659-4b98-8e3a-eaeb652498e3 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-26-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 010be3ea-4659-4b98-8e3a-eaeb652498e3
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=010be3ea-4659-4b98-8e3a-eaeb652498e3 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 010be3ea-4659-4b98-8e3a-eaeb652498e3
    echo    'Loading Linux 2.6.32-21-generic ...'
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=010be3ea-4659-4b98-8e3a-eaeb652498e3 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 010be3ea-4659-4b98-8e3a-eaeb652498e3
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 010be3ea-4659-4b98-8e3a-eaeb652498e3
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows Vista (loader) (on /dev/sda1)" {
    insmod ntfs
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set c2aea495aea4840f
    chainloader +1
}
menuentry "Windows 7 (loader) (on /dev/sda2)" {
    insmod ntfs
    set root='(hd0,2)'
    search --no-floppy --fs-uuid --set 5e82a60782a5e42d
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sda5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda5 during installation
UUID=010be3ea-4659-4b98-8e3a-eaeb652498e3 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=faf5dd47-797d-49b6-8912-8f3ae6bb281d none            swap    sw              0       0

=================== sda5: Location of files loaded by Grub: ===================


 208.7GB: boot/grub/core.img
 157.3GB: boot/grub/grub.cfg
 208.7GB: boot/initrd.img-2.6.32-21-generic
 208.8GB: boot/initrd.img-2.6.32-26-generic
 208.7GB: boot/vmlinuz-2.6.32-21-generic
 208.7GB: boot/vmlinuz-2.6.32-26-generic
 208.8GB: initrd.img
 208.7GB: initrd.img.old
 208.7GB: vmlinuz
 208.7GB: vmlinuz.old
```

---

### Post by artisan on 2011-01-02
Ah yes.
The USB got left in from trying to grab the Acer system backup.
The USB was blank but...
Looks like it should not have been there.

---

### Post by Quackers on 2011-01-02
Well, it's sort of good news, I think.
I don't think anything has been re-installed. It looks like it did before, except that it's now on sda rahter than sdb drive.

The instructions below assume that the Live usb is plugged in and recognised as sda, as it was before. 

From the Live cd desktop try Lilo
```
sudo apt-get install lilo
sudo lilo -M /dev/sdb mbr
```
and then see if Windows boots ok. (Ignore the errors that the Lilo installation flags).

---

### Post by artisan on 2011-01-02
> **Quackers said:**
> Well, it's sort of good news, I think.
I don't think anything has been re-installed. It looks like it did before, except that it's now on sda rahter than sdb drive.

The instructions below assume that the Live usb is plugged in and recognised as sda, as it was before. 

From the Live cd desktop try Lilo
```
sudo apt-get install lilo
sudo lilo -M /dev/sdb mbr
```
and then see if Windows boots ok. (Ignore the errors that the Lilo installation flags).

Sorry. Nothing.

Take out the USB, reboot and that just goes to a black screen.
No cursor. Nothing.


Change BIOS to boot from HD.
Same.

Will boot from USB into ubuntu
But apart from that nothing.

---

### Post by Quackers on 2011-01-02
Did Lilo report errors about installing there?

---

### Post by artisan on 2011-01-02
No nothing
First there was a warning about finishing before rebooting.
Then after the second line there was nothing else.

---

### Post by Quackers on 2011-01-02
Did the first command try to download anything?
```
sudo apt-get install lilo
```
Were you connected to the internet?

---

### Post by artisan on 2011-01-02
> **Quackers said:**
> Did the first command try to download anything?
```
sudo apt-get install lilo
```
Were you connected to the internet?

Yes and yes.
But now there is no record since it is a live usb

---

### Post by Quackers on 2011-01-02
Hmm, please re-run the boot script in the terminal and post the output again. 
At this stage I'm not sure what has been installed to the mbr. Lilo should be there, but I suspect it isn't.

---

### Post by artisan on 2011-01-02
```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Lilo is installed in the MBR of /dev/sda
 => Grub 2 is installed in the MBR of /dev/sdb and looks on the same drive in 
    partition #5 for (,msdos5)/boot/grub.

sda1: _________________________________________________________________________

    File system:       ext2
    Boot sector type:  Fat32
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /BOOTMGR /BOOT/BCD

sdb2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot/BCD

sdb3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe

sdb4: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.1 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 3944 MB, 3944742912 bytes
255 heads, 63 sectors/track, 479 cylinders, total 7704576 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63     7,695,134     7,695,072  83 Linux


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1               2,048    25,167,871    25,165,824  27 Hidden HPFS/NTFS
/dev/sdb2    *     25,167,872    25,372,671       204,800   7 HPFS/NTFS
/dev/sdb3          25,372,672   152,566,175   127,193,504   7 HPFS/NTFS
/dev/sdb4         152,567,806   488,396,799   335,828,994   5 Extended
/dev/sdb5         294,232,064   480,409,599   186,177,536  83 Linux
/dev/sdb6         480,411,648   488,396,799     7,985,152  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        f6a4eb89-9dc1-412e-bd6e-c18d710be241   ext2                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        C2AEA495AEA4840F                       ntfs       PQSERVICE                     
/dev/sdb2        5E82A60782A5E42D                       ntfs       SYSTEM RESERVED               
/dev/sdb3        F22A4BFD2A4BBCFB                       ntfs       Acer                          
/dev/sdb4: PTTYPE="dos" 
/dev/sdb5        010be3ea-4659-4b98-8e3a-eaeb652498e3   ext4                                     
/dev/sdb6        faf5dd47-797d-49b6-8912-8f3ae6bb281d   swap                                     
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sda1        /cdrom                   ext2       (ro,noatime,errors=continue)
/dev/loop0       /rofs                    squashfs   (ro,noatime)


=========================== sdb5/boot/grub/grub.cfg: ===========================

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
set root='(hd0,5)'
search --no-floppy --fs-uuid --set 010be3ea-4659-4b98-8e3a-eaeb652498e3
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
set root='(hd0,5)'
search --no-floppy --fs-uuid --set 010be3ea-4659-4b98-8e3a-eaeb652498e3
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
menuentry 'Ubuntu, with Linux 2.6.32-26-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 010be3ea-4659-4b98-8e3a-eaeb652498e3
    linux    /boot/vmlinuz-2.6.32-26-generic root=UUID=010be3ea-4659-4b98-8e3a-eaeb652498e3 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-26-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-26-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 010be3ea-4659-4b98-8e3a-eaeb652498e3
    echo    'Loading Linux 2.6.32-26-generic ...'
    linux    /boot/vmlinuz-2.6.32-26-generic root=UUID=010be3ea-4659-4b98-8e3a-eaeb652498e3 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-26-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 010be3ea-4659-4b98-8e3a-eaeb652498e3
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=010be3ea-4659-4b98-8e3a-eaeb652498e3 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 010be3ea-4659-4b98-8e3a-eaeb652498e3
    echo    'Loading Linux 2.6.32-21-generic ...'
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=010be3ea-4659-4b98-8e3a-eaeb652498e3 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 010be3ea-4659-4b98-8e3a-eaeb652498e3
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 010be3ea-4659-4b98-8e3a-eaeb652498e3
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows Vista (loader) (on /dev/sda1)" {
    insmod ntfs
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set c2aea495aea4840f
    chainloader +1
}
menuentry "Windows 7 (loader) (on /dev/sda2)" {
    insmod ntfs
    set root='(hd0,2)'
    search --no-floppy --fs-uuid --set 5e82a60782a5e42d
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sdb5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda5 during installation
UUID=010be3ea-4659-4b98-8e3a-eaeb652498e3 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=faf5dd47-797d-49b6-8912-8f3ae6bb281d none            swap    sw              0       0

=================== sdb5: Location of files loaded by Grub: ===================


 208.7GB: boot/grub/core.img
 157.3GB: boot/grub/grub.cfg
 208.7GB: boot/initrd.img-2.6.32-21-generic
 208.8GB: boot/initrd.img-2.6.32-26-generic
 208.7GB: boot/vmlinuz-2.6.32-21-generic
 208.7GB: boot/vmlinuz-2.6.32-26-generic
 208.8GB: initrd.img
 208.7GB: initrd.img.old
 208.7GB: vmlinuz
 208.7GB: vmlinuz.old
```

---

### Post by Quackers on 2011-01-02
Lilo has installed to the flash drive, instead of your hard drive.
Please leave the flash drive plugged in and set your bios to boot from it first (if it will boot now). Then go back to the Live usb desktop and re-run the commands for Lilo.
```
sudo apt-get install lilo
sudo lilo -M /dev/sdb mbr
```

---

### Post by artisan on 2011-01-02
Right now am running ubuntu from the USB drive.

ubuntu@ubuntu:~$ sudo apt-get install lilo
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  mbr
Suggested packages:
  lilo-doc
The following NEW packages will be installed:
  lilo mbr
0 upgraded, 2 newly installed, 0 to remove and 0 not upgraded.
Need to get 413kB of archives.
After this operation, 1,315kB of additional disk space will be used.
Do you want to continue [Y/n]? y

Y


                                                                        &#9474; LILO configuration                                                        

It seems to be your first LILO installation. It is absolutely necessary to run liloconfig(8) when you complete this process and execute /sbin/lilo after this.                                               

    LILO won't work if you don't do this.


Get:1 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick/main mbr i386 1.1.10-2 [23.0kB]
Get:2 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick/main lilo i386 1:22.8-8ubuntu1 [390kB]
Fetched 413kB in 1s (386kB/s)
Preconfiguring packages ...
Selecting previously deselected package mbr.
(Reading database ... 120331 files and directories currently installed.)
Unpacking mbr (from .../archives/mbr_1.1.10-2_i386.deb) ...
Selecting previously deselected package lilo.
Unpacking lilo (from .../lilo_1%3a22.8-8ubuntu1_i386.deb) ...
Processing triggers for man-db ...
Setting up mbr (1.1.10-2) ...
Setting up lilo (1:22.8-8ubuntu1) ...

WARNING: kernel & initrd not found in the root directory (/vmlinuz & /initrd.img)
WARNING: Do NOT reboot or LILO may fail to boot if your kernel+initrd is large.
WARNING: Please read /usr/share/doc/lilo/README.Debian



ubuntu@ubuntu:~$ sudo lilo -M /dev/sdb mbr
Backup copy of /dev/sdb in /boot/boot.0810
The Master Boot Record of  /dev/sdb  has been updated.
ubuntu@ubuntu:~$

---

### Post by Quackers on 2011-01-02
Ok, try rebooting without the usb in please.

---

### Post by artisan on 2011-01-02
That is one Acer netbook.
Unbricked.

Thank you for your time.

Seriously.
Thank you.

---

### Post by Quackers on 2011-01-02
You're welcome :-)
Nice one!
Please mark the thread solved using the Thread Tools near the top of the page.

---

### Post by artisan on 2011-01-02
I will mark this as solved.

Still have no idea what caused it but if any one is looking for an answer please re read this thread.

Quackers took four hours of his time with this.

It is worth trying to follow.

---

### Post by Quackers on 2011-01-02
I can explain in part what happened.
It seems that grub was installed in the mbr of your hard drive (as it should be) but it was looking for its boot files in sda7 - a partition which did not exist. This could have been due to a partitioning error, which could explain why fdisk could not read the drive at first.
Once grub was re-installed using sda5 boot files, it should have been bootable. However, it was not. This may mean that one or more of the boot files was damaged. There could also be other reason.
If you had a Windows repair disc we could have replaced grub with the Windows bootloader, but as you didn't have one we used Lilo (which is a compatible bootloader for Windows). However, Lilo oringinally got installed to the mbr of the flash drive, instead of your hard drive. That may be because its designation changed when the flash drive was unplugged, then plugged in again.
Now that Lilo is installed to your hard drive Windows now boots.
I would strongly suggest that you now make a Windows repair cd (for the cost of a usb cd drive, it is well worth having!) and Windows recovery dvd's as well.

---

### Post by artisan on 2011-01-02
To be honest I did not expect things to go that bad.

The whole thing should have been straight forward.
Partition drive and....


But somewhere....things took a walk.


I did backup all the data. (:p)

But not the mbr.
I will have to take a look at a Windows repair disc.
But the plan is/was to drop Windows. (later)
As for a Windows repair disk...
That was not in the plan for obvious reasons. Both me and the girlfriend are not windows fans.
She does need windows for work.
She is a teacher and has lots of stuff to do that losses format between open office and whatever in Windows. ??

(I have not used windows for years. Not since 2006 apparently am currently using Mint)


What bothers me is the who Acer windows thing where they are still relying on DVDS and CDs.

Everything is insert cd or dvd.

People say use Unebootin.

Sorry. No.
I do try to follow instructions and if something says it use a cd or live cd. To me that IS different than a live USB.

I cannot be convinced otherwise.
If it is for a cd drive then it is for er.. well  a cd drive.

What you have just helped with was from a live usb that was supposed to be a live usb and used as a live usb.

I would not want to try to recover something using something that is supposed to be a live cd.
Maybe it's me?

But surely considering the billions of dollars involved has no one managed create have a recovery usb download?
Especially since computers no longer have cd/dvd drives.

I will now spend the rest of the day getting windows secure.
And then look at a repair disk.

---

### Post by Quackers on 2011-01-02
There are 2 methods described in this link for making a Windows 7 repair USB flash drive. Only one applies to computers which don't have a cd drive.
And by the way, most computers do have a cd drive - only netbooks don't :-)
With regard to your complaint about the lack of backup/recovery/repair  arrangements for netbooks, I would suggest you tell Acer about your feelings.

[http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/](http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/)

---

### Post by artisan on 2011-01-02
Thank you for that.

It is not just Acer. It is MS as the main culprit.

4 hours later am still trying to get windows to accept the restore file I have on an external HD.

What is the point of a restore file if.....

I am sure you can fill in the rest.

---

### Post by Quackers on 2011-01-02
Yes, I agree, but you pay for MS through Ace, and they should know how their users feel.
What is the problem with restoring the backups? In fact, why do you need to restore backups? The system should be as it was before.
Also, as it seems the recovery partition may not now work, I would advise a backup image of Windows, when you get it sorted out. Clonezilla would do it - and it's free :-)

---

### Post by artisan on 2011-01-02
I dropped windows some years ago.
So am out of practice on this stuff. With Linux I know nothing about grub and mbr. It is a weak point.
I think Acer might hear about this.


As for the Winodws things.
I used the windows backup on the original system before trying easypeasy.

The backup cannot be seen.

I have one guess and that is.
Because I have added a couple of partitions since the original backup is now larger than the space available. A guess but....

So now have a working windows 7 that is empty and will not take its own restore.

---

### Post by Quackers on 2011-01-02
There's a couple of things I'm not clear about. If the re-install of Windows had worked, then Ubuntu would have gone. As Ubuntu is not gone, I would have thought Windows should be as it was before.
Secondly, if you used Windows backup image, if I recall correctly, it is only restorable from within the Windows recovery environment, and the image may not normally be visible _ maybe :-)

---

### Post by artisan on 2011-01-02
I have no idea if Linux is still there.
The thing boots into windows with no grub. But as I try take a look it looks like the partitions are still there. Since the HD is showing 60 GB.
 During this whole mess I have tried to get Windows back using a restore factory settings. (anything in a storm)

As for the second part....
I have to break it in order to restore it???

---

### Post by Quackers on 2011-01-02
If the restore to factory settings had worked, I would have expected it to demand the whole disc. As the boot script still reports Ubuntu as being present, I suspect Windows has not been restored to factory state, and as such, would not need backups to be restored. Obviously that seems not to be the case! I don't know what's happened there.
Which screen did you run backups from? That governs how you restore them. 
I too, expressed surprise when I was informed that the Windows backup image could only be restored through the Recovery environment, but it was true, andmine did restore correctly.
If you used the backup and restore centre to make an image I would look at the link I posted earlier for the usb recovery cd and, making sure the disc with the backup image is plugged in, try restoring that way.
[http://windows.microsoft.com/en-US/windows-vista/Restore-your-computer-from-a-system-image-backup](http://windows.microsoft.com/en-US/windows-vista/Restore-your-computer-from-a-system-image-backup)
In fact, having just read that link, it may be necessary to use an installation disc or a recovery dvd! Ouch.

---

### Post by artisan on 2011-01-02
> **Quackers said:**
> it may be necessary to use an installation disc or a recovery dvd! Ouch.

Ah you are starting to see the issue.

As for the rest.
The factory restore was done as a way of trying to get the whole thing unbricked.

So it was done whilst it was ... well I do not know what state it was in..
When There was grub restore showing.

I have a separate backup of the actual files. I did as I say a separate backup.
Just as well since the actual windows backup system needs a bricked computer with a cd/dvd drive.



Windows now shows that there are six "health" partitions on the netbook.
That is as far as I have got.
Girlfriend is now upset that the backup did not take.

:p

---

### Post by Quackers on 2011-01-02
I know you ran the recovery at some time, but if you did not choose a specific partition it should have used the whole disc, wiping out everything else. As it hasn't done that I have my doubts.
It would be an idea to find out how to recover things before it is needed - not after :wink: and if recovery needs a cd drive, then it needs a cd drive.

---

### Post by artisan on 2011-01-02
The Important things is that the files are safe since the was a physical copy of the files.
IF I had relied on windows restore system I would be very single by now.

I do appreciate the help you gave today.

Later this week I will take a look at the netbook.

---

### Post by Quackers on 2011-01-02
I had a thought!
You could try to access the backup image by running the recovery environment via a key at boot. There will be a key to tap during boot to access it. It is often F11 or ctrl + F11, or the del key. Find out which activates it on your computer and reboot tapping that key. Make sure the drive with your backup image is plugged in and follow these instructions
[http://windows.microsoft.com/en-US/windows7/Restore-your-computer-from-a-system-image-backup](http://windows.microsoft.com/en-US/windows7/Restore-your-computer-from-a-system-image-backup)

---

### Post by artisan on 2011-01-02
I think you are correct.


But unfortunately it will have to wait.

All this has finally made me start a backup of my system.
I have backup running right now and it looks like it will be another few hours.
The Acer is being used as well right now.

Work to be done before work tomorrow.

But as I say, yes you are most probably correct with your last post.
There should be time to try it tomorrow.

---

### Post by Quackers on 2011-01-02
Ok, good luck in your endeavours :-)

---

