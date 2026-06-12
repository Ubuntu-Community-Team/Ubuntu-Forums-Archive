---
title: "help boot menu"
date: 2010-01-08
forum: Installation &amp; Upgrades
---

### Post by aminmatrix on 2010-01-08
hey 
i tried to update my ubuntu and i changed some configurations when i restared my pc i didn't found the list that i use to find on the boot menu
ihave now only one choice "windows NT/2000/XP" and it didn't work
what's the solution pleaz help want to back it up!

---

### Post by raymondh on 2010-01-08
> **aminmatrix said:**
> hey 
i tried to update my ubuntu and i changed some configurations when i restared my pc i didn't found the list that i use to find on the boot menu
ihave now only one choice "windows NT/2000/XP" and it didn't work
what's the solution pleaz help want to back it up!

what "configurations' did you do?
what version ubuntu are you running?  Better yet, what version GRUB are you running?

For GRUB2 .... are you able to go to '[rescue mode]("https://help.ubuntu.com/community/Grub2#Rescue%20Mode")'?

[Some readings for GRUB2]("https://help.ubuntu.com/community/Grub2#Reinstalling GRUB 2").  [Some readings for GRUB-legacy.]("http://ubuntuforums.org/showthread.php?t=224351").

It all can depend on what configurations you did.

Regards,

Raymond

---

### Post by presence1960 on 2010-01-09
Let's get a better look at your setup & boot process. Boot the Ubuntu Live CD/USB. Choose "try ubuntu without any changes", when the desktop loads come back here and use the link in my signature to download the Boot Info Script to the desktop. Once on desktop open a terminal (Applications > Accessories > Terminal) and run this command ```
sudo bash ~/Desktop/boot_info_script*.sh
``` This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text.

---

### Post by aminmatrix on 2010-01-09
> **raymondh said:**
> what "configurations' did you do?
what version ubuntu are you running?  Better yet, what version GRUB are you running?

For GRUB2 .... are you able to go to '[rescue mode]("https://help.ubuntu.com/community/Grub2#Rescue%20Mode")'?

[Some readings for GRUB2]("https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202").  [Some readings for GRUB-legacy.]("http://ubuntuforums.org/showthread.php?t=224351").

It all can depend on what configurations you did.

Regards,

Raymond

i'm raunning Ubuntu 9.10
GNU GRUB 1.97 beta4
and the changed i tried to install some soft

---

### Post by aminmatrix on 2010-01-09
> **presence1960 said:**
> Let's get a better look at your setup & boot process. Boot the Ubuntu Live CD/USB. Choose "try ubuntu without any changes", when the desktop loads come back here and use the link in my signature to download the Boot Info Script to the desktop. Once on desktop open a terminal (Applications > Accessories > Terminal) and run this command ```
sudo bash ~/Desktop/boot_info_script*.sh
``` This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text.

This is zhqt i found in results.txt
```
============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda
sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /boot/bcd

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM /wubildr.mbr

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /ubuntu/winboot/wubildr.mbr /ubuntu/disks/root.disk 
                       /ubuntu/disks/swap.disk

sda3/Wubi: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x64740bcc

Partition  Boot         Start           End          Size  Id System

/dev/sda1              12,678     4,209,029     4,196,352  27 Hidden HPFS/NTFS
/dev/sda2    *      4,219,027    67,135,634    62,916,608   7 HPFS/NTFS
/dev/sda3          67,135,635   234,436,544   167,300,910   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

sda1: UUID="18605FA0605F8402" LABEL="WINRE" TYPE="ntfs" 
sda2: UUID="FE3814C8381481B7" LABEL="System" TYPE="ntfs" 
sda3: UUID="4434E0C434E0B9D6" LABEL="Data" TYPE="ntfs" 
sda3/Wubi: UUID="0ef3f1f0-d4c3-405c-aaf0-992be80cf313" TYPE="ext4" 

=============================== "mount" output: ===============================

aufs on / type aufs (rw)
none on /proc type proc (rw,noexec,nosuid,nodev)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
udev on /dev type tmpfs (rw,mode=0755)
/dev/sr0 on /cdrom type iso9660 (rw)
/dev/loop0 on /rofs type squashfs (rw)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
none on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/ubuntu/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=ubuntu)


================================ sda2/boot.ini: ================================

[boot loader] 
timeout=5 
default=multi(0)disk(0)rdisk(0)partition(2)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(2)\WINDOWS="Microsoft Windows XP Professionnel" /noexecute=optin /fastdetect /TUTag=LHVTWO /Kernel=TUKernel.exe 
multi(0)disk(0)rdisk(0)partition(2)\WINDOWS="Microsoft Windows XP Professionnel (TuneUp Backup)" /noexecute=optin /fastdetect /TUTag=LHVTWO-BAK 
C:\wubildr.mbr = "Ubuntu" 

======================== sda3/Wubi/boot/grub/grub.cfg: ========================

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
### END /etc/grub.d/10_lupin ###

### BEGIN /etc/grub.d/20_memtest86+ ###
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows NT/2000/XP (loader) (on /dev/sda2)" {
    insmod ntfs
    set root=(hd0,2)
    search --no-floppy --fs-uuid --set fe3814c8381481b7
    drivemap -s (hd0) ${root}
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

============================= sda3/Wubi/etc/fstab: =============================

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

================= sda3/Wubi: Location of files loaded by Grub: =================


    .0GB: boot/grub/grub.cfg
```

---

### Post by francisgan9 on 2010-01-09
I have a similar problem



I have installed the latest Ubuntu Desktop 9.10 for notebook on my Acer Aspire 4715Z Pentium Dual-Core
for last several months- working  very smoothly & enjoying the "new world."
I thought I never need to go back to Windows(rarely)



- but 2 days ago  as I updated the Update Manager
and restarted it as requested 
after the setup, there is 2 choices- then choosing the Ubuntu operating system--(   dual booting  with Windows)

a black screen appeared 
-----------------------------------

try FAT32: no WUBILDR
     (hd0,1): NTFS5
--------------------------------------
for a few seconds


- then suddenly the GNU GRUB version 1.97beta 4 appear --  
a prompt 

sh:grub>
appreared.




I dont know what to type in the command line editing BASH



please teach me- how to get into - Ubuntu (kernel) again

Thank you very much.

Please let me know as soon as possible. Miss using Linux(Ubuntu)

Francis Gan

Malaysia

---

### Post by presence1960 on 2010-01-09
> **francisgan9 said:**
> I have a similar problem



I have installed the latest Ubuntu Desktop 9.10 for notebook on my Acer Aspire 4715Z Pentium Dual-Core
for last several months- working  very smoothly & enjoying the "new world."
I thought I never need to go back to Windows(rarely)



- but 2 days ago  as I updated the Update Manager
and restarted it as requested 
after the setup, there is 2 choices- then choosing the Ubuntu operating system--(   dual booting  with Windows)

a black screen appeared 
-----------------------------------

try FAT32: no WUBILDR
     (hd0,1): NTFS5
--------------------------------------
for a few seconds


- then suddenly the GNU GRUB version 1.97beta 4 appear --  
a prompt 

sh:grub>
appreared.




I dont know what to type in the command line editing BASH



please teach me- how to get into - Ubuntu (kernel) again

Thank you very much.

Please let me know as soon as possible. Miss using Linux(Ubuntu)

Francis Gan

Malaysia

Unfortunately you have installed Ubuntu via wubi. I am not well versed in wubi and would not know where to begin.

There are plenty of glitches and problems with running wubi, especially in Karmic 9.10. Besides it is harder to get help with wubi because most Ubuntu users do not use wubi- they have full installations to a partition on their hard disk.

If you like Ubuntu I suggest you uninstall wubu through windows and do a full install by booting the Live CD/USB.

Although a lot of people today try to use wubi as a permanent installation, it is not meant to be used that way. It is rather to be used as a "trial" for those who don't want to risk partitioning their hard disk(s) until they are sure they like Ubuntu. [Here]("http://howsoftwareisbuilt.com/2009/03/12/interview-with-agostino-russo-wubi-ubuntu/") is a link to an interview with the developer of wubi, note his response to the second question.

I am sorry I can offer nothing to assist you.

---

### Post by darkod on 2010-01-09
Just to add, from the results of the script it seems the OP also has wubi, so the same reply from presence is applicable for the OP too.

---

