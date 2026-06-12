---
title: "New Costum build Desktop, IDE SATA HDD Problems"
date: 2011-02-01
forum: Installation &amp; Upgrades
---

### Post by LatinHacker on 2011-02-01
I have a problem, my screen goes to de "Grub rescue>" saying "Unknown filesystem"

My Boot info from the live CD says:

```

                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #6 for /boot/grub.
 => No boot loader is installed in the MBR of /dev/sdb
 => Windows is installed in the MBR of /dev/sdc

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot/BCD

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows 7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe

sda3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda6: _________________________________________________________________________

    File system:       ext2
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.1 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb2: _________________________________________________________________________

    File system:       ext2
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdc1: _________________________________________________________________________

    File system:       ext2
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048       206,847       204,800   7 HPFS/NTFS
/dev/sda2             206,848   731,006,975   730,800,128   7 HPFS/NTFS
/dev/sda3         731,021,821   976,768,064   245,746,244   5 Extended
/dev/sda5         731,021,823   764,453,024    33,431,202  82 Linux swap / Solaris
/dev/sda6         764,453,088   976,768,064   212,314,977  83 Linux


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63   156,537,359   156,537,297   7 HPFS/NTFS
/dev/sdb2         156,537,360   976,768,064   820,230,705  83 Linux


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdc1                  63 1,953,520,064 1,953,520,002  83 Linux


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        DE74E88F74E86BA9                       ntfs       System Reserved               
/dev/sda2        C8B4F5E6B4F5D742                       ntfs                                     
/dev/sda3: PTTYPE="dos" 
/dev/sda5        a5eea473-38c5-46dc-8249-515e0f31b59f   swap                                     
/dev/sda6        8ce055a2-ff5c-417d-82f7-43bdaffa3ed5   ext2                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        589BEA8471065D9C                       ntfs       LatinHacker_75                
/dev/sdb2        bfe89584-3960-407d-b53b-7ea07c3c28c8   ext2       LatinHacker_450               
/dev/sdb: PTTYPE="dos" 
/dev/sdc1        786cc81e-292d-4f6a-95ce-7ac16b4cb45f   ext2       LatinHacker_USB               
/dev/sdc: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sdc1        /media/LatinHacker_USB   ext2       (rw,nosuid,nodev,uhelper=udisks)
/dev/sdb1        /media/LatinHacker_75    fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sdb2        /media/LatinHacker_450   ext2       (rw,nosuid,nodev,uhelper=udisks)


=========================== sda6/boot/grub/grub.cfg: ===========================

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
set root='(hd0,6)'
search --no-floppy --fs-uuid --set 8ce055a2-ff5c-417d-82f7-43bdaffa3ed5
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
set root='(hd0,6)'
search --no-floppy --fs-uuid --set 8ce055a2-ff5c-417d-82f7-43bdaffa3ed5
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
menuentry 'Ubuntu, with Linux 2.6.32-28-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,6)'
    search --no-floppy --fs-uuid --set 8ce055a2-ff5c-417d-82f7-43bdaffa3ed5
    linux    /boot/vmlinuz-2.6.32-28-generic-pae root=/dev/sda6 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-28-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.32-28-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,6)'
    search --no-floppy --fs-uuid --set 8ce055a2-ff5c-417d-82f7-43bdaffa3ed5
    echo    'Loading Linux 2.6.32-28-generic-pae ...'
    linux    /boot/vmlinuz-2.6.32-28-generic-pae root=/dev/sda6 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-28-generic-pae
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd0,6)'
    search --no-floppy --fs-uuid --set 8ce055a2-ff5c-417d-82f7-43bdaffa3ed5
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd0,6)'
    search --no-floppy --fs-uuid --set 8ce055a2-ff5c-417d-82f7-43bdaffa3ed5
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" {
    insmod ntfs
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set de74e88f74e86ba9
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
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda6 during installation
UUID=8ce055a2-ff5c-417d-82f7-43bdaffa3ed5 /               ext2    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=a5eea473-38c5-46dc-8249-515e0f31b59f none            swap    sw              0       0

=================== sda6: Location of files loaded by Grub: ===================


 480.6GB: boot/grub/core.img
 480.6GB: boot/grub/grub.cfg
 480.5GB: boot/initrd.img-2.6.32-28-generic-pae
 480.4GB: boot/vmlinuz-2.6.32-28-generic-pae
 480.5GB: initrd.img
 480.4GB: vmlinuz

```

And when I tried:

> 
I would recommend to try once again press and hold down Shift key from  your Bios screen. You can try with both the Shift keys one by one and  see if it takes you to Grub menu.

Or if not, I wonder if Grub was correctly installed. For diagnosing  that, we need to you to boot an Ubuntu Live CD/USB (desktop edition) in  Try mode and post the output of bootinfoscript as per instructions here.

[http://bootinfoscript.sourceforge.net]("http://bootinfoscript.sourceforge.net/")


```

                                                                           ** boot_info_script**  is a bash script which searches all hard drives attached to the  computer for information related to booting and displays it in a  convenient format. Its primary use is for troubleshooting booting  problems.                                  
 			  ** How to use the boot info script**

  
[LIST]
[*] Boot into any Linux based operating system, LiveCD or LiveUSB with an Internet connection.
[*]  [                                                 Download the Boot Info Script ]("http://sourceforge.net/projects/bootinfoscript")
[*] Open a terminal (Applications>Accessories>Terminal in Gnome) and type           sudo bash [path/to/the/download_folder]/boot_info_script*.sh  For example if you downloaded the file to the desktop, use          sudo bash ~/Desktop/boot_info_script*.sh
[*] If your operation system does not use sudo, use              su 
     bash ~/Desktop/boot_info_script*.sh
[*] You will now have the file RESULTS.txt in the same directory as     the script.[SIZE=-1] But if the script is inside a system directory (like     /usr or /etc) RESULTS.txt will be in the home directory.[/SIZE]
[*] If you already have an existing RESULTS.txt, subsequent  files will be called RESULTS1.txt, RESULTS2.txt,...
[*] Open RESULTS.txt in your favorite text editor.
[*] If you came here from a Linux forum, paste the content of  RESULTS.txt into your next post. Make sure to use the appropriate  formating.   For example in the Ubuntu forums click on the code tags (the symbol #)  before pasting RESULTS.txt.
[/LIST]
                                                                                         

```

it gave me this:

```

ubuntu@ubuntu:~$ sudo grub-install --root-directory=/mnt /dev/sda
/usr/sbin/grub-probe: error: cannot find a device for /mnt/boot/grub (is /dev mounted?).
No path or device is specified.
Try `/usr/sbin/grub-probe --help' for more information.
Auto-detection of a filesystem module failed.
Please specify the module with the option `--modules' explicitly.

```My guess is that because it is loading from a SATA drive in the 4th  position and this new computer (custom build) is more likely to work  with a HDD in the 1st or 3rd SSATA position, I most change something,  but the CMOS/BIOS is set to start from sda... not sure what to do.

Update...

 I am attempting to install the Grub on sda1 instead of sda6.  No video  card issues here, Linux and Windows cannot read the HDD once I installed  either.](*,)

Update...

It did not work, same result.

---

### Post by oldfred on 2011-02-01
I do not see anything in the boot script that looks wrong.

Do not install grub to a partition. If you did install grub to sda1 or sda2 windows will be broken as those partitions have to have windows boot loader. You install grub2 to the MBR of a drive like sda not sda6, the partition.

You have to mount the partition containing the rest of grub2, so the grub in the MBR knows where to go to continue to boot.

#Comments are anything after the #, enter commands in terminal session
#Install MBR from LiveCD, Ubuntu install on sda6 and want grub2 in drive sda's MBR:
#Find linux partition, change sda6 if not correct:
sudo fdisk -l
#confirm that linux is sda6 from fdisk
[COLOR=Red]sudo mount /dev/sda6 /mnt
sudo grub-install --root-directory=/mnt/ /dev/sda[/COLOR]
#If that returns any errors run:
sudo grub-install --recheck --root-directory=/mnt/ /dev/sda
# After rebooting into working system
sudo update-grub

Spaces are also important, so it is best to copy the commands if possible.

---

### Post by LatinHacker on 2011-02-01
> **oldfred said:**
> I do not see anything in the boot script that looks wrong.

Do not install grub to a partition. If you did install grub to sda1 or sda2 windows will be broken as those partitions have to have windows boot loader. You install grub2 to the MBR of a drive like sda not sda6, the partition.

You have to mount the partition containing the rest of grub2, so the grub in the MBR knows where to go to continue to boot.

#Comments are anything after the #, enter commands in terminal session
#Install MBR from LiveCD, Ubuntu install on sda6 and want grub2 in drive sda's MBR:
#Find linux partition, change sda6 if not correct:
sudo fdisk -l
#confirm that linux is sda6 from fdisk
[COLOR=Red]sudo mount /dev/sda6 /mnt
sudo grub-install --root-directory=/mnt/ /dev/sda[/COLOR]
#If that returns any errors run:
sudo grub-install --recheck --root-directory=/mnt/ /dev/sda
# After rebooting into working system
sudo update-grub

Spaces are also important, so it is best to copy the commands if possible.


Everything went well, it installed the grub on sda, passed the check with no errors, and yet, when I tried to boot without the LiveCD, it told me the same thing:

> 
error: unknown filesystem
grub rescue>



This did not work, but I was able to make it work temporarily by installing Ubuntu 10.04 on a 4Gbs Flash Drive, I had to configured the BIOS to boot from it... This most mean that I have to have a SSATA 3 - 6 GBs/s as my primary HDD.  Windows 7 is still not able to boot, it stays in a black screen and after 1 or 2 minutes, comes back to the Flash Drive Grub. As soon as I am able to get the new HDD, I will post the results here.

---

### Post by oldfred on 2011-02-02
I do not know if they have updated to the 6GB/s standard. Some users a month or two ago had to change to the 3GB ports to get the systems to work. Not sure if it was BIOS, motherboard hardware or Ubuntu.

Other solutions to many issues:
Grub Rescue Prompt Megathread - drs305
[http://ubuntuforums.org/showthread.php?t=1594052](http://ubuntuforums.org/showthread.php?t=1594052)

---

### Post by LatinHacker on 2011-02-05
I have to informed that with the SATA HDD it does work, my new computer its up and running, not using a dual boot anymore, Windows 7 on a Virtual Box... SOLVED.:lolflag:

Thanks to ALL for your input!!!

---

