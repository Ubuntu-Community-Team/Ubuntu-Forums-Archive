---
title: "GRUB problems after distro upgrade (10.04&gt;10.10)"
date: 2011-05-13
forum: Installation &amp; Upgrades
---

### Post by Distorzion on 2011-05-13
Well, yesterday I left my PC upgrading my distro to 10.10 to fix a problem of audio compatibility of 10.04.

After the required reboot, I had problems with grub

```
ERROR The symbol grub_xputs not found.
```

I tried to recover it by running a few lines I found on another post, but I was unable to load kernel due to the same error. **Since I had no Ubuntu live CD, I had to write MBR from a Windows CD. I managed to boot windows, and downloaded 10.04 .iso. Currently, Im on ubuntu live**. Since I read somewhere that this cases are "similar but different" I proceed to request help.[B] I already downloaded and ran bootinfo script (at the end of post). 
[/B] 
**NOTE** I never managed to get on Ubuntu after distro upgrade

Sorry for my bad english and sorry if Im doing something wrong, this is my first post on this forums

Hope you can help me, and **thanks in advance**.

>                 Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda
 => Grub 2 is installed in the MBR of /dev/sdb and looks on the same drive in 
    partition #6 for (,msdos6)/boot/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot/BCD

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sdb2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe

sdb3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb4: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb6: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb7: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63   585,938,744   585,938,682   7 HPFS/NTFS
/dev/sda2    *    585,938,944   586,143,743       204,800   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63   122,881,184   122,881,122   7 HPFS/NTFS
/dev/sdb2         122,882,048   204,802,047    81,920,000   7 HPFS/NTFS
/dev/sdb3         204,802,048   409,602,047   204,800,000   7 HPFS/NTFS
/dev/sdb4         409,609,366   488,396,799    78,787,434   5 Extended
/dev/sdb5         409,609,368   411,553,169     1,943,802  82 Linux swap / Solaris
/dev/sdb6         411,553,792   485,150,719    73,596,928  83 Linux
/dev/sdb7         485,152,768   488,396,799     3,244,032  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        7D72F4F17B769B66                       ntfs       Distorzion                    
/dev/sda2        F42CE6A02CE65D5C                       ntfs       Reservado para el sistema     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        4A9CF3529CF33753                       ntfs       Windows XP                    
/dev/sdb2        1ACCD444CCD41C37                       ntfs       Windows 7                     
/dev/sdb3        B41C1C911C1C50AA                       ntfs       Distorzion                    
/dev/sdb4: PTTYPE="dos" 
/dev/sdb5        90ac0d8c-3dec-4600-91a5-f6da97129ed8   swap                                     
/dev/sdb6        a6e5fdf3-be1f-44dc-82ae-b59494932303   ext4                                     
/dev/sdb7        8555cf84-0897-4b9c-961c-4fc5202aed22   swap                                     
/dev/sdb: PTTYPE="dos" 
error: /dev/sdc: No medium found
error: /dev/sdd: No medium found
error: /dev/sde: No medium found
error: /dev/sdf: No medium found

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)


================================ sdb1/boot.ini: ================================

[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect 

=========================== sdb6/boot/grub/grub.cfg: ===========================

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
set root='(hd1,msdos6)'
search --no-floppy --fs-uuid --set a6e5fdf3-be1f-44dc-82ae-b59494932303
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd1,msdos6)'
search --no-floppy --fs-uuid --set a6e5fdf3-be1f-44dc-82ae-b59494932303
set locale_dir=($root)/boot/grub/locale
set lang=es
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
menuentry 'Ubuntu, with Linux 2.6.35-28-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos6)'
    search --no-floppy --fs-uuid --set a6e5fdf3-be1f-44dc-82ae-b59494932303
    linux    /boot/vmlinuz-2.6.35-28-generic root=UUID=a6e5fdf3-be1f-44dc-82ae-b59494932303 ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-28-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-28-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos6)'
    search --no-floppy --fs-uuid --set a6e5fdf3-be1f-44dc-82ae-b59494932303
    echo    'Loading Linux 2.6.35-28-generic ...'
    linux    /boot/vmlinuz-2.6.35-28-generic root=UUID=a6e5fdf3-be1f-44dc-82ae-b59494932303 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-28-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-31-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos6)'
    search --no-floppy --fs-uuid --set a6e5fdf3-be1f-44dc-82ae-b59494932303
    linux    /boot/vmlinuz-2.6.32-31-generic root=UUID=a6e5fdf3-be1f-44dc-82ae-b59494932303 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-31-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-31-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos6)'
    search --no-floppy --fs-uuid --set a6e5fdf3-be1f-44dc-82ae-b59494932303
    echo    'Loading Linux 2.6.32-31-generic ...'
    linux    /boot/vmlinuz-2.6.32-31-generic root=UUID=a6e5fdf3-be1f-44dc-82ae-b59494932303 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-31-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos6)'
    search --no-floppy --fs-uuid --set a6e5fdf3-be1f-44dc-82ae-b59494932303
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos6)'
    search --no-floppy --fs-uuid --set a6e5fdf3-be1f-44dc-82ae-b59494932303
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda2)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos2)'
    search --no-floppy --fs-uuid --set f42ce6a02ce65d5c
    chainloader +1
}
menuentry "Microsoft Windows XP Professional (on /dev/sdb1)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd1,msdos1)'
    search --no-floppy --fs-uuid --set 4a9cf3529cf33753
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

=============================== sdb6/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda6 during installation
UUID=a6e5fdf3-be1f-44dc-82ae-b59494932303 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda7 during installation
UUID=8555cf84-0897-4b9c-961c-4fc5202aed22 none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sdb6: Location of files loaded by Grub: ===================


 219.4GB: boot/grub/core.img
 211.5GB: boot/grub/grub.cfg
 219.9GB: boot/initrd.img-2.6.32-31-generic
 220.2GB: boot/initrd.img-2.6.35-28-generic
 219.6GB: boot/vmlinuz-2.6.32-31-generic
 219.8GB: boot/vmlinuz-2.6.35-28-generic
 220.2GB: initrd.img
 219.9GB: initrd.img.old
 219.8GB: vmlinuz
 219.6GB: vmlinuz.old
=======Devices which don't seem to have a corresponding hard drive==============

sdc sdd sde sdf 

---

### Post by drs305 on 2011-05-13
Distorzion,

Welcome to the Ubuntu forums.

This error message normally means that Grub2 was not fully installed. We don't know if that is the only problem, or if there are other problems with the installation.

From the LiveCD, you will need to 'chroot' into your Ubuntu partition and reinstall Grub. It's often best just to get rid of Grub 2 completely and then reinstall it.

You may have a problem chrooting into 10.10 with a 10.04 CD - you normally want to use the same release. You may get a bash error message - we will see. 

Since we just want to install Grub, it may or may not work. Here are the commands if you want to try. They are from the 'Chroot' link in my signature line.

Boot the LiveCD, mount your Ubuntu partition, and chroot. If you are already running the CD, the first command will try to umount sda5. If it won't unmount, reboot.

```
sudo umount /dev/sdb6
sudo mkdir /mnt/temp
sudo mount /dev/sdb6 /mnt/temp
for i in /dev /dev/pts /proc /sys; do sudo mount -B $i /mnt/temp$i;  done
sudo chroot /mnt/temp

```
This should leave you at a 'root' prompt, meaning you have successfully chrooted.

The first command tests your Internet connection. If the command doesn't work, do NOT continue. As you run the commands, you will be warned you are removing the bootloader. Also, you will be asked for kernel options - TAB to OK and press ENTER. When asked where to install grub, use the SPACEBAR to select sdb, then TAB to OK. Do NOT select any partition, only sdb.

```
apt-get update
apt-get purge grub grub-pc grub-common
apt-get install grub-common grub-pc
update-grub
exit
```

Unmount:
```
for i in /dev/pts /dev /proc /sys; do sudo umount /mnt/temp$i ; done
```
During the reboot, make sure your BIOS is set to boot sdb first.

---

### Post by Distorzion on 2011-05-13
Thank you very much for reply.

I managed to get root.

> This may be an stupid question, but while purging im being asked about remove all GRUB2 files from system, should I answer yes or no?

Sorry I guess removing bootloader was a different to removing files... I continue working on this

---

### Post by drs305 on 2011-05-13
> **Distorzion said:**
> This may be an stupid question, but while purging im being asked about remove all GRUB2 files from system, should I answer yes or no?

Not a stupid question at all. This is probably the message stating you will be left with no bootloader.

Since it isn't working, you won't lose anything if you remove the files. As long as your Internet connection is working, you will be almost immediately reinstalling it, so it's okay to remove all G2 files.

---

### Post by Distorzion on 2011-05-13
Ok, next question:

I made it, and GRUB generated the new cfg,  then I unmounted and reboot the system but GRUB doesn't appear. Instead, one of my windows loaded right away.

I reboot the system again and check for HDD to boot. Select the one of 250gb, saved and exit from BIOS, but to my surprise, windows loaded directly again.

What should I do now?

I guess this is related to FIXMBR command I used to be able to boot windows in order to download the ubuntu .iso.

By the way, double check to HDD to boot, and its set to the one of 250GB (which I believe is the sdb, am I wrong?)

So... whats the next step?

I'm on windows right now.

---

### Post by garvinrick4 on 2011-05-13
drs305 when through with OP can you explain the "for i" and the "$i /mnt/temp" for me.
I understand you are mounting and binding /dev /dev/pts /sys /proc to /mnt/temp but it is the
i and $i that I have never used.

```
for i in /dev /dev/pts /proc /sys; do sudo mount -B $i /mnt/temp$i;  done
```

*nor do you have to cp /etc/resolv.conf

---

### Post by Distorzion on 2011-05-13
> **garvinrick4 said:**
> drs305 when through with OP can you explain the "for i" and the "$i /mnt/temp" for me.
I understand you are mounting and binding /dev /dev/pts /sys /proc to /mnt/temp but it is the
i and $i that I have never used.

```
for i in /dev /dev/pts /proc /sys; do sudo mount -B $i /mnt/temp$i;  done
```
I'm not an expert, but I guess it's a "for loop"

---

### Post by drs305 on 2011-05-13
sdb, at the time you ran the boot info script, was your Ubuntu partition. You could enter BIOS to check that the correct drive (look at the sizes) is booting. Ubuntu is on the 250GB drive.

Is it the Windows bootloader you are seeing, or is it just booting into Windows? It's possible, though not likely, that Grub is booting into Windows. If Grub is controlling, holding down the SHIFT key during boot should allow the menu to display.

We really won't know what's happened until we see a new RESULTS.txt. I'm about to log off for the night. Someone else can check it or I'll look again tomorrow.

@ garvinrick4, I'll try to remember to do it tomorrow.

---

### Post by garvinrick4 on 2011-05-13
> @ garvinrick4, I'll try to remember to do it tomorrow.     Thank you drs305 appreciate it.
EDIT: Read in your tutorial "How to purge and reinstall Grub" Sorry to interrupt your thread.
[HOWTO: Purge and Reinstall Grub 2 from the Live CD - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=1581099")

---

### Post by garvinrick4 on 2011-05-13
> **Distorzion said:**
> Ok, next question:

I made it, and GRUB generated the new cfg,  then I unmounted and reboot the system but GRUB doesn't appear. Instead, one of my windows loaded right away.

I reboot the system again and check for HDD to boot. Select the one of 250gb, saved and exit from BIOS, but to my surprise, windows loaded directly again.

What should I do now?

So... whats the next step?

I'm on windows right now.


I believe you are booting off of the Windows drive sda and not the drive sdb that
has Ubuntu in sdb6, if you ran drs305 commands and they all worked fine then
if you boot into sdb drive first in order then you will get choice of  all your windows installs plus your Ubuntu using grub2. 
If you boot off  of sda will go straight to Windows because using Windows boot manager  "bcd" in drive sda
If any problems post boot script but should be fine. Should be a way in BIOS to select boot drive at each boot also.

---

### Post by Distorzion on 2011-05-14
In fact, it was like drs305 said, GRUB was going right into Windows (IDK why).

It's fixed by now, solution to second problem was to press shift and boot into ubuntu a reconfigure GRUB as you would.

By the way, I said I double checked for sdb to be HDD to boot, instead of sda.

Problem is solved.

Thank you very much **drs305** and **garvinrick4**.

One last doubt, I never switched to sda instead of sdb. I believe I read somewhere (when looking for the fix on GRUB rescue prompt, that solution was just to change the order in BIOS. I never think it would be "as simple as that", so I don't even try that. Well to the doubt:

Why this happen'd? Is it a bug as reported in some sites? Do you think (if it happens to me again, because upgrading didn't solve my problems with the audio of the application as I wanted to, so I'm seriously considering moving into Ubuntu 11.04) that switching "boot order" (which was changed apparently "without my action nor authorization") would solve the problem?

I'll mark this post as solved by tomorrow, just waiting to see if someone would answer.

Thank you for all your help.

---

### Post by drs305 on 2011-05-14
> **Distorzion said:**
> One last doubt, I never switched to sda instead of sdb. I believe I read somewhere (when looking for the fix on GRUB rescue prompt, that solution was just to change the order in BIOS. I never think it would be "as simple as that", so I don't even try that. Well to the doubt:

Why this happen'd? 

Grub cannot change the BIOS boot order. What it can do is change where the BIOS goes to next. So if sda's MBR says go to sda6, and sdb's MBR says to go to sdb5, where the system ends up will be different depending on which drive BIOS looks at first. I think you understand that.

What follows may or may apply to your situation. I think #2 is really what you are asking...

1. One thing that sometimes causes difficulties is that Grub remembers the settings when it was originally installed. If it is installed in an upgrade, unless told differently, it will attempt to install itself in the original location. So if you originally installed it in drive A, but then moved your OS to drive B for some reason, Grub may still try to install itself on drive A.

You can check where Grub thinks it should go with the following command:
```
sudo dpkg-reconfigure grub-pc
```
Use the TAB feature to move to the OK option.

2. As far as what the default OS setting is when Grub boots, it is determined by the GRUB_DEFAULT setting in /etc/default/grub. The default is a number ( 0 ), meaning the first entry in the menu. This number never changes unless the user changes it. So whatever the first menu item is will boot if the number is 0.

If the user doesn't play with the Grub files, this should always boot the latest Ubuntu kernel. Problems can arise if the user changes files. 

For instance: I think you indicated Windows is now booting first *from the grub menu*. If you didn't change the GRUB_DEFAULT setting (0), here are 4 ways that could happen:

[LIST]
[*]If you made the /etc/grub.d/10_linux script unexecutable,removed the file, or renamed it starting with a number larger than 30.
[*]If you changed the name of 30_os-prober in /etc/grub.d to a name with a number starting less than 10 (example: 06_os-prober).
[*]If you made a custom menu with Windows as the first entry and it's name started with a number lower than 10.
[*]At some point, Grub 2 introduced the ability to try a second entry if the boot failed (I think it was with Grub 1.99 but am not sure). In some cases, if the selected menuentry did not work, it would try the next one. I don't know enough to know if a failed linux OS would allow it to boot into Windows (the next option) or not. My vague recollection is that it might boot the next *higher* entry but I just haven't played with it enough to know.
[/LIST]

Except for the last item, these are things that an inexperienced user would probably not attempt. I expect the Grub developers believed that if a user were attempting these types of modifications they would be able to understand what the results would be.

Happy Ubuntu-ing !

---

### Post by drs305 on 2011-05-14
> **garvinrick4 said:**
> drs305 when through with OP can you explain the "for i" and the "$i /mnt/temp" for me.
I understand you are mounting and binding /dev /dev/pts /sys /proc to /mnt/temp but it is the
i and $i that I have never used.


Here's a layman's explanation:
```
for i in /dev /dev/pts /proc /sys; do sudo mount -B $i /mnt/temp$i;  done
```
What it replaces (with a Ubuntu partition already mounted on /mnt/temp (for those late to this party...):
```
sudo mount -B /dev /mnt/temp/dev
sudo mount -B /dev/pts /mnt/temp/dev/pts
sudo mount -B /proc /mnt/temp/proc
sudo mount -B /sys /mnt/temp/sys
```

The command is in three parts:
> for i in /dev /dev/pts /proc /sys;
What it does:
The 'for i in' means that the command will be run sequentially for each entry after the variable *i*.
The variable *i* thus becomes "/dev", "/dev/pts", "/proc", and "/sys" in sequence.

> do sudo mount -B $i /mnt/temp$i;
What it does:
"do" (execute) "sudo" (as root) mounting (with the -B switch) the variable *i* to /mnt/temp[variable *i*]. In the first run, *i* would be equal to "/dev", so the command becomes "sudo mount -B */dev* /mnt/temp*/dev*

The mount command would be run for each *i* variable. When it runs out of variables, it procedes to:

The final section:> 
done;
Which ends the command.

Here is another example, not involving mounting:
```
for x in 1 2 3 4 OK; do echo $x; done
```
Produces:
> 1
2
3
4
OK

---

### Post by garvinrick4 on 2011-05-14
@ drs305
  Thank you for taking the time to explain. Makes all the sense in the world for
the use of mounting and binding. Saves oodles of keystrokes to chroot for anything
you wish to accomplish. I am sure I will find other good uses also. Learning something 
new in the use of code makes my day, thank you kindly.

---

