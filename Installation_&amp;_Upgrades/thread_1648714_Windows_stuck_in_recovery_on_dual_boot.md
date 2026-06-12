---
title: "Windows stuck in recovery on dual boot"
date: 2010-12-19
forum: Installation &amp; Upgrades
---

### Post by PaulPreston on 2010-12-19
Hello

I am familiar with Linux servers at work so I fancied ubuntu on my Samsung X120 laptop as a dual boot.

I had to partition disks and grub comes up and gives me a choice of boot.  Ubuntu works fine.

Trouble is when I choose the Windows7 option it says windows started, gives me the windows 4 colour flag and then goes into recovery mode 4 and complains about X:\WinClon\Manager1.exe can't be found.

I never had an X drive.  If I grep for Manager1.exe it is there on the Windows partition.  So I am wondering if the partitioning has messed up the Windows partition for boot.

Any ideas?

Paul

---

### Post by fatal_ERROR777 on 2010-12-19
Have you installed ubuntu using [wubi]("http://wubi.sourceforge.net/")? If you did, have you deleted the wubi.exe file? If you did, this is your problem. Try to boot windows in safe mode and install wubi again.

---

### Post by theasprint on 2010-12-19
Just to let you know, the X drive in  Windows recovery is the Recovery Drive.

For basic recovery procedures, people used to copy and replace the  corrupted or lost files in their C: drive from the X: drive. The X:  drive should have at least something similar like your C:\Windows  folder.

I think if you grep Manager1.exe, it will show up as  C:\WinClon\Manager1.exe. Perhaps to solve the problem, try and run this  command:

```
copy C:\WinClon\Manager1.exe X:\WinClon\Manager1.exe
```

Its quite ironic to recover the recovery partition. Hope it works.

And did you do something wrong during your partitioning? Like partially taking away your X (recovery drive)?

Good Luck :D

---

### Post by sikander3786 on 2010-12-19
In order to let us take a look at your setup/drives/boot and diagnose the problem, you need to post the output of bootinfoscript as per instructions here.

[http://bootinfoscript.sourceforge.net](http://bootinfoscript.sourceforge.net)

While posting, click the # icon in post menu and paste your text in between the generated code tags.

Thanks.

---

### Post by PaulPreston on 2010-12-19
Ok here is the results.txt

```


                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #3 for (,msdos3)/boot/grub.

sda1: _________________________________________________________________________

    File system:       
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /boot/bcd

sda3: _________________________________________________________________________

    File system:       ext2
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda4: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe /wubildr.mbr 
                       /ubuntu/winboot/wubildr.mbr /wubildr 
                       /ubuntu/winboot/wubildr

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63         2,047         1,985  42 SFS
/dev/sda2               2,048    31,459,327    31,457,280  27 Hidden HPFS/NTFS
/dev/sda3    *    369,655,650   486,843,149   117,187,500  83 Linux
/dev/sda4          31,664,128   369,641,471   337,977,344  42 SFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda2        CE26BADE26BAC6AD                       ntfs       RECOVERY                      
/dev/sda3        27584650-9210-4f81-a1f2-380526e88815   ext2                                     
/dev/sda4        CE2EB81D2EB7FC91                       ntfs                                     
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda3        /                        ext2       (rw,errors=remount-ro)


=========================== sda3/boot/grub/grub.cfg: ===========================

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
set root='(hd0,msdos3)'
search --no-floppy --fs-uuid --set 27584650-9210-4f81-a1f2-380526e88815
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos3)'
search --no-floppy --fs-uuid --set 27584650-9210-4f81-a1f2-380526e88815
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
menuentry 'Ubuntu, with Linux 2.6.35-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos3)'
    search --no-floppy --fs-uuid --set 27584650-9210-4f81-a1f2-380526e88815
    linux    /boot/vmlinuz-2.6.35-22-generic root=/dev/sda3 ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos3)'
    search --no-floppy --fs-uuid --set 27584650-9210-4f81-a1f2-380526e88815
    echo    'Loading Linux 2.6.35-22-generic ...'
    linux    /boot/vmlinuz-2.6.35-22-generic root=/dev/sda3 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-22-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos3)'
    search --no-floppy --fs-uuid --set 27584650-9210-4f81-a1f2-380526e88815
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos3)'
    search --no-floppy --fs-uuid --set 27584650-9210-4f81-a1f2-380526e88815
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows Vista (loader) (on /dev/sda2)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos2)'
    search --no-floppy --fs-uuid --set ce26bade26bac6ad
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

=============================== sda3/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda3 during installation
UUID=27584650-9210-4f81-a1f2-380526e88815 /               ext2    errors=remount-ro 0       1
/dev/scd0       /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sda3: Location of files loaded by Grub: ===================


 208.9GB: boot/grub/core.img
 209.0GB: boot/grub/grub.cfg
 208.9GB: boot/initrd.img-2.6.35-22-generic
 208.9GB: boot/vmlinuz-2.6.35-22-generic
 208.9GB: initrd.img
 208.9GB: vmlinuz



```

---

### Post by PaulPreston on 2010-12-19
Hi

thanks for the advice about copy.  I suspect you are correct, I may have ruined whatever was the X partition.  The copy command you posted is DOS comman - how do I get to DOS to issue that copy command?

Thanks to all for help.

Paul

---

### Post by sikander3786 on 2010-12-19
You've also got a Wubi install on your Windows partition. Do you want to recover that as well? If not, follow the procedure below. If yes, post back and _don't_ follow.

The easiest solution here is to boot Windows 7 install or repair disc and perform startup repair 3 times at least. Yes, 3 times. If you don't have a Windows 7 disc, grab one here (not pirated).

[http://neosmart.net/blog/2009/windows-7-system-repair-discs/](http://neosmart.net/blog/2009/windows-7-system-repair-discs/)

Once you are able to boot Windows successfully, you need to re-install Grub2. Boot an Ubuntu Live CD and from Applications > Accessories > Terminal,

```
sudo mount /dev/sda3 /mnt
```

```
sudo grub-install --root-directory=/mnt/ /dev/sd[COLOR="Red"]a[/COLOR]
```

Note, for the second command, it is just sda without an integer and not sda3 ;-)

Reboot and boot Ubuntu. If Windows was not listed, from Ubuntu booted from HDD,

```
sudo update-grub
```

---

### Post by PaulPreston on 2010-12-19
Thanks that's really helpful, what you suggest makes good sense.  I am not worried about wubi so I am downloading the repair disk.  I am hoping it will detect it and boot from the repair disk - I am not sure what the key sequence is to make it boot from CD and grub is the first thing it shows now.

I will let you know if this succeeds, I will try later when the download is done and I manage to get a disk burnt.

Paul

---

### Post by PaulPreston on 2010-12-20
Update is:

after doing a bios edit so it would boot from  the CD the recovery disk prompts for drivers so it can read the hard drive - I do't have a separate disk with these drivers.  I then decided that as I can see all my files that GRUB may not be seeing the correct partition so I copied then edited grub.cfg which then gave me the option to boot Windows 7 in choice of 2 partitions.  In either case one becomes X and the other C but all avenues lead to it telling me it can't recover.

I think I must have messed up a  partition and I feel I am so close.  I have copied all my documents on the windows partition to a flash drive so I am good to get Win7 reinstalled and try it all again.

Thanks for suggestions, they were all good, shame have not succeeded.  I am going to leave it for a while but pleased to receive suggestions if there are any bright ideas.

Paul

---

### Post by sikander3786 on 2010-12-20
> after doing a bios edit so it would boot from the CD the recovery disk prompts for drivers so it can read the hard drive - 

In my opinion, that is happening because of this.

> sda1: _________________________________________________________________________

    File system:       
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:
[COLOR="Red"]mount: unknown filesystem type ''[/COLOR]

What was there on sda1? Some sort of Utility partition I believe. If that was nothing important there, just deleting the partition and re-creating it using Gparted from an Ubuntu Live CD might resolve the issue here. But not 100 % sure about that.

---

