---
title: "Windows won't start and instalation failed"
date: 2010-09-15
forum: Installation &amp; Upgrades
---

### Post by bill23 on 2010-09-15
I have a double problem here. I had a problem with ubuntu which I more or less took care of but at the loss of much information but that is neither here nor there. The problem has to do with the here and now. I purchased a ubuntu 10.04 LTS CD. I installed it and partitioned it with my win xp. All seemed to go good but the problems seem to arrive when I booted to the other partition side.

I am  able to select the windows xp side and hit  enter and and boot to xp. However when I wanted to go to the ubuntu side of things this is where the problems happens. I click enter the ubuntu selection and this error shows up.

"Windows could not start because the following file is missing or corrupt. <windows root> \system32\hal.dll
Please re-install a copy of the above file."

The only way I can of getting to the ubuntu side is by inserting the ubuntu cd into the cd/dvd drive. However when I do I get this message.

"Installation Failed.
The installer encountered an unrecoverable error. A desktop session will now run so you may investigate the problem or try installing again."

I am hoping that someone here will be able to assist me in finding an solution to my dilemma.

bill23

---

### Post by Marcelo Ruiz on 2010-09-15
Hi Bill,

Can you please provide more info about what you did? What computer do you have? How old is it? How did you partition the hard drive? Do you have the windows installation CD?
Cheers,

Marcelo

---

### Post by Rubi1200 on 2010-09-15
Are you sure this isn't a Wubi install?

See here for more details and solutions:
[https://wiki.ubuntu.com/WubiGuide#Windows%20Missing%20hal.dll](https://wiki.ubuntu.com/WubiGuide#Windows%20Missing%20hal.dll)

---

### Post by bill23 on 2010-09-15
Hello Marcelo and Rubio1200

I have a gateway profile5 and it is about six years old. I partitioned the hard drive in the usual way, at least I think it was usual, I have not done that too often. I do have the installation cd.

I did not install ubuntu using the Wubi method, I checked and I am sure.

bill23

---

### Post by Rubi1200 on 2010-09-15
Can you please boot the computer with the Ubuntu CD in live mode and post the results of the bootscript linked to at the bottom of my post.

The results should help us determine what is going on.

---

### Post by bill23 on 2010-09-15
Rubio1200,

I may have some trouble with that suggestion. As stated in my first thread. When I try and go to the ubuntu partition I have to use the ubuntu cd and it is then that I receive the message that the installation failed and that a desktop session will run and it does when I hit enter.

I can boost the computer in live mode but will not have the bootscript to ascertain any possible answers. I can try and go the semi regular route and download the bootscript but there is no guarantee that it will still be available to me if and when I boot from the ubuntu cd. 

There is another problem which I  had hoped would  be rectified if the other problems were resolved. When  I restart from ubuntu the computer does not restart with the option of selecting either ubuntu or windows xp. None of the keyboard buttons does anything to correct this dilemma. All I can do is to remove the ubuntu disc and manually shut the computer off and then turn it back on again.

If you think it will be worth the try, I can boost the computer using the ubuntu disc and see what happens.

bill23

---

### Post by wilee-nilee on 2010-09-15
The bootscript can be run from any Ubuntu environment. Get in it sounds like there is some way, and run thescript and post the results in code tags as described in my sig.

The script text output will give us a lot of valuable information about your setup, frankly without this info we are just flailing in the dark.

It sounds to me as well that your not aware of the f-key prompt to choose the boot from a menu outside of the bios. Mine is f12 it can be esc or another key. You use this key prompt to boot from a specific drive ie HD, thumb, cd/dvd reader, ...etc. Sometimes just having the CD reader first in bios just doesn't work.

---

### Post by bill23 on 2010-09-15
I got to ubuntu and downloaded bootscript. I made a copy of the 'line' then opened the terminal and pasted it there. I then received the line that there was no such file or directory.

bill23

---

### Post by wilee-nilee on 2010-09-15
> **bill23 said:**
> I got to ubuntu and downloaded bootscript. I made a copy of the 'line' then opened the terminal and pasted it there. I then received the line that there was no such file or directory.

bill23

It probably downloaded to the download folder drag it to the desktop and run this command.
```
sudo bash ~/Desktop/boot_info_script*.sh
```

Where ever it is get it on the desktop, it could be in home, your browser preferences will tell where things go.

---

### Post by bill23 on 2010-09-15
Well it worked and this is what I got.

 2010                    

============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sda2: _________________________________________________________________________

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

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   135,138,787   135,138,725   7 HPFS/NTFS
/dev/sda2         135,139,326   312,580,095   177,440,770   5 Extended
/dev/sda5         135,139,328   306,579,455   171,440,128  83 Linux
/dev/sda6         306,581,504   312,580,095     5,998,592  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        76602671602637EF                       ntfs                                     
/dev/sda2: PTTYPE="dos" 
/dev/sda5        9a560095-26d8-4a2c-85cf-11e19bf3b05d   ext4                                     
/dev/sda6        0e57c061-51c5-4580-a1fd-1800d1411d39   swap                                     
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)


================================ sda1/boot.ini: ================================

[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Home Edition" /fastdetect /NoExecute=OptIn 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Home Edition" /fastdetect 
C:\wubildr.mbr="Ubuntu"  

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
search --no-floppy --fs-uuid --set 9a560095-26d8-4a2c-85cf-11e19bf3b05d
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
search --no-floppy --fs-uuid --set 9a560095-26d8-4a2c-85cf-11e19bf3b05d
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
menuentry 'Ubuntu, with Linux 2.6.32-24-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 9a560095-26d8-4a2c-85cf-11e19bf3b05d
    linux    /boot/vmlinuz-2.6.32-24-generic root=UUID=9a560095-26d8-4a2c-85cf-11e19bf3b05d ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-24-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 9a560095-26d8-4a2c-85cf-11e19bf3b05d
    echo    'Loading Linux 2.6.32-24-generic ...'
    linux    /boot/vmlinuz-2.6.32-24-generic root=UUID=9a560095-26d8-4a2c-85cf-11e19bf3b05d ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 9a560095-26d8-4a2c-85cf-11e19bf3b05d
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=9a560095-26d8-4a2c-85cf-11e19bf3b05d ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 9a560095-26d8-4a2c-85cf-11e19bf3b05d
    echo    'Loading Linux 2.6.32-21-generic ...'
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=9a560095-26d8-4a2c-85cf-11e19bf3b05d ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 9a560095-26d8-4a2c-85cf-11e19bf3b05d
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 9a560095-26d8-4a2c-85cf-11e19bf3b05d
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows NT/2000/XP (on /dev/sda1)" {
    insmod ntfs
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 76602671602637ef
    drivemap -s (hd0) ${root}
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
UUID=9a560095-26d8-4a2c-85cf-11e19bf3b05d /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=0e57c061-51c5-4580-a1fd-1800d1411d39 none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sda5: Location of files loaded by Grub: ===================


 101.5GB: boot/grub/core.img
 144.6GB: boot/grub/grub.cfg
 101.5GB: boot/initrd.img-2.6.32-21-generic
 101.6GB: boot/initrd.img-2.6.32-24-generic
 101.5GB: boot/vmlinuz-2.6.32-21-generic
 101.5GB: boot/vmlinuz-2.6.32-24-generic
 101.6GB: initrd.img
 101.5GB: initrd.img.old
 101.5GB: vmlinuz
 101.5GB: vmlinuz.old


Hope this information will be of some help. It is to confusing to me but I am hopeful that it might lead to some answer.

---

### Post by wilee-nilee on 2010-09-15
Your script with a quick read only shows Windows in the master boot record. The windows bootloader doesn't read the Linux part how and where are you choosing Ubuntu?

To install the grub botloader here is a link and the commands from it.
[https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD](https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD)

So from a live cd run these commands reboot to Ubuntu and run 
```
sudo update-grub
```

From the live cd.
```
sudo mount /dev/sda5 /mnt
```
then
```
sudo grub-install --root-directory=/mnt/ /dev/sda
```

The reboot to Ubuntu.

---

### Post by bill23 on 2010-09-15
Well what do you know, that seems to work. Hooray!!!!

Thank all of you for coming to my aide. I really appreciate it.

bill23    ):P

---

