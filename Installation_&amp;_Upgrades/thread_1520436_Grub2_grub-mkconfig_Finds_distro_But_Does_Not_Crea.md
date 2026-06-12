---
title: "Grub2: grub-mkconfig Finds distro But Does Not Create menuentry"
date: 2010-06-29
forum: Installation &amp; Upgrades
---

### Post by retroartist on 2010-06-29
I attach below the partial output from running grub-mkconfig without the option to create the configuration file.  As you will see from the last few lines grub-mk-config has found Ubuntu 10.4 on dev/sda5 but has failed to create a menu entry. The output is the same using update-grub (although it does not post to the terminal screen).   I suspect that the reason for the lack of the menu entry may be that dev/sda5 is a partition within an extended partition and that grub2 requires operating systems to be placed on primary partitions, however, I am not certain of this... can anyone help??

I have and Acer Ferrari One and I am trying to set up multi boot without disturbing the Windows boot.  I have resized the Windows partition and loaded Ubuntu 32bit within partitions inside the extended partition that was created from the unallocated space. I used the advanced option on page 8 of the Ubuntu install so that I could load Ubuntu 32bit without loading grub2.  This was installed on dev/sda5.  I then loaded Ubuntu 10.4 64bit complete with grub2 onto the sdhc in the Acer. After this I used grub-mkconfig to update the grub configuration file, however, as you see that while it could find the 32bit Ubuntu it did not create a menu entry.

-retroartist-

n
> 

### BEGIN /etc/grub.d/10_linux ###
Found linux image: /boot/vmlinuz-2.6.32-21-generic
Found initrd image: /boot/initrd.img-2.6.32-21-generic
menuentry 'Ubuntu, with Linux 2.6.32-21-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set e90d4f26-de8b-4ae5-a182-c9125ec809ee
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=e90d4f26-de8b-4ae5-a182-c9125ec809ee ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set e90d4f26-de8b-4ae5-a182-c9125ec809ee
    echo    'Loading Linux 2.6.32-21-generic ...'
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=e90d4f26-de8b-4ae5-a182-c9125ec809ee ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
Found memtest86+ image: /boot/memtest86+.bin
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set e90d4f26-de8b-4ae5-a182-c9125ec809ee
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set e90d4f26-de8b-4ae5-a182-c9125ec809ee
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
Found Windows Vista (loader) on /dev/sda1
menuentry "Windows Vista (loader) (on /dev/sda1)" {
    insmod ntfs
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set bc8465f58465b296
    chainloader +1
}
Found Windows 7 (loader) on /dev/sda2
menuentry "Windows 7 (loader) (on /dev/sda2)" {
    insmod ntfs
    set root='(hd0,2)'
    search --no-floppy --fs-uuid --set 04366770366761a2
    chainloader +1
}
Found Ubuntu 10.04 LTS (10.04) on /dev/sda5
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###
done

---

### Post by arrange on 2010-06-29
Can you post the output of the [boot_info_script]("https://sourceforge.net/projects/bootinfoscript/")? (If you don't know how to run the script, [look here]("http://bootinfoscript.sourceforge.net/").)

---

### Post by retroartist on 2010-06-29
Thanks for picking up the thread.... the output from bootinfoscript is.....
> 
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda
 => Grub 2 is installed in the MBR of /dev/sdb and looks on the same drive in 
    partition #1 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /BOOTMGR /BOOT/BCD

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot/BCD

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe

sda4: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04 LTS
    Boot files/dirs:   /etc/fstab

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda7: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb2: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1               2,048    25,167,871    25,165,824  27 Hidden HPFS/NTFS
/dev/sda2    *     25,167,872    25,372,671       204,800   7 HPFS/NTFS
/dev/sda3          25,372,672   263,112,064   237,739,393   7 HPFS/NTFS
/dev/sda4         263,112,631   488,392,064   225,279,434   5 Extended
/dev/sda5         263,112,633   284,736,059    21,623,427  83 Linux
/dev/sda6         284,736,123   294,101,954     9,365,832  82 Linux swap / Solaris
/dev/sda7         294,102,018   488,392,064   194,290,047  83 Linux


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 16.1 GB, 16068378624 bytes
255 heads, 63 sectors/track, 1953 cylinders, total 31383552 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63    11,855,969    11,855,907  83 Linux
/dev/sdb2          11,855,970    31,374,944    19,518,975  83 Linux


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        BC8465F58465B296                       ntfs       PQSERVICE                     
/dev/sda2        04366770366761A2                       ntfs       SYSTEM RESERVED               
/dev/sda3        01CB0FCD3809A6A0                       ntfs       Acer                          
/dev/sda4: PTTYPE="dos" 
/dev/sda5        183b81e8-4813-4cd0-a18e-e6ed3f06d5e0   ext3                                     
/dev/sda6        a95bba1b-f639-49ff-bde7-f410fab4f9d0   swap                                     
/dev/sda7        fc1a0fcb-a891-49df-85b6-59e285d96a8b   ext3                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        e90d4f26-de8b-4ae5-a182-c9125ec809ee   ext3                                     
/dev/sdb2        7171c515-4714-4117-967e-09cf5dbd80a5   ext3                                     
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sdb1        /                        ext3       (rw,errors=remount-ro)
/dev/sdb2        /home                    ext3       (rw)


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
UUID=183b81e8-4813-4cd0-a18e-e6ed3f06d5e0 /               ext3    errors=remount-ro 0       1
/dev/sdc1       /boot           ext3    defaults        0       2
# /home was on /dev/sda7 during installation
UUID=fc1a0fcb-a891-49df-85b6-59e285d96a8b /home           ext3    defaults        0       2
# swap was on /dev/sda6 during installation
UUID=a95bba1b-f639-49ff-bde7-f410fab4f9d0 none            swap    sw              0       0

=========================== sdb1/boot/grub/grub.cfg: ===========================

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
set root='(hd1,1)'
search --no-floppy --fs-uuid --set e90d4f26-de8b-4ae5-a182-c9125ec809ee
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
set root='(hd1,1)'
search --no-floppy --fs-uuid --set e90d4f26-de8b-4ae5-a182-c9125ec809ee
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
menuentry 'Ubuntu, with Linux 2.6.32-21-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set e90d4f26-de8b-4ae5-a182-c9125ec809ee
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=e90d4f26-de8b-4ae5-a182-c9125ec809ee ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set e90d4f26-de8b-4ae5-a182-c9125ec809ee
    echo    'Loading Linux 2.6.32-21-generic ...'
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=e90d4f26-de8b-4ae5-a182-c9125ec809ee ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set e90d4f26-de8b-4ae5-a182-c9125ec809ee
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set e90d4f26-de8b-4ae5-a182-c9125ec809ee
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows Vista (loader) (on /dev/sda1)" {
    insmod ntfs
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set bc8465f58465b296
    chainloader +1
}
menuentry "Windows 7 (loader) (on /dev/sda2)" {
    insmod ntfs
    set root='(hd0,2)'
    search --no-floppy --fs-uuid --set 04366770366761a2
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
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/sdb1       /               ext3    errors=remount-ro 0       1
# /home was on /dev/sdb2 during installation
UUID=7171c515-4714-4117-967e-09cf5dbd80a5 /home           ext3    defaults        0       2
# swap was on /dev/sda6 during installation
UUID=a95bba1b-f639-49ff-bde7-f410fab4f9d0 none            swap    sw              0       0

=================== sdb1: Location of files loaded by Grub: ===================


   1.8GB: boot/grub/core.img
   1.8GB: boot/grub/grub.cfg
   1.8GB: boot/initrd.img-2.6.32-21-generic
   2.1GB: boot/vmlinuz-2.6.32-21-generic
   1.8GB: initrd.img
   2.1GB: vmlinuz
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda4

00000000  ff ff ff ff ff ff ff ff  ff ff ff ff ff ff ff ff  |................|
*
000001b0  ff ff ff ff ff ff ff ff  ff ff ff ff ff ff 00 fe  |................|
000001c0  ff ff 83 fe ff ff 02 00  00 00 83 f2 49 01 00 fe  |............I...|
000001d0  ff ff 05 fe ff ff 85 f2  49 01 87 e9 8e 00 00 00  |........I.......|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200

---

### Post by ajgreeny on 2010-06-29
The information in the boot info summary for sda5 seems wrong to me as it mentions fstab, but not any boot files.

> File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04 LTS
    [COLOR=Red]Boot files/dirs:   /etc/fstab[/COLOR]

So far so good.  The problem is, however, that I have no idea how you can put that right.  The fstab file just tells the booting system what to mount, but beyond that has no real effect on booting the system.

I hope someone else can give you more information.

By the way, a linux OS can boot without problem from an extended partition.  Windows, however, not being quite so clever, can not do that. I don't think that has any bearing on your problem.

---

### Post by arrange on 2010-06-29
Can you please open up a Terminal and hook up to *syslog*```
tail -f /var/log/syslog
```Then open another Terminal and type```
sudo linux-boot-prober /dev/sda5
```Then copy the output from both terminals here. Add the contents of the */boot* directory on */dev/sda5*.

---

### Post by retroartist on 2010-06-29
Thanks for your follow up.... the outputs are as follows.... any thoughts or ideas will be appreciated...
> 
davidlinda@davidlinda-linux:~$ tail -f /var/log/syslog
Jun 29 20:06:24 davidlinda-linux kernel: [ 5340.506145] usbcore: registered new interface driver usbhid
Jun 29 20:06:24 davidlinda-linux kernel: [ 5340.506150] usbhid: v2.6:USB HID core driver
Jun 29 20:17:01 davidlinda-linux CRON[3264]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Jun 29 20:32:20 davidlinda-linux kernel: [ 6896.733978] usb 3-3: USB disconnect, address 2
Jun 29 20:32:56 davidlinda-linux anacron[3335]: Anacron 2.3 started on 2010-06-29
Jun 29 20:32:56 davidlinda-linux anacron[3335]: Normal exit (0 jobs run)
Jun 29 20:53:55 davidlinda-linux kernel: [ 8191.670075] usb 3-3: new low speed USB device using ohci_hcd and address 3
Jun 29 20:53:55 davidlinda-linux kernel: [ 8191.861313] usb 3-3: configuration #1 chosen from 1 choice
Jun 29 20:53:55 davidlinda-linux kernel: [ 8191.869232] input: USB OpticalWheel Mouse as /devices/pci0000:00/0000:00:12.0/usb3/3-3/3-3:1.0/input/input11
Jun 29 20:53:55 davidlinda-linux kernel: [ 8191.871651] generic-usb 0003:04FC:0003.0002: input,hidraw0: USB HID v1.10 Mouse [USB OpticalWheel Mouse] on usb-0000:00:12.0-3/input0
Jun 29 20:57:44 davidlinda-linux linux-boot-prober: debug: running /usr/lib/linux-boot-probes/50mounted-tests
Jun 29 20:57:44 davidlinda-linux kernel: [ 8420.699242] kjournald starting.  Commit interval 5 seconds
Jun 29 20:57:44 davidlinda-linux kernel: [ 8420.699271] EXT3-fs: mounted filesystem with ordered data mode.
Jun 29 20:57:44 davidlinda-linux 50mounted-tests: debug: found boot partition /dev/sdc1 for linux system on /dev/sda5, but cannot map to existing device
Jun 29 20:57:44 davidlinda-linux 50mounted-tests: debug: running /usr/lib/linux-boot-probes/mounted/40grub /dev/sda5 /dev/sda5 /var/lib/os-prober/mount ext3
Jun 29 20:57:44 davidlinda-linux 50mounted-tests: debug: running /usr/lib/linux-boot-probes/mounted/40grub2 /dev/sda5 /dev/sda5 /var/lib/os-prober/mount ext3
Jun 29 20:57:44 davidlinda-linux 50mounted-tests: debug: running /usr/lib/linux-boot-probes/mounted/50lilo /dev/sda5 /dev/sda5 /var/lib/os-prober/mount ext3
Jun 29 20:57:44 davidlinda-linux 50mounted-tests: debug: running /usr/lib/linux-boot-probes/mounted/90fallback /dev/sda5 /dev/sda5 /var/lib/os-prober/mount ext3
Jun 29 20:57:54 davidlinda-linux linux-boot-prober: debug: running /usr/lib/linux-boot-probes/mountedand...
> 
davidlinda@davidlinda-linux:~$ sudo linux-boot-prober /dev/sda5
[sudo] password for davidlinda: 
Sorry, try again.
[sudo] password for davidlinda: 
davidlinda@davidlinda-linux:~$ 

---

### Post by arrange on 2010-06-29
Your problem really seems to be missing boot files. Can you mount the */dev/sda5* partition (for instance via *Places* on the panel) and show us the contents of its **/boot** directory?

---

### Post by retroartist on 2010-06-29
Thanks ..... you are right there is nothing in the /boot directory on /dev/sda5...I should have checked...I installed the 32 bit Ubuntu as described in the original thread as I do not want to place grub on the mai hard drive with Windows... is there any way I can repopulate the boot directory.... the live Ubuntu usb  does not obviously have anything that I can simply copy across.

-retroartist-

---

### Post by arrange on 2010-06-29
Well, I don't really know why your */boot* directory is empty, as it si not directly connected with Grub itself. The kernel images, which are supposed to be there, are necessary for the system to boot.

You can try the following method, I just changed the device to */dev/sda5* and the kernel to **2.6.32-21**.
[http://ubuntuforums.org/showpost.php?p=6252617&postcount=2](http://ubuntuforums.org/showpost.php?p=6252617&postcount=2)
```
sudo mount /dev/sda5 /mnt
sudo mount --bind /dev /mnt/dev
sudo mount --bind /proc /mnt/proc
sudo mount --bind /sys /mnt/sys
sudo chroot /mnt /bin/bash
apt-get install linux-headers-2.6.32-21-generic linux-image-2.6.32-21-generic
```

---

### Post by retroartist on 2010-06-29
Thanks for your reply... I have tried the suggestion but the output was not as expected.. despite having an empty boot file on dev/sda5 

The input/output in terminal was as follows....

> davidlinda@davidlinda-linux:~$ sudo mount /dev/sda5 /mnt
[sudo] password for davidlinda: 
davidlinda@davidlinda-linux:~$ sudo mount --bind /dev /mnt/dev
davidlinda@davidlinda-linux:~$ sudo mount --bind /proc /mnt/proc
davidlinda@davidlinda-linux:~$ sudo mount --bind /sys /mnt/sys
davidlinda@davidlinda-linux:~$ sudo chroot /mnt /bin/bash
root@davidlinda-linux:/# apt-get install linux-headers-2.6.32-21-generic linux-image-2.6.32-21-generic
Reading package lists... Done
Building dependency tree       
Reading state information... Done
linux-headers-2.6.32-21-generic is already the newest version.
linux-headers-2.6.32-21-generic set to manually installed.
linux-image-2.6.32-21-generic is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
root@davidlinda-linux:/# 

The output from df immediately afterwards was....
> 
root@davidlinda-linux:/# df
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sda5             10641980   2095008   8006388  21% /
none                    893844       328    893516   1% /dev
none                    893844       328    893516   1% /dev/pts
none                    893844       328    893516   1% /dev/shm
none                  10641980   2095008   8006388  21% /var/run
none                  10641980   2095008   8006388  21% /var/lock
none                  10641980   2095008   8006388  21% /lib/init/rw
none                  10641980   2095008   8006388  21% /var/lib/ureadahead/debugfs
root@davidlinda-linux:/# 

Any thoughts would be appreciated...

-retroartist-

---

### Post by arrange on 2010-06-29
OK, then still in the *chroot* environment do```
apt-get --reinstall install linux-image-2.6.32-21-generic
```then look into the */boot* directory.

---

### Post by retroartist on 2010-06-29
Thanks for your continued advice - unfortunately there are still problems.....

> root@davidlinda-linux:/# apt-get --reinstall install linux-image-2.6.32-21-generic
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reinstallation of linux-image-2.6.32-21-generic is not possible, it cannot be downloaded.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
root@davidlinda-linux:/# 

(its not a physical problem - I was still connected to the web - I presume the sources list should be ok)
-retroartist-

---

### Post by oldfred on 2010-06-29
Rather than downloading a specific package lets just get the newest kernel available.

From your chrooted into sda5.

#refresh
apt-get update #resync package index
apt-get upgrade #newest versions of all packages update must be run first
#would upgrade you to the latest kernel in the repositories
#dist-upgrade is also able to remove existing packages if required
apt-get dist-upgrade
apt-get -f install
dpkg --configure -a

---

### Post by retroartist on 2010-06-29
Thanks for your help.....Unfortunately there are still problems....

> root@davidlinda-linux:/# apt-get update
Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) lucid Release.gpg
  Something wicked happened resolving 'gb.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security Release.gpg
  Something wicked happened resolving 'security.ubuntu.com:http' (-5 - No address associated with hostname)
Err [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) lucid/main Translation-en_GB
  Something wicked happened resolving 'gb.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/main Translation-en_GB
  Something wicked happened resolving 'security.ubuntu.com:http' (-5 - No address associated with hostname)
Err [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/restricted Translation-en_GB
  Something wicked happened resolving 'security.ubuntu.com:http' (-5 - No address associated with hostname)
Err [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) lucid/restricted Translation-en_GB
  Something wicked happened resolving 'gb.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/universe Translation-en_GB
  Something wicked happened resolving 'security.ubuntu.com:http' (-5 - No address associated with hostname)
Err [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) lucid/universe Translation-en_GB
  Something wicked happened resolving 'gb.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/multiverse Translation-en_GB
  Something wicked happened resolving 'security.ubuntu.com:http' (-5 - No address associated with hostname)
Err [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) lucid/multiverse Translation-en_GB
  Something wicked happened resolving 'gb.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) lucid-updates Release.gpg
  Something wicked happened resolving 'gb.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Ign [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security Release
Ign [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/main Packages
Err [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) lucid-updates/main Translation-en_GB
  Something wicked happened resolving 'gb.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) lucid-updates/restricted Translation-en_GB
  Something wicked happened resolving 'gb.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) lucid-updates/universe Translation-en_GB
  Something wicked happened resolving 'gb.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Ign [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/restricted Packages
Err [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) lucid-updates/multiverse Translation-en_GB
  Something wicked happened resolving 'gb.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Ign [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/main Sources
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) lucid Release
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) lucid-updates Release
Ign [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/restricted Sources
Ign [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/universe Packages
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) lucid/main Packages
Ign [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/universe Sources
Ign [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/multiverse Packages
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) lucid/restricted Packages
Ign [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/multiverse Sources
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) lucid/main Sources
Ign [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/main Packages
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) lucid/restricted Sources
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) lucid/universe Packages
Ign [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/restricted Packages
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) lucid/universe Sources
Ign [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/main Sources
Ign [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/restricted Sources
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) lucid/multiverse Packages
Ign [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/universe Packages
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) lucid/multiverse Sources
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) lucid-updates/main Packages
Ign [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/universe Sources
Ign [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/multiverse Packages
Ign [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/multiverse Sources
Err [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/main Packages
  Something wicked happened resolving 'security.ubuntu.com:http' (-5 - No address associated with hostname)
Err [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/restricted Packages
  Something wicked happened resolving 'security.ubuntu.com:http' (-5 - No address associated with hostname)
Err [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/main Sources
  Something wicked happened resolving 'security.ubuntu.com:http' (-5 - No address associated with hostname)
Err [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/restricted Sources
  Something wicked happened resolving 'security.ubuntu.com:http' (-5 - No address associated with hostname)
Err [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/universe Packages
  Something wicked happened resolving 'security.ubuntu.com:http' (-5 - No address associated with hostname)
Err [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/universe Sources
  Something wicked happened resolving 'security.ubuntu.com:http' (-5 - No address associated with hostname)
Err [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/multiverse Packages
  Something wicked happened resolving 'security.ubuntu.com:http' (-5 - No address associated with hostname)
Err [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/multiverse Sources
  Something wicked happened resolving 'security.ubuntu.com:http' (-5 - No address associated with hostname)
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) lucid-updates/restricted Packages
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) lucid-updates/main Sources
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) lucid-updates/restricted Sources
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) lucid-updates/universe Packages
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) lucid-updates/universe Sources
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) lucid-updates/multiverse Packages
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) lucid-updates/multiverse Sources
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) lucid/main Packages
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) lucid/restricted Packages
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) lucid/main Sources
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) lucid/restricted Sources
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) lucid/universe Packages
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) lucid/universe Sources
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) lucid/multiverse Packages
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) lucid/multiverse Sources
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) lucid-updates/main Packages
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) lucid-updates/restricted Packages
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) lucid-updates/main Sources
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) lucid-updates/restricted Sources
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) lucid-updates/universe Packages
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) lucid-updates/universe Sources
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) lucid-updates/multiverse Packages
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) lucid-updates/multiverse Sources
Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) lucid/main Packages
  Something wicked happened resolving 'gb.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) lucid/restricted Packages
  Something wicked happened resolving 'gb.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) lucid/main Sources
  Something wicked happened resolving 'gb.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) lucid/restricted Sources
  Something wicked happened resolving 'gb.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) lucid/universe Packages
  Something wicked happened resolving 'gb.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) lucid/universe Sources
  Something wicked happened resolving 'gb.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) lucid/multiverse Packages
  Something wicked happened resolving 'gb.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) lucid/multiverse Sources
  Something wicked happened resolving 'gb.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) lucid-updates/main Packages
  Something wicked happened resolving 'gb.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) lucid-updates/restricted Packages
  Something wicked happened resolving 'gb.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) lucid-updates/main Sources
  Something wicked happened resolving 'gb.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) lucid-updates/restricted Sources
  Something wicked happened resolving 'gb.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) lucid-updates/universe Packages
  Something wicked happened resolving 'gb.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) lucid-updates/universe Sources
  Something wicked happened resolving 'gb.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) lucid-updates/multiverse Packages
  Something wicked happened resolving 'gb.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) lucid-updates/multiverse Sources
  Something wicked happened resolving 'gb.archive.ubuntu.com:http' (-5 - No address associated with hostname)
W: Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/lucid/Release.gpg](http://gb.archive.ubuntu.com/ubuntu/dists/lucid/Release.gpg)  Something wicked happened resolving 'gb.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/lucid/main/i18n/Translation-en_GB.bz2](http://gb.archive.ubuntu.com/ubuntu/dists/lucid/main/i18n/Translation-en_GB.bz2)  Something wicked happened resolving 'gb.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/lucid/restricted/i18n/Translation-en_GB.bz2](http://gb.archive.ubuntu.com/ubuntu/dists/lucid/restricted/i18n/Translation-en_GB.bz2)  Something wicked happened resolving 'gb.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/lucid/universe/i18n/Translation-en_GB.bz2](http://gb.archive.ubuntu.com/ubuntu/dists/lucid/universe/i18n/Translation-en_GB.bz2)  Something wicked happened resolving 'gb.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/lucid/multiverse/i18n/Translation-en_GB.bz2](http://gb.archive.ubuntu.com/ubuntu/dists/lucid/multiverse/i18n/Translation-en_GB.bz2)  Something wicked happened resolving 'gb.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/lucid-updates/Release.gpg](http://gb.archive.ubuntu.com/ubuntu/dists/lucid-updates/Release.gpg)  Something wicked happened resolving 'gb.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/lucid-updates/main/i18n/Translation-en_GB.bz2](http://gb.archive.ubuntu.com/ubuntu/dists/lucid-updates/main/i18n/Translation-en_GB.bz2)  Something wicked happened resolving 'gb.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/lucid-updates/restricted/i18n/Translation-en_GB.bz2](http://gb.archive.ubuntu.com/ubuntu/dists/lucid-updates/restricted/i18n/Translation-en_GB.bz2)  Something wicked happened resolving 'gb.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/lucid-updates/universe/i18n/Translation-en_GB.bz2](http://gb.archive.ubuntu.com/ubuntu/dists/lucid-updates/universe/i18n/Translation-en_GB.bz2)  Something wicked happened resolving 'gb.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/lucid-updates/multiverse/i18n/Translation-en_GB.bz2](http://gb.archive.ubuntu.com/ubuntu/dists/lucid-updates/multiverse/i18n/Translation-en_GB.bz2)  Something wicked happened resolving 'gb.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/lucid-security/Release.gpg](http://security.ubuntu.com/ubuntu/dists/lucid-security/Release.gpg)  Something wicked happened resolving 'security.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/lucid-security/main/i18n/Translation-en_GB.bz2](http://security.ubuntu.com/ubuntu/dists/lucid-security/main/i18n/Translation-en_GB.bz2)  Something wicked happened resolving 'security.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/lucid-security/restricted/i18n/Translation-en_GB.bz2](http://security.ubuntu.com/ubuntu/dists/lucid-security/restricted/i18n/Translation-en_GB.bz2)  Something wicked happened resolving 'security.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/lucid-security/universe/i18n/Translation-en_GB.bz2](http://security.ubuntu.com/ubuntu/dists/lucid-security/universe/i18n/Translation-en_GB.bz2)  Something wicked happened resolving 'security.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/lucid-security/multiverse/i18n/Translation-en_GB.bz2](http://security.ubuntu.com/ubuntu/dists/lucid-security/multiverse/i18n/Translation-en_GB.bz2)  Something wicked happened resolving 'security.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/lucid-security/main/binary-i386/Packages.gz](http://security.ubuntu.com/ubuntu/dists/lucid-security/main/binary-i386/Packages.gz)  Something wicked happened resolving 'security.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/lucid-security/restricted/binary-i386/Packages.gz](http://security.ubuntu.com/ubuntu/dists/lucid-security/restricted/binary-i386/Packages.gz)  Something wicked happened resolving 'security.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/lucid-security/main/source/Sources.gz](http://security.ubuntu.com/ubuntu/dists/lucid-security/main/source/Sources.gz)  Something wicked happened resolving 'security.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/lucid-security/restricted/source/Sources.gz](http://security.ubuntu.com/ubuntu/dists/lucid-security/restricted/source/Sources.gz)  Something wicked happened resolving 'security.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/lucid-security/universe/binary-i386/Packages.gz](http://security.ubuntu.com/ubuntu/dists/lucid-security/universe/binary-i386/Packages.gz)  Something wicked happened resolving 'security.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/lucid-security/universe/source/Sources.gz](http://security.ubuntu.com/ubuntu/dists/lucid-security/universe/source/Sources.gz)  Something wicked happened resolving 'security.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/lucid-security/multiverse/binary-i386/Packages.gz](http://security.ubuntu.com/ubuntu/dists/lucid-security/multiverse/binary-i386/Packages.gz)  Something wicked happened resolving 'security.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/lucid-security/multiverse/source/Sources.gz](http://security.ubuntu.com/ubuntu/dists/lucid-security/multiverse/source/Sources.gz)  Something wicked happened resolving 'security.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/lucid/main/binary-i386/Packages.gz](http://gb.archive.ubuntu.com/ubuntu/dists/lucid/main/binary-i386/Packages.gz)  Something wicked happened resolving 'gb.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/lucid/restricted/binary-i386/Packages.gz](http://gb.archive.ubuntu.com/ubuntu/dists/lucid/restricted/binary-i386/Packages.gz)  Something wicked happened resolving 'gb.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/lucid/main/source/Sources.gz](http://gb.archive.ubuntu.com/ubuntu/dists/lucid/main/source/Sources.gz)  Something wicked happened resolving 'gb.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/lucid/restricted/source/Sources.gz](http://gb.archive.ubuntu.com/ubuntu/dists/lucid/restricted/source/Sources.gz)  Something wicked happened resolving 'gb.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/lucid/universe/binary-i386/Packages.gz](http://gb.archive.ubuntu.com/ubuntu/dists/lucid/universe/binary-i386/Packages.gz)  Something wicked happened resolving 'gb.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/lucid/universe/source/Sources.gz](http://gb.archive.ubuntu.com/ubuntu/dists/lucid/universe/source/Sources.gz)  Something wicked happened resolving 'gb.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/lucid/multiverse/binary-i386/Packages.gz](http://gb.archive.ubuntu.com/ubuntu/dists/lucid/multiverse/binary-i386/Packages.gz)  Something wicked happened resolving 'gb.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/lucid/multiverse/source/Sources.gz](http://gb.archive.ubuntu.com/ubuntu/dists/lucid/multiverse/source/Sources.gz)  Something wicked happened resolving 'gb.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/lucid-updates/main/binary-i386/Packages.gz](http://gb.archive.ubuntu.com/ubuntu/dists/lucid-updates/main/binary-i386/Packages.gz)  Something wicked happened resolving 'gb.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/lucid-updates/restricted/binary-i386/Packages.gz](http://gb.archive.ubuntu.com/ubuntu/dists/lucid-updates/restricted/binary-i386/Packages.gz)  Something wicked happened resolving 'gb.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/lucid-updates/main/source/Sources.gz](http://gb.archive.ubuntu.com/ubuntu/dists/lucid-updates/main/source/Sources.gz)  Something wicked happened resolving 'gb.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/lucid-updates/restricted/source/Sources.gz](http://gb.archive.ubuntu.com/ubuntu/dists/lucid-updates/restricted/source/Sources.gz)  Something wicked happened resolving 'gb.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/lucid-updates/universe/binary-i386/Packages.gz](http://gb.archive.ubuntu.com/ubuntu/dists/lucid-updates/universe/binary-i386/Packages.gz)  Something wicked happened resolving 'gb.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/lucid-updates/universe/source/Sources.gz](http://gb.archive.ubuntu.com/ubuntu/dists/lucid-updates/universe/source/Sources.gz)  Something wicked happened resolving 'gb.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/lucid-updates/multiverse/binary-i386/Packages.gz](http://gb.archive.ubuntu.com/ubuntu/dists/lucid-updates/multiverse/binary-i386/Packages.gz)  Something wicked happened resolving 'gb.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/lucid-updates/multiverse/source/Sources.gz](http://gb.archive.ubuntu.com/ubuntu/dists/lucid-updates/multiverse/source/Sources.gz)  Something wicked happened resolving 'gb.archive.ubuntu.com:http' (-5 - No address associated with hostname)

E: Some index files failed to download, they have been ignored, or old ones used instead.
root@davidlinda-linux:/# apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
root@davidlinda-linux:/# apt-get dist-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
root@davidlinda-linux:/# apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
root@davidlinda-linux:/# dpkg --configure -a
root@davidlinda-linux:/# 

---

### Post by oldfred on 2010-06-29
Your chroot may be missing a command or two. kansasnoob has it as one line but includes the resolv.conf which sometimes is required to connect to the internet. Also the last two commands have been mentioned. (they are not in kansasnoob's one line version)

[http://ubuntuforums.org/showpost.php?p=8068512&postcount=10](http://ubuntuforums.org/showpost.php?p=8068512&postcount=10)
[http://ubuntuforums.org/showthread.php?t=1470597](http://ubuntuforums.org/showthread.php?t=1470597)
Neat huh?
Added sudo cp /etc/resolv.conf /mnt/etc/resolv.conf

kansasnoob's change sda5 to correct partition
sudo mount /dev/sda5 /mnt && sudo mount --bind /dev /mnt/dev && sudo mount --bind /proc /mnt/proc && sudo mount --bind /dev/pts /mnt/dev/pts && sudo cp /etc/resolv.conf /mnt/etc/resolv.conf && sudo chroot /mnt

# new for lucid & karmic 
dpkg-divert --local --rename --add /sbin/initctl
ln -s /bin/true /sbin/initctl

---

### Post by retroartist on 2010-06-29
Thanks for the further advice... its a little late in the UK so I will try it tomorrow when my mind is a little fresher.

-retroartist-

---

### Post by retroartist on 2010-06-30
Thanks for the help and support - the one line chroot works well..

-retroartist-

---

