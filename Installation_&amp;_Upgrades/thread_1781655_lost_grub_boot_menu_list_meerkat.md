---
title: "lost grub boot menu list meerkat"
date: 2011-06-13
forum: Installation &amp; Upgrades
---

### Post by jimbean on 2011-06-13
I am using an old 8.04 live desktop disk

I am running meerkat 10.10 on the partition that is now ,not accessible

I dont know if i have grub or grub2

My machine boots to the grub boot menu list but its all of my old kernels
that have been removed from 9.04

I have a menu list in my ubuntu boot/grub partition  but they all point to 9.04, i have backups but they are the same 9.04

I have no grub2 menu list in etc/default

Can i just edit the menu list in boot/grub directory to look for my latest kernel
and how should i insert it

sudo??

---

### Post by nzjethro on 2011-06-13
Did you run
```
update-grub
```

If not, chroot in from your live CD, and run it. It'll rewrite grub.cfg with all the kernels that are installed.

---

### Post by oldfred on 2011-06-14
May be best to see what is where. You may have to chroot into your system to make all the repairs. Do you have liveCD of version you are running 10.10?

Boot Info Script courtesy of forum members meierfra & Gert Hulselmans
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt in a New Reply, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the New Reply Edit toolbar and then paste the contents between the generated [ code] paste here [ /code] tags.
V60 has improved formating and requires code tags to make it legible. New Version is a zip file that you have to extract to get .sh to run.

---

### Post by jimbean on 2011-06-14
sorry could not get rid of # 








                Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub Legacy (v0.97) is installed in the MBR of /dev/sda and looks on the 
    same drive in partition #5 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files:        /bootmgr /Boot/BCD /Windows/System32/winload.exe 
                       /ntldr /NTDETECT.COM

sda2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: __________________________________________________________________________

    File system:       ext3
    Boot sector type:  Grub Legacy
    Boot sector info:   Grub Legacy (v) is installed in the boot sector of 
                       sda5 and looks at sector 503201531 of the same hard 
                       drive for the stage2 file, but no stage2 files can be 
                       found at this location.
    Operating System:  Ubuntu 10.10
    Boot files:        /boot/grub/menu.lst /boot/grub/grub.conf /etc/fstab

sda6: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 300.0 GB, 300069052416 bytes
255 heads, 63 sectors/track, 36481 cylinders, total 586072368 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00000001

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *             63   268,414,019   268,413,957   7 NTFS / exFAT / HPFS
/dev/sda2         268,414,020   586,067,264   317,653,245   5 Extended
/dev/sda5         268,414,083   573,906,059   305,491,977  83 Linux
/dev/sda6         573,906,123   586,067,264    12,161,142  82 Linux swap / Solaris


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        BEEC2CBAEC2C6F39                       ntfs       
/dev/sda5        0c141384-a44e-4920-abdd-96e940d76fc2   ext3       
/dev/sda6        38c9a780-f85e-467f-8fd6-45fa2272fd8b   swap       

================================ Mount points: =================================

Device           Mount_Point              Type       Options



=========================== sda5/boot/grub/menu.lst: ===========================

--------------------------------------------------------------------------------
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
# kopt=root=UUID=0c141384-a44e-4920-abdd-96e940d76fc2 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,4)

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

title		Ubuntu 9.04, kernel 2.6.28-15-generic
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.28-15-generic root=UUID=0c141384-a44e-4920-abdd-96e940d76fc2 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-15-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-15-generic (recovery mode)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.28-15-generic root=UUID=0c141384-a44e-4920-abdd-96e940d76fc2 ro  single
initrd		/boot/initrd.img-2.6.28-15-generic

title		Ubuntu 9.04, kernel 2.6.28-14-generic
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.28-14-generic root=UUID=0c141384-a44e-4920-abdd-96e940d76fc2 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-14-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-14-generic (recovery mode)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.28-14-generic root=UUID=0c141384-a44e-4920-abdd-96e940d76fc2 ro  single
initrd		/boot/initrd.img-2.6.28-14-generic

title		Ubuntu 9.04, kernel 2.6.28-13-generic
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.28-13-generic root=UUID=0c141384-a44e-4920-abdd-96e940d76fc2 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-13-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-13-generic (recovery mode)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.28-13-generic root=UUID=0c141384-a44e-4920-abdd-96e940d76fc2 ro  single
initrd		/boot/initrd.img-2.6.28-13-generic

title		Ubuntu 9.04, kernel 2.6.27-14-generic
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.27-14-generic root=UUID=0c141384-a44e-4920-abdd-96e940d76fc2 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-14-generic
quiet

title		Ubuntu 9.04, kernel 2.6.27-14-generic (recovery mode)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.27-14-generic root=UUID=0c141384-a44e-4920-abdd-96e940d76fc2 ro  single
initrd		/boot/initrd.img-2.6.27-14-generic

title		Ubuntu 9.04, kernel 2.6.24-22-generic
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.24-22-generic root=UUID=0c141384-a44e-4920-abdd-96e940d76fc2 ro quiet splash 
initrd		/boot/initrd.img-2.6.24-22-generic
quiet

title		Ubuntu 9.04, kernel 2.6.24-22-generic (recovery mode)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.24-22-generic root=UUID=0c141384-a44e-4920-abdd-96e940d76fc2 ro  single
initrd		/boot/initrd.img-2.6.24-22-generic

title		Ubuntu 9.04, memtest86+
root		(hd0,4)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows Vista/Longhorn (loader)
root		(hd0,0)
savedefault
makeactive
chainloader	+1

--------------------------------------------------------------------------------

=============================== sda5/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda5
UUID=0c141384-a44e-4920-abdd-96e940d76fc2 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda6
UUID=38c9a780-f85e-467f-8fd6-45fa2272fd8b none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
--------------------------------------------------------------------------------

=================== sda5: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

            ?? = ??             boot/grub/grub.conf
            ?? = ??             boot/grub/menu.lst
            ?? = ??             boot/grub/stage2
            ?? = ??             boot/initrd.img-2.6.32-32-generic
            ?? = ??             boot/initrd.img-2.6.35-28-generic
            ?? = ??             boot/vmlinuz-2.6.32-32-generic
            ?? = ??             boot/vmlinuz-2.6.35-28-generic
            ?? = ??             initrd.img
            ?? = ??             initrd.img.old
            ?? = ??             vmlinuz
            ?? = ??             vmlinuz.old

```
[CODE][CODE]
```[/CODE][/CODE]

---

### Post by oldfred on 2011-06-14
You have grub legacy's boot loader in the MBR, a menu.lst for 9.04 in your install, but the kernels you have installed do are not shown at all in the menu.lst. You also have a grub.conf, but grub2 uses grub.cfg?

I think you need to chroot into your system, run updates, uninstall grub & grub2 & reinstall grub2.

drs305 chroot to reinstall grub2
[http://ubuntuforums.org/showthread.php?t=1581099](http://ubuntuforums.org/showthread.php?t=1581099)
Other chroot instructions:
kansasnoob- full chroot one line version with &&---- change sda3 to your install
[http://ubuntuforums.org/showpost.php?p=8068512&postcount=10](http://ubuntuforums.org/showpost.php?p=8068512&postcount=10)
[http://ubuntuforums.org/showthread.php?t=1470597](http://ubuntuforums.org/showthread.php?t=1470597)

Besides the reinstall of grub2 shown in drs305's link above run all of these while in the chroot:

#Then run whatever other commands needed - no sudo needed if chroot (maybe good to run "df- H" and "cat /etc/issue" to be certain #you mounted the correct partition).
#Commands once in chroot:
#if not chroot use: sudo -i
#houseclean
apt-get autoclean   # only removes files that cannot be downloaded anymore (obsolete)
apt-get clean
#refresh
apt-get update #resync package index
apt-get upgrade #newest versions of all packages, update must be run first
#would upgrade you to the latest kernel in the repositories
#dist-upgrade is also able to remove existing packages if required
apt-get dist-upgrade
apt-get -f install
dpkg --configure -a

#reinstall kernel:
sudo apt-get update
sudo apt-get install linux-image
sudo update-grub

sudo dpkg-reconfigure grub-pc

---

### Post by jimbean on 2011-06-16
its greek to me,  been known to hose quite a few systems of mine

is this right


ubuntu@ubuntu:~$ sudo grub-install --root-directory=/mnt /dev/sda5
/usr/sbin/grub-setup: warn: Attempting to install GRUB to a partition instead of the MBR.  This is a BAD idea..
/usr/sbin/grub-setup: warn: Embedding is not possible.  GRUB can only be installed in this setup by using blocklists.  However, blocklists are UNRELIABLE and its use is discouraged..
/usr/sbin/grub-setup: error: if you really want blocklists, use --force.
ubuntu@ubuntu:~$ sudo mount /dev/sda1 /mnt
ubuntu@ubuntu:~$ sudo grub-install --root-directory=/mnt /dev/sda1
/usr/sbin/grub-setup: warn: Attempting to install GRUB to a partition instead of the MBR.  This is a BAD idea..
/usr/sbin/grub-setup: warn: Embedding is not possible.  GRUB can only be installed in this setup by using blocklists.  However, blocklists are UNRELIABLE and its use is discouraged..
/usr/sbin/grub-setup: error: if you really want blocklists, use --force.

---

### Post by jimbean on 2011-06-16
ok after a couple of days of just staring at page of chroot instructions
it starting to look like my native language

---

### Post by jimbean on 2011-06-16
well this is a test if this had been a real emergency like work i would have had to pay ,thanks ubuntu forum again and {{{{{old fred}}}}}} if its still running in a day or so i will marked solved

---

