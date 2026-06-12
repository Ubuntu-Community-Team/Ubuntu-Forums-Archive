---
title: "Re-do dual boot part 2"
date: 2010-06-05
forum: Installation &amp; Upgrades
---

### Post by TXbirder on 2010-06-05
[FONT=Microsoft Sans Serif]I have had problems starting up Win7 on my computer.  I have two hard drives with Win7 on one and Ubuntu on the other.  Since repairing the startup problems with Win7, when I start the computer I no longer get the screen that has me chose to start Win7 or Ubuntu.  Win7 starts automatically.  
How do I recover the option screen? Reinstall Ubuntu?  I don't remember how to install Ubuntu on its own hard drive.  I did it a couple of months ago when the computer was new but I don't remember the details.
John

[/FONT]

---

### Post by kansasnoob on 2010-06-05
You don't need to reinstall Ubuntu! Please post the output of the Boot Info Script as described here:

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

Then we should be able to tell you how to recover grub :)

---

### Post by TXbirder on 2010-06-05
OK.  Sorry.  I had forgotten about that.  But I have been reading the instructions and they begin with "Boot into any Linux based operating system..." which  I haven't been able to do on the desktop in question.
John

---

### Post by oldfred on 2010-06-05
Just use the Ubuntu liveCD.

---

### Post by TXbirder on 2010-06-05
Sorry this is taking so long.

Downloaded the infoscript.  Found it in **Downloads** and opened it to make sure it was there.  OK.
Opened **Terminal** and typed in sudo entries.  Tried 'em all.  Response is always "No such file or directory.  Tried 3-4 times.

Closed **Downloads** and **Terminal **and reopened them.  Tried twice again and got same negative results.

I will delete bootinfoscript and try again.
John

---

### Post by darkod on 2010-06-05
Linux makes difference between small and capital letters, so you need to type it exactly as the folder name where it is. For example if it's in Downloads it would be in terminal:

sudo bash ~/Downloads/boot_info_script*.sh

---

### Post by TXbirder on 2010-06-08
I'm still trying.  Downloaded again.  In LiveCD I have 2 icons in the upper left of the screen:  Examples and Install Ubuntu 9.10.  When ask what to use to open the downloaded file I have a choice( on the Desktop) of **examples.desktop **or **ubiquity-gtkui.desktop**.
It seems I am not able to open it with just plain **Desktop**.

I have tried to open the script using these entries and have failed.
#
ubuntu@ubuntu:~$ sudo bash ~/examples.desktop/boot_info_script*.sh
bash: /home/ubuntu/examples.desktop/boot_info_script*.sh: No such file or directory
ubuntu@ubuntu:~$ sudo bash ~/examples.Desktop/boot_info_script*.sh
bash: /home/ubuntu/examples.Desktop/boot_info_script*.sh: No such file or directory
ubuntu@ubuntu:~$ sudo bash ~/Desktop/boot_info_script*.sh
bash: /home/ubuntu/Desktop/boot_info_script*.sh: No such file or directory
ubuntu@ubuntu:~$ 
ubuntu@ubuntu:~$ sudo bash ~/Desktop/boot_info_script*.sh
bash: /home/ubuntu/Desktop/boot_info_script*.sh: No such file or directory
ubuntu@ubuntu:~$ sudo bash ~/ubiquity-gtkui.desktop/boot_info_script*.sh
bash: /home/ubuntu/ubiquity-gtkui.desktop/boot_info_script*.sh: No such file or directory
ubuntu@ubuntu:~$ 
#

Apparently just plain** Desktop** is not available.  If I can't use Desktop, what is another means of opening the script?

I have a CD from another source.  I'll try it.  

John

---

### Post by darkod on 2010-06-08
If you can't see the script on the desktop, that means it didn't download there. It's a file, you would see it just like any file you places on the desktop. Check in Places-Downloads. If it's in the downloads folder, don't try to click or open the script file anyhow. Just confirm it's there.

Then open terminal and do:

sudo bash ~/Downloads/boot_info_script*.sh

The resulting results.txt file will also be created in the downloads folder, in the same folder where the script file is.

PS. Live mode from cd doesn't remember downloaded files. You can't expect to find it now. Boot in live mode, download it again, check to confirm it's in the downloads folder and do as above.

---

### Post by TXbirder on 2010-06-08
Hard to believe but I think I finally got it:
```

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda
 => Windows is installed in the MBR of /dev/sdb

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
    Boot files/dirs:   /Windows/System32/winload.exe /wubildr.mbr /wubildr

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /ubuntu/winboot/wubildr.mbr /ubuntu/winboot/wubildr 
                       /ubuntu/disks/root.disk /ubuntu/disks/swap.disk

sdb1/Wubi: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xfd8f14fe

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048       206,847       204,800   7 HPFS/NTFS
/dev/sda2             206,848   625,139,711   624,932,864   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xcf3e014e

Partition  Boot         Start           End          Size  Id System

/dev/sdb1               2,048   625,139,711   625,137,664   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/loop1       70df55c3-e365-4612-80c6-96bdca2720b5   ext4                                     
/dev/sda1        FC00B02C00AFEC38                       ntfs       System Reserved               
/dev/sda2        8632B22432B2195F                       ntfs                                     
/dev/sdb1        187E99427E991A18                       ntfs       New Volume                    

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (rw)
/dev/loop0       /rofs                    squashfs   (rw)


======================== sdb1/Wubi/boot/grub/grub.cfg: ========================

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
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/10_lupin ###
menuentry "Ubuntu, Linux 2.6.31-21-generic" {
    insmod ntfs
    set root=(hd1,1)
    search --no-floppy --fs-uuid --set 187e99427e991a18
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    linux /boot/vmlinuz-2.6.31-21-generic root=/dev/sdb1 loop=/ubuntu/disks/root.disk ro   quiet splash
    initrd /boot/initrd.img-2.6.31-21-generic
}
menuentry "Ubuntu, Linux 2.6.31-21-generic (recovery mode)" {
    insmod ntfs
    set root=(hd1,1)
    search --no-floppy --fs-uuid --set 187e99427e991a18
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    linux /boot/vmlinuz-2.6.31-21-generic root=/dev/sdb1 loop=/ubuntu/disks/root.disk ro single 
    initrd /boot/initrd.img-2.6.31-21-generic
}
menuentry "Ubuntu, Linux 2.6.31-20-generic" {
    insmod ntfs
    set root=(hd1,1)
    search --no-floppy --fs-uuid --set 187e99427e991a18
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    linux /boot/vmlinuz-2.6.31-20-generic root=/dev/sdb1 loop=/ubuntu/disks/root.disk ro   quiet splash
    initrd /boot/initrd.img-2.6.31-20-generic
}
menuentry "Ubuntu, Linux 2.6.31-20-generic (recovery mode)" {
    insmod ntfs
    set root=(hd1,1)
    search --no-floppy --fs-uuid --set 187e99427e991a18
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    linux /boot/vmlinuz-2.6.31-20-generic root=/dev/sdb1 loop=/ubuntu/disks/root.disk ro single 
    initrd /boot/initrd.img-2.6.31-20-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic" {
    insmod ntfs
    set root=(hd1,1)
    search --no-floppy --fs-uuid --set 187e99427e991a18
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    linux /boot/vmlinuz-2.6.31-14-generic root=/dev/sdb1 loop=/ubuntu/disks/root.disk ro   quiet splash
    initrd /boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
    insmod ntfs
    set root=(hd1,1)
    search --no-floppy --fs-uuid --set 187e99427e991a18
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    linux /boot/vmlinuz-2.6.31-14-generic root=/dev/sdb1 loop=/ubuntu/disks/root.disk ro single 
    initrd /boot/initrd.img-2.6.31-14-generic
}
### END /etc/grub.d/10_lupin ###

### BEGIN /etc/grub.d/20_memtest86+ ###
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" {
    insmod ntfs
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set fc00b02c00afec38
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

============================= sdb1/Wubi/etc/fstab: =============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/host/ubuntu/disks/root.disk /               ext4    loop,errors=remount-ro 0       1
/host/ubuntu/disks/swap.disk none            swap    loop,sw         0       0

================= sdb1/Wubi: Location of files loaded by Grub: =================


   3.4GB: boot/grub/grub.cfg
   2.0GB: boot/initrd.img-2.6.31-14-generic
   3.9GB: boot/initrd.img-2.6.31-20-generic
   5.0GB: boot/initrd.img-2.6.31-21-generic
   1.8GB: boot/vmlinuz-2.6.31-14-generic
   3.5GB: boot/vmlinuz-2.6.31-20-generic
   5.1GB: boot/vmlinuz-2.6.31-21-generic
   5.0GB: initrd.img
   3.9GB: initrd.img.old
   5.1GB: vmlinuz
   3.5GB: vmlinuz.old```

```

John

---

### Post by oldfred on 2010-06-08
You have wubi installed in the NTFS partition on you second drive.

If your Vista does not show wubi as a choice you will have to use BCDedit to add an entry:

[http://ubuntuforums.org/showthread.php?t=1198406](http://ubuntuforums.org/showthread.php?t=1198406)
[http://ubuntuforums.org/showthread.php?t=1483368](http://ubuntuforums.org/showthread.php?t=1483368)

[http://www.sevenforums.com/tutorials/2676-bcdedit-how-use.html](http://www.sevenforums.com/tutorials/2676-bcdedit-how-use.html)

---

### Post by Zeppfan on 2010-06-08
> **darkod said:**
> If you can't see the script on the desktop, that means it didn't download there. It's a file, you would see it just like any file you places on the desktop. Check in Places-Downloads. If it's in the downloads folder, don't try to click or open the script file anyhow. Just confirm it's there.

Then open terminal and do:

sudo bash ~/Downloads/boot_info_script*.sh

The resulting results.txt file will also be created in the downloads folder, in the same folder where the script file is.

PS. Live mode from cd doesn't remember downloaded files. You can't expect to find it now. Boot in live mode, download it again, check to confirm it's in the downloads folder and do as above.

I tried this and got the same message:

patrick@patrick-desktop:~$ sudo bash ~/Downloads/boot_info_script0.55.sh
[sudo] password for patrick: 
bash: /home/patrick/Downloads/boot_info_script0.55.sh: No such file or directory
patrick@patrick-desktop:~$ 

I'm trying to dual boot 2 HDDs...1 with Ubuntu, 1 with Win XP. I can boot directly into Ubuntu, but I don't even get the choice of booting into XP...it just goes straight into Ubuntu.

I know it's there...I'm looking right at it!!! HELP PLEASE!

Thanks in advance.

---

### Post by darkod on 2010-06-08
> **Zeppfan said:**
> I tried this and got the same message:

patrick@patrick-desktop:~$ sudo bash ~/Downloads/boot_info_script[COLOR=Red]0.55[/COLOR].sh
[sudo] password for patrick: 
bash: /home/patrick/Downloads/boot_info_script0.55.sh: No such file or directory
patrick@patrick-desktop:~$ 

I know it's there...I'm looking right at it!!! HELP PLEASE!

Thanks in advance.

That's why in the instructions I use a * to replace the script version in the filename. It's 055 not 0.55.
You typed the filename wrong.

PS. In your case if you don't have a choice about XP, did you unplug the XP disk during ubuntu install? If yes, just run in terminal:

sudo update-grub

and it should sort it out.

---

### Post by Zeppfan on 2010-06-08
> **darkod said:**
> That's why in the instructions I use a * to replace the script version in the filename. It's 055 not 0.55.
You typed the filename wrong.

PS. In your case if you don't have a choice about XP, did you unplug the XP disk during ubuntu install? If yes, just run in terminal:

sudo update-grub

and it should sort it out.

OK, here are my results:

                Boot Info Script 0.55    dated February 15th, 2010                    

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
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x5c7fb438

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   224,829,674   224,829,612  83 Linux
/dev/sda2         224,829,675   234,436,544     9,606,870   5 Extended
/dev/sda5         224,829,738   234,436,544     9,606,807  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 60.1 GB, 60060155904 bytes
255 heads, 63 sectors/track, 7301 cylinders, total 117304992 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xf08af08a

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63   117,274,499   117,274,437   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        94d8ebaa-173c-4e5c-bd59-5479c426afd2   ext4                                     
/dev/sda5        d5e193ae-83e8-4f24-aa08-866ba4ba2a2f   swap                                     
/dev/sdb1        94DC82ADDC8288E6                       ntfs                                     

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
search --no-floppy --fs-uuid --set 94d8ebaa-173c-4e5c-bd59-5479c426afd2
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
menuentry "Ubuntu, Linux 2.6.31-22-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set 94d8ebaa-173c-4e5c-bd59-5479c426afd2
    linux    /boot/vmlinuz-2.6.31-22-generic root=UUID=94d8ebaa-173c-4e5c-bd59-5479c426afd2 ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-22-generic
}
menuentry "Ubuntu, Linux 2.6.31-22-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set 94d8ebaa-173c-4e5c-bd59-5479c426afd2
    linux    /boot/vmlinuz-2.6.31-22-generic root=UUID=94d8ebaa-173c-4e5c-bd59-5479c426afd2 ro single 
    initrd    /boot/initrd.img-2.6.31-22-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set 94d8ebaa-173c-4e5c-bd59-5479c426afd2
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=94d8ebaa-173c-4e5c-bd59-5479c426afd2 ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set 94d8ebaa-173c-4e5c-bd59-5479c426afd2
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=94d8ebaa-173c-4e5c-bd59-5479c426afd2 ro single 
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
proc            /proc           proc    defaults        0       0
# / was on /dev/sda1 during installation
UUID=94d8ebaa-173c-4e5c-bd59-5479c426afd2 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=d5e193ae-83e8-4f24-aa08-866ba4ba2a2f none            swap    sw              0       0
/dev/scd1       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda1: Location of files loaded by Grub: ===================


   3.9GB: boot/grub/core.img
   3.3GB: boot/grub/grub.cfg
    .5GB: boot/initrd.img-2.6.31-14-generic
   1.0GB: boot/initrd.img-2.6.31-22-generic
    .5GB: boot/vmlinuz-2.6.31-14-generic
    .8GB: boot/vmlinuz-2.6.31-22-generic
   1.0GB: initrd.img
    .5GB: initrd.img.old
    .8GB: vmlinuz
    .5GB: vmlinuz.old

So now my question is, how can I get it to boot XP? I am in the process of doing update-grub but it stalls...is this normal? How long could that take.

Thanks for the info.

PS. When I installed Karmic, The XP HDD was plugged in. fdisk does recognize it.

---

### Post by darkod on 2010-06-08
sdb1: __________________________________________________   _______________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    [COLOR=Red]Boot files/dirs:[/COLOR]

I don't know how it happened but the XP boot files are missing.

Go into BIOS and temporarily set the 60GB disk to be first in hdd boot options. This is necessary before recovery of windows boot files so they don't go to the wrong disk. But boot with your XP install cd and open Recovery Console. In there run:

fixboot
fixmbr

or maybe it was (can't remember exactly now):

fixboot c:
fixmbr

Restart and see if XP boots fine. If it does, reboot to go into BIOS and set the 120GB disk, your ubuntu disk, as first option again. Once ubuntu loads run the mentioned update-grub and it should locate the XP boot files and make entry for XP in the grub menu.

---

### Post by Zeppfan on 2010-06-08
OK. I tried fixboot and it said it was fixed. Tried to run fixmbr and it just gave me the command prompt...so I booted into Karmic and ran sudo update-grub. It shows:

Found linux image: /boot/vmlinuz-2.6.31-22-generic
Found initrd image: /boot/initrd.img-2.6.31-22-generic
Found linux image: /boot/vmlinuz-2.6.31-14-generic
Found initrd image: /boot/initrd.img-2.6.31-14-generic

Then, a flashing cursor on the next line. What's up with that?

Thanks for all of your help so far.

---

### Post by Zeppfan on 2010-06-08
Anyone else have any ideas?

---

### Post by oldfred on 2010-06-09
Zeppfan - you hijacked TXbirder's thread, these commands do not help him. Only if you problem is identical to his should you be in this thread.

COPY [CDDRIVE]:\I386\NTLDR  C:\
COPY [CDDRIVE]:\I386\NTDETECT.COM  C:\
or:
Can you boot into Ubuntu? If so you can mount your Windows drive and navigate to C:\windows\ServicePackFiles\i386 folder and copy
ntdetect.com and ntldr to root of C:\.

---

