---
title: "Problem booting with Ubuntu 10.04"
date: 2010-09-20
forum: Installation &amp; Upgrades
---

### Post by Chough39 on 2010-09-20
I have been using Ubuntu 9.10 dual booted with MS Vista on a Dell Inspiron 1501. This worked perfectly. I have now upgraded to 10.04 and have had problems booting. I cannot boot into 2.6.32-24-generic, the screen freeze with a grey screen and fine vertical coloured lines. I can boot into 2.6.31-22-generic but only after it says that it cannot and subsequently runs through a number of pages.  
 I have updated the BIOS and done a completely fresh reinstall and update both as a dual boot system and solely Ubuntu. Running &#8220;update-grub&#8221; produces the following information but does not change the situation:
 

 gerald@gerald-laptop:~$ sudo update-grub 
 Generating grub.cfg ... 
 Found linux image: /boot/vmlinuz-2.6.32-24-generic 
 Found initrd image: /boot/initrd.img-2.6.32-24-generic 
 Found linux image: /boot/vmlinuz-2.6.31-22-generic 
 Found initrd image: /boot/initrd.img-2.6.31-22-generic 
 Found memtest86+ image: /boot/memtest86+.bin 
 Found Windows Vista (loader) on /dev/sda1 
 done 
 gerald@gerald-laptop:~$  
  
  
  
 

 Some help would be much appreciated in order that I can get this otherwise excellent system working properly.
 

 Many thanks

---

### Post by Rubi1200 on 2010-09-20
Before the upgrade did 9.10 work without these issues you described?

What graphics card do you have installed?

---

### Post by Chough39 on 2010-09-20
The following is the information requested.

gerald@gerald-laptop:~$ sudo lshw -C video
[sudo] password for gerald: 
  *-display UNCLAIMED     
       description: VGA compatible controller
       product: RS482 [Radeon Xpress 200M]
       vendor: ATI Technologies Inc
       physical id: 5
       bus info: pci@0000:01:05.0
       version: 00
       width: 32 bits
       clock: 66MHz
       capabilities: pm bus_master cap_list
       configuration: latency=66 mingnt=8
       resources: memory:c8000000-cfffffff(prefetchable) ioport:9000(size=256) memory:c0100000-c010ffff memory:c0120000-c013ffff(prefetchable)
gerald@gerald-laptop:~$ 

That shows what the videocard is and there were no problems untill I tried to use 10.04 as detailed previously. 
Thanks for the prompt response!!

---

### Post by Rubi1200 on 2010-09-20
Did you try the xforcevesa parameter at boot?

As GRUB comes up highlight the entry and press "e" to edit.

Look for the line that ends with ```
ro quiet splash
``` and remove quiet splash and type in xforcevesa instead.

Then "Ctrl" + "x" to boot.

If it helps we can talk about a more permanent solution.

---

### Post by Chough39 on 2010-09-20
I have tried exactly that which you suggested. The system still will not boot to 2.6.32-24-generic . On repeating the exercise the line has returned to “ro quiet splash”,  should I have tried to save it first?
 

 Booting is a little peculiar with  2.6.31-22-generic as I said previously, but it does work. The details on the first screen are:
 

 mount: mounting none on /dev failed : No such device
 chroot: cannot execute /etc/apparamor/initramfs : No such file or directory
 

 

 after a pause and numerous pages it boots.
 

 Updates have been carried out today including  2.6.32-24-generic.
 

 Something I find interesting is that I have a desktop in the UK which upgraded to 10.04 with no problems at all.

I have now run boot_inf_script. The resulting file RESULTS.txt is attached, perhaps this will provide some useful information. As a civil engineer I am still feeling my way around Linux.

---

### Post by Chough39 on 2010-09-26
[SIZE=5]I would like some more help please[/SIZE]

---

### Post by Rubi1200 on 2010-09-26
Well, I am a bit stumped by this one as well. The results look normal as far as I can tell and even a fresh install did not work; strange?
This may not be what you want to hear, but if 9.10 worked you may want to consider going back to it until the next version comes out and then try that as a LiveCD to see if everything works on your system.

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #5 for /boot/grub.
 => No boot loader is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe

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

sdb1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat16
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048    62,974,799    62,972,752   7 HPFS/NTFS
/dev/sda2          62,974,800   156,296,384    93,321,585   5 Extended
/dev/sda5          62,974,863   152,376,524    89,401,662  83 Linux
/dev/sda6         152,376,588   156,296,384     3,919,797  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 1024 MB, 1024966656 bytes
32 heads, 63 sectors/track, 993 cylinders, total 2001888 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                 245     1,999,871     1,999,627   6 FAT16


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        4EE41A5CE41A469D                       ntfs                                     
/dev/sda2: PTTYPE="dos" 
/dev/sda5        ecbdee3a-c2b2-409f-b381-e1affe814c63   ext4                                     
/dev/sda6        e2a294c4-38b5-42a5-a044-90486ee11e94   swap                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        B617-1CEF                              vfat                                     
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda5        /                        ext4       (rw,errors=remount-ro)
/dev/sdb1        /media/B617-1CEF         vfat       (rw,nosuid,nodev,uhelper=udisks,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,flush)


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
search --no-floppy --fs-uuid --set ecbdee3a-c2b2-409f-b381-e1affe814c63
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
search --no-floppy --fs-uuid --set ecbdee3a-c2b2-409f-b381-e1affe814c63
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
    search --no-floppy --fs-uuid --set ecbdee3a-c2b2-409f-b381-e1affe814c63
    linux    /boot/vmlinuz-2.6.32-24-generic root=UUID=ecbdee3a-c2b2-409f-b381-e1affe814c63 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-24-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set ecbdee3a-c2b2-409f-b381-e1affe814c63
    echo    'Loading Linux 2.6.32-24-generic ...'
    linux    /boot/vmlinuz-2.6.32-24-generic root=UUID=ecbdee3a-c2b2-409f-b381-e1affe814c63 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.31-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set ecbdee3a-c2b2-409f-b381-e1affe814c63
    linux    /boot/vmlinuz-2.6.31-22-generic root=UUID=ecbdee3a-c2b2-409f-b381-e1affe814c63 ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.31-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set ecbdee3a-c2b2-409f-b381-e1affe814c63
    echo    'Loading Linux 2.6.31-22-generic ...'
    linux    /boot/vmlinuz-2.6.31-22-generic root=UUID=ecbdee3a-c2b2-409f-b381-e1affe814c63 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.31-22-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set ecbdee3a-c2b2-409f-b381-e1affe814c63
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set ecbdee3a-c2b2-409f-b381-e1affe814c63
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows Vista (loader) (on /dev/sda1)" {
    insmod ntfs
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 4ee41a5ce41a469d
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
proc            /proc           proc    defaults        0       0
# / was on /dev/sda5 during installation
UUID=ecbdee3a-c2b2-409f-b381-e1affe814c63 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=e2a294c4-38b5-42a5-a044-90486ee11e94 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda5: Location of files loaded by Grub: ===================


  32.5GB: boot/grub/core.img
  32.6GB: boot/grub/grub.cfg
  33.3GB: boot/initrd.img-2.6.31-22-generic
  33.5GB: boot/initrd.img-2.6.32-24-generic
  32.6GB: boot/vmlinuz-2.6.31-22-generic
  33.5GB: boot/vmlinuz-2.6.32-24-generic
  33.5GB: initrd.img
  33.3GB: initrd.img.old
  33.5GB: vmlinuz
  32.6GB: vmlinuz.old
```

---

### Post by Chough39 on 2010-09-29
Thanks for the reply. I am of much the same opinion as you, especially as 11.04 works perfectly on the computer I have in the UK. However using the kernel 2.6.31-22-generic the system does work on the laptop and I prefer 11.04.

Kind regards

Chough39

---

### Post by Chough39 on 2010-12-29
I seem now to have solved this problem, open a terminal and type:-
 

  Code:
 sudo gedit /etc/default/grub      change the following line to
  Code:
 GRUB_CMDLINE_LINUX_DEFAULT="nomodeset"
and the following to:-
  Code:
 GRUB_CMDLINE_LINUX="nomodeset quiet"
then save and exit. Then update grub:
  Code:
 sudo update-grub 

 It should now be possible to use kernels beyond 2.6.31-22-generic. This being the last kernel which seemed not to exhibit the problem of vertical coloured lines on trying to boot, i.e. up to 2.6.32-27-generic at the moment.

---

