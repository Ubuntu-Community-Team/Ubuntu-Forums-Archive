---
title: "Installation problems duel boot with windows"
date: 2009-12-02
forum: Installation &amp; Upgrades
---

### Post by rtows on 2009-12-02
Hi, I have just install a hard drive with windows XP and have another hard drive with Ubuntu 9.10. I am unable to access the Ubuntu harddrive. What is the program used to creat a duel boot ? How can I do this if both hard drives are up and running? Rich

---

### Post by darkod on 2009-12-02
Do you already have ubuntu installed on the other drive? If yes, and if the bootloader grub2 is on its MBR, you might need to select in BIOS that drive to be first in boot order. It might be booting windows directly from the windows disk if it's first in boot order.

---

### Post by Megafag on 2009-12-02
> **rtows said:**
> duel boot

](*,)

---

### Post by rtows on 2009-12-02
Thanks for the help so far. I have Windows xp on one drive and Ubuntu on the other drive. Neither drive has a grub program for choosing which drive to boot. The windows drive boots automatically and the ubuntu drive does not exist on the windows Drive. If I download and install Grub or Grub2 on the windows drive will I be able to access the Ubuntu drive or is tere another way to go? I know the problem is I cannot access the Ubuntu drive and would like to use that drive. Rich

---

### Post by presence1960 on 2009-12-02
windows does not have the ability to natively read Linux partitions/disks in My Computer or Windows Explorer. But in Disk Management the Linux partitions/disks will show up as unknown.

I need more info than you can probably give me yourself. Let's get a better look at your setup & boot process. Boot the Ubuntu Live CD/USB. Choose "try ubuntu without any changes", when the desktop loads come back here and use the link in my signature to download the Boot Info Script to the desktop. Once on desktop open a terminal and run this command ```
sudo bash ~/Desktop/boot_info_script*.sh
``` This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text.

---

### Post by Vajk69 on 2009-12-02
Hi,

I have a similar problem. Similar I say as I have one drive that is partitioned for Windows XP and UBUNTU 9.10. At boot-up I cannot access Ubuntu 9.10. 

Ubuntu was installed first, then Windows.  Windows was installed on Drive C first partition from an Acronis  back-up which was created from a clean install when UBUNTU had not yet been installed on Drive C    

What should I do to be able to access Ubuntu?

I beg you guys to be specific as I am new to Linux and I am not much of a programmer either. 

Thanks ahead,

Vajk69

---

### Post by presence1960 on 2009-12-02
> **Vajk69 said:**
> Hi,

I have a similar problem. Similar I say as I have one drive that is partitioned for Windows XP and UBUNTU 9.10. At boot-up I cannot access Ubuntu 9.10. 

Ubuntu was installed first, then Windows.  Windows was installed on Drive C first partition from an Acronis  back-up which was created from a clean install when UBUNTU had not yet been installed on Drive C    

What should I do to be able to access Ubuntu?

I beg you guys to be specific as I am new to Linux and I am not much of a programmer either. 

Thanks ahead,

Vajk69

Please start your own thread. it becomes difficult to help more than one person in the same thread. You can post a link to "your thread" back here so we will know where your thread is.

---

### Post by rtows on 2009-12-07
Hello I'm back. I have Windows Xp loaded onto 1 HD and Ubuntu 9.10 on another and the Windows disc is the only one that boots. The other is not recognized.  I recieved a reply from Presence 1960 that I don't understand. Said to boot from an ubuntu live cd and when the desktop loads come back here and use the link in my signature to download the boot info script to the desktop. I have booted from ubuntu 8.10 cd and had desktop load. I don't understand "come back here and use the link in my signature to download the boot info script to the desktop. 
Help. Rich

---

### Post by Kanshu on 2009-12-07
I encountered that problem when I repaired my XP by reinstalling. My solution was to prepare installing another copy of Ubuntu in a smaller partition by resizing the original Ubuntu partition. I think I aborted the install and the dual boot screen reappeared although I can't really remember if I "actually" reinstalled Ubuntu because I've done it several times already.

---

### Post by darkod on 2009-12-07
> **rtows said:**
> Hello I'm back. I have Windows Xp loaded onto 1 HD and Ubuntu 9.10 on another and the Windows disc is the only one that boots. The other is not recognized.  I recieved a reply from Presence 1960 that I don't understand. Said to boot from an ubuntu live cd and when the desktop loads come back here and use the link in my signature to download the boot info script to the desktop. I have booted from ubuntu 8.10 cd and had desktop load. I don't understand "come back here and use the link in my signature to download the boot info script to the desktop. 
Help. Rich

First of all make sure you set the ubuntu disk as first boot option in your BIOS. If BIOS is booting the windows disk first you can't expect to see any option for ubuntu.
If that doesn't work too, then follow the instructions presence gave you. What he meant is boot with the ubuntu cd, select Try Ubuntu, and that will load ubuntu from the cd, you will have internet, so come back to this thread, download the script in his signature, and follow his instructions.

---

### Post by presence1960 on 2009-12-07
> **rtows said:**
> Hello I'm back. I have Windows Xp loaded onto 1 HD and Ubuntu 9.10 on another and the Windows disc is the only one that boots. The other is not recognized.  I recieved a reply from Presence 1960 that I don't understand. Said to boot from an ubuntu live cd and when the desktop loads come back here and use the link in my signature to download the boot info script to the desktop. I have booted from ubuntu 8.10 cd and had desktop load. I don't understand "come back here and use the link in my signature to download the boot info script to the desktop. 
Help. Rich

Look at the bottom of my post. See the link Boot Info Script? Click on it and download it to your desktop. Then open a terminal and run the command I had posted.

---

### Post by rtows on 2009-12-08
I have downloaded the boot info script to my desktop. Now I can't find the terminal from my desktop after I booted ubuntu 9.10 from cd. How do I get there? Rich

---

### Post by presence1960 on 2009-12-08
> **rtows said:**
> I have downloaded the boot info script to my desktop. Now I can't find the terminal from my desktop after I booted ubuntu 9.10 from cd. How do I get there? Rich

Go Applications > Accessories > Terminal

A terminal window will open. paste the following command and hit Enter

```
sudo bash ~/Desktop/boot_info_script*.sh
```

It will ask for password. Type your user password in, but you will not see any characters on the screen. It will appear as if your typing is not recognized- don't worry about that. When done typing password hit Enter.

---

### Post by rtows on 2009-12-08
I have had another thought? I I use the Ubuntu 9.10 cd and install the ubuntu to my windows hd as a program will this recognize my other HD?

---

### Post by rtows on 2009-12-08
Thanks for your help so far. I got the results.txt file. I have that copied below. Hope you can help me do whatever is next? Rich

============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda
 => Windows is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sdb1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

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

Disk /dev/sda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders, total 390721968 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xcec2cec2

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   390,700,799   390,700,737   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders, total 78165360 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xaef68167

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63    75,152,069    75,152,007  83 Linux
/dev/sdb2          75,152,070    78,156,224     3,004,155   5 Extended
/dev/sdb5          75,152,133    78,156,224     3,004,092  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

/dev/loop0: TYPE="squashfs" 
/dev/sda1: UUID="366C83726C832BA5" TYPE="ntfs" 
/dev/sdb1: UUID="afa11f8e-0470-48ae-b140-6edac467a71a" TYPE="ext3" 
/dev/sdb5: UUID="7413333b-83a4-4255-85e7-6d2b04536824" TYPE="swap" 
/dev/ramzswap0: TYPE="swap" 

=============================== "mount" output: ===============================

aufs on / type aufs (rw)
none on /proc type proc (rw,noexec,nosuid,nodev)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
udev on /dev type tmpfs (rw,mode=0755)
/dev/sr0 on /cdrom type iso9660 (rw)
/dev/loop0 on /rofs type squashfs (rw)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
none on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/ubuntu/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=ubuntu)
/dev/sda1 on /media/366C83726C832BA5 type fuseblk (rw,nosuid,nodev,allow_other,default_permissions,blksize=4096)
/dev/sdb1 on /media/afa11f8e-0470-48ae-b140-6edac467a71a type ext3 (rw,nosuid,nodev,uhelper=devkit)


================================ sda1/boot.ini: ================================

[boot loader] 
timeout=1 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Home Edition" /noexecute=optin /fastdetect 

=========================== sdb1/boot/grub/menu.lst: ===========================

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
# kopt=root=UUID=afa11f8e-0470-48ae-b140-6edac467a71a ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd1,0)

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

title        Ubuntu 9.10, kernel 2.6.31-15-generic
root        (hd1,0)
kernel        /boot/vmlinuz-2.6.31-15-generic root=UUID=afa11f8e-0470-48ae-b140-6edac467a71a ro quiet splash 
initrd        /boot/initrd.img-2.6.31-15-generic
quiet

title        Ubuntu 9.10, kernel 2.6.31-15-generic (recovery mode)
root        (hd1,0)
kernel        /boot/vmlinuz-2.6.31-15-generic root=UUID=afa11f8e-0470-48ae-b140-6edac467a71a ro  single
initrd        /boot/initrd.img-2.6.31-15-generic

title        Ubuntu 9.10, kernel 2.6.31-14-generic
root        (hd1,0)
kernel        /boot/vmlinuz-2.6.31-14-generic root=UUID=afa11f8e-0470-48ae-b140-6edac467a71a ro quiet splash 
initrd        /boot/initrd.img-2.6.31-14-generic
quiet

title        Ubuntu 9.10, kernel 2.6.31-14-generic (recovery mode)
root        (hd1,0)
kernel        /boot/vmlinuz-2.6.31-14-generic root=UUID=afa11f8e-0470-48ae-b140-6edac467a71a ro  single
initrd        /boot/initrd.img-2.6.31-14-generic

title        Ubuntu 9.10, kernel 2.6.28-16-generic
root        (hd1,0)
kernel        /boot/vmlinuz-2.6.28-16-generic root=UUID=afa11f8e-0470-48ae-b140-6edac467a71a ro quiet splash 
initrd        /boot/initrd.img-2.6.28-16-generic
quiet

title        Ubuntu 9.10, kernel 2.6.28-16-generic (recovery mode)
root        (hd1,0)
kernel        /boot/vmlinuz-2.6.28-16-generic root=UUID=afa11f8e-0470-48ae-b140-6edac467a71a ro  single
initrd        /boot/initrd.img-2.6.28-16-generic

title        Ubuntu 9.10, kernel 2.6.27-11-generic
root        (hd1,0)
kernel        /boot/vmlinuz-2.6.27-11-generic root=UUID=afa11f8e-0470-48ae-b140-6edac467a71a ro quiet splash 
initrd        /boot/initrd.img-2.6.27-11-generic
quiet

title        Ubuntu 9.10, kernel 2.6.27-11-generic (recovery mode)
root        (hd1,0)
kernel        /boot/vmlinuz-2.6.27-11-generic root=UUID=afa11f8e-0470-48ae-b140-6edac467a71a ro  single
initrd        /boot/initrd.img-2.6.27-11-generic

title        Ubuntu 9.10, kernel 2.6.24-23-generic
root        (hd1,0)
kernel        /boot/vmlinuz-2.6.24-23-generic root=UUID=afa11f8e-0470-48ae-b140-6edac467a71a ro quiet splash 
initrd        /boot/initrd.img-2.6.24-23-generic
quiet

title        Ubuntu 9.10, kernel 2.6.24-23-generic (recovery mode)
root        (hd1,0)
kernel        /boot/vmlinuz-2.6.24-23-generic root=UUID=afa11f8e-0470-48ae-b140-6edac467a71a ro  single
initrd        /boot/initrd.img-2.6.24-23-generic

title        Ubuntu 9.10, memtest86+
root        (hd1,0)
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title        Microsoft Windows XP Home Edition
root        (hd0,0)
savedefault
makeactive
chainloader    +1


=============================== sdb1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdb1
UUID=afa11f8e-0470-48ae-b140-6edac467a71a /               ext3    relatime,errors=remount-ro 0       1
# /dev/sdb5
UUID=7413333b-83a4-4255-85e7-6d2b04536824 none            swap    sw              0       0
/dev/scd1       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/scd0       /media/cdrom1   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sdb1: Location of files loaded by Grub: ===================


    .0GB: boot/grub/menu.lst
    .0GB: boot/grub/stage2
    .0GB: boot/initrd.img-2.6.24-23-generic
    .0GB: boot/initrd.img-2.6.24-23-generic.bak
    .0GB: boot/initrd.img-2.6.27-11-generic
    .0GB: boot/initrd.img-2.6.28-16-generic
    .0GB: boot/initrd.img-2.6.31-14-generic
    .0GB: boot/initrd.img-2.6.31-15-generic
    .0GB: boot/vmlinuz-2.6.24-23-generic
    .0GB: boot/vmlinuz-2.6.27-11-generic
    .0GB: boot/vmlinuz-2.6.28-16-generic
    .0GB: boot/vmlinuz-2.6.31-14-generic
    .0GB: boot/vmlinuz-2.6.31-15-generic
    .0GB: initrd.img
    .0GB: initrd.img.old
    .0GB: vmlinuz
    .0GB: vmlinuz.old
=======Devices which don't seem to have a corresponding hard drive==============

sdc

---

### Post by presence1960 on 2009-12-08
you do not have GRUB installed, both your disks have windows on MBR. You will need your Ubuntu Live CD. Go into BIOS and set your 200 GB disk as first in the hard disk boot order. Save changes to CMOS & continue booting off the Ubuntu Live CD. When the desktop loads open a terminal and do this starting with #2:

```
1. Boot your computer up with Ubuntu CD
2. Open a terminal window or switch to a tty.
3. Type sudo grub. Should get text of which last line is grub>
4. Type "find /boot/grub/stage1". You'll get a response like "(hd1,0)". 
5. Type "root (hd1,0)"
6. Type "setup (hd0)", to install GRUB to MBR
7. Quit grub by typing "quit".
8. Reboot and remove the bootable CD.
```

You should get the GRUB menu when you boot.

P.S. I can tell you got to 9.10 via a dist upgrade because you have kernels in your menu.lst that do not belong to 9.10. Karmic's kernels are 2.6.31-x. Also your menu.lst uses the (hdx,y) designations rather than UUID. Hopefully this works!

---

### Post by rtows on 2009-12-08
Hello again, I have tried to do what you have asked: 
open terminal
type sudo grub 
      I get    sudo: grub: command not found
I don't know what to do?

---

### Post by presence1960 on 2009-12-08
> **rtows said:**
> Hello again, I have tried to do what you have asked: 
open terminal
type sudo grub 
      I get    sudo: grub: command not found
I don't know what to do?
I gave you the command to restore GRUB Legacy 0.97 since your 9.10 has a menu.lst file. I would now try to install GRUB 2 (which comes default in a 9.10 clean install) by following these directions:

Boot the Live CD, choose "try ubuntu without any changes...", when the desktop loads open a terminal and run ```
sudo apt-get install grub-pc
``` If asked your root directory is sdb1 and you want GRUB on sdb. On reboot change sdb to first in the hard disk boot order in BIOS.

---

### Post by ddas4 on 2009-12-08
Ideally windows should be installed first, followed by Ubuntu. To help recover go through this thread:
 
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

---

### Post by rtows on 2009-12-12
Hi, I am back again. Everything I have tried says no directory named? exists. I have decided to change my idea. I would like to re-install ubuntu 9.10 on my 40g HD. I started the process but when I came to the partitoning part There was no 40g HD just the the 200g HD. What process do I follow to have the install program to recognize my 40g HD?

---

