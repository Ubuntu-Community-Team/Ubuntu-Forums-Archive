---
title: "Error 'grub-xputs' Not Found"
date: 2010-12-17
forum: Installation &amp; Upgrades
---

### Post by SpikeLS6 on 2010-12-17
I did the Synaptic Upgrade to Maverick Meerkat 10.10 on my laptop. Win 7 on one of two separate hard drives, and Ubuntu on the other. I kept all the previous configurations the same when the software asked the question about changing to the new formats. On boot up the laptop went right into "grub rescue >".

I located the partitions and found the Ubuntu partition on (hd1,1).

I set the prefix and root which now show:
    prefix=(hd1,1)/boot/grub
    root=hd1,1

I am not sure what Modules to Load, because I can not find any references to them in my big Ubuntu Book.

I tried "insmod /boot/grub/linux.mod", but it returns "error 'grub-xputs' not found".

When using the "initrd" command, it responds "unknown command". Trying to exit Grub 2 with "normal" also yields an "unknown command".The command "exit", "help", and "linux" returns an "unknown command".

The hold up seems to be that pesky 'grub-xputs'. I can not find out what it is.

Is there a list somewhere of Grub 2 Commands?

I had a similar problem upgrading from 9.10 to 10.04 last April. I was able to reload grub and get the laptop operating normally. This time I am unable to get the laptop out of grub rescue.

What other homework do I need to do?

Spike
[email]spikels6@comcast.net[/email]

---

### Post by Quackers on 2010-12-17
Scroll down a little bit on this guide

[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

---

### Post by SpikeLS6 on 2010-12-18
I tried everything in the thread you provided (1195275) that applied to my problem.

I tried downloading the AMD 64 and making a USB stick drive ISO in Windows XP, but I could not get it to install into the laptop; grub rescue kept coming up no matter how I adjusted the BIOS to boot from USB drives first.

I am able to install an older 9.04 Live CD I have to the Desktop. When I go into PLACES, Home Folder, I can see the second hard drive with Ubuntu on it and it has the Boot/Grub/ folders in place. The abi-2.6.32-26-generic-pae that I use is there plus a couple of back up lesser versions, along with memtest86. I can see the config-2.6.32-26-generic-pae and the vmlinuz-2.6.32-26-generic-pae files, too. Is there any way to boot Ubuntu from this then re-install the grub loader?

Spike
[email]spikels6@comcast.net[/email]

---

### Post by Rubi1200 on 2010-12-18
Hi,
use a LiveCD to boot the computer choosing to try not install Ubuntu.

At the live desktop, download and run the boot info script linked at the bottom of my post (instructions included).

Post the results back here.

An xputs error often indicates that GRUB is missing some files. The results should hopefully show us what is going on.

Thanks.

---

### Post by SpikeLS6 on 2010-12-18
Ran your script with the following results:

                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #1 for /boot/grub.
 => Grub 2 is installed in the MBR of /dev/sdb and looks on the same drive in 
    partition #1 for (,msdos1)/boot/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot/BCD

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe

sdb1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  Grub
    Boot sector info:  Grub 0.97 is installed in the boot sector of sdb1 and 
                       looks at sector 78399 of the same hard drive for the 
                       stage2 file. A stage2 file is at this location on 
                       /dev/sdb. Stage2 looks on partition #1 for 
                       /boot/grub/menu.lst.
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x018b0c8f

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048       206,847       204,800   7 HPFS/NTFS
/dev/sda2             206,848   488,394,751   488,187,904   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xc6c7c6c7

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63   964,687,184   964,687,122  83 Linux
/dev/sdb2         964,687,185   976,768,064    12,080,880   5 Extended
/dev/sdb5         964,687,248   976,768,064    12,080,817  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        788C95AA8C956402                       ntfs       System Reserved               
/dev/sda2        F84C98E84C98A2C4                       ntfs                                     
/dev/sdb1        294a6cee-7977-4187-b5e2-c083bac672a9   ext4                                     
/dev/sdb5        3c92c42f-2c7a-408b-b9e2-1cff55201f50   swap                                     

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

rootfs           /                        rootfs     (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sdb1        /media/disk              ext4       (rw,nosuid,nodev,uhelper=hal)
/dev/sda1        /media/System Reserved   fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096)


=========================== sdb1/boot/grub/grub.cfg: ===========================

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
set root='(hd1,msdos1)'
search --no-floppy --fs-uuid --set 294a6cee-7977-4187-b5e2-c083bac672a9
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd1,msdos1)'
search --no-floppy --fs-uuid --set 294a6cee-7977-4187-b5e2-c083bac672a9
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
menuentry 'Ubuntu, with Linux 2.6.35-23-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos1)'
    search --no-floppy --fs-uuid --set 294a6cee-7977-4187-b5e2-c083bac672a9
    linux    /boot/vmlinuz-2.6.35-23-generic-pae root=UUID=294a6cee-7977-4187-b5e2-c083bac672a9 ro  splash  quiet splash
    initrd    /boot/initrd.img-2.6.35-23-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.35-23-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos1)'
    search --no-floppy --fs-uuid --set 294a6cee-7977-4187-b5e2-c083bac672a9
    echo    'Loading Linux 2.6.35-23-generic-pae ...'
    linux    /boot/vmlinuz-2.6.35-23-generic-pae root=UUID=294a6cee-7977-4187-b5e2-c083bac672a9 ro single  splash
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-23-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.32-26-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos1)'
    search --no-floppy --fs-uuid --set 294a6cee-7977-4187-b5e2-c083bac672a9
    linux    /boot/vmlinuz-2.6.32-26-generic-pae root=UUID=294a6cee-7977-4187-b5e2-c083bac672a9 ro  splash  quiet splash
    initrd    /boot/initrd.img-2.6.32-26-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.32-26-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos1)'
    search --no-floppy --fs-uuid --set 294a6cee-7977-4187-b5e2-c083bac672a9
    echo    'Loading Linux 2.6.32-26-generic-pae ...'
    linux    /boot/vmlinuz-2.6.32-26-generic-pae root=UUID=294a6cee-7977-4187-b5e2-c083bac672a9 ro single  splash
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-26-generic-pae
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos1)'
    search --no-floppy --fs-uuid --set 294a6cee-7977-4187-b5e2-c083bac672a9
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos1)'
    search --no-floppy --fs-uuid --set 294a6cee-7977-4187-b5e2-c083bac672a9
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 788c95aa8c956402
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

=============================== sdb1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sdb1 during installation
UUID=294a6cee-7977-4187-b5e2-c083bac672a9 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdb5 during installation
UUID=3c92c42f-2c7a-408b-b9e2-1cff55201f50 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sdb1: Location of files loaded by Grub: ===================


    .3GB: boot/grub/core.img
   1.3GB: boot/grub/grub.cfg
    .0GB: boot/grub/stage2
   7.6GB: boot/initrd.img-2.6.32-26-generic-pae
   7.9GB: boot/initrd.img-2.6.35-23-generic-pae
   6.2GB: boot/vmlinuz-2.6.32-26-generic-pae
   5.5GB: boot/vmlinuz-2.6.35-23-generic-pae
   7.9GB: initrd.img
   7.6GB: initrd.img.old
   5.5GB: vmlinuz
   6.2GB: vmlinuz.old

---

### Post by Rubi1200 on 2010-12-19
Sorry for the delayed response and thanks for posting the results.

Couple of things:
how do you normally boot; by changing the priority in BIOS for the relevant drive?

There seems to be a problem on sdb1:
> Boot sector info:  Grub 0.97 is installed in the boot sector of sdb1 and 
                       looks at sector 78399 of the same hard drive for the 
                       stage2 file. A stage2 file is at this location on 
                       /dev/sdb. Stage2 looks on partition #1 for 
                       /boot/grub/menu.lst.
You seem to have the remnants of a GRUB-legacy install despite the fact that versions after 9.04 use GRUB2.

Moreover, GRUB2 is installed in the MBR of the drive.

In my opinion, the best way to deal with this is to restore the Windows bootloader for sda and then purge and reinstall GRUB2 for sdb.

When you are done, select the correct device in BIOS to boot the relevant drive.

Others may have different opinions, and you may want to wait and hear what they have to say as there are other methods to do this.

---

### Post by SpikeLS6 on 2010-12-19
I normally turn on the laptop and it comes up into the Grub Menu where I can select one of several Ubuntu versions, the Memtest86, or Win 7.

I tried restoring the Windows 7 boot loader on sda1 by inserting the Win 7 DVD and bring up Windows 7, but it turned the DVD for several seconds and came up in the usual Grub Rescue> response with the 'grub-xputs' error.

The BIOS Boot order is:
  USB Floppy
  USB Hard Drive
  ATAPI CD/DVD ROM Drive
  Notebook Hard Drive
  USB Diskette on Key
  !Network Adapter

Same thing happened when I tried to load a new USB Stick with the Ubuntu 10.10 iso extracted on it.

My forest is getting darker because none of the Grub 2 commands that are supposed to work in Grub Rescue are working except Set Prefix= and Set Root=

Thank you for your response and help.

---

### Post by SpikeLS6 on 2010-12-19
Whoa! I just found a CD with Ubuntu 10.01 i386 the computer shop must have put in my paperwork. That would be the 32-bit version. Would that help more versus the 9.04 I tried to use before?

Spike

---

### Post by Rubi1200 on 2010-12-19
Well, based on the results of the boot script you will need to reinstall GRUB either way.

This is what I suggest:
Use the guide by drs305 that I link to to purge and reinstall GRUB using the chroot method.

Make sure you mount the Ubuntu install on sdb1 and reinstall GRUB to the MBR of sdb.
[http://ubuntuforums.org/showthread.php?t=1581099](http://ubuntuforums.org/showthread.php?t=1581099)

You must use the chroot method; the "simple" reinstall won't work in this situation.

Then reboot, run ```
sudo update-grub
``` back in Ubuntu and let's see where we are holding.

---

### Post by SpikeLS6 on 2010-12-19
I did the Chroot from Live CD from your recommended thread 1581099. 1 I did Normal Installation and got to root@ubuntu:/# prompt, 2,3, and 4. During 4 I was not presented with a device option.

5 gave me an error of "no command 'update' found".

Spike

---

### Post by Rubi1200 on 2010-12-19
Did you exit the chroot yet?

If yes, run the boot info script again please and post the results here.

Is sdb a second hard-drive or an external USB drive?

---

### Post by SpikeLS6 on 2010-12-19
No, I am still in Chroot. I left it where it errored.

Spike

---

### Post by SpikeLS6 on 2010-12-19
They put Win 7 in the first internal 250 gig HD and I loaded Ubuntu on the 2nd internal 500 gig HD.

Spike

---

### Post by Rubi1200 on 2010-12-19
I suggest you exit the chroot and rerun the boot info script and post it here please.

---

### Post by SpikeLS6 on 2010-12-19
Running sudo bash boot_info_script055.sh at the ubuntu@ubuntu:~$ prompt returns:

bash: boot_info_script055.sh: No such file or directory

I tried su -
Password: entered mine and it returned:
su: Authentication failure.

Any light in the forest or is it time to reformat the drives and start from scratch?

Spike

---

### Post by Rubi1200 on 2010-12-19
> **SpikeLS6 said:**
> Running sudo bash boot_info_script055.sh at the ubuntu@ubuntu:~$ prompt returns:

bash: boot_info_script055.sh: No such file or directory

I tried su -
Password: entered mine and it returned:
su: Authentication failure.

Any light in the forest or is it time to reformat the drives and start from scratch?

Spike
Please don't do that!

Okay, change of plan.

I assume everything was running fine at some point with this setup?

If BIOS is set to boot from the Notebook Hard Drive, can I assume this means both the 250 and 500GB drives?

If yes, then we can reinstall using the chroot method, but this time to the MBR of sda.

In other words, you would mount the Ubuntu partition on sdb1 but reinstall GRUB to the MBR of sda.

---

### Post by coffeecat on 2010-12-19
Looking through this, I *believe* it should be possible to reinstall grub in a simpler way than using the chroot method. This relies on the current grub.cfg file still being valid for the Ubuntu install at sdb1. @SpikLS6, you have the 10.04 live CD and your hard drive install on sdb1 was originally 10.04, but you updated it to 10.10. Am I correct? Try this:

Boot up with the live 10.04 CD and go to the desktop. **Do not reinstall.** I've adapted the instructions from here:

[https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202](https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202)

Mount your sdb1 partition:

```
sudo mount /dev/sdb1 /mnt
```

Now reinstall grub to the mbr of sda:

```
sudo grub-install --root-directory=/mnt/ /dev/sda
```

Now reboot. That will, hopefully, get you booting into Ubuntu on sdb1 with the first stanza in the grub menu. Once you're in Ubuntu, open a terminal and tidy things up with:

```
sudo update-grub
```

---

### Post by SpikeLS6 on 2010-12-19
I tried coffeecat's suggestion. The laptop booted up to a black screen showing:

               GNU GRUB version 1.97beta4

with a prompt of: sh:grub>

All of coffeecat's assumptions are correct.

Spike

---

### Post by Rubi1200 on 2010-12-19
Odd! That should have worked.

Two suggestions:

1. change the boot priority in BIOS and set the HD as first priority, then try again to boot.

2. run the boot info script again for us so we can see what has changed now.

Thanks.

---

### Post by SpikeLS6 on 2010-12-19
I changed the BIOS to Notebook HD in the top position and rebooted.

I got the same black screen prompt as before: sh:grub>

I did the TAB and looked at the commands and tried boot. It responded Error: no loaded kernel.

Spike

---

### Post by Rubi1200 on 2010-12-19
Take a look at the commands to boot from the prompt in this fantastic guide by drs305:
[http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1594052](http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1594052)

Again, it would really help if you ran and posted the results from the boot info script once more.

---

### Post by Quackers on 2010-12-19
If the boot script is on the desktop the command to run it is
```
sudo bash ~/Desktop/boot_info_script*.sh
```
I think earlier you left out the Desktop bit.

---

### Post by SpikeLS6 on 2010-12-19
Whew, I finally got it to run the script. Sorry for the delay.

                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks for 
    (UUID=294a6cee-7977-4187-b5e2-c083bac672a9)/boot/grub.
 => Grub 2 is installed in the MBR of /dev/sdb and looks on the same drive in 
    partition #1 for (,msdos1)/boot/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot/BCD

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe

sdb1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  Grub
    Boot sector info:  Grub 0.97 is installed in the boot sector of sdb1 and 
                       looks at sector 78399 of the same hard drive for the 
                       stage2 file. A stage2 file is at this location on 
                       /dev/sdb. Stage2 looks on partition #1 for 
                       /boot/grub/menu.lst.
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /etc/fstab /boot/grub/core.img

sdb2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x018b0c8f

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048       206,847       204,800   7 HPFS/NTFS
/dev/sda2             206,848   488,394,751   488,187,904   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xc6c7c6c7

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63   964,687,184   964,687,122  83 Linux
/dev/sdb2         964,687,185   976,768,064    12,080,880   5 Extended
/dev/sdb5         964,687,248   976,768,064    12,080,817  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        788C95AA8C956402                       ntfs       System Reserved               
/dev/sda2        F84C98E84C98A2C4                       ntfs                                     
/dev/sdb1        294a6cee-7977-4187-b5e2-c083bac672a9   ext4                                     
/dev/sdb5        3c92c42f-2c7a-408b-b9e2-1cff55201f50   swap                                     

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (rw)
/dev/loop0       /rofs                    squashfs   (rw)


=============================== sdb1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sdb1 during installation
UUID=294a6cee-7977-4187-b5e2-c083bac672a9 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdb5 during installation
UUID=3c92c42f-2c7a-408b-b9e2-1cff55201f50 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sdb1: Location of files loaded by Grub: ===================


   1.1GB: boot/grub/core.img
    .0GB: boot/grub/stage2
   7.6GB: boot/initrd.img-2.6.32-26-generic-pae
   7.9GB: boot/initrd.img-2.6.35-23-generic-pae
   6.2GB: boot/vmlinuz-2.6.32-26-generic-pae
   5.5GB: boot/vmlinuz-2.6.35-23-generic-pae
   7.9GB: initrd.img
   7.6GB: initrd.img.old
   5.5GB: vmlinuz
   6.2GB: vmlinuz.old

Spike

---

### Post by coffeecat on 2010-12-19
@SpikeLS6, grub 2 has been correctly installed to the mbr of sda and is looking to sdb1, all as it should be. The problem is that your grub.cfg on sdb1 has disappeared. Not quite sure why that should be. I'm afraid you will have to chroot, but here's my (slightly easier) chroot guide. Boot into the live CD again and open a terminal. Now:

```
sudo mount /dev/sdb1 /mnt
```Now su to root:

```
sudo su
```You will now have a # prompt, denoting full root privileges. Take care! Now:

```
mount -t proc none /mnt/proc
mount -o bind /dev /mnt/dev
chroot /mnt /bin/bash
```After the last command, you will actually be "in" sdb1. Now all you have to do is:

```
update-grub
```If all goes well, this command will regenerate  grub.cfg and create menu entries for Ubuntu.

Now:

```
exit
exit
exit
```That's right - three times. The terminal will close after the  last exit. Reboot and remove the CD and you should see a grub menu this time. Let us know how you get on.

---

### Post by Quackers on 2010-12-19
> **SpikeLS6 said:**
> I did the Chroot from Live CD from your recommended thread 1581099. 1 I did Normal Installation and got to root@ubuntu:/# prompt, 2,3, and 4. During 4 I was not presented with a device option.

5 gave me an error of "no command 'update' found".

Spike

I'm not clear on what happened here. Did you run all these commands before the apt-get purge and apt-get install commands?
```
sudo mkdir /mnt/temp 
sudo mount /dev/sdb1 /mnt/temp
for i in /dev /dev/pts /proc /sys; do sudo mount -B $i /mnt/temp$i;  done
sudo cp /etc/resolv.conf /mnt/temp/etc/resolv.conf
sudo chroot /mnt/temp
```

Thanks

---

### Post by SpikeLS6 on 2010-12-19
Progress. I ran all the commands from Coffeecat's last post. The reboot brought the laptop up to the Ubuntu 10.10 Desktop that is on the 2nd 500 Gig hard drive.

I did not get the usual Grub Menu to select Windows 7 on the 1st 250 gig hard drive.

I must need to update grub somehow to be able to select the Win 7 option line.

Quakers, yes I ran all of those commands, but #4 did not offer the device option I was looking for. I update-grub with #5, exit #6, then used #7 to unmount the previous mounts, rebooted, but the screen still came up to grub rescue>

Spike

---

### Post by Quackers on 2010-12-19
Aha! Very nice.
From your newly booted Ubuntu desktop open a terminal and run
```
sudo update-grub
```
and watch the screen as grub.cfg is configured to see if the Windows Loader is picked up.

---

### Post by coffeecat on 2010-12-19
> **SpikeLS6 said:**
> I did not get the usual Grub Menu to select Windows 7 on the 1st 250 gig hard drive.

I must need to update grub somehow to be able to select the Win 7 option line.

Open a terminal in your hard drive install of Ubuntu and:

```
sudo update-grub
```The update-grub you ran from my quick 'n' dirty chroot method wasn't able to detect the Windows partition, but now you're booting into Ubuntu properly, running update-grub again should fix that.

**EDIT**: oops. Didn't see that Quackers had already posted that. :)

---

### Post by SpikeLS6 on 2010-12-19
Believe it or not that was my next guess. I did the sudo update-grub, and it did pick up the WIN 7 loader.

I rebooted and choose Windows 7 and it came up normally. I rebooted again to get back to Ubuntu. The screen came up black with a blinking cursor and after 15-20 seconds I pressed ENTER and Ubuntu came up.

Apparently I am back to square one and owe everyone a great big thank you!

I will go back and show this thread solved. If there are other updates or changes I need to make I will continue to monitor this thread and my emails for another day or two.

Thanks again and have a Merry Christmas!

Spike

---

### Post by Rubi1200 on 2010-12-20
Excellent! Glad you got it sorted out :)

And a big thanks to coffeecat and Quackers too.

---

