---
title: "Window XP will not restart"
date: 2010-04-18
forum: Installation &amp; Upgrades
---

### Post by roynoblin on 2010-04-18
I have three partitions on this 1T HDD. I Installed XP Pro on it and then I installed UBUNTU. I set it up 250 G partition for XP. 250G for UBUNTU and the remaining 500G for data. As best I can tell I have 3 partitions on this HDD. I wish now I had known how to locate them and written them down

 

 Everything has been working great until I started XP and did a update. It installed several security updates and requested I restart this PC.
 

 Since the restart I can still use UBUNTU and I can access the data in the data partition but XP gets to the XP window with the little blue dots running in the bar. The screen then goes black as usual but instead of XP starting it does a restart.

 

 My thoughts are the bootlog is messed up and it appears in UBUNTU it is GRUB. By doing 'E' I see what looks like I assume is the boot log.
 

 The xp line I arrow down to has (on /dev/SDA1)
 does this mean it should looking in partition 2?


if this is the bootlog and someone can help me get it fixed i promise i will write it done this time:) I have no idea what it should be or how to change if needed.

 


Thank you

---

### Post by Bucky Ball on 2010-04-18
Try changing that to sda2 by editing the grub menu. They should be lower case unless they appear in upper case as in your example. It is unlikely this is the problem as Windows was installed first and would no doubt be on sda1. 

Put in a Ubuntu installation cd and 'Try Now'. Once at a desktop, open a terminal (Applications->Accessories) and paste this:

sudo blkid

... then hit enter. This should give you a good idea of what's where. Windows will be on the NTFS partitions and Linux on the EXT3 or EXT4.

Last resort, as you say, the Windows boot loader could be screwed. What happens is grub actually points to the Windows boot loader when you select it and Windows takes it from there. Strange though; Ubuntu should have picked up your Windows install and added it to the grub menu when you installed it. 

Good luck.

---

### Post by roynoblin on 2010-04-18
thanks bucky ball--I will try what you suggest

i did a 'E' and 

in linux i see: (and other things that i assume are not part of the boot)
setquite=1
 insmod ext2
setroot=(hd0,6)

in XP I see:

insmod NTFS
setroot=(hd0,1)
search --no-floppy --fs-uuid --set aec4a45cc4a42893
drive map -s(hd0) $?root?  ? = i do not know what that symbol is
chainloader +1

don't know if the above helps knowing but thanks again and i'll be back after i try your suggestion

---

### Post by roynoblin on 2010-04-18
this is what i see:
/dev/sda1: UUID="AEC4A45CC4A42893" TYPE="ntfs" 
/dev/sda5: UUID="4A3CEB323CEB17A9" LABEL="partition 2" TYPE="ntfs" 
/dev/sda6: UUID="7bda59d8-9b94-4d1f-ba8b-6caf7a4b65f0" TYPE="ext4" 
/dev/sda7: UUID="2c02be14-f031-4e93-aae8-3fef03895a79" TYPE="swap" 
/dev/sdb1: UUID="E6C82634C8260381" LABEL="external drive" TYPE="ntfs" 

i have two HDD so /dev/sdb1: UUID="E6C82634C8260381" LABEL="external drive" TYPE="ntfs"should be the second hdd and not have anything to do with the trouble

the /dev/sda5: UUID="4A3CEB323CEB17A9" LABEL="partition 2" TYPE="ntfs" is the 500G i set for data

so i assume /dev/sda1: UUID="AEC4A45CC4A42893" TYPE="ntfs"is the partition for XP
the /dev/sda6: UUID="7bda59d8-9b94-4d1f-ba8b-6caf7a4b65f0" TYPE="ext4" is for ubuntu

but what is /dev/sda7: UUID="2c02be14-f031-4e93-aae8-3fef03895a79" TYPE="swap" for?

i am in and using ububtu and i have no trouble accessing the data in partition 2. i was able to get the above with out using the install cd. i just opened terminal and pasted

my only trouble is using XP. when i arrow down and select it used to go to window screen with the blue dots running then the screen would go black and shortly XP deasktop would appear.

now i get the widow with the blue dots but after the screen goes black it does a restart. i can f8 and get to safe mode but it also just does a restart no mater what i try

it is trying to do a restart from the security update i did and something is missing i guess

i have the xp install disk but it is no help either and my guess is the trouble is with xp update and not in ubuntu

any help or thoughts on how to fix this?

---

### Post by Bucky Ball on 2010-04-18
. Posted in error.

---

### Post by oldfred on 2010-04-18
To see where all the files are run this script:

Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Be sure to highlight and use code tags (# in edit panel) to make it easier to read when you post the results.txt.

---

### Post by roynoblin on 2010-04-18
i down loaded the Boot Info Script and got a screen showing how to use it and a lot of command lines. does this install itself or how do i get it to work?

from terminal this is all i get
roy@roy-desktop:~$ sudo bash boot_info_script055.sh
bash: boot_info_script055.sh: No such file or directory
roy@roy-desktop:~$ su -
Password: 
su: Authentication failure
roy@roy-desktop:~$ su -
Password: 
su: Authentication failure
roy@roy-desktop:~$ sudo bash boot_info_script055.sh
bash: boot_info_script055.sh: No such file or directory
roy@roy-desktop:~$ bash boot_info_script055.sh
bash: boot_info_script055.sh: No such file or directory
roy@roy-desktop:~$ 

i assume it is asking for the same pass word i always use. it failed twice and i do not know how many times it will let me try before locking me out

---

### Post by wilee-nilee on 2010-04-18
You have left out the [path/to/the/download_folder] and you don't need the 055 in there have it download put it on the desktop and run the provided script for the desktop location provided on the download page.
sudo bash ~/Desktop/boot_info_script*.sh

---

### Post by roynoblin on 2010-04-18
it down loaded to downloads so i had to use this in terminal

sudo bash ~/Downloads/boot_info_script*.sh
here are the results

                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #6 for /boot/grub.
 => No boot loader is installed in the MBR of /dev/sdb

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

sda6: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda7: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xa243532b

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   525,454,019   525,453,957   7 HPFS/NTFS
/dev/sda2         525,454,020 1,953,520,064 1,428,066,045   f W95 Ext d (LBA)
/dev/sda5         525,454,083 1,425,495,644   900,041,562   7 HPFS/NTFS
/dev/sda6       1,425,495,708 1,942,965,359   517,469,652  83 Linux
/dev/sda7       1,942,965,423 1,953,520,064    10,554,642  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x000098ec

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63 1,953,520,064 1,953,520,002   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        AEC4A45CC4A42893                       ntfs                                     
/dev/sda5        4A3CEB323CEB17A9                       ntfs       partition 2                   
/dev/sda6        7bda59d8-9b94-4d1f-ba8b-6caf7a4b65f0   ext4                                     
/dev/sda7        2c02be14-f031-4e93-aae8-3fef03895a79   swap                                     
/dev/sdb1        E6C82634C8260381                       ntfs       external drive                

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda6        /                        ext4       (rw,errors=remount-ro)
/dev/sda5        /media/partition 2       fuseblk    (rw,nosuid,nodev,allow_other,default_permissions,blksize=4096)
/dev/sdb1        /media/external drive    fuseblk    (rw,nosuid,nodev,allow_other,default_permissions,blksize=4096)


================================ sda1/boot.ini: ================================

[boot loader] 
timeout=10 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect /usepmtimer 

=========================== sda6/boot/grub/grub.cfg: ===========================

#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by /usr/sbin/grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s /boot/grub/grubenv ]; then
  have_grubenv=true
  load_env
fi
set default="0"
if [ ${prev_saved_entry} ]; then
  saved_entry=${prev_saved_entry}
  save_env saved_entry
  prev_saved_entry=
  save_env prev_saved_entry
fi
insmod ext2
set root=(hd0,6)
search --no-floppy --fs-uuid --set 7bda59d8-9b94-4d1f-ba8b-6caf7a4b65f0
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
if [ ${recordfail} = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/white
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry "Ubuntu, Linux 2.6.31-21-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd0,6)
    search --no-floppy --fs-uuid --set 7bda59d8-9b94-4d1f-ba8b-6caf7a4b65f0
    linux    /boot/vmlinuz-2.6.31-21-generic root=UUID=7bda59d8-9b94-4d1f-ba8b-6caf7a4b65f0 ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-21-generic
}
menuentry "Ubuntu, Linux 2.6.31-21-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd0,6)
    search --no-floppy --fs-uuid --set 7bda59d8-9b94-4d1f-ba8b-6caf7a4b65f0
    linux    /boot/vmlinuz-2.6.31-21-generic root=UUID=7bda59d8-9b94-4d1f-ba8b-6caf7a4b65f0 ro single 
    initrd    /boot/initrd.img-2.6.31-21-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd0,6)
    search --no-floppy --fs-uuid --set 7bda59d8-9b94-4d1f-ba8b-6caf7a4b65f0
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=7bda59d8-9b94-4d1f-ba8b-6caf7a4b65f0 ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd0,6)
    search --no-floppy --fs-uuid --set 7bda59d8-9b94-4d1f-ba8b-6caf7a4b65f0
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=7bda59d8-9b94-4d1f-ba8b-6caf7a4b65f0 ro single 
    initrd    /boot/initrd.img-2.6.31-14-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Professional (on /dev/sda1)" {
    insmod ntfs
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set aec4a45cc4a42893
    drivemap -s (hd0) ${root}
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
proc            /proc           proc    defaults        0       0
# / was on /dev/sda6 during installation
UUID=7bda59d8-9b94-4d1f-ba8b-6caf7a4b65f0 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda7 during installation
UUID=2c02be14-f031-4e93-aae8-3fef03895a79 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sda6: Location of files loaded by Grub: ===================


 747.2GB: boot/grub/core.img
 731.4GB: boot/grub/grub.cfg
 730.1GB: boot/initrd.img-2.6.31-14-generic
 730.6GB: boot/initrd.img-2.6.31-21-generic
 730.4GB: boot/vmlinuz-2.6.31-14-generic
 730.3GB: boot/vmlinuz-2.6.31-21-generic
 730.6GB: initrd.img
 730.1GB: initrd.img.old
 730.3GB: vmlinuz
 730.4GB: vmlinuz.old

---

### Post by wilee-nilee on 2010-04-19
That is great, there are some forum members who can read this script and help you, the original poster suggesting the script is one of them, and there are others so hopefully all will be well soon. I would suggest something but I don't see where the problem is as of now, also like many members we try to at the least do no harm, it's all ethics you know, and protecting your OS.

The other thing I have heard about the latest in the last weeks large updates to XP and W7 have caused problems, I had none I have both OS.

---

### Post by KillerLoki on 2010-04-19
Ok not sure if i did not see it but have you tried to boot your XP in Last known Good?
it sounds like you atleast can get into your safemode screen due to you said it gets to the XP Splash screen then stops. if that does not work for you you can try a parallel boot of XP. Basiclly you will reinstall XP in the same Partition but where it askes what folder to put it in or when it says Windows folder you just a 1 with no spaces (Windows1) it will install with out you loosing any of your files and folders so you can get in and fix it as well you also do not want to reformat the drive so tell it not to do that and you have more than enough room on your drive from what I see Hell XP only really needs  4096 to install. my 2 cents worth if it helps or im sure someone will want to differ on this!=D>

---

### Post by wilee-nilee on 2010-04-19
> **KillerLoki said:**
> Ok not sure if i did not see it but have you tried to boot your XP in Last known Good?
it sounds like you atleast can get into your safemode screen due to you said it gets to the XP Splash screen then stops. if that does not work for you you can try a parallel boot of XP. Basiclly you will reinstall XP in the same Partition but where it askes what folder to put it in or when it says Windows folder you just a 1 with no spaces (Windows1) it will install with out you loosing any of your files and folders so you can get in and fix it as well you also do not want to reformat the drive so tell it not to do that and you have more than enough room on your drive from what I see Hell XP only really needs  4096 to install. my 2 cents worth if it helps or im sure someone will want to differ on this!=D>

I wouldn't touch this with a ten foot pole!

---

### Post by roynoblin on 2010-04-19
thanks for the help and i will list what does and does not work

when i restart i get the GRUB screen with all the options and i can enter and find no problem using any of them

EXCEPT when i try to access windows XP

the xp screen comes up and the blue dots move and every thing looks normal except where normally the screen goes black momentarily then your desk top starts appearing

my screen stays black then its like i did a restart on the pc. i get all the goodies about my pc and then the GRUB choices

in XP i can not access safe mode. i can F8 and get the screen but all options including restore to the last know good fail. the screen goes black and after awhile it is like i pressed the restart.

my other 2 PC's that only have xp on them i keep current with the latest security updates and they are fine. all most all updates require a restart after the install. those 2 pc are up to date and work fine.

this pc with duel boot is the only one i am having trouble with. after i did the security update in XP it said need to restart and i have been trying to get it to restart ever since.

to make this long story short
i have no trouble accessing or using ubuntu on this pc
i can not get to the desk top in XP normally or with soft mode

i am fairly sure something in the security up date is missing and i have no clue what or where it may be

i will try to reinstall xp but when i first built this pc i tried and wound up with so many partitions i had to do a complete clean of the HDD and reload everything. i do not have another HDD to save all i have on this now and sure dont want to crash and burn:)

---

### Post by roynoblin on 2010-04-19
[SIZE=3]i was able to reinstall xp but on startup i have no grub. it is windows duel boot with choice of 2 xp's but no ubuntu
is there some way to access grub or ubuntu with out reinstalling linux?
[/SIZE]

---

### Post by pricetech on 2010-04-19
> **wilee-nilee said:**
> I wouldn't touch this with a ten foot pole!

Nothing wrong with a parallel install.  I've done it before myself, but a couple of posts beyond yours is why I would not recommend it.

But anyway; to the Original Poster:  It sounds like the update is what botched your XP boot files.  Kind of a moot point now, but hopefully you can straighten the whole thing out and make your XP work as well as your Ubuntu.

---

### Post by roynoblin on 2010-04-19
:popcorn:
i now have xp working if i chose the first in the list. i reinstalled xp and now have two.
first one loads the other still does not but i can live with it:)

i was unable to get back to GRUB so i posted another thread and it sloved all my problems
:)

here is link to my next thread
[http://ubuntuforums.org/showthread.php?t=1458129](http://ubuntuforums.org/showthread.php?t=1458129)

some where and some day i'll find the way to show this solved

---

### Post by wilee-nilee on 2010-04-19
> **pricetech said:**
> Nothing wrong with a parallel install.  I've done it before myself, but a couple of posts beyond yours is why I would not recommend it.

But anyway; to the Original Poster:  It sounds like the update is what botched your XP boot files.  Kind of a moot point now, but hopefully you can straighten the whole thing out and make your XP work as well as your Ubuntu.

I wasn't so much questioning the validity, but it seemed a little more complex, then most would understand, and had a easy failure and borking of the OS possibility, when as the op did was just reinstall. This reinstall now has 2 XP versions so this is why I was concerned about throwing complex answers at somebody who might not understand. @ roynoblin I am not trying to question your abilities but when I post my first goal is do no harm.

---

