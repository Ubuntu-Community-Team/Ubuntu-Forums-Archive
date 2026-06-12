---
title: "Problem after upgrading"
date: 2010-12-02
forum: Installation &amp; Upgrades
---

### Post by clint8679 on 2010-12-02
Hi

I recently upgraded to the newest version of Ubuntu.  I dual boot with Windows 7.  

All was going fine the first few times I used my system after the upgrade but I have now run into a serious problem.  I'm not that technical so will explain this as best i can.

Basically, when I switch my computer on, I can not get to the screen that allows me to choose an operating system.  Before it gets there it just restarts.  

I guess its a problem with the GNU GRUB software.  It just seems like the computer can't find it and restarts itself.  So I can't get into either Ubuntu or Windows at the moment.

Any thoughts on what is causing the problem and how it could be fixed would be appreciated.

---

### Post by sikander3786 on 2010-12-02
Hi.

Please boot an Ubuntu Live CD/USB. Select the try mode. Then download bootinfoscript here.

[http://bootinfoscript.sourceforge.net](http://bootinfoscript.sourceforge.net)

Copy it to your desktop. Go to Applications > Accessories > Terminal and paste this command.

```
sudo bash ~/Desktop/boot_info_script*.sh
```

It would generate a Results.txt on your desktop. Open it and copy paste all the text from that file in to your post here.

Before pasting, either click # from post menu and paste the text in between generated code tags or after pasting, highlight the text and click #. Or type [/code] at the end and [code] at the beginning of your text.

Thanks.

---

### Post by clint8679 on 2010-12-03
```
Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #5 for (,msdos5)/boot/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /boot/bcd

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
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x07a54ffb

Partition  Boot         Start           End          Size  Id System

/dev/sda1               2,048    31,459,327    31,457,280  27 Hidden HPFS/NTFS
/dev/sda2    *     31,459,328    31,664,127       204,800   7 HPFS/NTFS
/dev/sda3          31,664,128   356,100,975   324,436,848   7 HPFS/NTFS
/dev/sda4         356,112,855   625,137,344   269,024,490   5 Extended
/dev/sda5         356,112,918   488,857,949   132,745,032  83 Linux
/dev/sda6         614,116,818   625,137,344    11,020,527  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        62EA4535EA45072F                       ntfs       RECOVERY                      
/dev/sda2        D86645D76645B752                       ntfs       SYSTEM                        
/dev/sda3        60CC47A3CC4771F8                       ntfs                                     
/dev/sda5        701412ff-d9c5-4371-bbaa-424c1626616e   ext4                                     
/dev/sda6        3722e16e-85c9-4d13-b5ec-6736d9b4efa5   swap                                     

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (rw)
/dev/loop0       /rofs                    squashfs   (rw)


=========================== sda5/boot/grub/grub.cfg: ===========================

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
}

insmod part_msdos
insmod ext2
set root='(hd0,msdos5)'
search --no-floppy --fs-uuid --set 701412ff-d9c5-4371-bbaa-424c1626616e
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos5)'
search --no-floppy --fs-uuid --set 701412ff-d9c5-4371-bbaa-424c1626616e
set locale_dir=($root)/boot/grub/locale
set lang=en
insmod gettext
if [ "${recordfail}" = 1 ]; then
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
menuentry 'Ubuntu, with Linux 2.6.35-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set 701412ff-d9c5-4371-bbaa-424c1626616e
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=701412ff-d9c5-4371-bbaa-424c1626616e ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set 701412ff-d9c5-4371-bbaa-424c1626616e
    echo    'Loading Linux 2.6.35-22-generic ...'
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=701412ff-d9c5-4371-bbaa-424c1626616e ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-25-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set 701412ff-d9c5-4371-bbaa-424c1626616e
    linux    /boot/vmlinuz-2.6.32-25-generic root=UUID=701412ff-d9c5-4371-bbaa-424c1626616e ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-25-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set 701412ff-d9c5-4371-bbaa-424c1626616e
    echo    'Loading Linux 2.6.32-25-generic ...'
    linux    /boot/vmlinuz-2.6.32-25-generic root=UUID=701412ff-d9c5-4371-bbaa-424c1626616e ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.31-21-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set 701412ff-d9c5-4371-bbaa-424c1626616e
    linux    /boot/vmlinuz-2.6.31-21-generic root=UUID=701412ff-d9c5-4371-bbaa-424c1626616e ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.31-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set 701412ff-d9c5-4371-bbaa-424c1626616e
    echo    'Loading Linux 2.6.31-21-generic ...'
    linux    /boot/vmlinuz-2.6.31-21-generic root=UUID=701412ff-d9c5-4371-bbaa-424c1626616e ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.31-21-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set 701412ff-d9c5-4371-bbaa-424c1626616e
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set 701412ff-d9c5-4371-bbaa-424c1626616e
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows Vista (loader) (on /dev/sda1)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 62ea4535ea45072f
    chainloader +1
}
menuentry "Windows 7 (loader) (on /dev/sda2)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos2)'
    search --no-floppy --fs-uuid --set d86645d76645b752
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

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

=============================== sda5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda5 during installation
UUID=701412ff-d9c5-4371-bbaa-424c1626616e /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=3722e16e-85c9-4d13-b5ec-6736d9b4efa5 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda5: Location of files loaded by Grub: ===================


 182.4GB: boot/grub/core.img
 185.4GB: boot/grub/grub.cfg
 186.7GB: boot/initrd.img-2.6.31-21-generic
 188.1GB: boot/initrd.img-2.6.32-25-generic
 189.3GB: boot/initrd.img-2.6.35-22-generic
 184.3GB: boot/vmlinuz-2.6.31-21-generic
 188.1GB: boot/vmlinuz-2.6.32-25-generic
 188.5GB: boot/vmlinuz-2.6.35-22-generic
 189.3GB: initrd.img
 188.1GB: initrd.img.old
 188.5GB: vmlinuz
 188.1GB: vmlinuz.old
```

---

### Post by clint8679 on 2010-12-03
Sikander3786 - I think I have done what you asked.  Thanks for trying to help.  Very much appreciated.

---

### Post by sikander3786 on 2010-12-03
Thanks for the output of bootinfoscript :popcorn:

That output seems pretty normal to me. I would wait for some more members opinions before advising to reinstall Grub. Please hang in there.

And please reconfirm that as soon as your computer gets past the Bios screen and before getting to the Grub menu, it just restarts? Mean in a cycle of 5-10 sec, it keeps on restarting over and over again?

---

### Post by clint8679 on 2010-12-04
Hi - yes, that's exactly what is happening.

---

### Post by Quackers on 2010-12-04
When the grub menu loads make sure the correct item is highlighted and press the "e" key. Then with the down and right arrow keys navigate to the "quiet splash" and delete it, then press ctrl+x to boot.
This will scroll loads of messages during boot and it will stop where there is a problem. It may stop for a short while and then carry on. When it ultimately stops make a note of the error or maybe "recordfail" and post the details please.

---

### Post by Quackers on 2010-12-04
Sorry! Please disregard previous post. You're not getting that far!

---

### Post by Rubi1200 on 2010-12-04
The problem you are experiencing sounds as if it might be hardware related. Have you checked your settings in BIOS to make sure that everything is as it should be?

To rule out a possible problem with the upgrade, here is what you need to try:

Boot the computer with the LiveCD and run the following commands to chroot into your Ubuntu install (chroot basically means you take control of the root file system *as if* you has booted normally).

```
sudo mount /dev/sda5 /mnt && sudo mount --bind /dev /mnt/dev && sudo mount --bind /proc /mnt/proc && sudo mount --bind /sys /mnt/sys && sudo mount --bind /dev/pts /mnt/dev/pts && sudo cp /etc/resolv.conf /mnt/etc/resolv.conf && sudo chroot /mnt
```
Once you have the chroot, indicated by a root prompt in the terminal, run the following commands. Report back if there are errors:
```
apt-get autoclean
apt-get clean
apt-get update
apt-get upgrade 
apt-get dist-upgrade
apt-get -f install
dpkg --configure -a
```
When finished running the commands, exit and unmount before rebooting:
```
exit
```
```
sudo umount /mnt/dev/pts && sudo umount /mnt/sys && sudo umount /mnt/proc && sudo umount /mnt/dev && sudo umount /mnt
```
Reboot, taking out the LiveCD and let us know if you still have a problem.

Good luck!

---

### Post by clint8679 on 2010-12-05
Rubi1200 - 

Thanks for trying to help. I've done what you suggested but I'm still having the problem.

If you have any other ideas that would be great.  If not, I guess it might be a hardware problem so I will take it to be fixed.

Thanks.

---

### Post by Rubi1200 on 2010-12-05
The only other thing I can think of is to run a file-system check, but I am not sure what good it would do as this really does sound like a hardware issue from what you describe.

In any event, since it won't do any harm; from a LiveCD again, run these commands:

```
 sudo e2fsck -C0 -p -f -v /dev/sda5
```

If it reports errors, run this:

```
 sudo e2fsck -f -y -v /dev/sda5
```

Exit, reboot, taking the CD out and let me know what happens please.

---

### Post by sikander3786 on 2010-12-05
Before taking it for hardware repairing, I would suggest to re-install Grub. There are no errors in your Results.txt but who knows? And some-times, bootinfoscript can report in-correctly.

You need to do these 2 simple commands from Ubuntu Live CD and then reboot and try to boot from the HDD.

```
sudo mount /dev/sda5 /mnt
```

```
sudo grub-install --root-directory=/mnt/ /dev/sda
```

Note, for the second one it is just sda without an integer and not sda5 ;-)

---

### Post by clint8679 on 2010-12-05
Sinkander - it worked.  I reinstalled Grub as you suggested and things are now running fine.  

Thanks to everyone who offered help.  Its quite a relief that I can now use my computer.

---

### Post by sikander3786 on 2010-12-05
> **clint8679 said:**
> Sinkander - it worked.  I reinstalled Grub as you suggested and things are now running fine.  

Thanks to everyone who offered help.  Its quite a relief that I can now use my computer.
Glad to know that :-)

I thought like your MBR was just corrupt in some way and Bios wasn't able to locate Grub.

If you don't see Windows listed in your Grub menu, boot Ubuntu from your Hard disk and do this command.

```
sudo update-grub
```

And it should find Windows and add it (if not already there).

---

### Post by Rubi1200 on 2010-12-05
Huh, how about that! I am also glad you got things working again :)

Please mark this thread Solved using the Thread Tools near the top of the page.

---

