---
title: "Dual boot windows 7 and ubuntu 9.10 separate hard drives"
date: 2010-01-13
forum: Installation &amp; Upgrades
---

### Post by tatmark1 on 2010-01-13
I had vista and ubuntu dual booting on separate hard drives. I unplugged my ubuntu drive and installed windows 7 on the vista drive. I now have ubuntu drive plugged back inand now I am stuck.
It boots to windows 7 and i can switch drive is in bios and boot ubuntu drive and it starts with grub menu. The grub menu still has vista on it but will not boot 7. I would like to get back to booting with the grub menu if anyone can help.
Thanks

---

### Post by Nuzair on 2010-01-13
update the grub list

```
sudo update-grub
```

---

### Post by tatmark1 on 2010-01-13
this is the result of that going to try to reboot now
Searching for GRUB installation directory ... found: /boot/grub
Searching for default file ... found: /boot/grub/default
Testing for an existing GRUB menu.lst file ... found: /boot/grub/menu.lst
Searching for splash image ... none found, skipping ...
Found kernel: /boot/vmlinuz-2.6.31-17-generic
Found kernel: /boot/vmlinuz-2.6.31-16-generic
Found kernel: /boot/vmlinuz-2.6.31-15-generic
Found kernel: /boot/vmlinuz-2.6.31-14-generic
Found kernel: /boot/vmlinuz-2.6.28-11-generic
Found kernel: /boot/memtest86+.bin
Updating /boot/grub/menu.lst ... done

---

### Post by tatmark1 on 2010-01-13
Yeah that didnt do anything

---

### Post by Nuzair on 2010-01-13
There are many posibilities that cause this problem.

Can't you mount the window volume file in ubuntu?
-If not, your Ubuntu is having troubles mounting the volume.

Then, in terminal type:

```
sudo fdisk -l
```

If you can mount the  volume:-

try to install grub2..

```
sudo apt-get install grub2
```

then, try to update the grub2 

```
sudo udate-grub2
```

---

### Post by tatmark1 on 2010-01-13
i can mount it

---

### Post by tatmark1 on 2010-01-13
Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xdefd3c49

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          13      102400    7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sda2              13       60802   488282112    7  HPFS/NTFS

Disk /dev/sdb: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00023388

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       29272   235127308+  83  Linux
/dev/sdb2           29273       30401     9068692+   5  Extended
/dev/sdb5           29273       30401     9068661   82  Linux swap / Solaris

---

### Post by Nuzair on 2010-01-13
may i know your kernel version?

type uname -r in terminal

---

### Post by tatmark1 on 2010-01-13
2.6.31-17-generic

---

### Post by Nuzair on 2010-01-13
Ok..it same with me..seem you have same problem like me before..

I also use ubuntu 9.10 and window 7

try to intall and update grub2..

you should get like this..

Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.31-17-generic
Found initrd image: /boot/initrd.img-2.6.31-17-generic
Found memtest86+ image: /boot/memtest86+.bin
Found Windows 7 (loader) on /dev/sda1
done

---

### Post by tatmark1 on 2010-01-13
this is whats in the terminal after typing sudo apt-get install grub2


 Package configuration

 &#9484;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9508; Configuring grub-pc &#9500;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9488;
 &#9474;                                                                           &#9474; 
 &#9474; GRUB upgrade scripts have detected a GRUB Legacy setup in /boot/grub.     &#8593; 
 &#9474;                                                                           &#9646; 
 &#9474; In order to replace the Legacy version of GRUB in your system, it is      &#9618; 
 &#9474; recommended that /boot/grub/menu.lst is adjusted to chainload GRUB 2      &#9618; 
 &#9474; from your existing GRUB Legacy setup.  This step may be automaticaly      &#9618; 
 &#9474; performed now.                                                            &#9618; 
 &#9474;                                                                           &#9618; 
 &#9474; It's recommended that you accept chainloading GRUB 2 from menu.lst, and   &#9618; 
 &#9474; verify that your new GRUB 2 setup is functional for you, before you       &#9618; 
 &#9474; install it directly to your MBR (Master Boot Record).                     &#9618; 
 &#9474;                                                                           &#9618; 
 &#9474; In either case, whenever you want GRUB 2 to be loaded directly from MBR,  &#9618; 
 &#9474; you can do so by issuing (as root) the following command:                 &#9618; 
 &#9474;                                                                           &#8595; 
 &#9474;                                                                             
 &#9474;                                  <Ok>                                       
 &#9474;                                                                           &#9474; 
 &#9492;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;

---

### Post by tatmark1 on 2010-01-14
well whatever i did screwed up grub because now when i go into bios to boot from ubuntu drive i get grub error 15...????

---

### Post by tatmark1 on 2010-01-14
can anyone here help me?

---

### Post by tatmark1 on 2010-01-14
please

---

### Post by tatmark1 on 2010-01-14
still need help....anyone  cannot boot ubuntu at all   if i switch in bios i get grub error 15....

---

### Post by darkod on 2010-01-14
You were using grub1 and not grub2. In that case after installing win7 usually it doesn't detect new OS automatically (that's introduced in grub2). All you needed to do is add win7 entry in menu.lst file manually. That's for grub1.

But now after messing around I have no idea what the current situation is.

Boot with the ubuntu cd, Try Ubuntu option, download the script in my signature, move it on desktop for example and execute it in terminal with:
sudo bash ~/Desktop/boot_info_script*.sh

It will create results.txt file. Copy the content of the file here, and wrap it in CODE tags (with the text selected hit the # button in the toolbar above). After viewing your boot details maybe we can figure it out.

---

### Post by tatmark1 on 2010-01-14
============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda
 => Grub 0.97 is installed in the MBR of /dev/sdb and looks on the same drive 
    in partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.
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

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/menu.lst /boot/grub/grub.cfg /etc/fstab 
                       /boot/grub/core.img

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

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xdefd3c49

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048       206,847       204,800   7 HPFS/NTFS
/dev/sda2             206,848   976,771,071   976,564,224   7 HPFS/NTFS

sudo bash ~/Desktop/boot_info_script*.sh

Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00023388

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63   470,254,679   470,254,617  83 Linux
/dev/sdb2         470,254,680   488,392,064    18,137,385   5 Extended
/dev/sdb5         470,254,743   488,392,064    18,137,322  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

/dev/loop0: TYPE="squashfs" 
/dev/sda1: UUID="F64455CE445591EB" LABEL="System Reserved" TYPE="ntfs" 
/dev/sda2: UUID="12BC5C4CBC5C2C8B" TYPE="ntfs" 
/dev/sdb1: UUID="7a84b891-6478-40a2-aeb4-ac36593ab846" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sdb1: UUID="7a84b891-6478-40a2-aeb4-ac36593ab846" TYPE="ext3" 
/dev/sdb5: UUID="caa90822-a704-4d6c-a18d-48188fedcaa8" TYPE="swap" 

=============================== "mount" output: ===============================

proc on /proc type proc (rw)
sysfs on /sys type sysfs (rw)
tmpfs on /lib/modules/2.6.28-11-generic/volatile type tmpfs (rw,mode=0755)
tmpfs on /lib/modules/2.6.28-11-generic/volatile type tmpfs (rw,mode=0755)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
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
# kopt=root=UUID=7a84b891-6478-40a2-aeb4-ac36593ab846 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=7a84b891-6478-40a2-aeb4-ac36593ab846

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

title		Ubuntu 9.10, kernel 2.6.31-17-generic
uuid		7a84b891-6478-40a2-aeb4-ac36593ab846
kernel		/boot/vmlinuz-2.6.31-17-generic root=UUID=7a84b891-6478-40a2-aeb4-ac36593ab846 ro quiet splash 
initrd		/boot/initrd.img-2.6.31-17-generic
quiet

title		Ubuntu 9.10, kernel 2.6.31-17-generic (recovery mode)
uuid		7a84b891-6478-40a2-aeb4-ac36593ab846
kernel		/boot/vmlinuz-2.6.31-17-generic root=UUID=7a84b891-6478-40a2-aeb4-ac36593ab846 ro  single
initrd		/boot/initrd.img-2.6.31-17-generic

title		Ubuntu 9.10, kernel 2.6.31-16-generic
uuid		7a84b891-6478-40a2-aeb4-ac36593ab846
kernel		/boot/vmlinuz-2.6.31-16-generic root=UUID=7a84b891-6478-40a2-aeb4-ac36593ab846 ro quiet splash 
initrd		/boot/initrd.img-2.6.31-16-generic
quiet

title		Ubuntu 9.10, kernel 2.6.31-16-generic (recovery mode)
uuid		7a84b891-6478-40a2-aeb4-ac36593ab846
kernel		/boot/vmlinuz-2.6.31-16-generic root=UUID=7a84b891-6478-40a2-aeb4-ac36593ab846 ro  single
initrd		/boot/initrd.img-2.6.31-16-generic

title		Ubuntu 9.10, kernel 2.6.31-15-generic
uuid		7a84b891-6478-40a2-aeb4-ac36593ab846
kernel		/boot/vmlinuz-2.6.31-15-generic root=UUID=7a84b891-6478-40a2-aeb4-ac36593ab846 ro quiet splash 
initrd		/boot/initrd.img-2.6.31-15-generic
quiet

title		Ubuntu 9.10, kernel 2.6.31-15-generic (recovery mode)
uuid		7a84b891-6478-40a2-aeb4-ac36593ab846
kernel		/boot/vmlinuz-2.6.31-15-generic root=UUID=7a84b891-6478-40a2-aeb4-ac36593ab846 ro  single
initrd		/boot/initrd.img-2.6.31-15-generic

title		Ubuntu 9.10, kernel 2.6.31-14-generic
uuid		7a84b891-6478-40a2-aeb4-ac36593ab846
kernel		/boot/vmlinuz-2.6.31-14-generic root=UUID=7a84b891-6478-40a2-aeb4-ac36593ab846 ro quiet splash 
initrd		/boot/initrd.img-2.6.31-14-generic
quiet

title		Ubuntu 9.10, kernel 2.6.31-14-generic (recovery mode)
uuid		7a84b891-6478-40a2-aeb4-ac36593ab846
kernel		/boot/vmlinuz-2.6.31-14-generic root=UUID=7a84b891-6478-40a2-aeb4-ac36593ab846 ro  single
initrd		/boot/initrd.img-2.6.31-14-generic

title		Ubuntu 9.10, kernel 2.6.28-11-generic
uuid		7a84b891-6478-40a2-aeb4-ac36593ab846
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=7a84b891-6478-40a2-aeb4-ac36593ab846 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-11-generic
quiet

title		Ubuntu 9.10, kernel 2.6.28-11-generic (recovery mode)
uuid		7a84b891-6478-40a2-aeb4-ac36593ab846
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=7a84b891-6478-40a2-aeb4-ac36593ab846 ro  single
initrd		/boot/initrd.img-2.6.28-11-generic

title		Ubuntu 9.10, memtest86+
uuid		7a84b891-6478-40a2-aeb4-ac36593ab846
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows Vista (loader)
rootnoverify	(hd0,0)
savedefault
makeactive
chainloader	+1


=========================== sdb1/boot/grub/grub.cfg: ===========================

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
set root=(hd1,1)
search --no-floppy --fs-uuid --set 7a84b891-6478-40a2-aeb4-ac36593ab846
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
menuentry "Ubuntu, Linux 2.6.31-17-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd1,1)
	search --no-floppy --fs-uuid --set 7a84b891-6478-40a2-aeb4-ac36593ab846
	linux	/boot/vmlinuz-2.6.31-17-generic root=UUID=7a84b891-6478-40a2-aeb4-ac36593ab846 ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-17-generic
}
menuentry "Ubuntu, Linux 2.6.31-17-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd1,1)
	search --no-floppy --fs-uuid --set 7a84b891-6478-40a2-aeb4-ac36593ab846
	linux	/boot/vmlinuz-2.6.31-17-generic root=UUID=7a84b891-6478-40a2-aeb4-ac36593ab846 ro single 
	initrd	/boot/initrd.img-2.6.31-17-generic
}
menuentry "Ubuntu, Linux 2.6.31-16-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd1,1)
	search --no-floppy --fs-uuid --set 7a84b891-6478-40a2-aeb4-ac36593ab846
	linux	/boot/vmlinuz-2.6.31-16-generic root=UUID=7a84b891-6478-40a2-aeb4-ac36593ab846 ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-16-generic
}
menuentry "Ubuntu, Linux 2.6.31-16-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd1,1)
	search --no-floppy --fs-uuid --set 7a84b891-6478-40a2-aeb4-ac36593ab846
	linux	/boot/vmlinuz-2.6.31-16-generic root=UUID=7a84b891-6478-40a2-aeb4-ac36593ab846 ro single 
	initrd	/boot/initrd.img-2.6.31-16-generic
}
menuentry "Ubuntu, Linux 2.6.31-15-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd1,1)
	search --no-floppy --fs-uuid --set 7a84b891-6478-40a2-aeb4-ac36593ab846
	linux	/boot/vmlinuz-2.6.31-15-generic root=UUID=7a84b891-6478-40a2-aeb4-ac36593ab846 ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-15-generic
}
menuentry "Ubuntu, Linux 2.6.31-15-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd1,1)
	search --no-floppy --fs-uuid --set 7a84b891-6478-40a2-aeb4-ac36593ab846
	linux	/boot/vmlinuz-2.6.31-15-generic root=UUID=7a84b891-6478-40a2-aeb4-ac36593ab846 ro single 
	initrd	/boot/initrd.img-2.6.31-15-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd1,1)
	search --no-floppy --fs-uuid --set 7a84b891-6478-40a2-aeb4-ac36593ab846
	linux	/boot/vmlinuz-2.6.31-14-generic root=UUID=7a84b891-6478-40a2-aeb4-ac36593ab846 ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd1,1)
	search --no-floppy --fs-uuid --set 7a84b891-6478-40a2-aeb4-ac36593ab846
	linux	/boot/vmlinuz-2.6.31-14-generic root=UUID=7a84b891-6478-40a2-aeb4-ac36593ab846 ro single 
	initrd	/boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.28-11-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd1,1)
	search --no-floppy --fs-uuid --set 7a84b891-6478-40a2-aeb4-ac36593ab846
	linux	/boot/vmlinuz-2.6.28-11-generic root=UUID=7a84b891-6478-40a2-aeb4-ac36593ab846 ro   quiet splash
	initrd	/boot/initrd.img-2.6.28-11-generic
}
menuentry "Ubuntu, Linux 2.6.28-11-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd1,1)
	search --no-floppy --fs-uuid --set 7a84b891-6478-40a2-aeb4-ac36593ab846
	linux	/boot/vmlinuz-2.6.28-11-generic root=UUID=7a84b891-6478-40a2-aeb4-ac36593ab846 ro single 
	initrd	/boot/initrd.img-2.6.28-11-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" {
	insmod ntfs
	set root=(hd0,1)
	search --no-floppy --fs-uuid --set f64455ce445591eb
	chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sdb1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sdb1 during installation
UUID=7a84b891-6478-40a2-aeb4-ac36593ab846 /               ext3    relatime,errors=remount-ro 0       1
# swap was on /dev/sdb5 during installation
UUID=caa90822-a704-4d6c-a18d-48188fedcaa8 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sdb1: Location of files loaded by Grub: ===================


 157.1GB: boot/grub/core.img
 157.0GB: boot/grub/grub.cfg
  86.5GB: boot/grub/menu.lst
  86.5GB: boot/initrd.img-2.6.28-11-generic
  86.4GB: boot/initrd.img-2.6.31-14-generic
  86.5GB: boot/initrd.img-2.6.31-15-generic
  86.5GB: boot/initrd.img-2.6.31-16-generic
  86.5GB: boot/initrd.img-2.6.31-17-generic
  86.5GB: boot/vmlinuz-2.6.28-11-generic
  86.5GB: boot/vmlinuz-2.6.31-14-generic
  86.5GB: boot/vmlinuz-2.6.31-15-generic
  86.5GB: boot/vmlinuz-2.6.31-16-generic
  86.4GB: boot/vmlinuz-2.6.31-17-generic
  86.5GB: initrd.img
  86.5GB: initrd.img.old
  86.4GB: vmlinuz
  86.5GB: vmlinuz.old


thanks

---

### Post by darkod on 2010-01-14
You have grub1 on the MBR of /dev/sdb and menu.lst on /dev/sdb1, but the rest of the boot files on /dev/sdb1 seem to be from grub2.
I think just reinstalling grub2 to the MBR of /dev/sdb should do the trick.
Boot with the ubuntu 9.10 cd (NOT 9.04 or earlier), Try Ubuntu option, and in terminal execute:

sudo mount /dev/sdb1 /mnt
sudo grub-install --root-directory=/mnt/ /dev/sdb

Reboot without the cd in the drive and see how it goes. If it boots up OK I would move menu.lst from /boot/grub folder to your home folder for example, not to create confusion.

Hope this works for you.

---

### Post by tatmark1 on 2010-01-14
well it kind of works. It wants to boot windows unless i go to bios and choose to boot from ubuntu drive. how can i fix that? thanks alot
and i should just move the menu file fro boot/grub to home?

---

### Post by darkod on 2010-01-14
Well, you do have two hdds. /dev/sda has windows on it and windows bootloader and if this drive is first in BIOS hdd boot order, it will just boot windows straight away.
The other drive, /dev/sdb, has ubuntu and grub2 on it, and you need to set this drive as first option in hdd boot order. Before the windows drive. Because grub2 will give you options for ubuntu and windows, unlike windows bootloader.

Yes, I would move (not delete) menu.lst from /boot/grub folder to your home folder for example. If that makes ubuntu to stop booting, just use the live desktop (Try Ubuntu option on the cd) and put the file back to /boot/grub. But this shouldn't happen.

---

### Post by tatmark1 on 2010-01-14
how do i can hdd boot order?

---

### Post by tatmark1 on 2010-01-14
and thanks again

---

### Post by darkod on 2010-01-14
Depending on your BIOS, when you go into it usually you need to look in Advanced BIOS options.
You have two types of settings. One type is for devices, like CD, HDD, USB, etc. In this setting usually you would set CD, HDD... That way it boots from hdd unless you have bootable disc in the optical drive.
In the other type of setting, usually close in the menu to the first one, out of all the hdds you have you select in what order they will be checked for bootloader. In this setting you want ubuntu drive, then windows drive.

If you have manual with the computer you can also look there. Some manufacturers would provide BIOS screenshots there.

---

### Post by tatmark1 on 2010-01-14
I switched the hard drive cables and it works. Thank you very much for your help.

---

