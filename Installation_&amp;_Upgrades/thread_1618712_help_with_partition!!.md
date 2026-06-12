---
title: "help with partition!!"
date: 2010-11-10
forum: Installation &amp; Upgrades
---

### Post by simelinux on 2010-11-10
so i know partitioning is like second nature to you guys but i am new to linux.
i need help installing UNR 10.04 but i get stuck at the partition because i want to dual boot with windows and im afraid to go far without professional help. 

what i want to do is install ubuntu on my D:/ drive and keep xp on my C drive. i have provided you guys with screenshots to help visualize my dilemma. this is the current state of my hard drives at the moment (screenshot.png). i dont know what all the boxes to the right are for either. also my D drive (which i want ubuntu on) has ext4 on it from a previous failed attemp to install linux mint.

because of this when i go to install ubuntu it shows xp on the C drive and linux mint on the D drive although the installation was botched and i cant really boot into linux mint. i have provided a screenshot of this too (screenshot-1.png).

how can i fix this and install UNR  on my D drive propery.
also  iknow i need to add a swap partition how do i do that?

---

### Post by Quackers on 2010-11-11
What is on /dev/sda3 which is 4.89GB fat32 partition? Is that a recovery partition?
Also /dev/sda4 shows an unknown 47.07MB partition, do you know what that is or was?

---

### Post by simelinux on 2010-11-11
im adding another screenshot ot show you guys what happens when i choose the option to setup my own partitions manually - screenshot-2.png

---

### Post by simelinux on 2010-11-11
> **Quackers said:**
> What is on /dev/sda3 which is 4.89GB fat32 partition? Is that a recovery partition?
Also /dev/sda4 shows an unknown 47.07MB partition, do you know what that is or was?
i believe the fat32 is a recovery partition for xp? does that make sense? i have used the system restore before so i think thats what it is. as for the 47mb i have no idea. can i delete it?

---

### Post by Quackers on 2010-11-11
I think we need to make sure.
Please boot from the live cd and choose "try Ubuntu". When the desktop loads make sure you are connected to the internet then please go to the site below and download the boot script to the DESKTOP. Then open a terminal ( Applications menu > Accessories > Terminal) and type the command given on the first page of that site. Press enter then enter your password. It will run and produce a results.txt file on the desktop. Please copy the contents of that file and paste it in between CODE tags in your next post.
For CODE tags click on New Reply then on the # symbol in the toolbar.

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

---

### Post by simelinux on 2010-11-11
```

```                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda
 => Syslinux is installed in the MBR of /dev/sdb

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
    Operating System:  Linux Mint 9 Isadora
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda3: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Windows XP: Fat32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /ntldr /NTDETECT.COM

sda4: _________________________________________________________________________

    File system:       
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''

sdb1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   151,123,454   151,123,392   7 HPFS/NTFS
/dev/sda2         151,123,966   302,229,503   151,105,538   5 Extended
/dev/sda5         151,123,968   296,269,823   145,145,856  83 Linux
/dev/sda6         296,271,872   302,229,503     5,957,632  82 Linux swap / Solaris
/dev/sda3         302,230,845   312,480,314    10,249,470  1c Hidden W95 FAT32 (LBA)
/dev/sda4         312,480,315   312,576,704        96,390  ef EFI (FAT-12/16/32)


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 4012 MB, 4012900352 bytes
120 heads, 55 sectors/track, 1187 cylinders, total 7837696 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             32     7,837,695     7,837,664   b W95 FAT32


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        2CFC21C1FC2185E4                       ntfs                                     
/dev/sda2: PTTYPE="dos" 
/dev/sda3        CCED-990E                              vfat                                     
/dev/sda4: PTTYPE="dos" 
/dev/sda5        af3cd3ef-031a-4329-94a8-74495fb140db   ext4                                     
/dev/sda6        0165da6a-1117-48fe-abda-5fa81e870ffb   swap                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        F0D7-F5B8                              vfat       DRIVE                         
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sdb1        /cdrom                   vfat       (ro,noatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sda5        /media/af3cd3ef-031a-4329-94a8-74495fb140db ext4       (rw,nosuid,nodev,uhelper=udisks)
/dev/sda1        /media/2CFC21C1FC2185E4  fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)


================================ sda1/boot.ini: ================================

[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Home Edition" /noexecute=optin /fastdetect 

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

### BEGIN /etc/grub.d/06_mint_theme ###
set menu_color_normal=white/black
set menu_color_highlight=white/light-gray
### END /etc/grub.d/06_mint_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry "Linux Mint 9, 2.6.32-22-generic (/dev/sda1)" --class linuxmint --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set d52bc8cd-e21c-4e02-b0b1-50e9fe6b9942
    linux    /boot/vmlinuz-2.6.32-22-generic root=UUID=d52bc8cd-e21c-4e02-b0b1-50e9fe6b9942 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-22-generic
}
menuentry "Linux Mint 9, 2.6.32-22-generic (/dev/sda1) -- recovery mode" --class linuxmint --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set d52bc8cd-e21c-4e02-b0b1-50e9fe6b9942
    echo    'Loading Linux 2.6.32-22-generic ...'
    linux    /boot/vmlinuz-2.6.32-22-generic root=UUID=d52bc8cd-e21c-4e02-b0b1-50e9fe6b9942 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-22-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/10_lupin ###
### END /etc/grub.d/10_lupin ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set d52bc8cd-e21c-4e02-b0b1-50e9fe6b9942
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set d52bc8cd-e21c-4e02-b0b1-50e9fe6b9942
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Linux Mint 9 Isadora, 2.6.32-21-generic (/dev/sda6) (on /dev/sda6)" {
    insmod ext2
    set root='(hd0,6)'
    search --no-floppy --fs-uuid --set 6b595678-11b3-4c9e-af28-6507f78df508
    linux /boot/vmlinuz-2.6.32-21-generic root=UUID=6b595678-11b3-4c9e-af28-6507f78df508 ro quiet splash
    initrd /boot/initrd.img-2.6.32-21-generic
}
menuentry "Linux Mint 9 Isadora, 2.6.32-21-generic (/dev/sda6) -- recovery mode (on /dev/sda6)" {
    insmod ext2
    set root='(hd0,6)'
    search --no-floppy --fs-uuid --set 6b595678-11b3-4c9e-af28-6507f78df508
    linux /boot/vmlinuz-2.6.32-21-generic root=UUID=6b595678-11b3-4c9e-af28-6507f78df508 ro single
    initrd /boot/initrd.img-2.6.32-21-generic
}
menuentry "Linux Mint 9, 2.6.32-22-generic-pae (/dev/sda7) (on /dev/sda7)" {
    insmod ext2
    set root='(hd0,7)'
    search --no-floppy --fs-uuid --set 817725a3-0839-4314-b6a9-0b5c09f82ce6
    linux /boot/vmlinuz-2.6.32-22-generic-pae root=UUID=817725a3-0839-4314-b6a9-0b5c09f82ce6 ro quiet splash
    initrd /boot/initrd.img-2.6.32-22-generic-pae
}
menuentry "Linux Mint 9, 2.6.32-22-generic-pae (/dev/sda7) -- recovery mode (on /dev/sda7)" {
    insmod ext2
    set root='(hd0,7)'
    search --no-floppy --fs-uuid --set 817725a3-0839-4314-b6a9-0b5c09f82ce6
    linux /boot/vmlinuz-2.6.32-22-generic-pae root=UUID=817725a3-0839-4314-b6a9-0b5c09f82ce6 ro single
    initrd /boot/initrd.img-2.6.32-22-generic-pae
}
menuentry "Peppermint, 2.6.32-22-generic (/dev/sda8) (on /dev/sda8)" {
    insmod ext2
    set root='(hd0,8)'
    search --no-floppy --fs-uuid --set 3a36e5fe-c0fb-4ac5-a01b-2b4ef22ebf64
    linux /boot/vmlinuz-2.6.32-22-generic root=UUID=3a36e5fe-c0fb-4ac5-a01b-2b4ef22ebf64 ro quiet splash
    initrd /boot/initrd.img-2.6.32-22-generic
}
menuentry "Peppermint, 2.6.32-22-generic (/dev/sda8) -- recovery mode (on /dev/sda8)" {
    insmod ext2
    set root='(hd0,8)'
    search --no-floppy --fs-uuid --set 3a36e5fe-c0fb-4ac5-a01b-2b4ef22ebf64
    linux /boot/vmlinuz-2.6.32-22-generic root=UUID=3a36e5fe-c0fb-4ac5-a01b-2b4ef22ebf64 ro single
    initrd /boot/initrd.img-2.6.32-22-generic
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
UUID=af3cd3ef-031a-4329-94a8-74495fb140db /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=0165da6a-1117-48fe-abda-5fa81e870ffb none            swap    sw              0       0

=================== sda5: Location of files loaded by Grub: ===================


  92.5GB: boot/grub/grub.cfg
  92.5GB: boot/initrd.img-2.6.32-22-generic
  77.5GB: boot/vmlinuz-2.6.32-22-generic
  92.5GB: initrd.img
  77.5GB: initrd.lz
  77.5GB: vmlinuz```

```

---

### Post by simelinux on 2010-11-11
did i do that right?

---

### Post by Quackers on 2010-11-11
Not quite :-) but the script is ok. You didn't get the code tags right :-)
I too am in a dilemma. It seems that sda3 could be a recovery partition, but if it is I would expect it to be sda1 and Windows to be sda2.
I am happy that you can delete sda5,sda6,sda2 and sda4, in that order and one at a time (assuming you are happy to ditch Mint/Peppermint). Using Gparted from the Live cd.
Do you know whether you have a recovery partition? Have you made recovery discs?

---

### Post by simelinux on 2010-11-11
> **Quackers said:**
> Not quite :-) but the script is ok. You didn't get the code tags right :-)
I too am in a dilemma. It seems that sda3 could be a recovery partition, but if it is I would expect it to be sda1 and Windows to be sda2.
I am happy that you can delete sda5,sda6,sda2 and sda4, in that order and one at a time (assuming you are happy to ditch Mint/Peppermint). Using Gparted from the Live cd.
Do you know whether you have a recovery partition? Have you made recovery discs?

yes i want to ditch it. it seems however that i cant delete sda5. i didnt do anything rash and the only programs i have open are gparted and firefox.i added a screenshot to show the delete option not popping up (screenshot-3.png)

---

### Post by Quackers on 2010-11-11
Can you right-click on the partition and select "unmount"?

---

### Post by simelinux on 2010-11-11
> **Quackers said:**
> Can you right-click on the partition and select "unmount"?
yes then what...

---

### Post by Quackers on 2010-11-11
Then the option to delete should appear. No?

---

### Post by simelinux on 2010-11-11
i got the message that i need to delete sda6 first

---

### Post by Quackers on 2010-11-11
Ah, ok try that :-) Unmount it first.

---

### Post by simelinux on 2010-11-11
however i cant when i right click on sda6 i dont get a delete option

---

### Post by simelinux on 2010-11-11
theres a swapoff option whats that? can that do us any help?

---

### Post by Quackers on 2010-11-11
Sorry, yes select swapoff.

---

### Post by simelinux on 2010-11-11
ok i deleted it in the order you recommended. heres the cleaned up version im looking at now

---

### Post by Quackers on 2010-11-11
Ok. You now have a 72GB unallocated space which Ubuntu can be installed into. Choose "install Ubuntu" now and in the partitioning stage select "specify partitions manually" or whatever it's called, and install to that 72GB space.

---

### Post by simelinux on 2010-11-11
ok i selected the option install into largest continous space and this  is how it set it up for me. is this the same as youre saying or should i  do it manually.

---

### Post by Quackers on 2010-11-11
Yes, that option is fine. I wasn't sure whether you'd get that option.

---

### Post by simelinux on 2010-11-11
also do i need to create a swap partition or it doing it automatically for me. in addition i want to be able to transfer files from xp to ubuntu and vice versa. do i need to create an additional partition for that to work?

---

### Post by Quackers on 2010-11-11
The swap partition will be created automatically. Regarding the transfer of files I'm afraid I don't know. It's not something I use.
If you want to leave room for another partition to be created you should use the Manual partitioning method and specify your own partitions, leaving room for another to be created later.
Say, for instance a root partition (mount point "/" of 8GB and a swap partition of an amount 100MB larger than the amount of ram your pc has (if you want to use hibernate) with a mount point of "swap". You can also create a separate /home partition for your personal files and settings with a mount point "/home" of a size you choose yourself. This leaving space for another partition to be created later.

---

### Post by simelinux on 2010-11-11
thank you very much for your help. it will make my transition into ubuntu very smooth. i appreciate it.

---

### Post by Quackers on 2010-11-11
No problem :-)
I hope to see you posting from your new installation! :-)

---

