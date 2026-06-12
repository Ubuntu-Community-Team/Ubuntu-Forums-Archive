---
title: "Windows 7 and Ubuntu"
date: 2009-12-21
forum: Installation &amp; Upgrades
---

### Post by theturbanator on 2009-12-21
Hi everyone,

I had a dual boot with Vista and Ubuntu (9.04), with Vista as the loader (I don't entirely know what that means, though I think I have a good idea -- can anyone expound on the subject, please?), and I recently installed Windows 7 (on the same partition that Vista previously was installed on) -- note that this was a clean install, not an upgrade.  Now, when I start my computer, it automatically loads Windows 7 -- I have no choice anymore.  But that partition still exists.  I believe that this has to do with the fact that Vista was the loader but now no longer exists.  What can I do to get it working again?  Do I have to reinstall Ubuntu again?

Thank you for all of your help!

---

### Post by bumanie on 2009-12-21
If still using grub-legacy (which is the default bootloader in 9.04) [follow this]("http://ubuntuforums.org/showthread.php?t=224351").

---

### Post by theturbanator on 2009-12-21
Thank you very much! Unfortunately, I don't have my live Ubuntu cd with me (and I won't for a while) -- can I simply burn another one and boot into that?  Also, does it have to be Ubuntu 9.04?  What if I download and burn the Ubuntu 9.10 version?

---

### Post by Marlonsm on 2009-12-21
Any Ubuntu CD with the correct version should work.
But if you have 9.04, I don't think a 9.10 CD would do it, because the boot loader has changed between these versions.

---

### Post by bumanie on 2009-12-21
9.10 has grub 2 as the default bootloader - it will not allow reinstallation of grub-legacy as the two versions of grub are completely different. Easiest thing would be to download and burn a .iso of 9.04, then follow the guide.

---

### Post by sliketymo on 2009-12-21
Try this : 

[http://www.intowindows.com/download-easybcd-for-windows-7/](http://www.intowindows.com/download-easybcd-for-windows-7/)

---

### Post by theturbanator on 2009-12-21
Thank you all so much for your help -- I was able to get the grub-legacy bootloader to start working again.  Now, is the boot menu list editable?  I ask this because it still says Windows Vista, though I now have Windows 7.  Also, it lists every single kernel of Ubuntu that I have updated to, and I want to remove all but the most recent of the kernels.  Also, I would like to modify the default OS.  Is there anyway I can do all of this?  Or maybe it will correct itself when I upgrade to Ubuntu 9.10?

---

### Post by presence1960 on 2009-12-21
> **theturbanator said:**
> Thank you all so much for your help -- I was able to get the grub-legacy bootloader to start working again.  Now, is the boot menu list editable?  I ask this because it still says Windows Vista, though I now have Windows 7.  Also, it lists every single kernel of Ubuntu that I have updated to, and I want to remove all but the most recent of the kernels.  Also, I would like to modify the default OS.  Is there anyway I can do all of this?  Or maybe it will correct itself when I upgrade to Ubuntu 9.10?

If you get me more info I can tell you what to edit to add any OS you want to boot from GRUB.

Let's get a better look at your setup & boot process. Boot into Ubuntu. Come back here and use the link in my signature to download the Boot Info Script to the desktop. Once on desktop open a terminal (Applications > Accessories > Terminal) and run this command ```
sudo bash ~/Desktop/boot_info_script*.sh
``` This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text

---

### Post by rlvarcoe on 2009-12-21
> **presence1960 said:**
> If you get me more info I can tell you what to edit to add any OS you want to boot from GRUB.

Let's get a better look at your setup & boot process. Boot into Ubuntu. Come back here and use the link in my signature to download the Boot Info Script to the desktop. Once on desktop open a terminal (Applications > Accessories > Terminal) and run this command ```
sudo bash ~/Desktop/boot_info_script*.sh
``` This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text

Hey not my original post but I have the same issue... I tried as you suggested above sudo bash ~/Desktop/boot_info_script*.sh and got back a No such file or directory I am using 9.04

---

### Post by oldfred on 2009-12-21
rivacoe, please start a new thread with your problem even if it is similar as it gets confusing on who we are replying to.

Karmic now downloads into of all things /Downloads if in a working system. And my version 041 of the script put results into /home/fred - my home directory. I am not sure on download from liveCD anymore.

---

### Post by meierfra. on 2009-12-22
> got back a No such file or directory I am using 9.04 
Did you download the boot_info_script? To the Desktop?

> kkarmic now downloads into of all things /Downloads if in a working system. And my version 041 of the script put results into /home/fred - my home directory. I am not sure on download from liveCD anymore.

If the script in anywhere in the home directory, RESULTS.txt will be in the same folder as the script. So if the script is in ~/Downloads, RESULTS.txt will also be in  ~/Downloads.

But if the script is any of the system directories (/usr, /etc, /bin, ...) RESULTS.txt will be in the home directory.

---

### Post by theturbanator on 2009-12-24
Sorry for the delayed reply -- I was away for a few days.

Thank you for your help [presence1960]("http://ubuntuforums.org/member.php?u=657448") and meierfra.!  Here are the contents of the shell script:

```
============================= Boot Info Summary: ==============================

 => Grub 0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #5 for /boot/grub/stage2 and /boot/grub/menu.lst.
sda1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Dell Utility: Fat16
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda4: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xf0000000

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63       160,649       160,587  de Dell Utility
/dev/sda2    *        161,792   102,561,791   102,400,000   7 HPFS/NTFS
/dev/sda3         102,561,792   217,657,520   115,095,729   7 HPFS/NTFS
/dev/sda4         217,664,685   234,436,544    16,771,860   5 Extended
/dev/sda5         217,664,748   233,617,229    15,952,482  83 Linux
/dev/sda6         233,617,293   234,436,544       819,252  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

/dev/sda1: SEC_TYPE="msdos" LABEL="DellUtility" UUID="07D7-090F" TYPE="vfat" 
/dev/sda2: UUID="947C30397C301886" TYPE="ntfs" 
/dev/sda3: UUID="7C0221DD02219D60" LABEL="Files Partition" TYPE="ntfs" 
/dev/sda5: UUID="7d244d04-03d7-49be-99f5-a41a976dccdc" TYPE="ext3" 
/dev/sda6: UUID="f1dc20c2-45c7-41a1-9e94-9aae5e9e951e" TYPE="swap" 

=============================== "mount" output: ===============================

/dev/sda5 on / type ext3 (rw,relatime,errors=remount-ro)
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
gvfs-fuse-daemon on /home/desh/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=desh)


=========================== sda5/boot/grub/menu.lst: ===========================

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
# kopt=root=UUID=7d244d04-03d7-49be-99f5-a41a976dccdc ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=7d244d04-03d7-49be-99f5-a41a976dccdc

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

title        Ubuntu 9.10, kernel 2.6.31-16-generic
uuid        7d244d04-03d7-49be-99f5-a41a976dccdc
kernel        /boot/vmlinuz-2.6.31-16-generic root=UUID=7d244d04-03d7-49be-99f5-a41a976dccdc ro quiet splash 
initrd        /boot/initrd.img-2.6.31-16-generic
quiet

title        Ubuntu 9.10, kernel 2.6.31-16-generic (recovery mode)
uuid        7d244d04-03d7-49be-99f5-a41a976dccdc
kernel        /boot/vmlinuz-2.6.31-16-generic root=UUID=7d244d04-03d7-49be-99f5-a41a976dccdc ro  single
initrd        /boot/initrd.img-2.6.31-16-generic

title        Ubuntu 9.10, kernel 2.6.28-15-generic
uuid        7d244d04-03d7-49be-99f5-a41a976dccdc
kernel        /boot/vmlinuz-2.6.28-15-generic root=UUID=7d244d04-03d7-49be-99f5-a41a976dccdc ro quiet splash 
initrd        /boot/initrd.img-2.6.28-15-generic
quiet

title        Ubuntu 9.10, kernel 2.6.28-15-generic (recovery mode)
uuid        7d244d04-03d7-49be-99f5-a41a976dccdc
kernel        /boot/vmlinuz-2.6.28-15-generic root=UUID=7d244d04-03d7-49be-99f5-a41a976dccdc ro  single
initrd        /boot/initrd.img-2.6.28-15-generic

title        Ubuntu 9.10, memtest86+
uuid        7d244d04-03d7-49be-99f5-a41a976dccdc
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title        Dell Utility Partition
root        (hd0,0)
savedefault
makeactive
chainloader    +1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title        Windows Vista (loader)
rootnoverify    (hd0,1)
savedefault
makeactive
chainloader    +1


=============================== sda5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda5 during installation
UUID=7d244d04-03d7-49be-99f5-a41a976dccdc /               ext3    relatime,errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=f1dc20c2-45c7-41a1-9e94-9aae5e9e951e none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda5: Location of files loaded by Grub: ===================


 111.4GB: boot/grub/menu.lst
 111.4GB: boot/grub/stage2
 111.4GB: boot/initrd.img-2.6.28-15-generic
 111.4GB: boot/initrd.img-2.6.31-16-generic
 111.4GB: boot/vmlinuz-2.6.28-15-generic
 111.4GB: boot/vmlinuz-2.6.31-16-generic
 111.4GB: initrd.img
 111.4GB: initrd.img.old
 111.4GB: vmlinuz
 111.4GB: vmlinuz.old
```

---

### Post by meierfra. on 2009-12-24
You just need to edit menu.lst. Open the file via:

```
gksudo gedit /boot/grub/menu.lst 
```

Change   

"default 0" to "default ?".

Replace "?" by the position of the title you want to be the default. (grub starts counting at 0". So for Windows you currently have to use "default 7".)

Change 

"# howmany=all" to  "#howmany=1"

if you only want only one  kernel on your Grub menu. But I recommend to use "#howmany=2", just in case the first kernel does not work after the next kernel update.


You might also change 

"# updatedefaultentry=false" to "# updatedefaultentry=true"

This makes sure that, if the number of kernels on the menu.lst changes, "default ?" still points to the same item.

Then run

```
sudo update-grub
```
this  will remove the excess kernels from "menu.lst"

---

### Post by oldfred on 2009-12-24
Since you still are using grub legacy all the editing is in one place. Several of the boot parameters can be changed and you can just rename the Vista to 7.

just incase editing causes problem we want something to go back to:
sudo cp /boot/grub/menu.lst /boot/grub/menu.lst.backup

gksudo gedit /boot/grub/menu.lst

You will want to limit the number of kernels shown so the windows entry number will not change. It is best to show 2 kernels just incase a new one does not work.

Change this :
default        7
 I assume you will delete the Utility entry and it also counts the 'other operating' systems as one of the numbers (i had that number as the default and wondered why it would not boot), You may have to adjust the number.

Single # in this section is used as a parameter on update-grub.
# howmany=all
to:
# howmany=2

Delete the Utility entry if you want as you will not normally want it and edit the Vista to 7.

Then do an
update-grub

Another alternative is if you want windows first on the menu. You have to cut and paste it above the automagic area and leave the default to 0. If you do not move it above the automagic area it will be deleted on the first update-grub.
# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST
[COLOR=DarkRed]put entry here[/COLOR]
### BEGIN AUTOMAGIC KERNELS LIST

I see now meierfra beat me to it, I cannot type that fast.

---

### Post by Zoot7 on 2009-12-24
Gotta love the way Windows takes over the whole system. :)

you've to re-install Grub to the MBR, have a read here:
[https://wiki.ubuntu.com/Grub2#Recover%20Grub%202%20via%20LiveCD](https://wiki.ubuntu.com/Grub2#Recover%20Grub%202%20via%20LiveCD)

---

### Post by theturbanator on 2009-12-25
Thank you all very much! I was able to make all of the desired changes.  I greatly appreciate it!

---

