---
title: "Compicated grub issue"
date: 2010-02-23
forum: Installation &amp; Upgrades
---

### Post by fub4r on 2010-02-23
Hello, thx for reading.

OK I have 2 physical drives one 1TB, one 250GB.  I was using the 250GB for a dual-booting XP and Ubuntu 9.10, and the other for NTFS mass storage.  I decided to make them fully independent, so I left XP were it was and installed Ubuntu 9.10 on the 1TB. Works fine.

Now it gets complicated.  Grub still sees the Ubuntu install on the 250GB.  It's not just about changing the menu.  My desire is to just format over it with the XP, but that will make grub function wrong, It's happened to me too many times to do that again.  Editing the .cfg just sounds dangerous considering the added variables.  I have searched high and low for answers. As I said everything technically works fine, but I sure would like the added space for my XP drive, So I thought I'd give you guys this one. Thanks again.

---

### Post by darkod on 2010-02-23
Grub in the MBR is "connected" to the corresponding ubuntu root partition. It will only break if you delete the ubuntu partition where it needs to find its config files.
If you are using grub from your new ubuntu install, deleting the partitions from the old one and running update-grub is the right way to go. That will remove the older ubuntu from the menu (because it won't be able to find it any more).

If you wanna make sure you get it right, post the results of

sudo fdisk -l

and I'll take a quick look.

---

### Post by fub4r on 2010-02-23
Thx for the quick reply. Here.

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xac4d5ae1

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       17593   141315741    7  HPFS/NTFS
/dev/sda2           17594       18444     6835657+  83  Linux
/dev/sda3           18445       30401    96044602+   5  Extended
/dev/sda5           18445       18939     3976056   82  Linux swap / Solaris
/dev/sda6           18940       30401    92068483+  83  Linux

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0002a7eb

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        1216     9767488+  83  Linux
/dev/sdb2            1217      121601   966992512+   5  Extended
/dev/sdb5            1217        2432     9767488+  82  Linux swap / Solaris
/dev/sdb6            2433      121601   957224961   83  Linux

I have had many headaches with grub, so I am wary of even simple changes in it.

---

### Post by darkod on 2010-02-23
Because both sdb1 and sdb6 are linux partitions, in order to make sure I get it right, please boot your 1TB ubuntu and also post the results of:

```
df -h
```

---

### Post by darkod on 2010-02-23
Sorry, there is much simpler way, just remembered. Because you can boot your newer ubuntu, the one from the 1TB disk, just boot it and do:

sudo grub-install /dev/sdb

That will install grub from the newer install on the MBR of /dev/sdb, just in case. After that, as long as you boot from the 1TB disk, you will boot that correct grub.

---

### Post by oldfred on 2010-02-23
I like to have the boot loader for each system in the MBR of the drive the system is installed. I then make Ubuntu drive the first boot in BIOS since it will see windows and set up boot for windows.

I also just found out from meierfra about boot flag and BIOS.

Some bios refuse to boot a hard drive without a boot flag. Although linux does not need one.
More precisely: Some Bios require a boot flag on a primary partition.
So it is not important that the first partition has the boot flag, but that one of the first four partitions has a boot flag.

set boot flag (Active flag) on for sdb1 (off on others)
sudo sfdisk -A1 /dev/sdb

---

### Post by fub4r on 2010-02-25
Thanks for the quick replys
sorry for the late response, been busy

Anyway, these are all valid bits of advice, but not what I am looking for.
I am wanting to take sda1 and make it the only partition on the 250GB, formating over the old linux. The sdb is fine.  Now. in my experience simply formating over partitions on any disk, and restarting to grub, makes grub freeze with an error messege before any viable boot process can be executed, causing me to get very frustrated and start the long tedious process of reinstalling OS's back to the way they where.  The working grub is in the /boot of sdb.
I guess this is a rare problem because I can't find anything considering this particular issue, though I have encountered it many times.  I would reinstall XP over all of sda but that would mean reinstalling Ubuntu for as we all know Windows is a picky snob of OS's and will only boot if ntldr is at the very beginning of the boot sector.  I think it might take some real editing of grub files and/or configs. But I can't even find help in the grub manual.  I have backups and everything. But I gotta learn about grub sometime.  I'm studying for linux certifications.

Thx again.  Any input is appreciated.

---

### Post by oldfred on 2010-02-25
If you are sure the 1000GB is the MBR that is used to boot and just want to modify the 250GB drive you should be just able to delete the extra partitions and expand the windows partition. I still am not sure you can boot sdb directly without a boot flag somewhere. BIOS controls which drive is used to boot.

If not sure you can always run this script to tell where the entire boot process is (same as the one in Darko's signature):

Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Be sure to highlight and use code tags (#) to make it easier to read when you post the results.txt.

---

### Post by darkod on 2010-02-25
> **fub4r said:**
> Thanks for the quick replys
sorry for the late response, been busy

Anyway, these are all valid bits of advice, but not what I am looking for.
I am wanting to take sda1 and make it the only partition on the 250GB, formating over the old linux. The sdb is fine.  Now. in my experience simply formating over partitions on any disk, and restarting to grub, makes grub freeze with an error messege before any viable boot process can be executed, causing me to get very frustrated and start the long tedious process of reinstalling OS's back to the way they where.  The working grub is in the /boot of sdb.
I guess this is a rare problem because I can't find anything considering this particular issue, though I have encountered it many times.  I would reinstall XP over all of sda but that would mean reinstalling Ubuntu for as we all know Windows is a picky snob of OS's and will only boot if ntldr is at the very beginning of the boot sector.  I think it might take some real editing of grub files and/or configs. But I can't even find help in the grub manual.  I have backups and everything. But I gotta learn about grub sometime.  I'm studying for linux certifications.

Thx again.  Any input is appreciated.

I understand what you want to do with sda, but I just wanted to make sure you are running grub2 from /dev/sdb which is from the sdb ubuntu install.
Formatting a partition will not automatically make grub freeze, only if you actually format the linux partition that was hosting its config files. In that case, of course it can't run correctly.

Another option is to boot your new ubuntu that is on /dev/sdb and just execute:

grub-install /dev/sdb

That will make sure you put grub2 on the MBR of /dev/sdb. After that deleting all linux partitions from sda doesn't matter. Of course, you will lose the data on them but you said you have it backed up.
And you will only need to run

sudo update-grub

in ubuntu again after deleting the partitions on /dev/sda in order a new grub.cfg file to be created which will not include the ubuntu that was on /dev/sda.

---

### Post by fub4r on 2010-02-25
Very interesting script...

sdb indeed had grub legacy for some reason. after grub-install and update I have this.

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks for 
    (UUID=df9458a0-97ac-43f0-80a1-7a4ba2cb1de0)/boot/grub.
 => Grub 2 is installed in the MBR of /dev/sdb and looks on the same drive in 
    partition #1 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sda2: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda6: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb6: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xac4d5ae1

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   282,631,544   282,631,482   7 HPFS/NTFS
/dev/sda2         282,631,545   296,302,859    13,671,315  83 Linux
/dev/sda3         296,302,860   488,392,064   192,089,205   5 Extended
/dev/sda5         296,302,923   304,255,034     7,952,112  82 Linux swap / Solaris
/dev/sda6         304,255,098   488,392,064   184,136,967  83 Linux


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x0002a7eb

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63    19,535,039    19,534,977  83 Linux
/dev/sdb2          19,535,040 1,953,520,064 1,933,985,025   5 Extended
/dev/sdb5          19,535,103    39,070,079    19,534,977  82 Linux swap / Solaris
/dev/sdb6          39,070,143 1,953,520,064 1,914,449,922  83 Linux


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        BE7451BD7451795B                       ntfs                                     
/dev/sda2        18c2f713-16fb-41ed-822a-22bf0042e7f6   ext4                                     
/dev/sda5                                               swap                                     
/dev/sda6        0ac46d75-f1be-4b3c-803f-304b3cc1e896   ext4                                     
/dev/sdb1        df9458a0-97ac-43f0-80a1-7a4ba2cb1de0   ext4                                     
/dev/sdb5        2c33a6b5-4394-47b5-8c7d-7711d0414fe3   swap                                     
/dev/sdb6        b008e7fe-c048-4ae5-a4f8-5744317415b3   ext4                                     

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sdb1        /                        ext4       (rw,errors=remount-ro)
/dev/sdb6        /home                    ext4       (rw)


================================ sda1/boot.ini: ================================

[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /fastdetect /noexecute=optin 

=========================== sda2/boot/grub/grub.cfg: ===========================

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
set root=(hd0,2)
search --no-floppy --fs-uuid --set 18c2f713-16fb-41ed-822a-22bf0042e7f6
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
menuentry "Ubuntu, Linux 2.6.31-20-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd0,2)
    search --no-floppy --fs-uuid --set 18c2f713-16fb-41ed-822a-22bf0042e7f6
    linux    /boot/vmlinuz-2.6.31-20-generic root=UUID=18c2f713-16fb-41ed-822a-22bf0042e7f6 ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-20-generic
}
menuentry "Ubuntu, Linux 2.6.31-20-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd0,2)
    search --no-floppy --fs-uuid --set 18c2f713-16fb-41ed-822a-22bf0042e7f6
    linux    /boot/vmlinuz-2.6.31-20-generic root=UUID=18c2f713-16fb-41ed-822a-22bf0042e7f6 ro single 
    initrd    /boot/initrd.img-2.6.31-20-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd0,2)
    search --no-floppy --fs-uuid --set 18c2f713-16fb-41ed-822a-22bf0042e7f6
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=18c2f713-16fb-41ed-822a-22bf0042e7f6 ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd0,2)
    search --no-floppy --fs-uuid --set 18c2f713-16fb-41ed-822a-22bf0042e7f6
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=18c2f713-16fb-41ed-822a-22bf0042e7f6 ro single 
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
menuentry "Microsoft Windows XP Professional (on /dev/sda1)" {
    insmod ntfs
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set be7451bd7451795b
    drivemap -s (hd0) ${root}
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sda2/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda2 during installation
UUID=18c2f713-16fb-41ed-822a-22bf0042e7f6 /               ext4    errors=remount-ro 0       1
# /home was on /dev/sda6 during installation
UUID=0ac46d75-f1be-4b3c-803f-304b3cc1e896 /home           ext4    defaults        0       2
/dev/sda5       none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda2: Location of files loaded by Grub: ===================


 147.8GB: boot/grub/core.img
 148.2GB: boot/grub/grub.cfg
 148.1GB: boot/initrd.img-2.6.31-14-generic
 149.6GB: boot/initrd.img-2.6.31-20-generic
 147.2GB: boot/vmlinuz-2.6.31-14-generic
 149.2GB: boot/vmlinuz-2.6.31-20-generic
 149.6GB: initrd.img
 148.1GB: initrd.img.old
 149.2GB: vmlinuz
 147.2GB: vmlinuz.old

=========================== sdb1/boot/grub/grub.cfg: ===========================

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
set root=(hd1,1)
search --no-floppy --fs-uuid --set df9458a0-97ac-43f0-80a1-7a4ba2cb1de0
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
menuentry "Ubuntu, Linux 2.6.31-20-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd1,1)
    search --no-floppy --fs-uuid --set df9458a0-97ac-43f0-80a1-7a4ba2cb1de0
    linux    /boot/vmlinuz-2.6.31-20-generic root=UUID=df9458a0-97ac-43f0-80a1-7a4ba2cb1de0 ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-20-generic
}
menuentry "Ubuntu, Linux 2.6.31-20-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd1,1)
    search --no-floppy --fs-uuid --set df9458a0-97ac-43f0-80a1-7a4ba2cb1de0
    linux    /boot/vmlinuz-2.6.31-20-generic root=UUID=df9458a0-97ac-43f0-80a1-7a4ba2cb1de0 ro single 
    initrd    /boot/initrd.img-2.6.31-20-generic
}
menuentry "Ubuntu, Linux 2.6.31-19-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd1,1)
    search --no-floppy --fs-uuid --set df9458a0-97ac-43f0-80a1-7a4ba2cb1de0
    linux    /boot/vmlinuz-2.6.31-19-generic root=UUID=df9458a0-97ac-43f0-80a1-7a4ba2cb1de0 ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-19-generic
}
menuentry "Ubuntu, Linux 2.6.31-19-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd1,1)
    search --no-floppy --fs-uuid --set df9458a0-97ac-43f0-80a1-7a4ba2cb1de0
    linux    /boot/vmlinuz-2.6.31-19-generic root=UUID=df9458a0-97ac-43f0-80a1-7a4ba2cb1de0 ro single 
    initrd    /boot/initrd.img-2.6.31-19-generic
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
menuentry "Microsoft Windows XP Professional (on /dev/sda1)" {
    insmod ntfs
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set be7451bd7451795b
    drivemap -s (hd0) ${root}
    chainloader +1
}
menuentry "Ubuntu, Linux 2.6.31-20-generic (on /dev/sda2)" {
    insmod ext2
    set root=(hd0,2)
    search --no-floppy --fs-uuid --set 18c2f713-16fb-41ed-822a-22bf0042e7f6
    linux /boot/vmlinuz-2.6.31-20-generic root=UUID=18c2f713-16fb-41ed-822a-22bf0042e7f6 ro quiet splash
    initrd /boot/initrd.img-2.6.31-20-generic
}
menuentry "Ubuntu, Linux 2.6.31-20-generic (recovery mode) (on /dev/sda2)" {
    insmod ext2
    set root=(hd0,2)
    search --no-floppy --fs-uuid --set 18c2f713-16fb-41ed-822a-22bf0042e7f6
    linux /boot/vmlinuz-2.6.31-20-generic root=UUID=18c2f713-16fb-41ed-822a-22bf0042e7f6 ro single
    initrd /boot/initrd.img-2.6.31-20-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (on /dev/sda2)" {
    insmod ext2
    set root=(hd0,2)
    search --no-floppy --fs-uuid --set 18c2f713-16fb-41ed-822a-22bf0042e7f6
    linux /boot/vmlinuz-2.6.31-14-generic root=UUID=18c2f713-16fb-41ed-822a-22bf0042e7f6 ro quiet splash
    initrd /boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode) (on /dev/sda2)" {
    insmod ext2
    set root=(hd0,2)
    search --no-floppy --fs-uuid --set 18c2f713-16fb-41ed-822a-22bf0042e7f6
    linux /boot/vmlinuz-2.6.31-14-generic root=UUID=18c2f713-16fb-41ed-822a-22bf0042e7f6 ro single
    initrd /boot/initrd.img-2.6.31-14-generic
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
UUID=df9458a0-97ac-43f0-80a1-7a4ba2cb1de0 /               ext4    errors=remount-ro 0       1
# /home was on /dev/sdb6 during installation
UUID=b008e7fe-c048-4ae5-a4f8-5744317415b3 /home           ext4    defaults        0       2
/dev/sda5       none            swap    sw              0       0
# swap was on /dev/sdb5 during installation
UUID=2c33a6b5-4394-47b5-8c7d-7711d0414fe3 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sdb1: Location of files loaded by Grub: ===================


    .1GB: boot/grub/core.img
   3.7GB: boot/grub/grub.cfg
   3.2GB: boot/initrd.img-2.6.31-19-generic
   5.0GB: boot/initrd.img-2.6.31-20-generic
   2.7GB: boot/vmlinuz-2.6.31-19-generic
   4.9GB: boot/vmlinuz-2.6.31-20-generic
   5.0GB: initrd.img
   3.2GB: initrd.img.old
   4.9GB: vmlinuz
   2.7GB: vmlinuz.old
```I think you're right. It looks good. What do you people think?
Thanks

---

### Post by darkod on 2010-02-25
I think you can delete the linux partitions on /dev/sda when ever you like now. This is what you wanted to see:

Grub 2 is installed in the MBR of /dev/sdb and looks on the same drive in 
    partition #1 for /boot/grub.

As long as you boot from /dev/sdb it doesn't care what you do with the linux partitions on sda. After you delete them boot ubuntu and do sudo update-grub to figure out the other ubuntu is gone.

Also, I would put windows mbr on /dev/sda, since you will have windows only on that disk anyway. You could do this easily from within ubuntu:

sudo apt-get install lilo
sudo lilo -M /dev/sda mbr

Ignore the warnings. That will install generic mbr on /dev/sda which boots the partition with the boot flag, in this case /dev/sda1, the XP partition.

---

### Post by fub4r on 2010-02-26
OK, so I'm with you for the first half of your statement, but could you elaborate on how installing lilo can restore the Windows MBR? Granted I don't think a MS recovery disk is the correct option.  But 2 boot programs in the same boot config?
I mean I'm staring at your operations and it looks like they make sense, I've just never heard of that before. What's the -M switch?

Thank you so much.

---

### Post by darkod on 2010-02-27
These exact command don't actually install the full lilo bootloader, it just looks like that. It puts a generic mbr on your hdd MBR which continues booting the partition with the boot flag. As long as your windows system partition has the boot flag, which is the usual way, it will continue loading windows.

And your windows partition has the boot flag, notice the * mark next to /dev/sda1 in the script results. So it should work out fine.

---

### Post by kansasnoob on 2010-02-27
I see no reason to change the mbr of any drive. If you look:

```
 => Grub 2 is installed in the MBR of /dev/sda and looks for 
    (UUID=**df9458a0-97ac-43f0-80a1-7a4ba2cb1de0**)/boot/grub.
 => Grub 2 is installed in the MBR of /dev/sdb and looks on the same drive in 
    partition #1 for /boot/grub.

```

That UUID is the UUID of the new Karmic:

```
blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        BE7451BD7451795B                       ntfs                                     
/dev/sda2        18c2f713-16fb-41ed-822a-22bf0042e7f6   ext4                                     
/dev/sda5                                               swap                                     
/dev/sda6        0ac46d75-f1be-4b3c-803f-304b3cc1e896   ext4                                     
/dev/sdb1        **df9458a0-97ac-43f0-80a1-7a4ba2cb1de0**   ext4                                     
/dev/sdb5        2c33a6b5-4394-47b5-8c7d-7711d0414fe3   swap                                     
/dev/sdb6        b008e7fe-c048-4ae5-a4f8-5744317415b3   ext4                
```

So if the BIOS is now set to boot sda first changing it's mbr will just open a can of worms that need not be opened.

---

### Post by meierfra. on 2010-02-27
[QUOTE=kansasnoob]I see no reason to change the mbr of any drive.[/QUOTE]

From the first post:

[QUOTE=fub4r]I decided to make them fully independent, [/QUOTE]

To have the drives fully independent, the mbr of /dev/sda needs to be changed. Otherwise, it will not be possible to boot  Windows if  /dev/sdb or Ubuntu gets corrupted for some reason.  So I support darkrod's advice to install a lilo MBR.


But I would recommend to make sure that you can boot into Ubuntu and XP  from /dev/sdb before changing  the MBR of /dev/sda:
Set your bios to boot  from  the Ubuntu drive and see whether you can boot into Ubuntu and Windows XP.

---

### Post by fub4r on 2010-03-08
It boots from sdb flawlessly.

So do I install the lilo mbr before or after deleting ubuntu on sda?

Also, 
> As long as you boot from /dev/sdb it doesn't care what you do with the linux partitions on sda. After you delete them boot ubuntu and do sudo update-grub to figure out the other ubuntu is gone.I thought this to be true before, though it has always happened to me that grub does in fact care very much about all partitions as it will stall with 'GRUB error [##]' if grub's config tries to detect a non existent partition.  Unless I can update sdb from a live disc maybe?  This has always been the very frustrating case with me, which is why I am so hesitant to follow all of your seemingly quite correct advice.  Has this happened to anyone else?  

Thanks again, I shouldn't be so busy this week.

---

### Post by fub4r on 2010-03-16
Thanks so much.  Worked like a charm.  I finally got over my fear of grub!

---

