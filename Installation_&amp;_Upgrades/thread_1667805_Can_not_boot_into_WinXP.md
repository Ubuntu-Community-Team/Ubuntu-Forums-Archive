---
title: "Can not boot into WinXP"
date: 2011-01-15
forum: Installation &amp; Upgrades
---

### Post by merlec on 2011-01-15
Hi...I'm new to Ubuntu and decided to install on a desktop that didnt have critical data on it first. I basically have a generic desktop with a 1TB harddrive. I installed Ubuntu 10.10 alongside of Windows and everything seemed to go well except I saw a few errors fly by after it was installed and was re booting. I got the boot menu and booted into Ubuntu and for two days explored and set things up. My sound and, scanner, and printer (wireless canon MP990) won't work yet so I restarted and tried to boot into XP but I immediately get a black screen with a blinking cursor in the top left hand corner of the screen. I have tried serching the forum and didn't find anything specific on this but found some trouble shooting terminal commands to try so I am posting them below. Any suggestions would be great...Thank You

ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000001

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       84742   680682675    7  HPFS/NTFS
/dev/sda2           84742      121602   296078337    5  Extended
/dev/sda5           84742      120104   284045312   83  Linux
/dev/sda6          120104      121602    12032000   82  Linux swap / Solaris
ubuntu@ubuntu:~$ ^C

ubuntu@ubuntu:~$ sudo parted -l
Model: ATA WDC WD10EAVS-00M (scsi)
Disk /dev/sda: 1000GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type      File system     Flags
 1      32.3kB  697GB   697GB   primary   ntfs            boot
 2      697GB   1000GB  303GB   extended
 5      697GB   988GB   291GB   logical   ext4
 6      988GB   1000GB  12.3GB  logical   linux-swap(v1)


Warning: Unable to open /dev/sr1 read-write (Read-only file system).  /dev/sr1
has been opened read-only.
Error: /dev/sr1: unrecognised disk label

---

### Post by Quackers on 2011-01-15
Welcome to UF.
Please go to the site below and download the boot script to your DESKTOP and then open up a terminal and run
```
sudo bash ~/Desktop/boot_info_script*.sh
```

This will produce a results.txt file on your desktop. Please copy the contents of that file and paste them in your next post between CODE tags. For CODE tags click on New Reply (not quick reply) and then click on the # symbol in the toolbar.
This will give a full overview of your current system.
Thanks.

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

---

### Post by merlec on 2011-01-15
Thank You for the quick response. Here is the results.txt-

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #5 for (,msdos5)/boot/grub.

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
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda6: _________________________________________________________________________

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

/dev/sda1    *             63 1,361,365,412 1,361,365,350   7 HPFS/NTFS
/dev/sda2       1,361,367,038 1,953,523,711   592,156,674   5 Extended
/dev/sda5       1,361,367,040 1,929,457,663   568,090,624  83 Linux
/dev/sda6       1,929,459,712 1,953,523,711    24,064,000  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        0ED8BAE6D8BACAEB                       ntfs                                     
/dev/sda2: PTTYPE="dos" 
/dev/sda5        8dfbccf0-cf2f-47b3-af74-2a5ed0542851   ext4                                     
/dev/sda6        0298812b-d0cf-42cb-a19b-36bea106e31f   swap                                     
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda5        /                        ext4       (rw,errors=remount-ro,commit=0)


================================ sda1/boot.ini: ================================

[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /fastdetect /NoExecute=OptIn 

=========================== sda5/boot/grub/grub.cfg: ===========================

#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s $prefix/grubenv ]; then
  set have_grubenv=true
  load_env
fi
set default="0"
if [ "${prev_saved_entry}" ]; then
  set saved_entry="${prev_saved_entry}"
  save_env saved_entry
  set prev_saved_entry=
  save_env prev_saved_entry
  set boot_once=true
fi

function savedefault {
  if [ -z "${boot_once}" ]; then
    saved_entry="${chosen}"
    save_env saved_entry
  fi
}

function recordfail {
  set recordfail=1
  if [ -n "${have_grubenv}" ]; then if [ -z "${boot_once}" ]; then save_env recordfail; fi; fi
}

function load_video {
  insmod vbe
  insmod vga
}

insmod part_msdos
insmod ext2
set root='(hd0,msdos5)'
search --no-floppy --fs-uuid --set 8dfbccf0-cf2f-47b3-af74-2a5ed0542851
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos5)'
search --no-floppy --fs-uuid --set 8dfbccf0-cf2f-47b3-af74-2a5ed0542851
set locale_dir=($root)/boot/grub/locale
set lang=en
insmod gettext
if [ "${recordfail}" = 1 ]; then
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
menuentry 'Ubuntu, with Linux 2.6.35-24-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set 8dfbccf0-cf2f-47b3-af74-2a5ed0542851
    linux    /boot/vmlinuz-2.6.35-24-generic-pae root=UUID=8dfbccf0-cf2f-47b3-af74-2a5ed0542851 ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-24-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.35-24-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set 8dfbccf0-cf2f-47b3-af74-2a5ed0542851
    echo    'Loading Linux 2.6.35-24-generic-pae ...'
    linux    /boot/vmlinuz-2.6.35-24-generic-pae root=UUID=8dfbccf0-cf2f-47b3-af74-2a5ed0542851 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-24-generic-pae
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set 8dfbccf0-cf2f-47b3-af74-2a5ed0542851
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set 8dfbccf0-cf2f-47b3-af74-2a5ed0542851
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Professional (on /dev/sda1)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 0ed8bae6d8bacaeb
    drivemap -s (hd0) ${root}
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

### BEGIN /etc/grub.d/41_custom ###
if [ -f  $prefix/custom.cfg ]; then
  source $prefix/custom.cfg;
fi
### END /etc/grub.d/41_custom ###

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
UUID=8dfbccf0-cf2f-47b3-af74-2a5ed0542851 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=0298812b-d0cf-42cb-a19b-36bea106e31f none            swap    sw              0       0

=================== sda5: Location of files loaded by Grub: ===================


 864.6GB: boot/grub/core.img
 753.0GB: boot/grub/grub.cfg
 697.7GB: boot/initrd.img-2.6.35-24-generic-pae
 864.6GB: boot/vmlinuz-2.6.35-24-generic-pae
 697.7GB: initrd.img
 864.6GB: vmlinuz
```

---

### Post by hansolo4949 on 2011-01-15
This might help: [code]sudo update-grub2[\code]

If it doesn't, how did you install Ubuntu? did you use the default options, or did you use the custom partitioning option?

---

### Post by hansolo4949 on 2011-01-15
This might help: [code]sudo update-grub2[\code]

If it doesn't, how did you install Ubuntu? did you use the default options, or did you use the custom partitioning option?

---

### Post by merlec on 2011-01-15
Hanssolo,
I just used the defaults for the most part. It gave me the option of accepting a default size for the Ubuntu partition and I dragged it to a little to make it about 300GB. I will try the code below and see what happens.

This might help: [code]sudo update-grub2[\code]

---

### Post by merlec on 2011-01-15
Hansolo4949,
No change with your suggestion. I rand boot_info_script055.sh per Quackers rquest which I think showed an issue and I am waiting for a response on that.

---

### Post by Quackers on 2011-01-15
Hi merlec, I don't see anything wrong with your boot script output. All of Windows boot files are present, the boot flag is set correctly, and Windows is being picked up by the os-prober.
Is this the first time you have tried to boot Windows since installing Ubuntu?

---

### Post by merlec on 2011-01-15
Quackers,
Yes, it was the first time after installing Ubuntu. I have tried a few times since but only get the blinking cursor in the top left corner of the screen.

---

### Post by Quackers on 2011-01-15
We can try re-installing grub from within your Ubuntu system with the following commands. Please copy/paste them into the terminal one at a time, pressing enter after each line.
```
sudo mount /dev/sda5 /mnt
sudo grub-install --root-directory=/mnt /dev/sda
```
If that runs without reporting errors please then run ```
sudo update-grub
``` and watch to see that the Windows Loader is picked up when grub.cfg is run. If it is reboot and try booting Windows.

---

### Post by merlec on 2011-01-15
Well, That didn't go too well. Everything went OK with no errors and after I rebooted, I get a command prompt..

error:file not found
grub rescue>_

I'm dead in the water now Haha... I thought this would go easy.
Is there a way to "rescue" ??

---

### Post by Quackers on 2011-01-15
Please re-run the boot script from the live cd desktop and post the results.

---

### Post by merlec on 2011-01-15
I just re-ran the last command that you gave me from the live CD. After doing it I realized that may not have been what you had asked. I am going to try to reboot then run the boot script.
What is that warning about Sector 32??

Here is what I ran from the live cd--
ubuntu@ubuntu:~$ sudo mount /dev/sda5 /mnt
ubuntu@ubuntu:~$ sudo mount /dev/sda5 /mnt
mount: /dev/sda5 already mounted or /mnt busy
mount: according to mtab, /dev/sda5 is already mounted on /mnt
ubuntu@ubuntu:~$ sudo grub-install --root-directory=/mnt /dev/sda
/usr/sbin/grub-setup: warn: Sector 32 is already in use by FlexNet; avoiding it.  This software may cause boot or other problems in future.  Please ask its authors not to store data in the boot track..
Installation finished. No error reported.

---

### Post by Quackers on 2011-01-15
The boot script would be good, thanks.
Is this a Dell machine? Does it have Dell data safe?

---

### Post by merlec on 2011-01-15
OK, I now get the boot menu again and can boot into Ubuntu but still not Win XP. I will try the boot script from the live CD next.

Odd thing that happened was I tried Winxp first and got the black screen with cursor, then rebooted and selected Ubuntu and got the same screen for only a few seconds...?  More soon

---

### Post by merlec on 2011-01-15
Sorry-- no its not a dell. Only a generic PC that I built.

---

### Post by Quackers on 2011-01-15
You can run the script from the normal Ubuntu desktop. I suggested the live cd because I thought you couldn't boot Ubuntu any more

---

### Post by Quackers on 2011-01-15
Do you have Adobe Photoshop installed in Windows?

---

### Post by merlec on 2011-01-15
Here is the latest boot script file. No photoshop. The only software that I had was Scansnap software for my scanner and not too much else. I just subscribed to the free version of iDrive last week and I had a trial of Mosey online backup. nothing else that I can think of.




```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #5 for (,msdos5)/boot/grub.

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
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda6: _________________________________________________________________________

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

/dev/sda1    *             63 1,361,365,412 1,361,365,350   7 HPFS/NTFS
/dev/sda2       1,361,367,038 1,953,523,711   592,156,674   5 Extended
/dev/sda5       1,361,367,040 1,929,457,663   568,090,624  83 Linux
/dev/sda6       1,929,459,712 1,953,523,711    24,064,000  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        0ED8BAE6D8BACAEB                       ntfs                                     
/dev/sda2: PTTYPE="dos" 
/dev/sda5        8dfbccf0-cf2f-47b3-af74-2a5ed0542851   ext4                                     
/dev/sda6        0298812b-d0cf-42cb-a19b-36bea106e31f   swap                                     
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda5        /                        ext4       (rw,errors=remount-ro,commit=0)


================================ sda1/boot.ini: ================================

[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /fastdetect /NoExecute=OptIn 

=========================== sda5/boot/grub/grub.cfg: ===========================

#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s $prefix/grubenv ]; then
  set have_grubenv=true
  load_env
fi
set default="0"
if [ "${prev_saved_entry}" ]; then
  set saved_entry="${prev_saved_entry}"
  save_env saved_entry
  set prev_saved_entry=
  save_env prev_saved_entry
  set boot_once=true
fi

function savedefault {
  if [ -z "${boot_once}" ]; then
    saved_entry="${chosen}"
    save_env saved_entry
  fi
}

function recordfail {
  set recordfail=1
  if [ -n "${have_grubenv}" ]; then if [ -z "${boot_once}" ]; then save_env recordfail; fi; fi
}

function load_video {
  insmod vbe
  insmod vga
}

insmod part_msdos
insmod ext2
set root='(hd0,msdos5)'
search --no-floppy --fs-uuid --set 8dfbccf0-cf2f-47b3-af74-2a5ed0542851
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos5)'
search --no-floppy --fs-uuid --set 8dfbccf0-cf2f-47b3-af74-2a5ed0542851
set locale_dir=($root)/boot/grub/locale
set lang=en
insmod gettext
if [ "${recordfail}" = 1 ]; then
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
menuentry 'Ubuntu, with Linux 2.6.35-24-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set 8dfbccf0-cf2f-47b3-af74-2a5ed0542851
    linux    /boot/vmlinuz-2.6.35-24-generic-pae root=UUID=8dfbccf0-cf2f-47b3-af74-2a5ed0542851 ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-24-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.35-24-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set 8dfbccf0-cf2f-47b3-af74-2a5ed0542851
    echo    'Loading Linux 2.6.35-24-generic-pae ...'
    linux    /boot/vmlinuz-2.6.35-24-generic-pae root=UUID=8dfbccf0-cf2f-47b3-af74-2a5ed0542851 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-24-generic-pae
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set 8dfbccf0-cf2f-47b3-af74-2a5ed0542851
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set 8dfbccf0-cf2f-47b3-af74-2a5ed0542851
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Professional (on /dev/sda1)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 0ed8bae6d8bacaeb
    drivemap -s (hd0) ${root}
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

### BEGIN /etc/grub.d/41_custom ###
if [ -f  $prefix/custom.cfg ]; then
  source $prefix/custom.cfg;
fi
### END /etc/grub.d/41_custom ###

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
UUID=8dfbccf0-cf2f-47b3-af74-2a5ed0542851 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=0298812b-d0cf-42cb-a19b-36bea106e31f none            swap    sw              0       0

=================== sda5: Location of files loaded by Grub: ===================


 864.6GB: boot/grub/core.img
 907.6GB: boot/grub/grub.cfg
 697.7GB: boot/initrd.img-2.6.35-24-generic-pae
 864.6GB: boot/vmlinuz-2.6.35-24-generic-pae
 697.7GB: initrd.img
 864.6GB: vmlinuz
```

---

### Post by Quackers on 2011-01-15
I understand that the Flexnet in sector 32 is often caused by DRM protection used by some programs. They are not supposed to write in the mbr of a disc, but some do.
Your boot script looks normal to me.
We're going to need to fix the mbr with a Windows XP repair disc. Do you have one?
You need to enter the recovery console and then in the command prompt enter ```
fixmbr
```
It may also be worth running a chkdsk from the command prompt by entering ```
chkdsk C: /r
``` 
This should be run until no errors are reported.
Then reboot and, hopefully, Windows will then boot directly (no grub).
If that goes ok, you can then re-install grub from the live cd with the same messages as before.

---

### Post by merlec on 2011-01-15
Quackers,
Thank You so much for your time. I dont have a windows repair disk but a friend at work on Monday will have one and hopefully can help. He has been using Ubuntu for years and was the one that got me started a few days ago. I'll post the results Monday evening.

---

### Post by Quackers on 2011-01-15
Ok, and good luck :-)
You're welcome!

---

### Post by presence1960 on 2011-01-15
To replicate what fixmbr does from windows recovery console you can do this from Ubuntu:

Boot to Ubuntu. Open a terminal and run ```
sudo apt-get install lilo
```

Ignore the warning(s) and proceed.

Next from terminal run ```
sudo lilo -M /dev/sda mbr
```
This will install a generic windows bootloader on the MBR. 

Reboot and if Windows is otherwise OK you will boot right to windows. Then you can reinstall GRUB.

---

### Post by Quackers on 2011-01-15
Good thinking presence1960, I forgot about Lilo. :-) It's late here :wink:  That's well worth a try :-)

---

### Post by presence1960 on 2011-01-15
> **Quackers said:**
> Good thinking presence1960, I forgot about Lilo. :-) It's late here :wink:  That's well worth a try :-)

Thanks, just trying to be of service  :)

P.S. meierfra taught me that one!

---

### Post by Quackers on 2011-01-15
Very welcome too :-)
merlec, if Lilo gets Windows booting, you can run a chkdsk from within Windows, see below. It may need one (at least!).
[http://support.microsoft.com/kb/315265](http://support.microsoft.com/kb/315265)

---

### Post by merlec on 2011-01-16
I followed the lilo suggestion and now I only get a blinking cursor when booting after the POST. No boot to anywhere. I think I'll try reinstalling grub as I was shown earlier in the thread. I'm guessing my winXP install may be history now so it may be a good time to reformat and give Win7 a try. I liked what I saw and was hoping it would work but without sound, printer, and scanner, I will still need windows.

---

### Post by merlec on 2011-01-16
I tried reinstalling grub and got the following.. Tell me if I am totally hosed now and I'll just move on. Thanks for all the help!

ubuntu@ubuntu:~$ sudo mount /dev/sda5 /mnt
ubuntu@ubuntu:~$ sudo grub-install --root-directory=/mnt /dev/sda
/usr/sbin/grub-setup: warn: Sector 32 is already in use by FlexNet; avoiding it.  This software may cause boot or other problems in future.  Please ask its authors not to store data in the boot track..
Installation finished. No error reported.
ubuntu@ubuntu:~$ sudo update-grub
/usr/sbin/grub-probe: error: cannot find a device for / (is /dev mounted?).
ubuntu@ubuntu:~$

---

### Post by wilee-nilee on 2011-01-16
Here is a thread on flexnet, probably worth looking at.
[http://ubuntuforums.org/showthread.php?t=1661254](http://ubuntuforums.org/showthread.php?t=1661254)

---

### Post by hansolo4949 on 2011-01-16
Hookayyy, you're computer is pretty screwed up. You should format it, then install the OSes again. Remember, windows _*first*_, then Ubuntu, so you don't screw anything up. For future reference, you should try the update-grub2 command first, then immedately afterward, if it doesn't work, boot from a recovery cd and rum fixmbr and fixboot. I have done that several times on this computer when I messed Ubuntu up:D, and it worked perfectly, and I just had to reinstall Ubuntu.

---

### Post by Quackers on 2011-01-16
sudo update-grub cannot be run from the live cd desktop.
Grub should be re-installed now.

---

### Post by merlec on 2011-01-16
Well, thats a problem since I can only boot into the live CD at this time. I followed willie-nillie advice and looked at the thread about sector 63 and since things are messed up anyway I went ahead and wiped sector 63 per the code listed. So how can I reinstall Grub? can I opt to install Ubuntu from the live CD again?? I'm getting weak but not ready to give up just yet!

---

### Post by Quackers on 2011-01-16
Try re-installing grub again with those commands that you used before. As Flexnet should now be gone you should be ok. However, I suspect something is wrong with XP if Lilo couldn't boot it. Also, I suspect sector 32 will be written to again if you boot XP. Your choice :-) I might give 7 a go (in fact, I have :-) )

---

### Post by merlec on 2011-01-16
After the last post, I rebooted and the grub boot menu was back. XP still no go but I was able to boot back into my installed Ubuntu. What a ride. A few errors about something missing flashed by but am now at least back into Ubuntu. I'll get my Ubuntu/Windows expert to see if he can restore xp and if not.. reformat and try it again. 

Thanks to Quackers, presence1960, hansolo4949, and wilee-nilee, for all your help!

---

### Post by Quackers on 2011-01-16
You're welcome. Good luck :-)

---

### Post by hansolo4949 on 2011-01-16
Sure! I am happy we helped, and as Quackers said, good luck! may the Ubuntu be with you! (unoriginal, I know, but what should I say, may the computer gremlins be with you?:D)

---

