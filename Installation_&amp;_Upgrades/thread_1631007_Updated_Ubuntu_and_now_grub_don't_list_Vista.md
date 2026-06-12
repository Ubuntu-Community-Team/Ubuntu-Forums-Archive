---
title: "Updated Ubuntu and now grub don't list Vista"
date: 2010-11-26
forum: Installation &amp; Upgrades
---

### Post by seaterk on 2010-11-26
I have a dual boot with Ubuntu and Windows Vista, I just updated the Ubuntu and when I rebooted Grub only lists various versions of Ubuntu and Windows Vista seems to have disappeared. I looked but could not find a similar problem but did run the script that is recommended and got the following:

                 Edit: See reply #6 for new posting of script output

---

### Post by wojox on 2010-11-26
When your in your new kernel for Ubuntu, open a terminal and run

```
sudo update-grub
```

Might work. I'm not to familiar with RAID set ups. ;)

---

### Post by seaterk on 2010-11-26
Tried that, doesn't seem to find the Windows Vista.

---

### Post by sikander3786 on 2010-11-26
This output is a complex one :-)

Can't figure out why Grub isn't detecting Vista as all the boot files for Windows and the boot flag seem ok to me.

I were you, regardless of anything, I would first try Starup repair from Vista install/recovery disc (might need to be done 3 times) and once I was able to boot Windows successfully, re-install Grub and see if can detect Vista now.

---

### Post by wilee-nilee on 2010-11-26
Is sdb first in line to be read in the bios. At this point without code tags so the text is easier to read thats all I can say. If you want to tags it correctly look in my signature for the description.

---

### Post by seaterk on 2010-11-26
```

               Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda
 => Grub 2 is installed in the MBR of /dev/sdb and looks on the same drive in 
    partition #5 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe

sdb2: _________________________________________________________________________

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

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1               2,048 1,953,521,663 1,953,519,616   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *          2,048   466,929,647   466,927,600   7 HPFS/NTFS
/dev/sdb2         466,929,662   488,394,751    21,465,090   5 Extended
/dev/sdb5         466,929,664   487,387,135    20,457,472  83 Linux
/dev/sdb6         487,389,184   488,394,751     1,005,568  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        E2387AF3387AC657                       ntfs       Data Disk 1                   
/dev/sda: PTTYPE="dos" 
/dev/sdb1        88F0BC76F0BC6C56                       ntfs                                     
/dev/sdb2: PTTYPE="dos" 
/dev/sdb5        3018953c-c645-45d3-9ce8-9454c3393631   ext4                                     
/dev/sdb6        dc61d6f1-c8e2-44d6-a050-1ff949fd0550   swap                                     
/dev/sdb                                                silicon_medley_raid_member                               

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sdb5        /                        ext4       (rw,errors=remount-ro)


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
set root='(hd1,5)'
search --no-floppy --fs-uuid --set 3018953c-c645-45d3-9ce8-9454c3393631
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
set root='(hd1,5)'
search --no-floppy --fs-uuid --set 3018953c-c645-45d3-9ce8-9454c3393631
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
menuentry 'Ubuntu, with Linux 2.6.32-25-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,5)'
    search --no-floppy --fs-uuid --set 3018953c-c645-45d3-9ce8-9454c3393631
    linux    /boot/vmlinuz-2.6.32-25-generic root=UUID=3018953c-c645-45d3-9ce8-9454c3393631 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-25-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,5)'
    search --no-floppy --fs-uuid --set 3018953c-c645-45d3-9ce8-9454c3393631
    echo    'Loading Linux 2.6.32-25-generic ...'
    linux    /boot/vmlinuz-2.6.32-25-generic root=UUID=3018953c-c645-45d3-9ce8-9454c3393631 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-24-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,5)'
    search --no-floppy --fs-uuid --set 3018953c-c645-45d3-9ce8-9454c3393631
    linux    /boot/vmlinuz-2.6.32-24-generic root=UUID=3018953c-c645-45d3-9ce8-9454c3393631 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-24-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,5)'
    search --no-floppy --fs-uuid --set 3018953c-c645-45d3-9ce8-9454c3393631
    echo    'Loading Linux 2.6.32-24-generic ...'
    linux    /boot/vmlinuz-2.6.32-24-generic root=UUID=3018953c-c645-45d3-9ce8-9454c3393631 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-24-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd1,5)'
    search --no-floppy --fs-uuid --set 3018953c-c645-45d3-9ce8-9454c3393631
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd1,5)'
    search --no-floppy --fs-uuid --set 3018953c-c645-45d3-9ce8-9454c3393631
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
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
/dev/mapper/sil_aiafdhcbdfeb5 /               ext4    errors=remount-ro 0       1
/dev/mapper/sil_aiafdhcbdfeb6 none            swap    sw              0       0

=================== sdb5: Location of files loaded by Grub: ===================


 239.7GB: boot/grub/core.img
 239.3GB: boot/grub/grub.cfg
 240.4GB: boot/initrd.img-2.6.32-24-generic
 240.4GB: boot/initrd.img-2.6.32-25-generic
 240.2GB: boot/vmlinuz-2.6.32-24-generic
 239.3GB: boot/vmlinuz-2.6.32-25-generic
 240.4GB: initrd.img
 240.4GB: initrd.img.old
 239.3GB: vmlinuz
 240.2GB: vmlinuz.old
=============================== StdErr Messages: ===============================

ERROR: sil: wrong # of devices in RAID set "sil_aiafdhcbdfeb" [1/2] on /dev/sdb
ERROR: sil: wrong # of devices in RAID set "sil_aiafdhcbdfeb" [1/2] on /dev/sdb
ERROR: creating degraded mirror mapping for "sil_aiafdhcbdfeb"
ERROR: sil: wrong # of devices in RAID set "sil_aiafdhcbdfeb" [1/2] on /dev/sdb
ERROR: sil: wrong # of devices in RAID set "sil_aiafdhcbdfeb" [1/2] on /dev/sdb
ERROR: sil: wrong # of devices in RAID set "sil_aiafdhcbdfeb" [1/2] on /dev/sdb

```

---

### Post by wilee-nilee on 2010-11-26
Cool man ;) now remove the original one and put a letter or symbol just to shorten the page up.

Seems retentive I know but these threads can get long and things missed its just about efficiency.

You have tried 
sudo update-grub 
in Ubuntu corrct.

---

### Post by seaterk on 2010-11-26
Tried that a few times. Also recently had one f my RAID disks go out so I just pulled it out and added a new 1T HD (not on the raid). I was booting ok in this config but couldn't figure out how to turn off the RAID functions so just figured it would work, which it has.

---

### Post by wilee-nilee on 2010-11-26
> **seaterk said:**
> Tried that a few times. Also recently had one f my RAID disks go out so I just pulled it out and added a new 1T HD (not on the raid). I was booting ok in this config but couldn't figure out how to turn off the RAID functions so just figured it would work, which it has.

sikander3786 may be correct as far as reloading the vista boot setup or a chkdsk /r might be needed. If you have gparted installed in Ubuntu it might help to right click on the Vista partition-information and see if it says any errors.

So it may just need a chkdsk or a autorepiar. The other thing also is that we see systems run best with the sda with the OS rather then a second one. The script makes it look as though sda is first in line in the bios when sdb is the HD with Vista and Ubuntu. It may just be that sda is first in line for processing and is thrown off by this just speculating but you have a unusual setup.

I see the raid errors at the bottom of the script, hopefully in the end somebody will know or our suggestions with the auto repair or chkdsk, and checking gparted for errors will get you closer. I have had gparted even show a possible virus problem which actually was in W7. Not its normal function but it suggested that in the information.

---

### Post by Quackers on 2010-11-26
I was under the impression that when a disc fails in a raid 1 array and a new disc is put in the raid array should rebuild the new disc to be a copy of the existing one. That hasn't happened here. I would think the new disc would need to be included in the raid 1 array through the bios, but I'm not 100% about that.
In the boot script Windows is installed in the mbr of sda, but the Windows OS is installed in sdb1.
sdb1 carries the boot flag so I would presume that running the startup repair from the Windows repair cd should work. I'm not sure whether you should unplug sda first though. It would be interesting to see what others think about that.

It may also be the case that if the new drive is unplugged and grub re-installed to the mbr of the old drive it may then pick up Windows.

Removing the new drive would effectively make the old drive sda, which may also help as far as Windows is concerned.

---

### Post by seaterk on 2010-11-26
OK I took out the second drive and updated grub, didn't help. I ran the windows install disk to recover windows, windows said all was fine, tried to reinstall ubuntu and it would not recognize that there was any disk in the system. This must have to do with the RAID set-up but I'm not sure what. Is there anyway to unistall ubuntu?

---

### Post by sikander3786 on 2010-11-26
> **seaterk said:**
> OK I took out the second drive and updated grub, didn't help. I ran the windows install disk to recover windows, windows said all was fine, tried to reinstall ubuntu and it would not recognize that there was any disk in the system. This must have to do with the RAID set-up but I'm not sure what. Is there anyway to unistall ubuntu?
You need to try the startup recovery 3 times at least and then it might detect the problems. Keep on repeating until you are able to boot Windows successfully.

To uninstall Ubuntu, you just delete Ubuntu partition and then restore the Windows boot loader.

I'd recommend to switch back to your previous RAID setup and try Startup Recovery again.

---

