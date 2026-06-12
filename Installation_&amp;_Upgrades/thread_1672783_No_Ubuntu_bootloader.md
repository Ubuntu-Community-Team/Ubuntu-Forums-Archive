---
title: "No Ubuntu bootloader"
date: 2011-01-21
forum: Installation &amp; Upgrades
---

### Post by totallybeachin on 2011-01-21
Hi all. I hope I titled the thread correctly. I will do the best I can to explain my situation.
I WAS running Windows 7 and Ubuntu 10.04 LTS on a dual boot system. Everything was fine, never had a problem. UNTIL, stupid me, I was in windows and ticked the box to compress files to save space. I was running out of room that I had partitioned for windows. Linux was my main OS, but just kept windows around for programs that I needed that only work with windows. Was running on about 200mb of space left in windows, so I thought the compression thing would help.
Everything appeared to be fine, at first, however, the first time I tried to boot to Windows after doing the compression thing, I kept getting a message that windows boot mgr was compressed or some such thing. I can't remember exactly what it said. I tried researching how to fix that, but everything I came across didn't work for me. SO...I thought I would just re-install Windows and solve all my problems. 
HA! If only I would have researched a little further. I did not back up Ubuntu or grub or anything else for that matter. I thought it would just be as simple as re-installing Windows.  
Well, windows is running just fine, however, I am not getting the bootloader screen at start up so I can start Ubuntu. 
I have read a couple of things on re-installing grub by booting from the live cd.
I would like to try that, however, I'm not sure if what I have is a live CD. Please keep in mind that while I am not a stupid person, I am not a computer tech either. I get the basics of most thing but it takes me a while and a lot of researching and reading before I finally get what I'm trying to do. With that in mind, my "CD" was created form  the Ubuntu website. When I boot the computer from the CD drive, the CD runs and I am given a choice to "Try" it or "install" it. 
From what I have read, I believe what I need to do is follow the steps outlined here:
[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)
Is that correct? If so, what do I choose on the start up screen, "Try" or "Install"?
If that is not what I should do, any guidance would be greatly appreciated. Like I said, Windows was just a "secondary" system for running programs not supported by Ubuntu, and Ubuntu is where all the "meat" of my computer is, and I have no back up! (Yeah--stupid me!)
Please help, and THANKS!!!


I wanted to add that right now I have all these partitions to my hard drive:
The first section says 47mb of Healthy-(I think this is something for Windows)
Next is (C: 20GB NTFS-this is where windows is
Next 9.54 GB (Healthy Primary Partition<have no idea what's there)
Next 77.77 GB Healthy Primary Partition (This is where Ubuntu is)
Next 1.43 GB Healthy Primary Partition (No idea what's there)
Next 3.00 GB (Healthy Primary Partition(No idea what's there)

Initially, I thought I just had the 47md part for windows, the 20gb for windows and the rest was all Ubuntu. I don't know what caused all the other"partitions" I didn't create them. I had 100GB for Ubuntu, and over time, this is what is has become. 

I don't mind going in and wiping out EVERYTHING with a kill disc, IF I can get into Ubuntu somehow to backup my stuff.

---

### Post by sikander3786 on 2011-01-21
Please boot an Ubuntu CD in the 'Try' mode and post the output of bootinfoscript as per instructions here.

[http://bootinfoscript.sourceforge.net](http://bootinfoscript.sourceforge.net)

It would tell us more about your boot setup and thus let us advise accordingly.

While posting, click the # icon in post menu and paste your text in between the generated [code] tags.

---

### Post by totallybeachin on 2011-01-21
Not sure why, but when I go into Ubuntu with the Live CD, I am not able to connect to the internet. It isn't finding my network, or anyone else's for that matter, so I am not able to download the Boot info Script.
I am going to attempt to download it to an external hard drive, then see if I can access it that way. I am connected to the internet, and accessing this forum on a completely different computer. 
I will post back my findings/failures in a few minutes....(I hope)!!

---

### Post by totallybeachin on 2011-01-21
All the download appeared to be was a text document, so I opened it and typed into my terminal 
```
sudo bash boot_info_script055.sh
``` as instructed and what I got back was 
```
sudo bash boot_info_script055.sh: command not found
```
Was I supposed to type that in? Am I doing something wrong?

Any suggestions??

---

### Post by bryanl on 2011-01-21
What you ran across with the BootMgr compressed error might be why a lot of Windows systems have a small (100 MB) partition with this file - it seems to be needed to help Windows figure out how to boot. It can be copied from the install or upgrade DVD or you can use the fix system option on these DVDs to repair the Windows startup.

When you run a live CD ubuntu system, the first thing to do is to see if the Ubuntu installation is still there. If you ran a Windows recovery, it might have restored your drive to its original state and wiped out Ubuntu as well as resetting the MBR boot record. Run gparted (in the system menu) to check to see if the partition layout still has the Ubuntu partitions.

If the Ubuntu partitions are still there then you can reinstall Grub2 fairly easily, especially if you use a fairly simple partition layout (like a root partition that includes /boot and so on. Mount that root partition to something like /mnt/newroot and then run
```
grub-install --root-directory=/mnt/newroot /dev/sdx
```
to reinstall grub on the /dev/sdx drive. 

that should get you to where you can boot the Ubuntu system. Run 'update-grub' if you need to get your grub menu straight. 

If it gets deeper than that, then the boot information script will help some of the gurus here to focus on potential fixes. (note that to run a script in your current directory, you need to specify it as ./script-name and make sure it is set with chmod +x script-name)

---

### Post by presence1960 on 2011-01-21
> **totallybeachin said:**
> All the download appeared to be was a text document, ***_so I opened it_*** and typed into my terminal 
```
sudo bash boot_info_script055.sh
``` as instructed and what I got back was 
```
sudo bash boot_info_script055.sh: command not found
```
Was I supposed to type that in? Am I doing something wrong?

Any suggestions??

Do not open the file. Move it to the desktop and run the command ```
sudo bash ~/Desktop/boot_info_script*.sh
``` it will generate a RESULTS.txt file on the Desktop. Open that file and copy/paste the contents back here.

---

### Post by totallybeachin on 2011-01-21
> **bryanl said:**
> What you ran across with the BootMgr compressed error might be why a lot of Windows systems have a small (100 MB) partition with this file - it seems to be needed to help Windows figure out how to boot. It can be copied from the install or upgrade DVD or you can use the fix system option on these DVDs to repair the Windows startup.

When you run a live CD ubuntu system, the first thing to do is to see if the Ubuntu installation is still there. If you ran a Windows recovery, it might have restored your drive to its original state and wiped out Ubuntu as well as resetting the MBR boot record. Run gparted (in the system menu) to check to see if the partition layout still has the Ubuntu partitions.

If the Ubuntu partitions are still there then you can reinstall Grub2 fairly easily, especially if you use a fairly simple partition layout (like a root partition that includes /boot and so on. Mount that root partition to something like /mnt/newroot and then run
```
grub-install --root-directory=/mnt/newroot /dev/sdx
```to reinstall grub on the /dev/sdx drive. 

that should get you to where you can boot the Ubuntu system. Run 'update-grub' if you need to get your grub menu straight. 

If it gets deeper than that, then the boot information script will help some of the gurus here to focus on potential fixes. (note that to run a script in your current directory, you need to specify it as ./script-name)
I appreciate all your help. I really do.
BUT, I am an idiot and have no idea what you are saying. Can you please say all that again, but in idiot instead of english.
I don't really know how to do any of that stuff in the terminal. Any time I do, I literally search for hours, sometimes days looking for step by step instructions to help me with whatever problems I may be having. Just didn't work out that way for me this time.  
 didn't run Windows recovery. I just ran it as an install. When I was aked where I wanted to install it, I chose the partition that I knew it HAD been on, formatted it, then install a fresh copy. 
All the other partitions are still there, I'm just don't know where they came from. When I put Ubuntu on my computer for the first time. I used a program called Kill Disk or something like that, COMPLETELY wiped out my whole computer, Then followed instructions I found somewhere on the web, created a 20gb partition for windows and the rest of the hard drive was for Ubuntu. Everything went great. A bit of work for someone that had no idea what they were doing, but it did work out. Know I have all those partitions as stated in my first post. Why they are they and what they are being used for, I haven't a clue. 
I did start the Live CD, and chose "try" and I am able to "see" my computer under "places" and it is showing:
120 GB Hard Disk 21 GB Filesystem
120 GB Hard Disk 84 GB Filesystem
File System
If I click on the 84 GB fileesystem, there are 3 folders there
My Name, boot, lost+found (which has an "x" on the folder)
I was hoping there would be some simple "fix" but Obviuosly, that is not going to be the case..................:lol:

---

### Post by presence1960 on 2011-01-21
> **totallybeachin said:**
> I appreciate all your help. I really do.
BUT, I am an idiot and have no idea what you are saying. Can you please say all that again, but in idiot instead of english.
I don't really know how to do any of that stuff in the terminal. Any time I do, I literally search for hours, sometimes days looking for step by step instructions to help me with whatever problems I may be having. Just didn't work out that way for me this time.  
 didn't run Windows recovery. I just ran it as an install. When I was aked where I wanted to install it, I chose the partition that I knew it HAD been on, formatted it, then install a fresh copy. 
All the other partitions are still there, I'm just don't know where they came from. When I put Ubuntu on my computer for the first time. I used a program called Kill Disk or something like that, COMPLETELY wiped out my whole computer, Then followed instructions I found somewhere on the web, created a 20gb partition for windows and the rest of the hard drive was for Ubuntu. Everything went great. A bit of work for someone that had no idea what they were doing, but it did work out. Know I have all those partitions as stated in my first post. Why they are they and what they are being used for, I haven't a clue. 
I did start the Live CD, and chose "try" and I am able to "see" my computer under "places" and it is showing:
120 GB Hard Disk 21 GB Filesystem
120 GB Hard Disk 84 GB Filesystem
File System
If I click on the 84 GB fileesystem, there are 3 folders there
My Name, boot, lost+found (which has an "x" on the folder)
I was hoping there would be some simple "fix" but Obviuosly, that is not going to be the case..................:lol:

Just run the boot info script and we will try to figure this out for you. Without the boot info script output we have no idea literally what is on your machine and where. So do this:

Let's get a better look at your setup & boot process. Boot the Ubuntu Live CD/USB. Choose "try ubuntu without any changes", when the desktop loads come back here and do the following:

1. Download the boot info script. There is a link in my signature.
2. Once downloaded move the boot info script to the desktop.
3. Open a terminal and run the command ```
sudo bash ~/Desktop/boot_info_script*.sh
```

  This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text. 

See [here]("http://bootinfoscript.sourceforge.net/") for more info on the boot info script.

---

### Post by sikander3786 on 2011-01-21
Hopefully, that would be a simple "fix" based on a total of 2 commands that we would give you to copy/paste to your Terminal. But we need to see the output of bootinfoscript for that. Otherwise, we are banging our heads against the wall as we don't know your setup, boot, partitions etc etc.

---

### Post by totallybeachin on 2011-01-21
> **presence1960 said:**
> Do not open the file. Move it to the desktop and run the command ```
sudo bash ~/Desktop/boot_info_script*.sh
``` it will generate a RESULTS.txt file on the Desktop. Open that file and copy/paste the contents back here.
Thank you!
Here is what I got
```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda
 => Syslinux is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Unknown
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /COMMAND.COM

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe /grldr

sda3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Windows XP: Fat32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /bootmgr /ntldr /NTDETECT.COM

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda7: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   /boot/grub/core.img

sda4: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.1 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb1: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat32
    Boot sector info:  According to the info in the boot sector, sdb5 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63        96,389        96,327  de Dell Utility
/dev/sda2    *         96,390    42,042,104    41,945,715   7 HPFS/NTFS
/dev/sda3          62,044,158   234,436,544   172,392,387   f W95 Ext d (LBA)
/dev/sda5         228,139,128   234,436,544     6,297,417  dd Dell Media Direct
/dev/sda6         225,138,688   228,139,007     3,000,320  82 Linux swap / Solaris
/dev/sda7          62,044,160   225,136,639   163,092,480  83 Linux
/dev/sda4          42,043,392    62,042,111    19,998,720  83 Linux


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *         16,065   976,768,064   976,752,000   f W95 Ext d (LBA)
/dev/sdb5              16,128   976,768,064   976,751,937   b W95 FAT32


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        07DA-0A09                              vfat       DellUtility                   
/dev/sda2        42A0DF4BA0DF4457                       ntfs                                     
/dev/sda3: PTTYPE="dos" 
/dev/sda4        edef439a-2d56-4f2b-bd6e-d5d266b6a95b   ext3                                     
/dev/sda5        07DA-0A09                              vfat       MEDIADIRECT                   
/dev/sda6        5863a059-685d-44d1-9b50-412750978acd   swap                                     
/dev/sda7        a398b89e-4c0b-432b-a1b2-ca26d44ba9d0   ext4                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1: PTTYPE="dos" 
/dev/sdb5        0159-73CA                              vfat       PENDRIVE                      
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sda7        /media/a398b89e-4c0b-432b-a1b2-ca26d44ba9d0 ext4       (rw,nosuid,nodev,uhelper=udisks)
/dev/sda4        /mnt                     ext3       (rw)
/dev/sdb5        /media/PENDRIVE          vfat       (rw,nosuid,nodev,uhelper=udisks,uid=999,gid=999,shortname=mixed,dmask=0077,utf8=1,flush)


================================ sda5/boot.ini: ================================

[boot loader]
timeout=0
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Embedded" /fastdetect /KERNEL=NTOSBOOT.EXE /maxmem=768

=================== sda7: Location of files loaded by Grub: ===================


  66.2GB: boot/grub/core.img

=========================== sda4/boot/grub/grub.cfg: ===========================

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
set root='(hd0,4)'
search --no-floppy --fs-uuid --set edef439a-2d56-4f2b-bd6e-d5d266b6a95b
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
set root='(hd0,4)'
search --no-floppy --fs-uuid --set edef439a-2d56-4f2b-bd6e-d5d266b6a95b
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
menuentry 'Ubuntu, with Linux 2.6.32-27-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,4)'
    search --no-floppy --fs-uuid --set edef439a-2d56-4f2b-bd6e-d5d266b6a95b
    linux    /boot/vmlinuz-2.6.32-27-generic root=UUID=edef439a-2d56-4f2b-bd6e-d5d266b6a95b ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-27-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-27-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,4)'
    search --no-floppy --fs-uuid --set edef439a-2d56-4f2b-bd6e-d5d266b6a95b
    echo    'Loading Linux 2.6.32-27-generic ...'
    linux    /boot/vmlinuz-2.6.32-27-generic root=UUID=edef439a-2d56-4f2b-bd6e-d5d266b6a95b ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-27-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-26-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,4)'
    search --no-floppy --fs-uuid --set edef439a-2d56-4f2b-bd6e-d5d266b6a95b
    linux    /boot/vmlinuz-2.6.32-26-generic root=UUID=edef439a-2d56-4f2b-bd6e-d5d266b6a95b ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-26-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-26-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,4)'
    search --no-floppy --fs-uuid --set edef439a-2d56-4f2b-bd6e-d5d266b6a95b
    echo    'Loading Linux 2.6.32-26-generic ...'
    linux    /boot/vmlinuz-2.6.32-26-generic root=UUID=edef439a-2d56-4f2b-bd6e-d5d266b6a95b ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-26-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-25-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,4)'
    search --no-floppy --fs-uuid --set edef439a-2d56-4f2b-bd6e-d5d266b6a95b
    linux    /boot/vmlinuz-2.6.32-25-generic root=UUID=edef439a-2d56-4f2b-bd6e-d5d266b6a95b ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-25-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,4)'
    search --no-floppy --fs-uuid --set edef439a-2d56-4f2b-bd6e-d5d266b6a95b
    echo    'Loading Linux 2.6.32-25-generic ...'
    linux    /boot/vmlinuz-2.6.32-25-generic root=UUID=edef439a-2d56-4f2b-bd6e-d5d266b6a95b ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,4)'
    search --no-floppy --fs-uuid --set edef439a-2d56-4f2b-bd6e-d5d266b6a95b
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=edef439a-2d56-4f2b-bd6e-d5d266b6a95b ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,4)'
    search --no-floppy --fs-uuid --set edef439a-2d56-4f2b-bd6e-d5d266b6a95b
    echo    'Loading Linux 2.6.32-21-generic ...'
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=edef439a-2d56-4f2b-bd6e-d5d266b6a95b ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd0,4)'
    search --no-floppy --fs-uuid --set edef439a-2d56-4f2b-bd6e-d5d266b6a95b
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd0,4)'
    search --no-floppy --fs-uuid --set edef439a-2d56-4f2b-bd6e-d5d266b6a95b
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda2)" {
    insmod ntfs
    set root='(hd0,2)'
    search --no-floppy --fs-uuid --set 7ca236c2a23680a6
    chainloader +1
}
menuentry "Microsoft Windows XP Embedded (on /dev/sda5)" {
    insmod fat
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 07da-0a09
    drivemap -s (hd0) ${root}
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sda4/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda4 during installation
UUID=edef439a-2d56-4f2b-bd6e-d5d266b6a95b /               ext3    errors=remount-ro 0       1
# /home was on /dev/sda7 during installation
UUID=a398b89e-4c0b-432b-a1b2-ca26d44ba9d0 /home           ext4    defaults        0       2
# swap was on /dev/sda6 during installation
UUID=5863a059-685d-44d1-9b50-412750978acd none            swap    sw              0       0

=================== sda4: Location of files loaded by Grub: ===================


  30.4GB: boot/grub/core.img
  30.5GB: boot/grub/grub.cfg
  30.4GB: boot/initrd.img-2.6.32-21-generic
  30.5GB: boot/initrd.img-2.6.32-25-generic
  30.3GB: boot/initrd.img-2.6.32-26-generic
  30.5GB: boot/initrd.img-2.6.32-27-generic
  30.4GB: boot/vmlinuz-2.6.32-21-generic
  30.5GB: boot/vmlinuz-2.6.32-25-generic
  30.5GB: boot/vmlinuz-2.6.32-26-generic
  30.4GB: boot/vmlinuz-2.6.32-27-generic
  30.5GB: initrd.img
  30.3GB: initrd.img.old
  30.4GB: vmlinuz
  30.5GB: vmlinuz.old
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda1

00000000  eb 50 90 44 65 6c 6c 20  38 2e 31 00 02 04 01 00  |.P.Dell 8.1.....|
00000010  02 00 02 00 00 f8 5e 00  3f 00 ff 00 3f 00 00 00  |......^.?...?...|
00000020  47 78 01 00 80 00 29 09  0a da 07 44 65 6c 6c 55  |Gx....)....DellU|
00000030  74 69 6c 69 74 79 46 41  54 31 36 20 20 20 10 00  |tilityFAT16   ..|
00000040  01 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000050  00 00 fa 33 c0 8e d0 bc  00 07 fb fc b9 80 00 8e  |...3............|
00000060  d8 be 00 7c b8 00 20 8e  c0 33 ff f3 66 a5 ea 73  |...|.. ..3..f..s|
00000070  00 00 20 0e 1f 66 0f b7  06 16 00 66 d1 e0 03 06  |.. ..f.....f....|
00000080  0e 00 66 03 06 1c 00 66  a3 46 00 a1 11 00 a3 4e  |..f....f.F.....N|
00000090  00 c1 e8 04 a2 40 00 b8  00 30 a3 44 00 8e c0 e8  |.....@...0.D....|
000000a0  f0 00 33 db b9 0b 00 be  ba 01 8b fb f3 a6 74 0f  |..3...........t.|
000000b0  83 c3 20 ff 0e 4e 00 75  eb be b0 01 e9 b4 00 26  |.. ..N.u.......&|
000000c0  8b 47 1a a3 50 00 a1 16  00 a3 4e 00 66 a1 1c 00  |.G..P.....N.f...|
000000d0  03 06 0e 00 66 a3 46 00  a1 4e 00 3d 40 00 76 03  |....f.F..N.=@.v.|
000000e0  b8 40 00 a2 40 00 e8 a9  00 66 0f b6 06 40 00 66  |.@..@....f...@.f|
000000f0  01 06 46 00 29 06 4e 00  74 09 c1 e0 05 01 06 44  |..F.).N.t......D|
00000100  00 eb d5 c7 06 44 00 70  00 a0 0d 00 a2 40 00 66  |.....D.p.....@.f|
00000110  0f b7 06 50 00 66 83 e8  02 66 0f b6 0e 0d 00 66  |...P.f...f.....f|
00000120  f7 e1 66 0f b7 0e 16 00  66 d1 e1 03 06 0e 00 66  |..f.....f......f|
00000130  03 0e 1c 00 66 03 c1 66  0f b7 0e 11 00 66 c1 e9  |....f..f.....f..|
00000140  04 66 03 c1 66 a3 46 00  e8 47 00 8b 36 50 00 b8  |.f..f.F..G..6P..|
00000150  00 30 d1 e6 73 03 05 00  10 8e c0 26 ad 3d f8 ff  |.0..s......&.=..|
00000160  73 16 a3 50 00 0f b6 06  0d 00 c1 e0 09 01 06 42  |s..P...........B|
00000170  00 eb 9c e8 0d 00 eb fe  8a 16 24 00 33 ed ea 00  |..........$.3...|
00000180  00 70 00 ac 3c 00 74 09  b4 0e bb 07 00 cd 10 eb  |.p..<.t.........|
00000190  f2 c3 b4 42 8a 16 24 00  be 3e 00 cd 13 72 01 c3  |...B..$..>...r..|
000001a0  be a5 01 eb ce 44 69 73  6b 20 65 72 72 6f 72 00  |.....Disk error.|
000001b0  4e 6f 20 4c 6f 61 64 65  72 00 44 45 4c 4c 42 49  |No Loader.DELLBI|
000001c0  4f 20 42 49 4e 00 00 00  00 00 00 00 00 00 00 00  |O BIN...........|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200



```

---

### Post by presence1960 on 2011-01-21
Boot the Ubuntu Live CD. Choose try ubuntu. When the desktop loads open a terminal (Applications > Accessories > Terminal)

Run in terminal ```
sudo mount /dev/sda4 /mnt
```This will mount your ubuntu root ( / ) partition.

Next in terminal run ```
sudo grub-install --root-directory=/mnt/ /dev/sda
```This will put GRUB in the MBR of your disk and pointing to sda4 when you boot. When completed close terminal and reboot without the Live CD. You should be good to go.

FYI when you install windows it always writes it's bootloader to the MBR of the first disk to boot, thus anything you had there is over -written.

**_Note Please:_**since you are new and not familiar with terminal copy/paste my commands into terminal. If you decide to type terminal is case sensitive and spacing must be exact.

---

### Post by totallybeachin on 2011-01-21
I can not thank you enough.
I am back up and running and everything appears to be A-OK!!!
Thank you--Thank You--Thank You.

I appreciate all you do for us Linux wanna-bees!!!   :lol:

---

### Post by presence1960 on 2011-01-21
> **totallybeachin said:**
> I can not thank you enough.
I am back up and running and everything appears to be A-OK!!!
Thank you--Thank You--Thank You.

I appreciate all you do for us Linux wanna-bees!!!   :lol:

We all started at the beginning, and were helped along. You are welcome!

---

