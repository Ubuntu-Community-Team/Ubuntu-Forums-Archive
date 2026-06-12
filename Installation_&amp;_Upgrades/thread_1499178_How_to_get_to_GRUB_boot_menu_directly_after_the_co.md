---
title: "How to get to GRUB boot menu directly after the computer start?"
date: 2010-06-01
forum: Installation &amp; Upgrades
---

### Post by nkao on 2010-06-01
Hello,
I did a clean installation of Ubuntu 10.04 and I found that after the computer booted, the GRUB stopped by waiting for entering command -- "grub >".   The GRUB version is 1.98.

I want to go directly to the GRUB boot menu after computer booted.  Could someone help me to fix this easy problem?  

Thanks.

---

### Post by darkod on 2010-06-01
Boot with the ubuntu cd in live mode, and in terminal do:

sudo fdisk -l (small L)

Post the results, so we can give exact commands.

---

### Post by nkao on 2010-06-02
I will post the required information later today because I don't have access to the computer this moment. (home vs. office)

---

### Post by nkao on 2010-06-02
Hi, the following is the output of "sudo fdisk -l" after booted from a 10.04 liveCD --
===========================================================
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00086806

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       18707   150259712   83  Linux
/dev/sda2           18707       19458     6028289    5  Extended
/dev/sda5           18707       19458     6028288   82  Linux swap / Solaris

Disk /dev/sdb: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xe888e888

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       38261   307331451    7  HPFS/NTFS
/dev/sdb2           38262       38913     5237190    5  Extended
/dev/sdb5           38262       38913     5237158+   b  W95 FAT32
ubuntu@ubuntu:~$ 
===========================================================

And please note that /dev/sdb is an IDE hard drive and /dev/sda is a SATA hard drive.

Thanks for the help.

---

### Post by oldfred on 2010-06-03
Usually you need to reinstall grub to the MBR of the drive you boot from. Which should be set to the sda or 160GB drive in BIOS.

While in the LiveCD, open terminal and run:
sudo mount /dev/sda1 /mnt
sudo grub-install --root-directory=/mnt/ /dev/sda
If that returns any errors run:
sudo grub-install --recheck --root-directory=/mnt /dev/sda

Then reboot and in Ubuntu:
sudo update-grub #should add windows to grub.cfg for next reboot.

---

### Post by alterpinguin on 2010-06-03
if it is grub2
you are using?
Then check the file:
/etc/grub/grub.cfg

In this file, there are some defaults setup,
like the GRUB_HIDDEN_TIMEOUT
```

# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.

GRUB_DEFAULT=0
#GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
...
.......

```
comment this line with a "#" in front, to not use it.
The HIDDEN_TIMEOUT may be activated to automatically boot
the standard version - this might be nice for a user
who dont cares and only want to do his/her job after the booting.

For people, who care for more, like installing, updating etc.
and who know a bit about the grub-commandlines and the grub-shell,
this might be bad - you need to boot and change the setting to get into
the grub-shell and to change some things ! but think about if you dont want the user to make changes without the knowledge what he/she is doing.

forgot it: you need to update the grub after doing this,
like with:
sudo update-grub

---

### Post by nkao on 2010-06-03
Thank you, oldfred and alterpinguin.
I will try your suggestion later.  (Again, home vs. office)
And let you know the outcome.

---

### Post by nkao on 2010-06-03
Hi alterpinguin,
I have dual OS (Ubuntu & XP) installed on separated hard drives in this computer, so I think the GRUB_HIDDEN_TIMOUT may not be the one to fix my problem.

Here is the reason quoted from **"The Grub 2 Guide"**:
> **GRUB_HIDDEN_TIMEOUT=0**   [ [COLOR=DarkRed]Note: This  setting only applies to computers with only a single operating system.[/COLOR]  ]
Thanks.

---

### Post by nkao on 2010-06-03
Hi oldfred,
I tried to re-install GRUB 2 by following your instruction but the outcome remains the same.  The GRUB boot loader get into interactive mode (prompting "grub >") and I had to enter command "exit" to have the boot menu displayed.

I believe that there must be only a setting somewhere in the GRUB configuration files that I need to modify in order to get into the boot menu directly after GRUB boot loader is loaded.

Thanks for suggestion or comment.

---

### Post by alterpinguin on 2010-06-03
> **nkao said:**
> Hi alterpinguin,
I have dual OS (Ubuntu & XP) installed on separated hard drives in this computer, so I think the GRUB_HIDDEN_TIMOUT may not be the one to fix my problem.

Here is the reason quoted from **"The Grub 2 Guide"**:

Thanks.

No - i had no problems with old grub (legacy). The new grub2
had some problems (like using different device-map order)
and it happened suddenly with one update in 10.04 beta ... or? - i dont remember it any more, later - when suddenly the grub2 menu did disappear.
I could enable it again after i did comment (#) this variable-setting.

---

### Post by nkao on 2010-06-03
> **alterpinguin said:**
> No - i had no problems with old grub (legacy). The new grub2
had some problems (like using different device-map order)

I agree with you.  When I upgrade my laptop from Ubuntu 8.x to 9.10, I have to remove grub2 and go back to grub to make the boot loader work at that time.  There are many changes in grub2 from grub.

---

### Post by darkod on 2010-06-03
For more details about your boot process you should run the boot info script:
[http://ubuntuforums.org/showpost.php?p=8844901&postcount=4](http://ubuntuforums.org/showpost.php?p=8844901&postcount=4)

That will show you detailed information. If you have any questions, you can post the content of the results file here as explained.

---

### Post by nkao on 2010-06-05
Here is the result by running boot_info_script055.sh.

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #1 for /boot/grub.
 => Grub 2 is installed in the MBR of /dev/sdb and looks on the same drive in 
    partition #1 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM /boot/grub/core.img

sdb2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat32
    Boot sector info:  According to the info in the boot sector, sdb5 starts 
                       at sector 0. But according to the info from fdisk, 
                       sdb5 starts at sector 614663028.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048   300,521,471   300,519,424  83 Linux
/dev/sda2         300,523,518   312,580,095    12,056,578   5 Extended
/dev/sda5         300,523,520   312,580,095    12,056,576  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63   614,662,964   614,662,902   7 HPFS/NTFS
/dev/sdb2         614,662,965   625,137,344    10,474,380   5 Extended
/dev/sdb5         614,663,028   625,137,344    10,474,317   b W95 FAT32


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        142b1a95-1698-4917-a61f-f0caaf0c220d   ext4                                     
/dev/sda2: PTTYPE="dos" 
/dev/sda5        951dde88-df66-4192-ab59-0b7708b69327   swap                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        8C0CC3A70CC38AA2                       ntfs                                     
/dev/sdb2: PTTYPE="dos" 
/dev/sdb5        5ED9-21AE                              vfat                                     
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda1        /                        ext4       (rw,errors=remount-ro)


=========================== sda1/boot/grub/grub.cfg: ===========================

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
set root='(hd0,1)'
search --no-floppy --fs-uuid --set 142b1a95-1698-4917-a61f-f0caaf0c220d
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
set root='(hd0,1)'
search --no-floppy --fs-uuid --set 142b1a95-1698-4917-a61f-f0caaf0c220d
set locale_dir=($root)/boot/grub/locale
set lang=en
insmod gettext
if [ ${recordfail} = 1 ]; then
  set timeout=-1
else
  set timeout=5
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry 'Ubuntu, with Linux 2.6.32-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 142b1a95-1698-4917-a61f-f0caaf0c220d
    linux    /boot/vmlinuz-2.6.32-22-generic root=UUID=142b1a95-1698-4917-a61f-f0caaf0c220d ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 142b1a95-1698-4917-a61f-f0caaf0c220d
    echo    'Loading Linux 2.6.32-22-generic ...'
    linux    /boot/vmlinuz-2.6.32-22-generic root=UUID=142b1a95-1698-4917-a61f-f0caaf0c220d ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 142b1a95-1698-4917-a61f-f0caaf0c220d
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=142b1a95-1698-4917-a61f-f0caaf0c220d ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 142b1a95-1698-4917-a61f-f0caaf0c220d
    echo    'Loading Linux 2.6.32-21-generic ...'
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=142b1a95-1698-4917-a61f-f0caaf0c220d ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 142b1a95-1698-4917-a61f-f0caaf0c220d
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 142b1a95-1698-4917-a61f-f0caaf0c220d
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Professional (on /dev/sdb1)" {
    insmod ntfs
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set 8c0cc3a70cc38aa2
    drivemap -s (hd0) ${root}
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sda1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=142b1a95-1698-4917-a61f-f0caaf0c220d /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=951dde88-df66-4192-ab59-0b7708b69327 none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sda1: Location of files loaded by Grub: ===================


 124.6GB: boot/grub/core.img
  73.6GB: boot/grub/grub.cfg
 124.7GB: boot/initrd.img-2.6.32-21-generic
 124.8GB: boot/initrd.img-2.6.32-22-generic
 124.6GB: boot/vmlinuz-2.6.32-21-generic
   1.7GB: boot/vmlinuz-2.6.32-22-generic
 124.8GB: initrd.img
 124.7GB: initrd.img.old
   1.7GB: vmlinuz
 124.6GB: vmlinuz.old

================================ sdb1/boot.ini: ================================

[boot loader] 
timeout=1 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect 

=================== sdb1: Location of files loaded by Grub: ===================


    ??GB: boot/grub/core.img
```And FYR, the output from "sudo fdisk -l", 
```
Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00086806

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       18707   150259712   83  Linux
/dev/sda2           18707       19458     6028289    5  Extended
/dev/sda5           18707       19458     6028288   82  Linux swap / Solaris

Disk /dev/sdb: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xe888e888

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       38261   307331451    7  HPFS/NTFS
/dev/sdb2           38262       38913     5237190    5  Extended
/dev/sdb5           38262       38913     5237158+   b  W95 FAT32

```

---

### Post by darkod on 2010-06-05
In the BIOS is the 160GB disk the first in hdd order? You need to make sure you are booting from the 160GB hdd.

And because you have a mix of SATA and IDE, sometimes BIOS would boot first from IDE but in your case it needs to be the SATA disk.

Otherwise, the results file looks OK except that you have the /boot/grub/core.img file in /dev/sdb1 (your XP partition) that you should remove from there. You could do that from ubuntu, after you repair the boot process.

---

### Post by nkao on 2010-06-06
> **darkod said:**
> In the BIOS is the 160GB disk the first in hdd order? You need to make sure you are booting from the 160GB hdd.

I changed the 160G HD to boot before the 320G one and my problem is gone!

Thank you!

---

### Post by jcoles on 2010-06-12
Alterpinguin,

On 10.04, the /etc/default/grub file is supposed to set grub options, isn't it? That's where it was on 9.10 and my clean 10.04 install has the same file in that location. There is no such location as /etc/grub.

I have made just the sort of changes you suggest and run update-grub afterwards. Indeed, I have done this in the past on 9.10. But, on 10.04 the changes are completely ignored. Grub reports the kernels it finds, as normal. But changes to defaults like the menu timeout have no effect at all.

This was a clean install of 10.04 64-bit into the same partition that 9.10 32-bit occupied before. Now, I have no access to the grub menu at all. I'm OK as long as I never need to boot command-line only or to a previous kernel. 

A good default would be to show the grub menu for two seconds before booting the default kernel.

---

### Post by darkod on 2010-06-12
> **jcoles said:**
> Alterpinguin,

On 10.04, the /etc/default/grub file is supposed to set grub options, isn't it? That's where it was on 9.10 and my clean 10.04 install has the same file in that location. There is no such location as /etc/grub.

I have made just the sort of changes you suggest and run update-grub afterwards. Indeed, I have done this in the past on 9.10. But, on 10.04 the changes are completely ignored. Grub reports the kernels it finds, as normal. But changes to defaults like the menu timeout have no effect at all.

This was a clean install of 10.04 64-bit into the same partition that 9.10 32-bit occupied before. Now, I have no access to the grub menu at all. I'm OK as long as I never need to boot command-line only or to a previous kernel. 

A good default would be to show the grub menu for two seconds before booting the default kernel.

I don't understand what you are trying to achieve. Do you need this or you just complain? Why would you like a menu to show when you have only one OS and showing a menu would delay booting?

On the contrary to what you say, a good practice is not to stop and show a menu with single OS. You always have the option by hitting Shift to show the menu.

If you still want to adjust the HIDDEN parameters in /etc/default/grub look here in the section for that file, it has everything you need:
[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

---

### Post by jcoles on 2010-06-12
Darko, 

"You always have the option by hitting Shift to show the menu."

Really? It was always ESC before. I'll try that....

Yes! That's exactly what I want! Thank you!

I still believe that I have a valid complaint that configuration options are being ignored. But, I'll check the How-To you cited in case this issue is because of another change that I've missed.

Thanks again.

---

### Post by darkod on 2010-06-12
> **jcoles said:**
> Darko, 

"You always have the option by hitting Shift to show the menu."

Really? It was always ESC before. I'll try that....

Yes! That's exactly what I want! Thank you!

I still believe that I have a valid complaint that configuration options are being ignored. But, I'll check the How-To you cited in case this issue is because of another change that I've missed.

Thanks again.

Esc is for grub1, Shift for grub2. Glad you are happier now. :)

---

