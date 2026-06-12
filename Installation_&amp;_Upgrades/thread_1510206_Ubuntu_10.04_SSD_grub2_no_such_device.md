---
title: "Ubuntu 10.04 SSD grub2: no such device"
date: 2010-06-15
forum: Installation &amp; Upgrades
---

### Post by Ichwardort on 2010-06-15
Sorry for cross-posting:

I just installed Ubuntu 10.04 via LiveCD on my SSD. There is also Windows XP which should come up in a dual boot and which is running on a totally different disk. The bootloader is grub2.

Well however when I unplug my LiveCD and reboot the machine I get an
[SIZE=3]"error: no such device a9f50c58-3cac-4204-93bd-cf05aa521dc0"
grub rescue>[/SIZE]

I already executed "sudo bash ~/Desktop/boot_info_script*.sh" and posted the results at
[http://ubuntuforums.org/showthread.php?t=1510163](http://ubuntuforums.org/showthread.php?t=1510163)

However as I'm totally new to Ubuntu I am not really able to understand the results. Is it my SSD which is not available when booting the PC or is it a different (configuration) issue with the bootloader?

I am very thankful for any advice - as I'm currently stuck in the LiveCD version of ubuntu ;(

Thanks,
kr Andrew

---

### Post by darkod on 2010-06-15
The SSD is first in boot order right?

From live mode, in terminal execute:

sudo mount /dev/sdc1 /mnt
sudo grub-install --root-directory=/mnt/ /dev/sdc

That will install grub2 to the SSD, at the moment it's on the 200GB disk.

See if that helped. I will look with more details in the results meanwhile.

PS. I just noticed this is express card. Maybe it's not available to be seen by the system until the OS loads some drivers? Can that be the problem? If it was standard SSD I'm sure it should work, but not sure with express card.

---

### Post by Ichwardort on 2010-06-15
Hi Darkod,

Thanks a lot for your reply. I just executed the steps you suggested and rebooted, but this didn't change the problem. I just re-executed the boot_info_script to check if the changes were taken into account properly:
[HTML]
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #1 for /boot/grub.
 => Syslinux is installed in the MBR of /dev/sdb
 => Grub 2 is installed in the MBR of /dev/sdc and looks on the same drive in 
    partition #1 for /boot/grub.

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

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda5 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdc1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdc2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders, total 390721968 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   103,426,469   103,426,407   7 HPFS/NTFS
/dev/sda2         103,426,470   390,716,864   287,290,395   f W95 Ext d (LBA)
/dev/sda5         103,426,533   390,716,864   287,290,332   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 4218 MB, 4218421248 bytes
2 heads, 63 sectors/track, 65389 cylinders, total 8239104 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             64     8,239,103     8,239,040   b W95 FAT32


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 32.2 GB, 32195477504 bytes
255 heads, 63 sectors/track, 3914 cylinders, total 62881792 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdc1                  63    42,395,534    42,395,472  83 Linux
/dev/sdc2          42,395,535    62,878,409    20,482,875   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        D06031196031082C                       ntfs       System                        
/dev/sda2: PTTYPE="dos" 
/dev/sda5        01C9548FF00D9BD0                       ntfs       Data                          
/dev/sda: PTTYPE="dos" 
/dev/sdb1        7C85-ADD0                              vfat                                     
/dev/sdb: PTTYPE="dos" 
/dev/sdc1        a9f50c58-3cac-4204-93bd-cf05aa521dc0   ext3                                     
/dev/sdc2        265C7FB55C7F7DFD                       ntfs       SSD-NTFS                      
/dev/sdc: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sdb1        /cdrom                   vfat       (ro,noatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
/dev/loop0       /rofs                    squashfs   (ro,noatime)


================================ sda1/boot.ini: ================================

[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect 

=========================== sdc1/boot/grub/grub.cfg: ===========================

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
set root='(hd2,1)'
search --no-floppy --fs-uuid --set a9f50c58-3cac-4204-93bd-cf05aa521dc0
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
set root='(hd2,1)'
search --no-floppy --fs-uuid --set a9f50c58-3cac-4204-93bd-cf05aa521dc0
set locale_dir=($root)/boot/grub/locale
set lang=de
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
menuentry 'Ubuntu, mit Linux 2.6.32-22-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd2,1)'
    search --no-floppy --fs-uuid --set a9f50c58-3cac-4204-93bd-cf05aa521dc0
    linux    /boot/vmlinuz-2.6.32-22-generic-pae root=UUID=a9f50c58-3cac-4204-93bd-cf05aa521dc0 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-22-generic-pae
}
menuentry 'Ubuntu, mit Linux 2.6.32-22-generic-pae (Wiederherstellungsmodus)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd2,1)'
    search --no-floppy --fs-uuid --set a9f50c58-3cac-4204-93bd-cf05aa521dc0
    echo    'Linux 2.6.32-22-generic-pae wird geladen …'
    linux    /boot/vmlinuz-2.6.32-22-generic-pae root=UUID=a9f50c58-3cac-4204-93bd-cf05aa521dc0 ro single 
    echo    'Initiale Ramdisk wird geladen …'
    initrd    /boot/initrd.img-2.6.32-22-generic-pae
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd2,1)'
    search --no-floppy --fs-uuid --set a9f50c58-3cac-4204-93bd-cf05aa521dc0
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd2,1)'
    search --no-floppy --fs-uuid --set a9f50c58-3cac-4204-93bd-cf05aa521dc0
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Professional (on /dev/sda1)" {
    insmod ntfs
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set d06031196031082c
    drivemap -s (hd0) ${root}
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sdc1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/sdc1       /               ext3    errors=remount-ro 0       1

=================== sdc1: Location of files loaded by Grub: ===================


  11.0GB: boot/grub/core.img
  11.0GB: boot/grub/grub.cfg
  11.0GB: boot/initrd.img-2.6.32-22-generic-pae
  11.0GB: boot/vmlinuz-2.6.32-22-generic-pae
  11.0GB: initrd.img
  11.0GB: vmlinuz
[/HTML]

I think you're right, it's probably the SSD which might not bee seen when booting the system. e.g. in BIOS I have only the option to boot from HD1, CD, USB or Network -> there's not HD2 listed there.

OK, so let's assume that's the problem - what's would you suggest is the best way of fixing this. I would like to make use of the SSD's read performance (150 MB/s) to boot up Ubuntu really speedy if possible

However at the moment that's not that important, as I really need to get my main Windows working again, as it is owned by my company!  

Thanks for your reply,
kr Andrew

---

### Post by darkod on 2010-06-15
We'll get windows working in a second, don't worry about that.

The fastest way is, from live mode execute:

sudo apt-get install lilo
sudo lilo -M /dev/sda mbr

That will install generic mbr on /dev/sda which can boot windows. Running the first command will give you warnings that might sound bad, just ignore them, it's normal. Ignore the warnings and just run the second command after that.

Restart and you should see windows boot. I have to think about the other problem with the express card.

---

### Post by Ichwardort on 2010-06-15
that's my windows box I'm posting the message from ... thanks a lot darkod, your proposed solution worked like charm! Thank you very much!! :guitar:

Regarding the SSD solution: It's probably my own fault as it seems there are SSDs for EC slots out there that carry the attribute 'bootable' which I should have known before. However if you can think of a nice workaround that would be fantastic.

Thanks again,
kr Andrew

---

### Post by darkod on 2010-06-15
I found some commands to try for an EC but the problem is that according to you the EC is not seen as boot device at all.

So, we would need to install grub2 to the int hdd again, and try the fix for the EC. If it doesn't work it will again make windows unbootable.

But you can always install again the generic mbr with the lilo procedure as you did.

Are you willing to try?

Another question, we might be able to use the 4GB /dev/sdb device to install grub2 there, not touching the int hdd. What is that device, a usb stick? Memory card? If it's usb stick we can probably try booting from it since you have USB in boot devices.

---

### Post by Ichwardort on 2010-06-15
>I found some commands to try for an EC but the problem is that according  to you the EC 
>is not seen as boot device at all.

That's true - I'm not able to select it as boot device in BIOS. 

>So, we would need to install grub2 to the int hdd again, and try the fix  for the EC. If it >doesn't work it will again make windows unbootable.
>But you can always install again the generic mbr with the lilo procedure  as you did.
>Are you willing to try?

Yes sure!! ... as long as we don't crash the existing windows partition that's fine ;)

>Another question, we might be able to use the 4GB /dev/sdb device to  install grub2 
>there, not touching the int hdd. What is that device, a  usb stick? Memory card? If it's 
>usb stick we can probably try booting  from it since you have USB in boot devices.     

Yes the 4 GB is a usb stick, from which I'm at the moment booting the liveCD from (using UNetbootin)

Have you already seen:
[http://ubuntuforums.org/showthread.php?t=1205674](http://ubuntuforums.org/showthread.php?t=1205674)
I do not fully understand all parts, but the problem described there is  exactly the same.

---

### Post by darkod on 2010-06-15
Yes, that were the steps I found too in another thread.

If you use the stick as live USB we can't use it for grub2.

We won't crash the windows partition but if the fix doesn't work you will have to reinstall the generic mbr back again with the lilo commands.

OK, here's the deal:

1. To make sure all devices are what we think they are, in live mode first run

sudo fdisk -l

The devices should be as in the results file, 200GB /dev/sda, 4GB /dev/sdb and the 32GB EC /dev/sdc. If that is so, continue.

2. Run these commands one by one to install grub2 on /dev/sda and try to fix the EC issue

sudo -i
mount /dev/sdc1 /mnt
mount --bind /proc /mnt/proc
mount --bind /sys /mnt/sys
mount --bind /dev /mnt/dev
mount --bind /dev/pts /mnt/dev/pts
mount --bind /dev/shm /mnt/dev/shm
grub-install --root-directory=/mnt/ --module=ata /dev/sda
chroot /mnt
echo phison >> /etc/initramfs-tools/modules
update-initramfs -u
exit
umount /mnt/dev/shm
umount /mnt/dev/pts
umount /mnt/dev
umount /mnt/sys
umount /mnt/proc
exit

I think I got all the commands right and there should be no errors. It's the first time I'm trying something like this. :)

Restart and see how it goes. If you can't boot as before, if there is the same error, you can always boot again with the stick in live mode.

---

### Post by Ichwardort on 2010-06-16
let me just call you a genius and thank you very much!! It works!! :shock:
The boot loader just comes up fine and lets me chose between ubuntu and windows!

Your instructions were perfectly working - I only had to replace
 > --module=ata /dev/sda with
> --disk-module=ata /dev/sdaIf you've still got some time would you mind giving me a short explanation on what the lines actually execute? How did you bring in the SSD drivers?
> chroot /mnt
echo phison >> /etc/initramfs-tools/modules
update-initramfs -uJust some final questions:

[LIST]
[*]I just noticed that Ubuntu is able to mount my windows NTFS disks ... is this safe to write on them as well?
[*]Do you know a proper disc-performance benchmarking tool which I could execute under ubuntu? I'm not sure I'm getting the full 150 MB/s out of the SSD. For Windows and Mac a speed-boost-driver was shipped with the Verbatim SSD - no Linux one?!
[/LIST]
Thanks again, I really appreciate your help!

---

### Post by Ichwardort on 2010-06-16
oh no -... sorry, I cheered to early! Although Ubuntu is working fine, I am not able to boot Windows anymore. When selecting XP from the boot loader I get an error:

no such device
no such disk

---

### Post by darkod on 2010-06-16
> **Ichwardort said:**
> oh no -... sorry, I cheered to early! Although Ubuntu is working fine, I am not able to boot Windows anymore. When selecting XP from the boot loader I get an error:

no such device
no such disk

I wonder if installing grub2 with that module parameter is making it recognize the EC but not recognize the int hdd now. That solution maybe was OK only for EC.

On another note, we just followed the recommended commands, I wonder if it should work without the module parameter.

The only thing we can do is try, but it may break the process so far. The driver is already inside ubuntu, so not much damage can be done.

Boot ubuntu, because you can boot it, and just reinstall grub2 to the mbr of /dev/sda without the module parameter:

sudo grub-install /dev/sda

---

### Post by Ichwardort on 2010-06-16
what do you actually mean by:
> The only thing we can do is try, but it may break the process so far.  The driver is already inside ubuntu, so not much damage can be done.

In the meantime I already executed:
> sudo apt-get install lilo
sudo lilo -M /dev/sda mbr
from ubuntu (on the SSD) as well as from liveCD (because calling this from the SSD-Ubuntu didn't take any effect.) - as I had to recover my windows again.

So the process remains the same as described in your last post or did my changes affect the procedure?

Thanks,
kr A.

---

### Post by darkod on 2010-06-16
I meant that the progress was that ubuntu started booting, and I'm not sure if installing grub2 without the --disk-module=ata can make it not booting, like when we started.

Returning the generic mbr to get windows booting shouldn't have affected anything. The only difference is that you will have to boot in live mode again now, and install grub2 from there which are different commands:

sudo mount /dev/sdc1 /mnt
sudo grub-install --root-directory=/mnt/ /dev/sda

Since you can't boot from the EC we have to do it like this. If you need windows urgently you might want to wait trying this later. Until we try few options you have to be ready not to be able to boot windows. You know how to bring it back when needed, but not on every 5mins. :)

---

### Post by Ichwardort on 2010-06-16
ah thanks for clarification! I'll retry that this evening when I'm home from work.

---

### Post by Ichwardort on 2010-06-20
>  
sudo mount /dev/sdc1 /mnt
sudo grub-install --root-directory=/mnt/ /dev/sdaJust installed grub, this time without the 'disk-module' flag as suggested within your last post ... unfortunately now we're back again to the '[SIZE=3]error: no such device[/SIZE] so no bootloader at all coming up?!

Any suggestions left?

---

### Post by darkod on 2010-06-20
> **Ichwardort said:**
> Just installed grub, this time without the 'disk-module' flag as suggested within your last post ... unfortunately now we're back again to the '[SIZE=3]error: no such device[/SIZE] so no bootloader at all coming up?!

Any suggestions left?

It seems there is no win-win situation. You can again install grub2 back to the mbr with the disk-module parameter and that at least allowed you to boot windows.

I'm not sure what to do to make ubuntu work from the EC. Tomorrow I'll have more time to google around but I can't promise I'll find something. Depends what google says, how often this situation happens.

---

### Post by Ichwardort on 2010-06-21
[http://swiss.ubuntuforums.org/showthread.php?p=9144366](http://swiss.ubuntuforums.org/showthread.php?p=9144366)

The link above points to exactly the same problem - but without the dual bootloader issue. 

In the meantime, I'll run a bios update today, but don't have any hopes that they have added the EC boot support...

Thanks for your time in helping me on that issue!

kr A.

---

### Post by dino99 on 2010-06-21
maybe some help here if you have not seen it:

mainly "Tweak some files on the new SSD root"

[http://www.ocztechnologyforum.com/forum/showthread.php?73413-Ubuntu-GNU-Linux-10.04-migration-from-HDD-to-SSD](http://www.ocztechnologyforum.com/forum/showthread.php?73413-Ubuntu-GNU-Linux-10.04-migration-from-HDD-to-SSD)

---

