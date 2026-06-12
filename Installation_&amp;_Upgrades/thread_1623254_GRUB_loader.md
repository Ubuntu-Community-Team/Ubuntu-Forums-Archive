---
title: "GRUB loader"
date: 2010-11-16
forum: Installation &amp; Upgrades
---

### Post by Desert ZoDiaC on 2010-11-16
Hi this is my first post so hope i've done this right.

I have a laptop with windows vista installed on the internal hardrive.
Last March I installed wanted to start to use linux so I brought a separate external hardrive partitioned it to enable media storage on one section and installed ubuntu on the other half. 
It works fine and so does the windows vista on my internal hardrive, however I have to have the hardrive plugged in to boot.
Until now this hasnt bothered me, however I've recently started to take my laptop into university and cannot switch it off unless I have the external hardrive with me as I cannot switch it on without it.
With it plugged in it loads up GRUB and then gives me the option to load either Ubuntu or windows vista, however if it is not plugged in when I power up it says GRUB loader failed.
It also occured to me that if for some reason my external hardrive fails in the future I wont be able to use my laptop anymore.
Has the installation of ubuntu (and GRUB) altered the MBR?
Is there some way I can edit the settings so that I can load windows vista without the hardrive plugged in, and then if it is plugged in I get the choice which one to load?

Thanks,
Nathan

---

### Post by erikvduyn on 2010-11-16
I have a feeling you installed the bootloader to your external rather than your internal HDD, correct?

---

### Post by Rubi1200 on 2010-11-16
Hi and welcome to the forums :)

Take a look here for more information on this situation and a solution:
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Computer_does_not_boot_without_external_drive](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Computer_does_not_boot_without_external_drive)

If you have any questions, feel free to ask.

I also recommend you run the boot info script linked at the bottom of my post.

Then, post the results back here before using the guide above just so we can make sure there are no other issues involved.

Thanks.

---

### Post by Desert ZoDiaC on 2010-11-17
```

```                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks for 
    (UUID=1af6c27e-574a-410b-8bc8-61ec1f5bb61b)/boot/grub.
 => No boot loader is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /bootmgr /boot/bcd

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /boot/BCD

sdb1: _________________________________________________________________________

    File system:       ext3
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

sdb3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb4: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x6dbd397f

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   218,210,894   218,210,832   7 HPFS/NTFS
/dev/sda2         218,210,895   234,436,544    16,225,650   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00037a49

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63   157,697,702   157,697,640  83 Linux
/dev/sdb2         157,700,095   163,842,047     6,141,953   f W95 Ext d (LBA)
/dev/sdb5         157,700,096   163,842,047     6,141,952  82 Linux swap / Solaris
/dev/sdb3         163,842,048   368,642,047   204,800,000   7 HPFS/NTFS
/dev/sdb4         368,642,048   625,137,663   256,495,616   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        50A06F8FA06F7A7C                       ntfs                                     
/dev/sda2        2C88743C8874071C                       ntfs       PRESARIO_RP                   
/dev/sdb1        1af6c27e-574a-410b-8bc8-61ec1f5bb61b   ext3                                     
/dev/sdb3        E09C0EEB9C0EBC52                       ntfs       Iomega                        
/dev/sdb4        4E60DE2F60DE1D91                       ntfs       Back Up                       
/dev/sdb5        35d4f589-bbe8-4c24-8a0e-8a2f6bbb79d4   swap                                     

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sdb1        /                        ext3       (rw,errors=remount-ro)
/dev/sdb4        /media/Back Up           fuseblk    (rw,nosuid,nodev,allow_other,default_permissions,blksize=4096)
/dev/sdb3        /media/Iomega            fuseblk    (rw,nosuid,nodev,allow_other,default_permissions,blksize=4096)


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
search --no-floppy --fs-uuid --set 1af6c27e-574a-410b-8bc8-61ec1f5bb61b
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
    set root=(hd1,1)
    search --no-floppy --fs-uuid --set 1af6c27e-574a-410b-8bc8-61ec1f5bb61b
    linux    /boot/vmlinuz-2.6.31-22-generic root=UUID=1af6c27e-574a-410b-8bc8-61ec1f5bb61b ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-22-generic
}
menuentry "Ubuntu, Linux 2.6.31-22-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd1,1)
    search --no-floppy --fs-uuid --set 1af6c27e-574a-410b-8bc8-61ec1f5bb61b
    linux    /boot/vmlinuz-2.6.31-22-generic root=UUID=1af6c27e-574a-410b-8bc8-61ec1f5bb61b ro single 
    initrd    /boot/initrd.img-2.6.31-22-generic
}
menuentry "Ubuntu, Linux 2.6.31-21-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd1,1)
    search --no-floppy --fs-uuid --set 1af6c27e-574a-410b-8bc8-61ec1f5bb61b
    linux    /boot/vmlinuz-2.6.31-21-generic root=UUID=1af6c27e-574a-410b-8bc8-61ec1f5bb61b ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-21-generic
}
menuentry "Ubuntu, Linux 2.6.31-21-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd1,1)
    search --no-floppy --fs-uuid --set 1af6c27e-574a-410b-8bc8-61ec1f5bb61b
    linux    /boot/vmlinuz-2.6.31-21-generic root=UUID=1af6c27e-574a-410b-8bc8-61ec1f5bb61b ro single 
    initrd    /boot/initrd.img-2.6.31-21-generic
}
menuentry "Ubuntu, Linux 2.6.31-20-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd1,1)
    search --no-floppy --fs-uuid --set 1af6c27e-574a-410b-8bc8-61ec1f5bb61b
    linux    /boot/vmlinuz-2.6.31-20-generic root=UUID=1af6c27e-574a-410b-8bc8-61ec1f5bb61b ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-20-generic
}
menuentry "Ubuntu, Linux 2.6.31-20-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd1,1)
    search --no-floppy --fs-uuid --set 1af6c27e-574a-410b-8bc8-61ec1f5bb61b
    linux    /boot/vmlinuz-2.6.31-20-generic root=UUID=1af6c27e-574a-410b-8bc8-61ec1f5bb61b ro single 
    initrd    /boot/initrd.img-2.6.31-20-generic
}
menuentry "Ubuntu, Linux 2.6.31-19-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd1,1)
    search --no-floppy --fs-uuid --set 1af6c27e-574a-410b-8bc8-61ec1f5bb61b
    linux    /boot/vmlinuz-2.6.31-19-generic root=UUID=1af6c27e-574a-410b-8bc8-61ec1f5bb61b ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-19-generic
}
menuentry "Ubuntu, Linux 2.6.31-19-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd1,1)
    search --no-floppy --fs-uuid --set 1af6c27e-574a-410b-8bc8-61ec1f5bb61b
    linux    /boot/vmlinuz-2.6.31-19-generic root=UUID=1af6c27e-574a-410b-8bc8-61ec1f5bb61b ro single 
    initrd    /boot/initrd.img-2.6.31-19-generic
}
menuentry "Ubuntu, Linux 2.6.31-17-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd1,1)
    search --no-floppy --fs-uuid --set 1af6c27e-574a-410b-8bc8-61ec1f5bb61b
    linux    /boot/vmlinuz-2.6.31-17-generic root=UUID=1af6c27e-574a-410b-8bc8-61ec1f5bb61b ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-17-generic
}
menuentry "Ubuntu, Linux 2.6.31-17-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd1,1)
    search --no-floppy --fs-uuid --set 1af6c27e-574a-410b-8bc8-61ec1f5bb61b
    linux    /boot/vmlinuz-2.6.31-17-generic root=UUID=1af6c27e-574a-410b-8bc8-61ec1f5bb61b ro single 
    initrd    /boot/initrd.img-2.6.31-17-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd1,1)
    search --no-floppy --fs-uuid --set 1af6c27e-574a-410b-8bc8-61ec1f5bb61b
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=1af6c27e-574a-410b-8bc8-61ec1f5bb61b ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd1,1)
    search --no-floppy --fs-uuid --set 1af6c27e-574a-410b-8bc8-61ec1f5bb61b
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=1af6c27e-574a-410b-8bc8-61ec1f5bb61b ro single 
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
menuentry "Windows Vista (loader) (on /dev/sda1)" {
    insmod ntfs
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set 50a06f8fa06f7a7c
    chainloader +1
}
menuentry "Windows Vista (loader) (on /dev/sda2)" {
    insmod ntfs
    set root=(hd0,2)
    search --no-floppy --fs-uuid --set 2c88743c8874071c
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
UUID=1af6c27e-574a-410b-8bc8-61ec1f5bb61b /               ext3    errors=remount-ro 0       1
# swap was on /dev/sdb5 during installation
UUID=35d4f589-bbe8-4c24-8a0e-8a2f6bbb79d4 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sdb1: Location of files loaded by Grub: ===================


  37.0GB: boot/grub/core.img
  37.0GB: boot/grub/grub.cfg
  37.1GB: boot/initrd.img-2.6.31-14-generic
  37.2GB: boot/initrd.img-2.6.31-17-generic
  37.2GB: boot/initrd.img-2.6.31-19-generic
  37.1GB: boot/initrd.img-2.6.31-20-generic
  37.1GB: boot/initrd.img-2.6.31-21-generic
  38.7GB: boot/initrd.img-2.6.31-22-generic
  37.2GB: boot/vmlinuz-2.6.31-14-generic
  37.1GB: boot/vmlinuz-2.6.31-17-generic
  37.0GB: boot/vmlinuz-2.6.31-19-generic
  37.1GB: boot/vmlinuz-2.6.31-20-generic
  37.1GB: boot/vmlinuz-2.6.31-21-generic
  37.2GB: boot/vmlinuz-2.6.31-22-generic
  37.2GB: boot/vmlinuz-2.6.31-22-generic.dpkg-tmp
  38.7GB: initrd.img
  37.1GB: initrd.img.old
  37.2GB: vmlinuz
  37.1GB: vmlinuz.old
=======Devices which don't seem to have a corresponding hard drive==============

sdc 





----------------
Hi Rubi1200

Thanks for your reply. I've read the solution you posted and its seems to match the problem I have! =]
I've pasted the results from the script you asked me to run. I don't really understand everything it says. Is it OK to go ahead with the solution you linked?

Thanks,
Nathan

---

### Post by Rubi1200 on 2010-11-17
Hi,
thanks for posting the information.

I am assuming you are able to boot into Vista normally except for the fact that the external needs to be plugged in; correct?

As far as I can tell, the results look fairly normal.

I would go ahead and follow the instructions in the guide I originally linked to. This should then allow you to boot both drives when and how you want (will probably involve changing boot priority settings in BIOS when you want to use the external).

If you run into problems afterwards, simply re-run the script and post it back here for us to take a look.

Good luck and let us know what happens please.

---

### Post by Desert ZoDiaC on 2010-11-17
Rubi you absolute legend! :):):) 
Worked perfectly, thanks a lot.
Wish id just posted on here 6months ago rather than ignoring it for ages. Never thought it would only take 5mins to fix!

Thanks
Nathan

oh guessing I mark this as solved now?

[]("http://ubuntuforums.org/member.php?u=1040746")

---

### Post by Rubi1200 on 2010-11-17
You are more than welcome :)

I am really glad you got things sorted out.

You can mark the thread Solved using the Thread Tools near the top of the page.

Enjoy and don't forget to post questions here whenever you need help.

---

