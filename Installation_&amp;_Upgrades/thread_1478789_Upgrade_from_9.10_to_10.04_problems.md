---
title: "Upgrade from 9.10 to 10.04 problems"
date: 2010-05-10
forum: Installation &amp; Upgrades
---

### Post by Arachan on 2010-05-10
Hello,

I had Ubuntu 9.10 with KDE added on installed on my HDD and I decided to upgrade to 10.04. I ran the update manager and selected Upgrade. I followed the instructions and it said it would need to download 999M. I accepted and it spent a few hours downloading the packages and installing them. It seemed to go fine until it rebooted, as it was shutting down it showed what I assume is the new shutdown screen, but it said Kubuntu even though I was in Gnome. 

When it restarted I got Grub as usual, except for the wrong screen resolution. I selected the top option which was the newest kernel (there were two, both with recovery modes). The screen then went black with a few coloured pixels at the top. It stayed like this, I tried pressing CTRL+ALT+BACKSPACE to attempt to restart X, but nothing happened. I tried ALT+F1, this also did nothing. 

I pressed the reset button on my case and booted first to the recovery mode, but the same thing happened. I then tried the other kernel as well as it's recovery mode. They all got the same result.

Is this a problem with my installation, or could it be a hardware-related problem in my monitor or graphics card (ATI Radeon HD2600)?

Any help would be much appreciated,
Thanks,
Arachan.

---

### Post by darkod on 2010-05-10
Have you tried running a 10.04 cd in live mode to see if it works with your hardware (graphics)? If it does, most likely it's not hardware related.

Since you can't boot at all it doesn't give much to troubleshoot that I can help with. Maybe someone else.

---

### Post by Arachan on 2010-05-10
Thanks for the fast response. 

Yes, I'm in the Live CD right now so that must mean it's not hardware related. 

I think it's something to do with Gnome and KDE confusing each other.

Thanks,
Arachan.

---

### Post by darkod on 2010-05-10
Few ideas for future reference (too late for that now). :)

1. Clean install is usually better than upgrade, if you can do it. For example if you don't have too many special settings to keep, you have separate /home partition which allows easily keeping settings/files, etc.

2. Another way to upgrade is using the Alternate CD which takes only 700MB to download, not 999MB and you don't risk anything getting corrupted during the long download. You just need to make sure the cd image itself is not corrupted after download (there is a test you can run in the menu). The Alternate CD offers the option to upgrade.

---

### Post by Arachan on 2010-05-10
Hello,

So basically you think that my upgrade failed and I need to do a fresh install?

If I do, will I have to reinstall (and download) my software again, or will that be in my /home folder?

Thanks,
Arachan.

---

### Post by darkod on 2010-05-10
Something obviously went wrong with the upgrade. But whether you can keep settings and personal files in Home depends how ubuntu was installed previously.

If you had a separate partition mounted as /home, that will still remain intact if you format / and install 10.04. However, if Home was only a folder in /, as it is in the default layout, it will be lost if / is formatted.

Right now before doing anything I think it's best to run the Boot Info Script (there is a link in my signature), which will produce a results.txt file with detailed results.

You can run it in live mode. If after download you place it in desktop, you execute it with:

sudo bash ~/Desktop/boot_info_script*.sh

You can also post the content of the results file here, and wrap it in [CODE] tags for easier reading. You can do that when with the text you want selected, hit the # button in the toolbar above when creating your reply.

---

### Post by Arachan on 2010-05-10
Hello,

I don't have /home on a separate partition, but I would like to. I just haven't been bothered to find out how to transfer it properly. 

Here is the RESULTS.txt: 

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda
 => Grub 2 is installed in the MBR of /dev/sdb and looks on the same drive in 
    partition #2 for /boot/grub.
 => Syslinux is installed in the MBR of /dev/sdc

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb2: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04 LTS
    Boot files/dirs:   /boot/grub/menu.lst /boot/grub/grub.cfg /etc/fstab 
                       /boot/grub/core.img

sdb3: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb4: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdc1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat32
    Boot sector info:  According to the info in the boot sector, sdc1 starts 
                       at sector 0. But according to the info from fdisk, 
                       sdc1 starts at sector 62.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63    20,482,874    20,482,812   7 HPFS/NTFS
/dev/sda2          20,482,875   312,576,704   292,093,830   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb2    *      8,353,800    39,070,079    30,716,280  83 Linux
/dev/sdb3          39,070,080    42,973,874     3,903,795  82 Linux swap / Solaris
/dev/sdb4          42,973,875   976,768,064   933,794,190  83 Linux


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 8011 MB, 8011120640 bytes
247 heads, 62 sectors/track, 1021 cylinders, total 15646720 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdc1    *             62    15,635,593    15,635,532   c W95 FAT32 (LBA)


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/loop1       77d02c52-4c48-4950-b131-c378e3f60102   ext3                                     
/dev/sda1        C080618E80618C2A                       ntfs       XP                            
/dev/sda2        75A3533E397335AA                       ntfs       GAMES                         
/dev/sda: PTTYPE="dos" 
/dev/sdb2        023578f6-5766-42e5-af67-ab995737e5aa   ext4       UBUNTU                        
/dev/sdb3        bec75a0d-5d80-4fa3-b195-9f3a267ea284   swap                                     
/dev/sdb4        08605420-3111-4828-9d89-88c68f87954e   ext3       DATA                          
/dev/sdb: PTTYPE="dos" 
/dev/sdc1        19DE-0E9B                              vfat       10~04 BOOT                    
/dev/sdc: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sdc1        /cdrom                   vfat       (rw,relatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sdb4        /media/DATA              ext3       (rw,nosuid,nodev,uhelper=udisks)
/dev/sdb2        /media/UBUNTU            ext4       (rw,nosuid,nodev,uhelper=udisks)


================================ sda1/boot.ini: ================================

[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect 

=========================== sdb2/boot/grub/menu.lst: ===========================

splashimage (hd0,1)/boot/grub/images/grubed_splash.xpm.gz
# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
default        -1

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout        3

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

# Pretty colours
color red/cyan green/red

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the
# command 'lock'
# e.g. password topsecret
#      password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
# password topsecret

#
# examples
#
# title        Windows 95/98/NT/2000
# root        (hd0,0)
# makeactive
# chainloader    +1
#
# title        Linux
# root        (hd0,1)
# kernel    /vmlinuz root=/dev/hda2 ro
#

#
# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST

### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=023578f6-5766-42e5-af67-ab995737e5aa ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,1)

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=false

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash

## should update-grub lock old automagic boot options
## e.g. lockold=false
##      lockold=true
# lockold=false

## Xen hypervisor options to use with the default Xen boot option
# xenhopt=

## Xen Linux kernel options to use with the default Xen boot option
# xenkopt=console=tty0

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery) single
# altoptions=(recovery mode) single

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=2

## specify if running in Xen domU or have grub detect automatically
## update-grub will ignore non-xen kernels when running in domU and vice versa
## e.g. indomU=detect
##      indomU=true
##      indomU=false
# indomU=detect

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=false

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

title        Ubuntu 9.10, kernel 2.6.31-19-generic
root        (hd0,1)
kernel        /boot/vmlinuz-2.6.31-19-generic root=UUID=023578f6-5766-42e5-af67-ab995737e5aa ro quiet splash
initrd        /boot/initrd.img-2.6.31-19-generic

title        Ubuntu 9.10, kernel 2.6.31-19-generic (recovery mode)
root        (hd0,1)
kernel        /boot/vmlinuz-2.6.31-19-generic root=UUID=023578f6-5766-42e5-af67-ab995737e5aa ro single
initrd        /boot/initrd.img-2.6.31-19-generic

title        Ubuntu 9.10, kernel 2.6.31-17-generic
root        (hd0,1)
kernel        /boot/vmlinuz-2.6.31-17-generic root=UUID=023578f6-5766-42e5-af67-ab995737e5aa ro quiet splash
initrd        /boot/initrd.img-2.6.31-17-generic

title        Ubuntu 9.10, kernel 2.6.31-17-generic (recovery mode)
root        (hd0,1)
kernel        /boot/vmlinuz-2.6.31-17-generic root=UUID=023578f6-5766-42e5-af67-ab995737e5aa ro single
initrd        /boot/initrd.img-2.6.31-17-generic

### END DEBIAN AUTOMAGIC KERNELS LIST

=========================== sdb2/boot/grub/grub.cfg: ===========================

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
set root='(hd1,2)'
search --no-floppy --fs-uuid --set 023578f6-5766-42e5-af67-ab995737e5aa
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
set root='(hd1,2)'
search --no-floppy --fs-uuid --set 023578f6-5766-42e5-af67-ab995737e5aa
set locale_dir=($root)/boot/grub/locale
set lang=en
insmod gettext
if [ ${recordfail} = 1 ]; then
  set timeout=-1
else
  set timeout=3
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/05_debian_theme.BACKUP ###
set menu_color_normal=white/black
set menu_color_highlight=black/white
### END /etc/grub.d/05_debian_theme.BACKUP ###

### BEGIN /etc/grub.d/10_linux ###
menuentry 'Ubuntu, with Linux 2.6.32-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,2)'
    search --no-floppy --fs-uuid --set 023578f6-5766-42e5-af67-ab995737e5aa
    linux    /boot/vmlinuz-2.6.32-22-generic root=UUID=023578f6-5766-42e5-af67-ab995737e5aa ro vga=792 splash  quiet splash
    initrd    /boot/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,2)'
    search --no-floppy --fs-uuid --set 023578f6-5766-42e5-af67-ab995737e5aa
    echo    'Loading Linux 2.6.32-22-generic ...'
    linux    /boot/vmlinuz-2.6.32-22-generic root=UUID=023578f6-5766-42e5-af67-ab995737e5aa ro single vga=792 splash
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.31-21-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,2)'
    search --no-floppy --fs-uuid --set 023578f6-5766-42e5-af67-ab995737e5aa
    linux    /boot/vmlinuz-2.6.31-21-generic root=UUID=023578f6-5766-42e5-af67-ab995737e5aa ro vga=792 splash  quiet splash
    initrd    /boot/initrd.img-2.6.31-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.31-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,2)'
    search --no-floppy --fs-uuid --set 023578f6-5766-42e5-af67-ab995737e5aa
    echo    'Loading Linux 2.6.31-21-generic ...'
    linux    /boot/vmlinuz-2.6.31-21-generic root=UUID=023578f6-5766-42e5-af67-ab995737e5aa ro single vga=792 splash
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.31-21-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Professional (on /dev/sda1)" {
    insmod ntfs
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set c080618e80618c2a
    drivemap -s (hd0) ${root}
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sdb2/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda2 during installation
UUID=023578f6-5766-42e5-af67-ab995737e5aa /               ext4    errors=remount-ro 0       1
# /data was on /dev/sda4 during installation
UUID=2AA3-6D4B  /data           vfat    utf8,umask=007,gid=46 0       1
# swap was on /dev/sda3 during installation
UUID=bec75a0d-5d80-4fa3-b195-9f3a267ea284 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
=================== sdb2: Location of files loaded by Grub: ===================


   4.5GB: boot/grub/core.img
   5.3GB: boot/grub/grub.cfg
   9.8GB: boot/grub/menu.lst
  16.3GB: boot/initrd.img-2.6.31-21-generic
  16.4GB: boot/initrd.img-2.6.32-22-generic
  10.6GB: boot/vmlinuz-2.6.31-21-generic
  12.2GB: boot/vmlinuz-2.6.32-22-generic
  16.4GB: initrd.img
  16.3GB: initrd.img.old
  12.2GB: vmlinuz
  10.6GB: vmlinuz.old
```

Do you see anything wrong? I didn't, but that's not saying much. 

Thanks,
Arachan.

---

### Post by darkod on 2010-05-10
Boot files/dirs: [COLOR=Red]  /boot/grub/menu.lst[/COLOR] /boot/grub/grub.cfg /etc/fstab 
                       /boot/grub/core.img

It looks fine except having menu.lst in boot/grub. That file is used in grub1 which was used in 9.04 and earlier. 9.10 started shipping with grub2 but if you did upgrade from 9.04->9.10 I guess that's how it remained there.

Try to boot without it to see what happens. In live mode browse to /dev/sdb2 in boot/grub and move menu.lst to your Home folder on /dev/sdb2 for example. That way you can put it back if needed. Don't delete it at this moment.

You do have grub.cfg in boot/grub so you should be able to boot. See how it goes.

---

### Post by Arachan on 2010-05-10
Hello,

My 9.10 was a fresh install, however at one point I had both GRUB 1 and 2, which caused some problems. I still don't really know how that happened.

I renamed the menu.ist to menu.ist.old and rebooted. I selected the new kernel and the screen went black, then after a few seconds it went to a light-ish blue with a few coloured pixels at the top of the screen, some of which flashed repeatedly. It stays like this for about five minutes, then I did a hard reset and booted back to Windows (ugh).

Any other ideas?
Thanks,
Arachan.

---

### Post by darkod on 2010-05-10
Open /boot/grub/device.map and check the mapping. It should be:
hd0 /dev/sda
hd1 /dev/sdb

If that is correct, as a final thought reinstall grub2 again to /dev/sdb with:

sudo mount /dev/sdb2 /mnt
sudo grub-install --root-directory=/mnt/ /dev/sdb

If that doesn't help I'm running out of ideas.

A last option would be to copy your Home folder to external hdd, and install fresh 10.04 over the current upgrade and at the same time you could use this situation to set up separate /home partition. You could reuse your /data partition that I see here without any data loss on it, you won't format it.

If you decide to go this way, ask if you need pointers how to set up manually separate /home partition.

---

### Post by ashokranade on 2010-05-10
Upgradation for Ubuntu from Karmic Koala to 10.04 went smoothly. My grub page shows window XP but when i do 'enter' a cursor in a blank screen appears and continues. I donot know how to fix this problem:confused:

---

### Post by Arachan on 2010-05-10
Hello,

My device.map is correct. I reinstalled GRUB and will try to boot again. I think if that fails I will just do a fresh install and make a /home partition. If I put my current /home there what kinds of things will I lose anyway? KDE, I suppose. 

Thanks for your help,
Arachan.

---

### Post by dondiego2 on 2010-05-10
> **ashokranade said:**
> Upgradation for Ubuntu from Karmic Koala to 10.04 went smoothly. My grub page shows window XP but when i do 'enter' a cursor in a blank screen appears and continues. I donot know how to fix this problem:confused:


The exact same thing happened on my upgrade from 9.10 to 10.04.  It seems to be a common problem for those of us that dual boot.  It appears to be a grub issue.

---

### Post by Arachan on 2010-05-10
Hmm. Mine problem seems to be the opposite, I dual boot but Windoze XP works fine and Ubuntu 10.04 doesn't. My OSes are on different HDDs though.

---

### Post by darkod on 2010-05-10
> **dondiego2 said:**
> The exact same thing happened on my upgrade from 9.10 to 10.04.  It seems to be a common problem for those of us that dual boot.  It appears to be a grub issue.

This is a different problem I think and it's not easy to solve different problems in the same thread because it mixes up the solutions. But I'll try to be short:

Run the boot info script (there is link with details in the link I am providing), also you can download it from my signature. If you see in the results file something like explained here:
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector)

the solution is on the same page.

---

### Post by darkod on 2010-05-10
> **Arachan said:**
> Hello,

My device.map is correct. I reinstalled GRUB and will try to boot again. I think if that fails I will just do a fresh install and make a /home partition. If I put my current /home there what kinds of things will I lose anyway? KDE, I suppose. 

Thanks for your help,
Arachan.

Did reinstalling grub2 help?

---

### Post by Arachan on 2010-05-10
No, the same thing happened. I noticed that every time I pressed a key, one or two more pixels of colour were added to the top of the screen. Does this mean that it's trying to display something and failing maybe?

What will I lose if I reinstall 10.04 but keep my /home?

I'm going to bed now (it's 1:00AM here), but hopefully I can get this resolved tomorrow.

Thanks for your help,
Arachan.

---

### Post by darkod on 2010-05-10
In your current situation, because you don't have separate /home partition, I'm not sure you can keep it at all.

But from the live mode you could copy all the files from Home you need. After that you could delete the / partition and in its place create new / and /home as separate (2 partitions in place of one).

I can see in the results you have about 4GB unused space in front of /dev/sdb2, your current /. And the / partition is about 15GB.

You could, for example, create 10GB / and approx 10GB /home. You have a huge /data partition so I guess you store all large data files there, so 10GB /home is not too small. Be careful, in that situation you would have only 10GB to use on it.

What will you lose? If you copy all files that you need from your current Home, you won't lose any of them of course. But with the fresh install you will need to reinstall any software that you added yourself (that wasn't included in the default 9.10 install) and any specific settings for that software will probably be lost so you will need to set things the way you like them again.

But if that is not too much work a fresh install is worth it because it will also allow you to start having separate /home partition that you just reuse in any future clean install.

If you decide to do this, and need some help, post here. You will have to use the manual partitioning method in the installer, the guided automatic methods don't offer separate /home partition.

---

### Post by Arachan on 2010-05-11
Hello,

My main reason for upgrading rather than reinstalling was so I wouldn't have to download and install my software again (including stuff like KDE it would be a lot relative to my bandwidth allowance). I suppose I will have to go through that now though.

Unless you (or anyone else) have any more suggestions about how to get my current install working, I think I'll reinstall and format my drive you like suggested (10GB /home and 10GB /).

Thanks,
Arachan.

---

