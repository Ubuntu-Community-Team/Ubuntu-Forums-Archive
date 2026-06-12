---
title: "Installing to a USB hard drive partition"
date: 2011-02-04
forum: Installation &amp; Upgrades
---

### Post by pakas on 2011-02-04
I'm trying to install Ubuntu 10.10 to a partition on an external hard drive. On my first attempt, I used a Ubuntu live USB stick and used the GUI installer to install to a 250GB ext4 partition on my hard drive. I restarted... and met the grub rescue prompt. 

The first time I tried to install, I clicked the skip button after the installer got hung up on "Copying file 2 of 6" for about a half hour. So I decided to try another install without hitting the skip button.

I booted my laptop again using the live USB stick and tried another install to the same partition. This time, the installer did not get stuck on "Copying file 2 of 6." I rebooted, and it worked! 

About an hour later, I returned, turned on my laptop, and got grub rescue. I stuck in the live USB stick and tried to find out what the problem was. It looked like my external hard drive was mounted as sdc (partition sdc5) when I installed, but was now mounted as sdb. I don't know if this is why Ubuntu failed to boot the second time.

At this point I gave up for the day and used a Windows recovery disk to fix the boot sector.

This is my first attempt at an Ubuntu install and I feel like I am doing something terribly wrong. Any advice?

---

### Post by oldfred on 2011-02-04
Welcome to the forums.

It must have mount the install flash drive as sdb and the external as sdc. Then you unplugged the flash drive and the external became sdb.
It still should have booted as it works off of UUIDs not drives.

But I had the same issue and thought it was because I had a large gap in drive order. I installed from one flash sde to another sdf. Then when I rebooted sdf became sde. (I have 3 drives, but no sdd).

I just used e on the grub menu and and changed the hd5 to hd4 and it worked. Then sudo update-grub fixed it.

Sometimes you just have to reinstall grub2. Did you install grub to the USB drive or let it install to your internal drive.

You should be able to install grub2 to the external and in BIOS set external to boot first. If not found then it defaults to the internal.

#Comments are anything after the #, enter commands in terminal session
#Install MBR from LiveCD, Ubuntu install on sdb5 and want grub2 in drive sda's MBR:
#Find linux partition, change sdb5 if not correct:
sudo fdisk -l
#confirm that linux is sdb5
sudo mount /dev/sdb5 /mnt
sudo grub-install --root-directory=/mnt/ /dev/sdb
#If that returns any errors run:
sudo grub-install --recheck --root-directory=/mnt/ /dev/sdb
# After rebooting into working system
sudo update-grub

---

### Post by pakas on 2011-02-04
Thanks for the help.

> **oldfred said:**
> It must have mount the install flash drive as sdb and the external as sdc. Then you unplugged the flash drive and the external became sdb.
It still should have booted as it works off of UUIDs not drives.
Ok, that was what I suspected.

> **oldfred said:**
> 
I just used e on the grub menu and and changed the hd5 to hd4 and it worked. Then sudo update-grub fixed it.

Sorry, I am a Linux noob. What does 'e' do in grub? Also, how do I know which hdX is my external hard drive?

> **oldfred said:**
> 
Sometimes you just have to reinstall grub2. Did you install grub to the USB drive or let it install to your internal drive.

I used the advanced partition selector in the Ubuntu installer and  selected my external hard drive as the grub location, but when I  disconnected the external drive and tried to boot (hoping to get to  Windows) I still got grub rescue, so I think grub may have been written  to the internal drive somehow.

> **oldfred said:**
> 
You should be able to install grub2 to the external and in BIOS set external to boot first. If not found then it defaults to the internal.

I already set the BIOS to boot from external devices first.

> **oldfred said:**
> 
#Comments are anything after the #, enter commands in terminal session
#Install MBR from LiveCD, Ubuntu install on sdb5 and want grub2 in drive sda's MBR:
#Find linux partition, change sdb5 if not correct:
sudo fdisk -l
#confirm that linux is sdb5
sudo mount /dev/sdb5 /mnt
sudo grub-install --root-directory=/mnt/ /dev/sdb
#If that returns any errors run:
sudo grub-install --recheck --root-directory=/mnt/ /dev/sdb
# After rebooting into working system
sudo update-grub
I forgot to mention that I already tried this. The first time it worked in that I managed to get to the grub boost menu rather than grub rescue, but after I selected Ubuntu, it failed to boot. The screen turned black and my computer kept humming. After about 15 minutes, I gave up and powered off my computer. The next time I booted, I got grub rescue again. I tried booting from the live USB stick and running those commands again, but it did not work.

Also, I never actually managed to boot Ubuntu. (My memory failed me while I was writing my last post.) The farthest I got was the grub boot menu, as I mentioned above.

---

### Post by oldfred on 2011-02-04
that often is a video issue. I had the same with my nVidia card.

How to set NOMODESET and other kernel boot options in grub2 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
I had to do this with my Nvidia 9600GT:
boot from the cd, press F6 and then select the nomodeset option.
then
On first boot after install, press e on getting the GRUB bootloader. 
Hold shift from BIOS boot to get menu if only one system installed.
Using arrow keys navigate to and delete quiet and splash and type the word nomodeset in their place
Press Ctrl and X to boot (low graphics mode)

After I installed Nvidia driver (default from pop up) then it has worked without issue.
gksudo nvidia-settings
Or it should be in System>administration>Hardware drivers.
Possible additional things to run once nvidia working:
gksudo nvidia-settings
sudo nvidia-xconfig

---

### Post by pakas on 2011-02-04
How do I set nomodeset? I hit F6 and tried running "install nomodeset" from the boot menu, but it said "could not find image 'install.'"

---

### Post by oldfred on 2011-02-04
From the liveCd you should get a menu from f6 that lets you choose nomodeset as a boot parameter. Link in my previous post shows screen you should see (older verison but essentially the same).

If you are at grub menu then you press e for edit and on linux line replace splash quiet with nomodeset.

---

### Post by pakas on 2011-02-04
I am using a live USB, and I do not see that screen. Instead, I see a black background with Ubuntu written across the top in white. There are a series of options on this screen. I can't remember the exact wording of the options, but they are pretty much the same ones shown in that thread. There are no function button shortcuts on the screen. Instead, there is a Boot Options item that takes you to a command line like thing in which the function buttons take you to different help pages. The F6 button brings up a help page about general boot options. Nomodeset is not listed anywhere within the help text. There is a prompt that says "boot:" and the help text had something like "boot: install nopaic" so I mimicked that and entered "install nomodeset." I got the response  "could not find image 'install.'"and then it booted into live Ubuntu.

---

### Post by oldfred on 2011-02-04
I have not used Cd for 2 or 3 versions, as i use USB now. Someone else may know exact details.

When you did it, did you copy it exactly. Silly computers want things just a certain way.
boot: install nomodeset

---

### Post by pakas on 2011-02-04
I'm also beginning to think that I'm choosing the wrong location for the boot loader.

Which of the following would be the right location?

/dev/mapper/isw_djhegfibgd_Volume0 Linux device-mapper (striped) (128.0 GB)
/dev/mapper/isw_djhegfibgd_Volume01 Windows Vista (loader)
/dev/mapper/isw_djhegfibgd_Volume02 Windows 7 (loader)
/dev/mapper/isw_djhegfibgd_Volume03
/dev/sdc WD My Passport 071A (1.0 TB)     <-- USB hard drive
/dev/sdc1    <--- Probably not this one: ntfs USB hard drive partition
/dev/sdc5    <-- ext4 USB hard drive partition
/dev/sda       <-- Internal drive

I've been using /dev/sdc WD My Passport.

---

### Post by C.S.Cameron on 2011-02-04
If sdc is the drive you are installing to, the external hdd, then the bootloader should go on root sdc, not sdc1, sdc2, etc.

Here is a step by step that generally works, adjust partition size to suit, The FAT32 partition is if you intend to plug into a Windows computer to transfer data:

Following step by step for Full install of 10.10 to USB device, adjust partition size to suit, sizes given are minimum:

Turn off and unplug the computer. (See note at bottom)
Remove the side from the case.
Unplug the power cable from the hard drive.
Plug the computer back in.
Insert the flash drive.
Insert the Live CD.
Start the computer, the CD should boot.
Select language
Select install Ubuntu.
Select Download updates while installing and Select Install this third-party software.
Forward
At "Allocate drive space" select "Specify partitions manually (advanced)".
Forward
Confirm Device is correct.
Select "New Partition Table" click Continue on the drop down.
Click "Free space" and "Add".
Select "Primary".
Make "New partition size..." about 1GB.
Location = Beginning.
"Use as:" = "NTFS file system"
And "Mount point" = windows.
Select "OK"
Click "free space" and then "Add".
Select "Primary", "New partition size ..." = 3 to 4 GB, Beginning, Ext4, and Mount point = "/" then OK.
(Optional)
Click "free space" and then "Add".
Select "Primary", "New partition size ..." = 1 to 2 GB, Beginning, Ext2, and Mount point = "/home" then OK.
(Optional)
Click "free space" and then "Add".
Select "Primary", "New partition size ..." = remaining space, (1 to 2 GB), Beginning and "Use as" = "swap area" then OK.
(Importent)
Confirm "Device for boot loader installation" points to the USB drive. Default should be ok if HDD was unplugged.
Click "Install Now".
Select your location.
Forward.
Select Keyboard layout.
Forward.
Insert your name, username, password, computer name and select if you want to log in automatically or require a password.
Selecting "Encrypt my home folder" is a good option if you are woried about loosing your USB drive.
Select forward.
Wait until install is complete.
Turn off computer and plug in the HDD.
Stick the side panel back on.

Note:
You may omit disabling the hard drive if after partitioning you choose to install grub to the root of the usb drive you are installing Ubuntu to, (ie sdb not sdb1). Be cautious, many people have overwritten the HDD MBR.
At boot you will then be given the option to boot your computer's hard drive, even when booting another computer.

---

### Post by oldfred on 2011-02-04
You did not mention you have RAID or LVM.

Post this so we can see what is where:

Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the post's menu and then paste the contents between the generated [ code] paste here [ /code] tags.

---

### Post by SeventhStreetAce on 2011-02-04
> **pakas said:**
> I'm trying to install Ubuntu 10.10 to a partition on an external hard drive. On my first attempt, I used a Ubuntu live USB stick and used the GUI installer to install to a 250GB ext4 partition on my hard drive. I restarted... and met the grub rescue prompt. 

The first time I tried to install, I clicked the skip button after the installer got hung up on "Copying file 2 of 6" for about a half hour. So I decided to try another install without hitting the skip button.

I booted my laptop again using the live USB stick and tried another install to the same partition. This time, the installer did not get stuck on "Copying file 2 of 6." I rebooted, and it worked! 

About an hour later, I returned, turned on my laptop, and got grub rescue. I stuck in the live USB stick and tried to find out what the problem was. It looked like my external hard drive was mounted as sdc (partition sdc5) when I installed, but was now mounted as sdb. I don't know if this is why Ubuntu failed to boot the second time.

At this point I gave up for the day and used a Windows recovery disk to fix the boot sector.

This is my first attempt at an Ubuntu install and I feel like I am doing something terribly wrong. Any advice?

I am having the same issues......

---

### Post by pakas on 2011-02-05
> **C.S.Cameron said:**
> 
Turn off and unplug the computer. (See note at bottom)
Remove the side from the case.
Unplug the power cable from the hard drive.
Plug the computer back in.

This isn't really an option as I'm installing to a laptop, not a desktop.

> **C.S.Cameron said:**
> 
You may omit disabling the hard drive if after partitioning you choose  to install grub to the root of the usb drive you are installing Ubuntu  to, (ie sdb not sdb1).

This is what I have been trying so far. I'm glad to know I was doing at least one thing right. :P

> **C.S.Cameron said:**
> 
At "Allocate drive space" select "Specify partitions manually (advanced)".
Forward
Confirm Device is correct.
Select "New Partition Table" click Continue on the drop down.
Click "Free space" and "Add".
Select "Primary".
Make "New partition size..." about 1GB.
Location = Beginning.
"Use as:" = "NTFS file system"
And "Mount point" = windows.
Select "OK"
Click "free space" and then "Add".
Select "Primary", "New partition size ..." = 3 to 4 GB, Beginning, Ext4, and Mount point = "/" then OK.
(Optional)
Click "free space" and then "Add".
Select "Primary", "New partition size ..." = 1 to 2 GB, Beginning, Ext2, and Mount point = "/home" then OK.
(Optional)
Click "free space" and then "Add".
Select "Primary", "New partition size ..." = remaining space, (1 to 2 GB), Beginning and "Use as" = "swap area" then OK.
(Importent)
Confirm "Device for boot loader installation" points to the USB drive. Default should be ok if HDD was unplugged.
So far I have just been creating one ext4 partition. I will try this method.

---

### Post by pakas on 2011-02-05
Boot information:

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda
 => Syslinux is installed in the MBR of /dev/sdb
 => Grub 2 is installed in the MBR of /dev/sdd and looks on the same drive in 
    partition #5 for (,msdos5)/boot/grub.
 => Windows is installed in the MBR of /dev/mapper/isw_djhegfibgd_Volume0

sda1: _________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''

sda2: _________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''
mount: unknown filesystem type ''

sda3: _________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''

sdb1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Unknown
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdd1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdd2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdd5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdd6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

isw_djhegfibgd_Volume01: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /boot/bcd

isw_djhegfibgd_Volume02: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot/BCD

isw_djhegfibgd_Volume03: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /NST/menu.lst /Windows/System32/winload.exe

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 64.0 GB, 64023257088 bytes
255 heads, 63 sectors/track, 7783 cylinders, total 125045424 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1               2,048    27,262,975    27,260,928  27 Hidden HPFS/NTFS
/dev/sda2    *     27,262,976    27,467,775       204,800   7 HPFS/NTFS
/dev/sda3          27,467,776   250,079,231   222,611,456   7 HPFS/NTFS

/dev/sda3 ends after the last sector of /dev/sda

Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 8011 MB, 8011087872 bytes
32 heads, 63 sectors/track, 7761 cylinders, total 15646656 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63    15,646,175    15,646,113   b W95 FAT32


Drive: sdd ___________________ _____________________________________________________

Disk /dev/sdd: 1000.2 GB, 1000175828992 bytes
255 heads, 63 sectors/track, 121597 cylinders, total 1953468416 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdd1    *          2,048 1,464,424,816 1,464,422,769   7 HPFS/NTFS
/dev/sdd2       1,464,426,494 1,953,466,367   489,039,874   5 Extended
/dev/sdd5       1,464,426,496 1,933,567,999   469,141,504  83 Linux
/dev/sdd6       1,933,570,048 1,953,466,367    19,896,320  82 Linux swap / Solaris


Drive: isw_djhegfibgd_Volume0 ___________________ _____________________________________________________

Disk /dev/mapper/isw_djhegfibgd_Volume0: 128.0 GB, 128041877504 bytes
255 heads, 63 sectors/track, 15566 cylinders, total 250081792 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/mapper/isw_djhegfibgd_Volume01              2,048    27,262,975    27,260,928  27 Hidden HPFS/NTFS
/dev/mapper/isw_djhegfibgd_Volume02   *     27,262,976    27,467,775       204,800   7 HPFS/NTFS
/dev/mapper/isw_djhegfibgd_Volume03         27,467,776   250,079,231   222,611,456   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/mapper/isw_djhegfibgd_Volume01 66FA6E21FA6DEE2D                       ntfs       Recovery                      
/dev/mapper/isw_djhegfibgd_Volume02 C6F6B340F6B32F93                       ntfs       System Reserved               
/dev/mapper/isw_djhegfibgd_Volume03 1C08B42308B3F9BA                       ntfs                                     
/dev/mapper/isw_djhegfibgd_Volume0: PTTYPE="dos" 
/dev/sda                                                isw_raid_member                               
/dev/sdb1        1CD9-434D                              vfat       PENDRIVE                      
/dev/sdb: PTTYPE="dos" 
/dev/sdc                                                isw_raid_member                               
/dev/sdd1        825883A258839417                       ntfs       MyPassport                    
/dev/sdd2: PTTYPE="dos" 
/dev/sdd5        95a7154e-571c-4c1e-9e3b-54fad541a752   ext4                                     
/dev/sdd6        2f048813-3336-4686-8d44-28e5eacfc84d   swap                                     
/dev/sdd: PTTYPE="dos" 
error: /dev/sda1: No such file or directory
error: /dev/sda2: No such file or directory
error: /dev/sda3: No such file or directory

=============================== "ls -R /dev/mapper/" output: ===============================
/dev/mapper:
control
isw_djhegfibgd_Volume0
isw_djhegfibgd_Volume01
isw_djhegfibgd_Volume02
isw_djhegfibgd_Volume03

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sdb1        /cdrom                   vfat       (ro,relatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sdd5        /media/95a7154e-571c-4c1e-9e3b-54fad541a752 ext4       (rw,nosuid,nodev,uhelper=udisks)
/dev/sdd1        /media/MyPassport        fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)


=========================== sdd5/boot/grub/grub.cfg: ===========================

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
set root='(hd3,msdos5)'
search --no-floppy --fs-uuid --set 95a7154e-571c-4c1e-9e3b-54fad541a752
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd3,msdos5)'
search --no-floppy --fs-uuid --set 95a7154e-571c-4c1e-9e3b-54fad541a752
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
menuentry 'Ubuntu, with Linux 2.6.35-25-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd3,msdos5)'
    search --no-floppy --fs-uuid --set 95a7154e-571c-4c1e-9e3b-54fad541a752
    linux    /boot/vmlinuz-2.6.35-25-generic-pae root=UUID=95a7154e-571c-4c1e-9e3b-54fad541a752 ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-25-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.35-25-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd3,msdos5)'
    search --no-floppy --fs-uuid --set 95a7154e-571c-4c1e-9e3b-54fad541a752
    echo    'Loading Linux 2.6.35-25-generic-pae ...'
    linux    /boot/vmlinuz-2.6.35-25-generic-pae root=UUID=95a7154e-571c-4c1e-9e3b-54fad541a752 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-25-generic-pae
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(hd3,msdos5)'
    search --no-floppy --fs-uuid --set 95a7154e-571c-4c1e-9e3b-54fad541a752
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd3,msdos5)'
    search --no-floppy --fs-uuid --set 95a7154e-571c-4c1e-9e3b-54fad541a752
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows Vista (loader) (on /dev/mapper/isw_djhegfibgd_Volume01)" {
    insmod part_msdos
    insmod ntfs
    set root='(/dev/mapper/isw_djhegfibgd_Volume0,msdos1)'
    search --no-floppy --fs-uuid --set 66fa6e21fa6dee2d
    chainloader +1
}
menuentry "Windows 7 (loader) (on /dev/mapper/isw_djhegfibgd_Volume02)" {
    insmod part_msdos
    insmod ntfs
    set root='(/dev/mapper/isw_djhegfibgd_Volume0,msdos2)'
    search --no-floppy --fs-uuid --set c6f6b340f6b32f93
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

=============================== sdd5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdd5 during installation
UUID=95a7154e-571c-4c1e-9e3b-54fad541a752 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdd6 during installation
UUID=2f048813-3336-4686-8d44-28e5eacfc84d none            swap    sw              0       0

=================== sdd5: Location of files loaded by Grub: ===================


 840.1GB: boot/grub/core.img
 960.4GB: boot/grub/grub.cfg
 750.6GB: boot/initrd.img-2.6.35-25-generic-pae
 840.1GB: boot/vmlinuz-2.6.35-25-generic-pae
 750.6GB: initrd.img
 840.1GB: vmlinuz

==================== isw_djhegfibgd_Volume03/NST/menu.lst: ====================

# NeoSmart NeoGrub Bootloader Configuration File 
# 
# This is the NeoGrub configuration file, and should be located at C:\NST\menu.lst 
# Please see the EasyBCD Documentation for information on how to create/modify entries: 
# http://neosmart.net/wiki/display/EBCD/ 
 
default 0                #Pick the task to be run if the user doesn't pick one within the time limit. 
timeout 10               #Give the user 10 seconds to choose a task. 
 
title        Ubuntu 
root        (hd3,5)  #Load Ubuntu from the 2nd harddrive's 3rd partition. 
kernel        /boot/vmlinuz-2.6.35-25-generic-pae root=/dev/sdb5 nomodeset 
initrd        /boot/initrd.img-2.6.35-25-generic-pae 
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda1


Unknown BootLoader  on sda2


Unknown BootLoader  on sda3


Unknown BootLoader  on sdb1

00000000  eb 58 90 53 59 53 4c 49  4e 55 58 00 02 20 20 00  |.X.SYSLINUX..  .|
00000010  02 00 00 00 00 f8 00 00  3f 00 20 00 3f 00 00 00  |........?. .?...|
00000020  a1 bd ee 00 eb 0e 00 00  00 00 00 00 02 00 00 00  |................|
00000030  01 00 06 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000040  00 00 29 4d 43 d9 1c 20  20 20 20 20 20 20 20 20  |..)MC..         |
00000050  20 20 46 41 54 33 32 20  20 20 fa fc 31 c9 8e d1  |  FAT32   ..1...|
00000060  bc 76 7b 52 06 57 8e c1  b1 26 bf 78 7b f3 a5 8e  |.v{R.W...&.x{...|
00000070  d9 bb 78 00 0f b4 37 0f  a0 56 20 d2 78 1b 31 c0  |..x...7..V .x.1.|
00000080  b1 06 89 3f 89 47 02 f3  64 a5 8a 0e 18 7c 88 4d  |...?.G..d....|.M|
00000090  bc 50 50 50 50 cd 13 eb  4b f6 45 b4 7f 75 25 38  |.PPPP...K.E..u%8|
000000a0  4d b8 74 20 66 3d 21 47  50 54 75 10 80 7d b8 ed  |M.t f=!GPTu..}..|
000000b0  75 0a 66 ff 75 ec 66 ff  75 e8 eb 0f 51 51 66 ff  |u.f.u.f.u...QQf.|
000000c0  75 bc eb 07 51 51 66 ff  36 1c 7c b4 08 cd 13 72  |u...QQf.6.|....r|
000000d0  13 20 e4 75 0f c1 ea 08  42 89 16 1a 7c 83 e1 3f  |. .u....B...|..?|
000000e0  89 0e 18 7c fb bb aa 55  b4 41 8a 16 74 7b cd 13  |...|...U.A..t{..|
000000f0  72 10 81 fb 55 aa 75 0a  f6 c1 01 74 05 c6 06 32  |r...U.u....t...2|
00000100  7d 00 66 b8 16 1e 00 00  66 ba 00 00 00 00 bb 00  |}.f.....f.......|
00000110  7e e8 10 00 66 81 3e 24  7e 34 be f5 72 75 76 ea  |~...f.>$~4..ruv.|
00000120  38 7e 00 00 66 03 06 64  7b 66 13 16 68 7b b9 10  |8~..f..d{f..h{..|
00000130  00 eb 2b 66 52 66 50 06  53 6a 01 6a 10 89 e6 66  |..+fRfP.Sj.j...f|
00000140  60 b4 42 e8 7f 00 66 61  8d 64 10 72 01 c3 66 60  |`.B...fa.d.r..f`|
00000150  31 c0 e8 70 00 66 61 e2  da c6 06 32 7d 2b 66 60  |1..p.fa....2}+f`|
00000160  66 0f b7 36 18 7c 66 0f  b7 3e 1a 7c 66 f7 f6 31  |f..6.|f..>.|f..1|
00000170  c9 87 ca 66 f7 f7 66 3d  ff 03 00 00 77 17 c0 e4  |...f..f=....w...|
00000180  06 41 08 e1 88 c5 88 d6  b8 01 02 e8 37 00 66 61  |.A..........7.fa|
00000190  72 01 c3 e2 c9 31 f6 8e  d6 bc 6c 7b 8e de 66 8f  |r....1....l{..f.|
000001a0  06 78 00 be cc 7d e8 09  00 31 c0 cd 16 cd 19 f4  |.x...}...1......|
000001b0  eb fd 66 60 ac 20 c0 74  09 b4 0e bb 07 00 cd 10  |..f`. .t........|
000001c0  eb f2 66 61 c3 8a 16 74  7b cd 13 c3 42 6f 6f 74  |..fa...t{...Boot|
000001d0  20 65 72 72 6f 72 0d 0a  00 00 00 00 00 00 00 00  | error..........|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


=============================== StdErr Messages: ===============================

hexdump: /dev/sda1: No such file or directory
hexdump: /dev/sda1: No such file or directory
hexdump: /dev/sda2: No such file or directory
hexdump: /dev/sda2: No such file or directory
hexdump: /dev/sda3: No such file or directory
hexdump: /dev/sda3: No such file or directory
```

---

### Post by oldfred on 2011-02-05
First you have a partition problem in sda and/or your LVM. I know nothing about LVMs.

/dev/sda3 ends after the last sector of /dev/sda

Not sure how to repair that with your LVM.

With the LVM this is probably not the way to fix it.
sfdisk to fix extended beyond end -partition outside the disk!
[http://ubuntuforums.org/showthread.php?t=1012825](http://ubuntuforums.org/showthread.php?t=1012825)

It also looks like your 8GB flash drive gets mounted as sdb and then your external drive is mounted as sdc or sdd. Grub in the 1000GB drive wants to boot from sdd. UUID  looks correct and hd3 should be sdd.

---

### Post by pakas on 2011-02-05
I also know nothing about LVMs. Could you please explain?

On my latest Ubuntu Install attempt, I gave up the idea of preserving my NTFS partition and divided my external hard drive into a 997 GB ext4 partition mounted at / and a 3 GB swap partition. I don't see any traces of grub. The computer boots right to Windows every time.

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda
 => Syslinux is installed in the MBR of /dev/sdb
 => Windows is installed in the MBR of /dev/mapper/isw_djhegfibgd_Volume0

sda1: _________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''

sda2: _________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''
mount: unknown filesystem type ''

sda3: _________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''

sdb1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Unknown
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

isw_djhegfibgd_Volume01: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /boot/bcd

isw_djhegfibgd_Volume02: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot/BCD

isw_djhegfibgd_Volume03: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /NST/menu.lst /Windows/System32/winload.exe

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 64.0 GB, 64023257088 bytes
255 heads, 63 sectors/track, 7783 cylinders, total 125045424 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1               2,048    27,262,975    27,260,928  27 Hidden HPFS/NTFS
/dev/sda2    *     27,262,976    27,467,775       204,800   7 HPFS/NTFS
/dev/sda3          27,467,776   250,079,231   222,611,456   7 HPFS/NTFS

/dev/sda3 ends after the last sector of /dev/sda

Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 8011 MB, 8011087872 bytes
32 heads, 63 sectors/track, 7761 cylinders, total 15646656 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63    15,646,175    15,646,113   b W95 FAT32


Drive: isw_djhegfibgd_Volume0 ___________________ _____________________________________________________

Disk /dev/mapper/isw_djhegfibgd_Volume0: 128.0 GB, 128041877504 bytes
255 heads, 63 sectors/track, 15566 cylinders, total 250081792 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/mapper/isw_djhegfibgd_Volume01              2,048    27,262,975    27,260,928  27 Hidden HPFS/NTFS
/dev/mapper/isw_djhegfibgd_Volume02   *     27,262,976    27,467,775       204,800   7 HPFS/NTFS
/dev/mapper/isw_djhegfibgd_Volume03         27,467,776   250,079,231   222,611,456   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/mapper/isw_djhegfibgd_Volume01 66FA6E21FA6DEE2D                       ntfs       Recovery                      
/dev/mapper/isw_djhegfibgd_Volume02 C6F6B340F6B32F93                       ntfs       System Reserved               
/dev/mapper/isw_djhegfibgd_Volume03 1C08B42308B3F9BA                       ntfs                                     
/dev/mapper/isw_djhegfibgd_Volume0: PTTYPE="dos" 
/dev/sda                                                isw_raid_member                               
/dev/sdb1        1CD9-434D                              vfat       PENDRIVE                      
/dev/sdb: PTTYPE="dos" 
/dev/sdc                                                isw_raid_member                               
error: /dev/sda1: No such file or directory
error: /dev/sda2: No such file or directory
error: /dev/sda3: No such file or directory

=============================== "ls -R /dev/mapper/" output: ===============================
/dev/mapper:
control
isw_djhegfibgd_Volume0
isw_djhegfibgd_Volume01
isw_djhegfibgd_Volume02
isw_djhegfibgd_Volume03

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sdb1        /cdrom                   vfat       (ro,relatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
/dev/loop0       /rofs                    squashfs   (ro,noatime)

=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda1


Unknown BootLoader  on sda2


Unknown BootLoader  on sda3


Unknown BootLoader  on sdb1

00000000  eb 58 90 53 59 53 4c 49  4e 55 58 00 02 20 20 00  |.X.SYSLINUX..  .|
00000010  02 00 00 00 00 f8 00 00  3f 00 20 00 3f 00 00 00  |........?. .?...|
00000020  a1 bd ee 00 eb 0e 00 00  00 00 00 00 02 00 00 00  |................|
00000030  01 00 06 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000040  00 00 29 4d 43 d9 1c 20  20 20 20 20 20 20 20 20  |..)MC..         |
00000050  20 20 46 41 54 33 32 20  20 20 fa fc 31 c9 8e d1  |  FAT32   ..1...|
00000060  bc 76 7b 52 06 57 8e c1  b1 26 bf 78 7b f3 a5 8e  |.v{R.W...&.x{...|
00000070  d9 bb 78 00 0f b4 37 0f  a0 56 20 d2 78 1b 31 c0  |..x...7..V .x.1.|
00000080  b1 06 89 3f 89 47 02 f3  64 a5 8a 0e 18 7c 88 4d  |...?.G..d....|.M|
00000090  bc 50 50 50 50 cd 13 eb  4b f6 45 b4 7f 75 25 38  |.PPPP...K.E..u%8|
000000a0  4d b8 74 20 66 3d 21 47  50 54 75 10 80 7d b8 ed  |M.t f=!GPTu..}..|
000000b0  75 0a 66 ff 75 ec 66 ff  75 e8 eb 0f 51 51 66 ff  |u.f.u.f.u...QQf.|
000000c0  75 bc eb 07 51 51 66 ff  36 1c 7c b4 08 cd 13 72  |u...QQf.6.|....r|
000000d0  13 20 e4 75 0f c1 ea 08  42 89 16 1a 7c 83 e1 3f  |. .u....B...|..?|
000000e0  89 0e 18 7c fb bb aa 55  b4 41 8a 16 74 7b cd 13  |...|...U.A..t{..|
000000f0  72 10 81 fb 55 aa 75 0a  f6 c1 01 74 05 c6 06 32  |r...U.u....t...2|
00000100  7d 00 66 b8 16 1e 00 00  66 ba 00 00 00 00 bb 00  |}.f.....f.......|
00000110  7e e8 10 00 66 81 3e 24  7e 34 be f5 72 75 76 ea  |~...f.>$~4..ruv.|
00000120  38 7e 00 00 66 03 06 64  7b 66 13 16 68 7b b9 10  |8~..f..d{f..h{..|
00000130  00 eb 2b 66 52 66 50 06  53 6a 01 6a 10 89 e6 66  |..+fRfP.Sj.j...f|
00000140  60 b4 42 e8 7f 00 66 61  8d 64 10 72 01 c3 66 60  |`.B...fa.d.r..f`|
00000150  31 c0 e8 70 00 66 61 e2  da c6 06 32 7d 2b 66 60  |1..p.fa....2}+f`|
00000160  66 0f b7 36 18 7c 66 0f  b7 3e 1a 7c 66 f7 f6 31  |f..6.|f..>.|f..1|
00000170  c9 87 ca 66 f7 f7 66 3d  ff 03 00 00 77 17 c0 e4  |...f..f=....w...|
00000180  06 41 08 e1 88 c5 88 d6  b8 01 02 e8 37 00 66 61  |.A..........7.fa|
00000190  72 01 c3 e2 c9 31 f6 8e  d6 bc 6c 7b 8e de 66 8f  |r....1....l{..f.|
000001a0  06 78 00 be cc 7d e8 09  00 31 c0 cd 16 cd 19 f4  |.x...}...1......|
000001b0  eb fd 66 60 ac 20 c0 74  09 b4 0e bb 07 00 cd 10  |..f`. .t........|
000001c0  eb f2 66 61 c3 8a 16 74  7b cd 13 c3 42 6f 6f 74  |..fa...t{...Boot|
000001d0  20 65 72 72 6f 72 0d 0a  00 00 00 00 00 00 00 00  | error..........|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


=============================== StdErr Messages: ===============================

hexdump: /dev/sda1: No such file or directory
hexdump: /dev/sda1: No such file or directory
hexdump: /dev/sda2: No such file or directory
hexdump: /dev/sda2: No such file or directory
hexdump: /dev/sda3: No such file or directory
hexdump: /dev/sda3: No such file or directory
```

---

### Post by oldfred on 2011-02-05
Either you have RAID turned on in BIOS or LVM which is a logical partition manager. LVM  gives you the flexibility to move partitions around easily and even across different drives, but it adds a level of complexity. RAID is often set in BIOS by some computers but need multiple drives to work well. Best for servers with hardware RAID, software RAID just adds complexity for slight speed gains.

this does not tell me what it is as I do not know either well.
/dev/mapper/isw_djhegfibgd_Volume0

---

