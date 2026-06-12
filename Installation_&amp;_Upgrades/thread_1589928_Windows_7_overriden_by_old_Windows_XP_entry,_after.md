---
title: "Windows 7 overriden by old Windows XP entry, after reinstall grub"
date: 2010-10-07
forum: Installation &amp; Upgrades
---

### Post by balaji_r_s on 2010-10-07
Hi All,

  I am actually facing a vague problem here.  I was previously running Windows XP and Ubuntu . Ubuntu was installed Windows XP

 The problem is 

1. First I tried to do some disk partitioning. That ended up with some error.

2. Ignoring that, I went to install Windows 7 over Windows XP but I was not able to proceed with Windows 7 , because the partitions were corrupted.

3. So I used Ubuntu LIVE CD (Grub was lost at this point )and used 'testdisk' and recovered the partitions.

4. Now installed the Windows 7 successfully. 

5. Now again I moved to Ubuntu Live CD to write the GRUB. After which I tried restarting

6. Now Ubuntu is booting perfectly as before. But the problem is with Windows

7. The GRUB loader instead of showing Windows 7, it shows Windows XP !!! . and there is no other entry for windows. When I tried opening it, it says "error, cant read file"  and  further inout moves back to the grub loader list again.

Now my question is, "How do I change the entry to Windows 7 from Windows XP and boot Windows7 successfully "

I tried it a couple of times, same thing happens . So how to change the entry ?

Any help in this regard would be most helpful !!!!

---

### Post by lechien73 on 2010-10-07
Hello & welcome to the forums.

Could you download and run the Boot Info Script from here: [http://bootinfoscript.sourceforge.net](http://bootinfoscript.sourceforge.net)

When you have generated the results.txt file, please post the contents here surrounded by [CODE] tags (the # button on the toolbar above).

That should give us a better idea of what's going on with your hard disk setup.

---

### Post by balaji_r_s on 2010-10-07
Thanks Leichien73 for the detailed reply. Here is the result :
```

                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #6 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  According to the info in the boot sector, sda1 starts 
                       at sector 63. But according to the info from fdisk, 
                       sda1 starts at sector 16128.
    Operating System:  
    Boot files/dirs:   

sda2: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  MSWIN4.1: Fat 32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe

sda4: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda6: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda7: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x49134912

Partition  Boot         Start           End          Size  Id System

/dev/sda1              16,128    41,865,389    41,849,262   7 HPFS/NTFS
/dev/sda2          41,865,453   157,565,519   115,700,067   c W95 FAT32 (LBA)
/dev/sda3    *    157,565,583   209,246,624    51,681,042   7 HPFS/NTFS
/dev/sda4         209,246,625   234,436,544    25,189,920   f W95 Ext d (LBA)
/dev/sda5         209,246,688   213,246,809     4,000,122  82 Linux swap / Solaris
/dev/sda6         213,246,873   220,572,449     7,325,577  83 Linux
/dev/sda7         220,572,513   234,436,544    13,864,032  83 Linux


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        72DA3218DA31D955                       ntfs                                     
/dev/sda2        16F4-26CC                              vfat       ENTERTAIN                     
/dev/sda3        BC52C85252C81356                       ntfs                                     
/dev/sda5        d880638c-d897-4e13-8951-9c5e0f9abebb   swap                                     
/dev/sda6        115d5ac4-f16f-4875-b37f-8baa9e4c439f   ext3                                     
/dev/sda7        b97fab46-ec87-4d2e-bd24-637e7d83dae8   ext3                                     

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda6        /                        ext3       (rw,errors=remount-ro)
/dev/sda7        /home                    ext3       (rw)


=========================== sda6/boot/grub/grub.cfg: ===========================

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
search --no-floppy --fs-uuid --set 115d5ac4-f16f-4875-b37f-8baa9e4c439f
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
    search --no-floppy --fs-uuid --set 115d5ac4-f16f-4875-b37f-8baa9e4c439f
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=115d5ac4-f16f-4875-b37f-8baa9e4c439f ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd0,9)
    search --no-floppy --fs-uuid --set 115d5ac4-f16f-4875-b37f-8baa9e4c439f
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=115d5ac4-f16f-4875-b37f-8baa9e4c439f ro single 
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
    insmod fat
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set 3005-3001
    drivemap -s (hd0) ${root}
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sda6/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda9 during installation
UUID=115d5ac4-f16f-4875-b37f-8baa9e4c439f /               ext3    errors=remount-ro 0       1
# /home was on /dev/sda10 during installation
UUID=b97fab46-ec87-4d2e-bd24-637e7d83dae8 /home           ext3    defaults        0       2
# swap was on /dev/sda7 during installation
UUID=d880638c-d897-4e13-8951-9c5e0f9abebb none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda6: Location of files loaded by Grub: ===================


 110.6GB: boot/grub/core.img
 110.6GB: boot/grub/grub.cfg
 110.6GB: boot/initrd.img-2.6.31-14-generic
 110.6GB: boot/vmlinuz-2.6.31-14-generic
 110.6GB: initrd.img
 110.6GB: vmlinuz

```

---

### Post by Rubi1200 on 2010-10-07
Did you run ```
sudo update-grub
``` after making the changes?

---

### Post by balaji_r_s on 2010-10-07
:D . Such a simple step !! Thanks a bunch. It worked :)

I wanted to learn Unix systems better thats the main reason I installed Ubuntu in the first place. Can you point me some resource which will help me in understanding the Unix-like systems better ?

---

### Post by Rubi1200 on 2010-10-07
Sometimes the simple steps are the ones we overlook! 

I am glad you got it working :)

To answer your question:
[http://www.tldp.org/LDP/intro-linux/html/](http://www.tldp.org/LDP/intro-linux/html/)

And please mark this thread Solved using the Thread Tools near the top of the page.

Enjoy!

---

### Post by balaji_r_s on 2010-10-07
@Rubi1200 and @lechien73: Thanks for the support :D

---

