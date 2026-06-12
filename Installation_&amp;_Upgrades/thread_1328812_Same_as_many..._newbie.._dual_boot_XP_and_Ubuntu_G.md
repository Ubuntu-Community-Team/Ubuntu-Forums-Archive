---
title: "Same as many... newbie.. dual boot XP and Ubuntu GRUB problems"
date: 2009-11-16
forum: Installation &amp; Upgrades
---

### Post by serpentine5 on 2009-11-16
I followed this tut to do my installs.... [http://ubuntuforums.org/showthread.php?p=8327632#post8327632](http://ubuntuforums.org/showthread.php?p=8327632#post8327632)
and as you can see in the thread, i posted my issues, but I am not getting much assistance by hijacking someone elses thread, so I figured I would copy my posts and start a new thread.... 
this way it was about my issues and not about everything else posted in that thread.

first post:

I did a google search on duel booting with Ultimate Edition and XP and this thread is what was on the top of the returns.
There are a couple issues I have with it. I see that it was written in 2007 and here it is 2009 almost 2010.... so i know your tut is outdated. I did not check the date of the tut when I started.... 

I have a copy of Ubuntu Ultimate Edition 2.3, and am running XP Pro.
I followed the tut and went to reinstall XP and told the formatter/partitioner to allocate 10gig of a 40 gig HHD to install XP on. Worked fine.
After XP installed totally, I rebooted to the LiveCD, could not find Gparted but I found "Partition Editor" under System>Administration> So I used it. It was a tad bit different than your tut described so I did what I thought was right... 
I took the remaining space, and cut it into three equal pieces because you failed to say anything about the swap area that was shown in the graphic. 
I did the first as:
File System ext3
Label UBHome
Create As: Primary Partition

Second:
File System ext3
Label UBRoot
Create as Primary Partition

Third:
File System ext3
Label SWAP
Create as Primary Partition

Then hit apply. Once it was finished, I hit the install from the desktop and went through the questions until it came to the partition step. I selected "Select Partitions Manually".
I found the HDD I made the partitions on, I selected the first one, and hit Edit partition. Here were a few steps that were not mentioned in your tut either....
First: 
USE AS: Ext3 journaling file system
Format Partition: selected
Mount Point: /home

Second:
Use AS: Ext3 Journaling File System
Format Partition: Selected
Mount Point: /

then I hit next on the installer and it popped up telling me that I did not have a drive selected for SWAP.... This is the step you skipped in the tut, so i hit back and edited the third partition
Third: 
Use As: SWAP AREA 
Would not allow me to select format
Mount Point: unselected (since there was not a SWAP listed in the drop down menu.)

I then finished the install process and rebooted. It booted straight to XP, not to a boot prompt asking me which OS I wanted to boot to or anything.

I have rebooted several times, and everytime it goes straight to XP. I did put the LiveCD back in and booted to it, and it shows that Ubuntu was installed to the drive I partitioned and Mount Pointed as "/", not to the SWAP or the "/home" drives. 

As I am sure you have realized by now, I am not a Linux user... I know my way around a Windoze box, but the ins and outs of Linux/Ubuntu escape me.

Any input that can be provided to help me with where ever I screded up, i would be most thankful.


Second post in reply to Annigma's post of:
Hello serpentine. Welcome to the forums ):P

I can't help you really I'm afraid, but just wanted to suggest that you don't do anything else until someone advises you. 
The reason I say this is that I believe you are not making the best use of your space. The swap partition only needs to be small (it's relative to the size of your RAM), so you're wasting a good few GB there. Also, the maximum number of Primary partitions you can have on a HDD is four, and I think you've used them all up unnecessarily.. Only your Windows 'demands' a Primary partition. Linux isn't so fussy :wink: (This will only matter if you want more partitions later. If you're sure you won't, then it doesn't matter.)

I'm sure you're researching whilst awaiting an answer. I am grateful for the help I got recently on [[COLOR=Blue]this thread[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1321649"), and you may find it helpful.

Good luck. Hope someone comes along soon to help.

My response:
Ok, I screwed up farther.... 
After reading several other posts and how to's.... I decided to try the super grub disk.
Downloaded and ran from inside windoze and rebooted. It came up to a prompt, I hit it, it listed several installs of Ubuntu and a windozes install. I selected the first linux, error 15 the second same thing and so on.... so i rebooted and tried it again. the first one allowed me to log into the linux install.... Cool... 
thought I had the issue fixed. So while I was trying to import my windoze settings for firefox, and then my mail folders from my outlook backups... Ifound that I had to go back to windoze to transfer the outlook file to firefox since the linux install of firefox did not have mozilla mail.... So... I rebooted got the grub prompt to select what I wanted to boot to, and when I selected windoze, I now get an error:

Starting up...

NTLDR is missing
Press Ctrl+Alt+Del to restart

Now I dont know what to do.....

I can still log into Linux... but not Windows

Then my follow up post:
ok, i am back to the beginning... I booted off the windoze install disc and went to the repair console... fixed the MBR.... rebooted and it gave me the very first 
grub prompt asking if I wanted to go to windoze or the super grub disc. I chose to boot to windoze and it did... but now I have an exe trying to run at start up, it is asking me before anything else loads to allow unetbtin.exe to run.... no clue what it is.... google search implies it is the uninstaller for super grub disc.

I rebooted from windows, and got the first grub menu, found the linux install, can boot to it but cannot boot to windoze, giving me the same error again....
thinking this is a super grub disc error....





Now what I am looking at doing at this moment is rebooting to the livecd, deleting the partitions except for the windoze, setting the swap to a gig, and the rest cut in half.... so about 15gig for /home, 15 gig for / and 1 gig for swap.

What cha think? When I first booted into Ubuntu, it wanted to update, and i told it to do so, but half way through it said it did not have enough space to update everything, so it reset... 10 gig is not large enough to install then update everything..... 

Is there an up to date tut on this site that I have overlooked that tells how to set everything up in a way that a noob with no terminal experience can use and get a system going with a functioning dual boot?

Thanks all

---

### Post by oldfred on 2009-11-16
If you do not want to totally reinstall:

Boot Info Script 0.34 courtesy of forum member meierfra
[http://sourceforge.net/projects/bootinfoscript/](http://sourceforge.net/projects/bootinfoscript/)
Instructions
[http://ubuntuforums.org/showpost.php?p=6725571&postcount=3](http://ubuntuforums.org/showpost.php?p=6725571&postcount=3)
cd to directory saved to:
chmod 755 boot_info_script034.sh
sudo ./boot_info_script034.sh
or  as example if on desktop
sudo bash ~/Desktop/boot_info_script*.sh
This will create a RESULTS.txt file in the same directory. Paste the entire contents of that file back here. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text.

But if you have no data to save sometimes reinstall is the quickest, but does not add to learning as much. We like to try to fix things just because its fun.

More sites with installing dual boot. Some have the more updated versions.
[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)
[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)
[http://apcmag.com/the_definitive_dualbooting_guide_linux_vista_and_xp_stepbystep.htm](http://apcmag.com/the_definitive_dualbooting_guide_linux_vista_and_xp_stepbystep.htm)
[http://members.iinet.net/~herman546/](http://members.iinet.net/~herman546/)

---

### Post by serpentine5 on 2009-11-16
Fred, thanks for the reply, but everything other than the link was greek or Linux to me.... I have no clue. just telling me:
chmod 755 boot_info_script034.sh
sudo ./boot_info_script034.sh
means absolutely nothing to me. 
I need step by step instructions, and if you want me to learn while I am doing it, I need to be told what it is I am doing and why. Like I said, I am a total Noob to anything outside of windoze.

Oh, BTW, I am reinstalling... I deleted the three partitions, creating a 20gig, a 6 gig and a 1 gig..... installing to the 20 gig (I hope) to use as the / and use the 6 for the /home and the 1 gig as the swap...... this sound right?

---

### Post by serpentine5 on 2009-11-16
here is a paste of the RESULTS.txt file

============================= Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/sda and looks on boot drive #2 in 
    partition #2 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => Grub0.97 is installed in the MBR of /dev/sdb and looks on the same drive 
    in partition #3 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => Windows is installed in the MBR of /dev/sdc
 => Windows is installed in the MBR of /dev/sdd
 => Windows is installed in the MBR of /dev/sde

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sdb2: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.04
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sdb3: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdb4: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdc1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdd1: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdd5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sdd5 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sdd6: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sdd6 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sde1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 160.0 GB, 160000000000 bytes
255 heads, 63 sectors/track, 19452 cylinders, total 312500000 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x41ab2316

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   312,496,379   312,496,317  42 SFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders, total 78165360 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x3fff3ffe

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63    20,482,874    20,482,812   7 HPFS/NTFS
/dev/sdb2          20,482,875    63,504,944    43,022,070  83 Linux
/dev/sdb3          63,504,945    75,055,679    11,550,735  83 Linux
/dev/sdb4          75,055,680    78,156,224     3,100,545  82 Linux swap / Solaris


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 122.9 GB, 122942324736 bytes
255 heads, 63 sectors/track, 14946 cylinders, total 240121728 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xbb4e328a

Partition  Boot         Start           End          Size  Id System

/dev/sdc1    *             63   240,107,489   240,107,427   7 HPFS/NTFS


Drive: sdd ___________________ _____________________________________________________

Disk /dev/sdd: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x033e033e

Partition  Boot         Start           End          Size  Id System

/dev/sdd1              16,065   156,296,384   156,280,320   f W95 Ext d (LBA)
/dev/sdd5              16,128   115,346,699   115,330,572   7 HPFS/NTFS
/dev/sdd6         115,346,763   156,296,384    40,949,622   7 HPFS/NTFS


Drive: sde ___________________ _____________________________________________________

Disk /dev/sde: 122.9 GB, 122942324736 bytes
255 heads, 63 sectors/track, 14946 cylinders, total 240121728 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x0441c37b

Partition  Boot         Start           End          Size  Id System

/dev/sde1                  63   240,091,424   240,091,362   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

/dev/loop0: TYPE="squashfs" 
/dev/sda1: UUID="0478BD7378BD6458" LABEL="160SATA" TYPE="ntfs" 
/dev/sdb1: UUID="5E4C339A4C336C41" TYPE="ntfs" 
/dev/sdb2: UUID="ad97927c-87f7-4f9e-adf6-938a75f7fb7d" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sdb3: UUID="ca6f0ad9-c486-4a3e-920b-d4c7ba1298ef" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sdb4: UUID="2f80cff0-906d-4894-826e-71dc8f28ffdb" TYPE="swap" 
/dev/sdc1: UUID="8200D05100D04DB3" LABEL="WAREZ" TYPE="ntfs" 
/dev/sdd5: UUID="1154A4BA06F2B659" LABEL="Musak" TYPE="ntfs" 
/dev/sdd6: UUID="455292EC4585C3C4" LABEL="Personal" TYPE="ntfs" 
/dev/sde1: UUID="F47C1BAC7C1B689E" LABEL="Warez2" TYPE="ntfs" 

=============================== "mount" output: ===============================

tmpfs on /lib/modules/2.6.28-11-generic/volatile type tmpfs (rw,mode=0755)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
tmpfs on /lib/modules/2.6.28-13-generic/volatile type tmpfs (rw,mode=0755)
tmpfs on /lib/modules/2.6.28-14-generic/volatile type tmpfs (rw,mode=0755)
tmpfs on /lib/modules/2.6.28-11-generic/volatile type tmpfs (rw,mode=0755)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
rootfs on / type rootfs (rw)
/dev/sr0 on /cdrom type iso9660 (ro,noatime)
/dev/loop0 on /rofs type squashfs (ro,noatime)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/ubuntu/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=ubuntu)


================================ sdb1/boot.ini: ================================

[boot loader]
timeout=15
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect
C:\ubnldr.mbr="Auto Super Grub Disk"

=========================== sdb2/boot/grub/menu.lst: ===========================

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
default        0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout        10

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

# Pretty colours
#color cyan/blue white/blue

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
# kopt=root=UUID=ad97927c-87f7-4f9e-adf6-938a75f7fb7d ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=ad97927c-87f7-4f9e-adf6-938a75f7fb7d

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
# howmany=all

## specify if running in Xen domU or have grub detect automatically
## update-grub will ignore non-xen kernels when running in domU and vice versa
## e.g. indomU=detect
##      indomU=true
##      indomU=false
# indomU=detect

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

title        Ubuntu 9.04, kernel 2.6.28-14-generic
uuid        ad97927c-87f7-4f9e-adf6-938a75f7fb7d
kernel        /boot/vmlinuz-2.6.28-14-generic root=UUID=ad97927c-87f7-4f9e-adf6-938a75f7fb7d ro quiet splash 
initrd        /boot/initrd.img-2.6.28-14-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-14-generic (recovery mode)
uuid        ad97927c-87f7-4f9e-adf6-938a75f7fb7d
kernel        /boot/vmlinuz-2.6.28-14-generic root=UUID=ad97927c-87f7-4f9e-adf6-938a75f7fb7d ro  single
initrd        /boot/initrd.img-2.6.28-14-generic

title        Ubuntu 9.04, kernel 2.6.28-13-generic
uuid        ad97927c-87f7-4f9e-adf6-938a75f7fb7d
kernel        /boot/vmlinuz-2.6.28-13-generic root=UUID=ad97927c-87f7-4f9e-adf6-938a75f7fb7d ro quiet splash 
initrd        /boot/initrd.img-2.6.28-13-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-13-generic (recovery mode)
uuid        ad97927c-87f7-4f9e-adf6-938a75f7fb7d
kernel        /boot/vmlinuz-2.6.28-13-generic root=UUID=ad97927c-87f7-4f9e-adf6-938a75f7fb7d ro  single
initrd        /boot/initrd.img-2.6.28-13-generic

title        Ubuntu 9.04, kernel 2.6.28-11-generic
uuid        ad97927c-87f7-4f9e-adf6-938a75f7fb7d
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=ad97927c-87f7-4f9e-adf6-938a75f7fb7d ro quiet splash 
initrd        /boot/initrd.img-2.6.28-11-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid        ad97927c-87f7-4f9e-adf6-938a75f7fb7d
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=ad97927c-87f7-4f9e-adf6-938a75f7fb7d ro  single
initrd        /boot/initrd.img-2.6.28-11-generic

title        Ubuntu 9.04, memtest86+
uuid        ad97927c-87f7-4f9e-adf6-938a75f7fb7d
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb1
title        Microsoft Windows XP Professional
rootnoverify    (hd1,0)
savedefault
makeactive
map        (hd0) (hd1)
map        (hd1) (hd0)
chainloader    +1


=============================== sdb2/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sdb2 during installation
UUID=ad97927c-87f7-4f9e-adf6-938a75f7fb7d /               ext3    relatime,errors=remount-ro 0       1
# /home was on /dev/sdb3 during installation
UUID=ca6f0ad9-c486-4a3e-920b-d4c7ba1298ef /home           ext3    relatime        0       2
# swap was on /dev/sdb4 during installation
UUID=2f80cff0-906d-4894-826e-71dc8f28ffdb none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sdb2: Location of files loaded by Grub: ===================


  20.5GB: boot/grub/menu.lst
  20.6GB: boot/grub/stage2
  20.8GB: boot/initrd.img-2.6.28-11-generic
  20.6GB: boot/initrd.img-2.6.28-13-generic
  20.7GB: boot/initrd.img-2.6.28-14-generic
  20.7GB: boot/vmlinuz-2.6.28-11-generic
  20.7GB: boot/vmlinuz-2.6.28-13-generic
  20.7GB: boot/vmlinuz-2.6.28-14-generic
  20.8GB: initrd.img
  20.6GB: initrd.img.old
  20.7GB: vmlinuz

---

### Post by oldfred on 2009-11-16
You can copy and paste those commands into the terminal.

in the terminal you first have to change to the directory you saved it to. If from a liveCD it is the desktop. If from your Ubuntu you can choose where to save it, perhaps your home
~ is a short cut for home.

Usually if you just start terminal it will be in home or 
cd /home/fred  # this is for mine yours of course is cd /home/serpentine5
or cd ~
copy the next two lines into the terminal one at a time
chmod 755 boot_info_script034.sh
then
sudo ./boot_info_script034.sh
It should ask for your password, show some progess and finally say you have a copy of results.txt in your directory.


If you used a liveCD to download it to the desktop
sudo bash ~/Desktop/boot_info_script*.sh
is just an alternative way to run the script.

If this is your first install I do not necessarily recommend a separate /home. You are not sure of how much space you will need and you have to arbitrarily divide it up.

I have not had a separate /home for the last 3 years and have updated in place every version. I now have accumulated so much old cruft that I want to do a clean new install and will now copy my /home to a new partition. I still only want a small /home as I want a /data for all data and leave only configurations and some default stuff in /home. I already have another shared data partition that is NTFS as 3 years ago I was mostly windows, I now am only in windows for one application and hope within a year to be off that.

---

### Post by serpentine5 on 2009-11-16
ok, are you telling me to do it again with the code you provided? Or is the paste above what you were looking for?

---

### Post by serpentine5 on 2009-11-16
now when I reboot, i get:
GRUB loading, please wait...
Error 15



wont even boot now.....

---

### Post by oldfred on 2009-11-16
I was just posting additional info on how to run the script as you had asked. You said you did not know how to run it & I did not see your post before I posted. Oh, It is easier to read if you use the code tags # in title bar above posting, as it is a long listing.

I alway go to Herman's site for grub errors:
[http://members.iinet.net.au/~herman546/p15.html#15]("http://members.iinet.net.au/%7Eherman546/p15.html#15")

Your listing looked ok, did you change something? You have grub legacy in your sda 160GB drive and it looks to partition #2 where Ubuntu is. sdb grub points to a bad install or something incorrect with no files to boot in partition #3. If you cannot boot it looks like you moved your second drive 40GB to first. BIOS always boots the first drive, but that is not always sda.

Did supergrub add this to your windows to fix it, I do not know this entry?
C:\ubnldr.mbr="Auto Super Grub Disk"

---

### Post by serpentine5 on 2009-11-17
I am thinking that is the uninstall for the super grub disc....

Fred, I thank you for popping in here to help me out....
You saw the 160 drive there too... I saw that and it got me to thinking... all my drives are IDE, except that 160gig drive, it is the last drive I added and it is a SATA drive.... when doing the partitions it was always the first drive to show... then in the list of the report, it showed that GRUB was installed there....
So I got to thinking... let me reinstall again... and this time, let me unplug the 160sata drive....

It installed, and I rebooted it and it went to the GRUB that was supposed to be there.... booted right into Linux... I rebooted from there and went into Windoze.... both working great!
Thanks again!

---

### Post by darkod on 2009-11-17
Glad you got it working. Just for future reference, as you noticed yourself, creating the partitions in advance can create confusing situation for newbies.
You started great installing XP first, then instead of using the Live CD partitioner you could have just started the install process and create the partitions selecting Manual Partitioning right then.
As you noticed, if you create them earlier, you still have to select each and "mount" it to the correct mount point, including swap.
Also, I don't know the ending layout but splitting it into three equal parts the first time is unnecessary. That way you left too much for swap.
The rule for swap is usully twice the amount of ram but with new computers having a lot of ram there is really no need swap to be more than 2GB. There are exceptions if having loads of ram and wanting to use sleep/hibernate, so people like to make swap 4-5GB but definitely not more than that.
Just plan your partitions before starting the installation, use the manual partitioning option right then, and don't dedicate too much space fro swap, use it in / and /home. Cheers.

---

### Post by oldfred on 2009-11-17
Glad you got it working serpentine5.

You are one more case where I have seen mixed Sata & Pata have issue. I had similar issues several years ago but now I am 100% Sata. It seems that BIOS, grub, ubuntu & windows do not define drive order the same. BIOS controls booting from whatever drive it sees as first, so to me that is the correct order.

You may also want to just install a new copy to grub into your 160GB drive. Some BIOS will not give you the choice on mixed Sata & Pata on all drive order.

---

### Post by raymondh on 2009-11-17
> **oldfred said:**
>  It seems that BIOS, grub, ubuntu & windows do not define drive order the same. BIOS controls booting from whatever drive it sees as first, so to me that is the correct order.

[COLOR="Navy"]Yes[/COLOR]


Regards,

---

### Post by MrSandman on 2009-11-30
Can someone please help. I upgraded to 9.10 and I borked my menu.lst. here is the results 


> ============================= Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => Grub0.97 is installed in the MBR of /dev/sdb and looks on the same drive 
    in partition #7 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

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
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xb0ebbf19

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   482,383,754   482,383,692  83 Linux
/dev/sda2         482,383,755   488,392,064     6,008,310   5 Extended
/dev/sda5         482,383,818   488,392,064     6,008,247  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xb0ebbf06

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63   472,680,494   472,680,432   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="4307898a-005c-4d67-bf60-e112687513df" TYPE="ext3" 
/dev/sda5: UUID="203bf0cd-e684-4500-8580-db28da3d5356" TYPE="swap" 
/dev/sdb1: UUID="8C4473D04473BC10" TYPE="ntfs" 

=============================== "mount" output: ===============================

/dev/sda1 on / type ext3 (rw,relatime,errors=remount-ro)
proc on /proc type proc (rw)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
udev on /dev type tmpfs (rw,mode=0755)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
none on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/sandman/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=sandman)


=========================== sda1/boot/grub/menu.lst: ===========================

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
default		0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		10

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

# Pretty colours
#color cyan/blue white/blue

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
# title		Windows 95/98/NT/2000
# root		(hd0,0)
# makeactive
# chainloader	+1
#
# title		Linux
# root		(hd0,1)
# kernel	/vmlinuz root=/dev/hda2 ro
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
# kopt=root=UUID=4307898a-005c-4d67-bf60-e112687513df ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=4307898a-005c-4d67-bf60-e112687513df

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
# howmany=all

## specify if running in Xen domU or have grub detect automatically
## update-grub will ignore non-xen kernels when running in domU and vice versa
## e.g. indomU=detect
##      indomU=true
##      indomU=false
# indomU=detect

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##


title		Ubuntu 9.10, kernel 2.6.31-15-generic
uuid		4307898a-005c-4d67-bf60-e112687513df
kernel		/boot/vmlinuz-2.6.31-15-generic root=UUID=4307898a-005c-4d67-bf60-e112687513df ro quiet splash 
initrd		/boot/initrd.img-2.6.31-15-generic
quiet

title		Ubuntu 9.10, kernel 2.6.31-15-generic (recovery mode)
uuid		4307898a-005c-4d67-bf60-e112687513df
kernel		/boot/vmlinuz-2.6.31-15-generic root=UUID=4307898a-005c-4d67-bf60-e112687513df ro  single
initrd		/boot/initrd.img-2.6.31-15-generic

title		Ubuntu 9.10, kernel 2.6.28-11-generic
uuid		4307898a-005c-4d67-bf60-e112687513df
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=4307898a-005c-4d67-bf60-e112687513df ro quiet splash 
initrd		/boot/initrd.img-2.6.28-11-generic
quiet

title		Ubuntu 9.10, kernel 2.6.28-11-generic (recovery mode)
uuid		4307898a-005c-4d67-bf60-e112687513df
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=4307898a-005c-4d67-bf60-e112687513df ro  single
initrd		/boot/initrd.img-2.6.28-11-generic

title		Ubuntu 9.10, memtest86+
uuid		4307898a-005c-4d67-bf60-e112687513df
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

=============================== sda1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda1 during installation
UUID=4307898a-005c-4d67-bf60-e112687513df /               ext3    relatime,errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=203bf0cd-e684-4500-8580-db28da3d5356 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda1: Location of files loaded by Grub: ===================


    .0GB: boot/grub/menu.lst
    .0GB: boot/grub/stage2
    .0GB: boot/initrd.img-2.6.28-11-generic
    .0GB: boot/initrd.img-2.6.31-15-generic
    .0GB: boot/vmlinuz-2.6.28-11-generic
    .0GB: boot/vmlinuz-2.6.31-15-generic
    .0GB: initrd.img
    .0GB: vmlinuz

================================ sdb1/boot.ini: ================================

[boot loader]

timeout=30

default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Home Edition" /noexecute=optin /fastdetect


Thanks in advance.

---

### Post by darkod on 2009-11-30
What exactly is the problem? As long as the drive marked sda is first in your BIOS boot order, you should be fine at least for Ubuntu.
Yes, menu.lst doesn't have entry for your XP. All you need to do is add it manually. Or install grub2 instead of grub1 that you have.
Your choice.

---

### Post by MrSandman on 2009-11-30
> **darkod said:**
> What exactly is the problem? As long as the drive marked sda is first in your BIOS boot order, you should be fine at least for Ubuntu.
Yes, menu.lst doesn't have entry for your XP. All you need to do is add it manually. Or install grub2 instead of grub1 that you have.
Your choice.

Well the problem is that I don't know what code to add in menu.lst so that XP is an option to boot. And I don't understand about installing grub2. Sorry I am a newbie. Thanks for your help

---

### Post by darkod on 2009-11-30
In terminal type:
sudo gedit /boot/grub/menu.lst

After the grouped entries starting with title Ubuntu etc and ending with empty line, add:

title Windows XP
rootnoverify(hd1,0)
makeactive
chainloader +1
--empty line--

Save the file and close. Reboot and see if that helps. If it doesn't, the next thing to try would be to insert after rootnoverify line:
map (hd0) (hd1)
map (hd1) (hd0)

Again save and close. Reboot, check.

---

### Post by MrSandman on 2009-11-30
> **darkod said:**
> In terminal type:
sudo gedit /boot/grub/menu.lst

After the grouped entries starting with title Ubuntu etc and ending with empty line, add:

title Windows XP
rootnoverify(hd1,0)
makeactive
chainloader +1
--empty line--

Save the file and close. Reboot and see if that helps. If it doesn't, the next thing to try would be to insert after rootnoverify line:
map (hd0) (hd1)
map (hd1) (hd0)

Again save and close. Reboot, check.

Worked beautifully. Thanks

title Microsoft Windows XP 
rootnoverify (hd1,0)
savedefault
makeactive
map (hd0) (hd1)
map (hd1) (hd0)
chainloader +1

---

