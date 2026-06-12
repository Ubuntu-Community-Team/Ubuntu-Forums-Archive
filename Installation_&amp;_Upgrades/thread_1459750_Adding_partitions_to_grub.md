---
title: "Adding partitions to grub"
date: 2010-04-21
forum: Installation &amp; Upgrades
---

### Post by joolz1234 on 2010-04-21
Hi, I've using win7 and 9.10 for a few months now.  Today I decided to install yet another OS, but during installation a new grub was written to the mbr. Result: I can no longer boot Ubuntu.
This is what my menu.lst looks like
> 
timeout 10
color black/cyan yellow/cyan
gfxmenu (hd0,4)/boot/gfxmenu
default 0

title linux
kernel (hd0,4)/boot/vmlinuz BOOT_IMAGE=linux root=UUID=51065660-52da-430d-b7e5-47101d215b86  resume=UUID=992e490c-19cf-474b-916a-4efcf98d189c splash=silent vga=788
initrd (hd0,4)/boot/initrd.img

title linux-nonfb
kernel (hd0,4)/boot/vmlinuz BOOT_IMAGE=linux-nonfb root=UUID=51065660-52da-430d-b7e5-47101d215b86  resume=UUID=992e490c-19cf-474b-916a-4efcf98d189c
initrd (hd0,4)/boot/initrd.img

title failsafe
kernel (hd0,4)/boot/vmlinuz BOOT_IMAGE=failsafe root=UUID=51065660-52da-430d-b7e5-47101d215b86  failsafe
initrd (hd0,4)/boot/initrd.img

title windows
root (hd0,1)
makeactive
chainloader +1

I can see and mount my 9.10 partition just fine from the new OS, it's located on dev/sda6.And I'd still very much like to keep using Ubuntu. So, how do I go about editing this file to make it work?

Thanks in advance.:)

---

### Post by presence1960 on 2010-04-21
I need more info. The fix is simple but I need to see your exact setup & boot process. Once I have that info I will give 2 precise commands to reinstall GRUB so you boot all OSs

Let's get a better look at your setup & boot process. Boot the Ubuntu Live CD/USB. Choose "try ubuntu without any changes", when the desktop loads come back here and do the following:

1. Download the boot info script. There is a link in my signature.
2. Once downloaded move the boot info script to the desktop.
3. Open a terminal and run the command ```
sudo bash ~/Desktop/boot_info_script*.sh
```

  This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text. 

See [here]("http://bootinfoscript.sourceforge.net/") for more info on the boot info script.

Above link is to meierfra's Sourceforge web page.

---

### Post by joolz1234 on 2010-04-21
```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #5 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => Windows is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /bootmgr /BOOTMGR /boot/bcd /BOOT/bcd /Boot/bcd 
                       /boot/BCD /BOOT/BCD /Boot/BCD 
                       /Windows/System32/winload.exe /grldr /GRLDR

sda3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  PCLinuxOS release 2010 
                       (PCLinuxOS) for i586 Kernel 2.6.32.11-pclos2.bfs on a 
                       Dual-processor i686 /
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sda6: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda7: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda8: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda9: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Windows XP: Fat32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xbfbfbfbf

Partition  Boot         Start           End          Size  Id System

/dev/sda1               2,048     3,074,047     3,072,000  27 Hidden HPFS/NTFS
/dev/sda2    *      3,074,048   120,005,549   116,931,502   7 HPFS/NTFS
/dev/sda3         120,005,550   488,392,064   368,386,515   5 Extended
/dev/sda5         120,005,613   145,195,469    25,189,857  83 Linux
/dev/sda6         219,319,443   477,371,474   258,052,032  83 Linux
/dev/sda7         477,371,538   488,392,064    11,020,527  82 Linux swap / Solaris
/dev/sda8         145,195,533   153,372,554     8,177,022  82 Linux swap / Solaris
/dev/sda9         153,372,618   219,319,379    65,946,762  83 Linux


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 4009 MB, 4009754624 bytes
145 heads, 48 sectors/track, 1125 cylinders, total 7831552 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xc3072e18

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             48     7,831,551     7,831,504   c W95 FAT32 (LBA)


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/mmcblk0p1   F3B7-3084                              vfat                                     
/dev/sda1        04CEE50CCEE4F738                       ntfs       TOSHIBA SYSTEM VOLUME         
/dev/sda2        907A14917A147666                       ntfs       SQ004660V08                   
/dev/sda5        51065660-52da-430d-b7e5-47101d215b86   ext4                                     
/dev/sda6        d14daec7-93ca-4f86-a8ad-2429916bcb38   ext4                                     
/dev/sda7        992e490c-19cf-474b-916a-4efcf98d189c   swap                                     
/dev/sda8        ad925312-e5d8-4c5c-9d93-db687a33678a   swap                                     
/dev/sda9        ffd0221c-58ec-4978-bb5b-ed494ce420cc   ext4                                     
/dev/sdb1        9B72-3138                              vfat       HP v100w                      

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda5        /                        ext4       (rw)
/dev/sda9        /home                    ext4       (rw)
/dev/sdb1        /media/HP v100w          vfat       (rw,nosuid,nodev,uhelper=hal,uid=500,utf8,shortname=mixed,flush)


=========================== sda5/boot/grub/menu.lst: ===========================

timeout 10
color black/cyan yellow/cyan
gfxmenu (hd0,4)/boot/gfxmenu
default 0

title linux
kernel (hd0,4)/boot/vmlinuz BOOT_IMAGE=linux root=UUID=51065660-52da-430d-b7e5-47101d215b86  resume=UUID=992e490c-19cf-474b-916a-4efcf98d189c splash=silent vga=788
initrd (hd0,4)/boot/initrd.img

title linux-nonfb
kernel (hd0,4)/boot/vmlinuz BOOT_IMAGE=linux-nonfb root=UUID=51065660-52da-430d-b7e5-47101d215b86  resume=UUID=992e490c-19cf-474b-916a-4efcf98d189c
initrd (hd0,4)/boot/initrd.img

title failsafe
kernel (hd0,4)/boot/vmlinuz BOOT_IMAGE=failsafe root=UUID=51065660-52da-430d-b7e5-47101d215b86  failsafe
initrd (hd0,4)/boot/initrd.img

title windows
root (hd0,1)
makeactive
chainloader +1

=============================== sda5/etc/fstab: ===============================

# Entry for /dev/sda5 :
UUID=51065660-52da-430d-b7e5-47101d215b86 / ext4 defaults 1 1
# Entry for /dev/sda9 :
UUID=ffd0221c-58ec-4978-bb5b-ed494ce420cc /home ext4 defaults 1 2
none /proc proc defaults 0 0
# Entry for /dev/sda7 :
UUID=992e490c-19cf-474b-916a-4efcf98d189c swap swap defaults 0 0
# Entry for /dev/sda8 :
UUID=ad925312-e5d8-4c5c-9d93-db687a33678a swap swap defaults 0 0
none /dev/pts devpts defaults 0 0
tmpfs /dev/shm tmpfs defaults 0 0

=================== sda5: Location of files loaded by Grub: ===================


  63.7GB: boot/grub/menu.lst
  64.8GB: boot/grub/stage2
  61.6GB: boot/initrd-2.6.32.11-pclos2.bfs.img
  61.6GB: boot/initrd.img
  63.7GB: boot/vmlinuz
  63.7GB: boot/vmlinuz-2.6.32.11-pclos2.bfs

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
set root=(hd0,5)
search --no-floppy --fs-uuid --set d14daec7-93ca-4f86-a8ad-2429916bcb38
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
    set root=(hd0,5)
    search --no-floppy --fs-uuid --set d14daec7-93ca-4f86-a8ad-2429916bcb38
    linux    /boot/vmlinuz-2.6.31-20-generic root=UUID=d14daec7-93ca-4f86-a8ad-2429916bcb38 ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-20-generic
}
menuentry "Ubuntu, Linux 2.6.31-20-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd0,5)
    search --no-floppy --fs-uuid --set d14daec7-93ca-4f86-a8ad-2429916bcb38
    linux    /boot/vmlinuz-2.6.31-20-generic root=UUID=d14daec7-93ca-4f86-a8ad-2429916bcb38 ro single 
    initrd    /boot/initrd.img-2.6.31-20-generic
}
menuentry "Ubuntu, Linux 2.6.31-19-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd0,5)
    search --no-floppy --fs-uuid --set d14daec7-93ca-4f86-a8ad-2429916bcb38
    linux    /boot/vmlinuz-2.6.31-19-generic root=UUID=d14daec7-93ca-4f86-a8ad-2429916bcb38 ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-19-generic
}
menuentry "Ubuntu, Linux 2.6.31-19-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd0,5)
    search --no-floppy --fs-uuid --set d14daec7-93ca-4f86-a8ad-2429916bcb38
    linux    /boot/vmlinuz-2.6.31-19-generic root=UUID=d14daec7-93ca-4f86-a8ad-2429916bcb38 ro single 
    initrd    /boot/initrd.img-2.6.31-19-generic
}
menuentry "Ubuntu, Linux 2.6.31-17-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd0,5)
    search --no-floppy --fs-uuid --set d14daec7-93ca-4f86-a8ad-2429916bcb38
    linux    /boot/vmlinuz-2.6.31-17-generic root=UUID=d14daec7-93ca-4f86-a8ad-2429916bcb38 ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-17-generic
}
menuentry "Ubuntu, Linux 2.6.31-17-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd0,5)
    search --no-floppy --fs-uuid --set d14daec7-93ca-4f86-a8ad-2429916bcb38
    linux    /boot/vmlinuz-2.6.31-17-generic root=UUID=d14daec7-93ca-4f86-a8ad-2429916bcb38 ro single 
    initrd    /boot/initrd.img-2.6.31-17-generic
}
menuentry "Ubuntu, Linux 2.6.31-16-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd0,5)
    search --no-floppy --fs-uuid --set d14daec7-93ca-4f86-a8ad-2429916bcb38
    linux    /boot/vmlinuz-2.6.31-16-generic root=UUID=d14daec7-93ca-4f86-a8ad-2429916bcb38 ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-16-generic
}
menuentry "Ubuntu, Linux 2.6.31-16-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd0,5)
    search --no-floppy --fs-uuid --set d14daec7-93ca-4f86-a8ad-2429916bcb38
    linux    /boot/vmlinuz-2.6.31-16-generic root=UUID=d14daec7-93ca-4f86-a8ad-2429916bcb38 ro single 
    initrd    /boot/initrd.img-2.6.31-16-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd0,5)
    search --no-floppy --fs-uuid --set d14daec7-93ca-4f86-a8ad-2429916bcb38
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=d14daec7-93ca-4f86-a8ad-2429916bcb38 ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd0,5)
    search --no-floppy --fs-uuid --set d14daec7-93ca-4f86-a8ad-2429916bcb38
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=d14daec7-93ca-4f86-a8ad-2429916bcb38 ro single 
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
menuentry "Windows 7 (loader) (on /dev/sda2)" {
    insmod ntfs
    set root=(hd0,2)
    search --no-floppy --fs-uuid --set 907a14917a147666
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
# / was on /dev/sda5 during installation
UUID=d14daec7-93ca-4f86-a8ad-2429916bcb38 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=992e490c-19cf-474b-916a-4efcf98d189c none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda6: Location of files loaded by Grub: ===================


 115.6GB: boot/grub/core.img
 116.5GB: boot/grub/grub.cfg
 112.8GB: boot/initrd.img-2.6.31-14-generic
 113.3GB: boot/initrd.img-2.6.31-16-generic
 113.0GB: boot/initrd.img-2.6.31-17-generic
 114.1GB: boot/initrd.img-2.6.31-19-generic
 142.3GB: boot/initrd.img-2.6.31-20-generic
 112.8GB: boot/vmlinuz-2.6.31-14-generic
 112.8GB: boot/vmlinuz-2.6.31-16-generic
 113.4GB: boot/vmlinuz-2.6.31-17-generic
 114.2GB: boot/vmlinuz-2.6.31-19-generic
 140.2GB: boot/vmlinuz-2.6.31-20-generic
 142.3GB: initrd.img
 114.1GB: initrd.img.old
 140.2GB: vmlinuz
 114.2GB: vmlinuz.old


```There you go!

---

### Post by joolz1234 on 2010-04-21
hope you can help me out

---

### Post by oldfred on 2010-04-22
You have Karmic with grub2. If you want grub2 in the MBR it should find your other install and let you boot both.

From either the liveCD or your bootable install of PCLinuxOS
How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

reinstall from live cd
sudo mount /dev/sda6 /mnt
sudo grub-install --root-directory=/mnt/ /dev/sda

Then boot into Ubuntu and run this to find your other install:
sudo update-grub

---

### Post by joolz1234 on 2010-04-22
Awesome, it did work. That link was fantastic, thnx everybody.

---

