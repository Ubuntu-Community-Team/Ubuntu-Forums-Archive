---
title: "Grub doesn't recognize my Windows 7 partition - Ubuntu 10.10 Maverick User"
date: 2010-12-23
forum: Installation &amp; Upgrades
---

### Post by xionlander on 2010-12-23
Hi!! I recently have installed Ubuntu 10.10 Maverick Netbook Edition in my personal netbook. The thing is that I had installed Windows 7 in the hard disk drive so I decided to install Ubuntu alongside with it...
After the process of installation everything was cool but I hadn't the Grub working. I then pressed the Shift button during the booting process so I got the Grub menu but it didn't show the Windows 7 partition.
The Windows installation was not erased because its file system is present in Nautilus.
I have tried reinstalling the Grub a thousand times but nothing changes...
I have attached the results of the boot info script so you can have some info about my booting configuration.
I hope you really can help me...I will be very thankful. Any help will be appreciated  :)

---

### Post by karthick87 on 2010-12-23
**Results:**

```
============================= Boot Info Summary: ==============================

 => Grub1.97 is installed in the MBR of /dev/sda and looks at sector 
    1561578837 on boot drive #-42 for core.img, but core.img can not be found 
    at this location.

sda1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  Unknown
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/menu.lst /boot/grub/grub.cfg /etc/fstab 
                       /boot/grub/core.img

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /Windows/System32/winload.exe

sda3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *    115,687,424   306,440,191   190,752,768  83 Linux
/dev/sda2             206,848   115,686,852   115,480,005   7 HPFS/NTFS
/dev/sda3         306,442,238   312,580,095     6,137,858   5 Extended
/dev/sda5         306,442,240   312,580,095     6,137,856  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="7cbc126b-605a-46fa-ab2d-cdc83b2936a2" TYPE="ext4" 
/dev/sda2: UUID="F414E71E14E6E31A" TYPE="ntfs" 
/dev/sda5: UUID="ef09e135-8a03-4f19-a745-f88c7e3fdfb8" TYPE="swap" 

=============================== "mount" output: ===============================

/dev/sda1 on / type ext4 (rw,errors=remount-ro,commit=0)
proc on /proc type proc (rw,noexec,nosuid,nodev)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
none on /dev type devtmpfs (rw,mode=0755)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/jorge/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=jorge)


=========================== sda1/boot/grub/menu.lst: ===========================

# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-legacy-doc/.

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
timeout        3

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
hiddenmenu

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
# kopt=root=UUID=7cbc126b-605a-46fa-ab2d-cdc83b2936a2 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=7cbc126b-605a-46fa-ab2d-cdc83b2936a2

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

title        Ubuntu 10.10, kernel 2.6.35-24-generic
uuid        7cbc126b-605a-46fa-ab2d-cdc83b2936a2
kernel        /boot/vmlinuz-2.6.35-24-generic root=UUID=7cbc126b-605a-46fa-ab2d-cdc83b2936a2 ro quiet splash 
initrd        /boot/initrd.img-2.6.35-24-generic

title        Ubuntu 10.10, kernel 2.6.35-24-generic (recovery mode)
uuid        7cbc126b-605a-46fa-ab2d-cdc83b2936a2
kernel        /boot/vmlinuz-2.6.35-24-generic root=UUID=7cbc126b-605a-46fa-ab2d-cdc83b2936a2 ro  single
initrd        /boot/initrd.img-2.6.35-24-generic

title        Ubuntu 10.10, kernel 2.6.35-22-generic
uuid        7cbc126b-605a-46fa-ab2d-cdc83b2936a2
kernel        /boot/vmlinuz-2.6.35-22-generic root=UUID=7cbc126b-605a-46fa-ab2d-cdc83b2936a2 ro quiet splash 
initrd        /boot/initrd.img-2.6.35-22-generic

title        Ubuntu 10.10, kernel 2.6.35-22-generic (recovery mode)
uuid        7cbc126b-605a-46fa-ab2d-cdc83b2936a2
kernel        /boot/vmlinuz-2.6.35-22-generic root=UUID=7cbc126b-605a-46fa-ab2d-cdc83b2936a2 ro  single
initrd        /boot/initrd.img-2.6.35-22-generic

title        Chainload into GRUB 2
root        7cbc126b-605a-46fa-ab2d-cdc83b2936a2
kernel        /boot/grub/core.img

title        Ubuntu 10.10, memtest86+
uuid        7cbc126b-605a-46fa-ab2d-cdc83b2936a2
kernel        /boot/memtest86+.bin

title        Windows 7
root        (hd0,2) 
chainloader    +1

### END DEBIAN AUTOMAGIC KERNELS LIST

=========================== sda1/boot/grub/grub.cfg: ===========================

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
set root='(hd0,msdos1)'
search --no-floppy --fs-uuid --set 7cbc126b-605a-46fa-ab2d-cdc83b2936a2
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos1)'
search --no-floppy --fs-uuid --set 7cbc126b-605a-46fa-ab2d-cdc83b2936a2
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
menuentry 'Ubuntu, with Linux 2.6.35-24-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 7cbc126b-605a-46fa-ab2d-cdc83b2936a2
    linux    /boot/vmlinuz-2.6.35-24-generic root=UUID=7cbc126b-605a-46fa-ab2d-cdc83b2936a2 ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-24-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 7cbc126b-605a-46fa-ab2d-cdc83b2936a2
    echo    'Loading Linux 2.6.35-24-generic ...'
    linux    /boot/vmlinuz-2.6.35-24-generic root=UUID=7cbc126b-605a-46fa-ab2d-cdc83b2936a2 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 7cbc126b-605a-46fa-ab2d-cdc83b2936a2
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=7cbc126b-605a-46fa-ab2d-cdc83b2936a2 ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 7cbc126b-605a-46fa-ab2d-cdc83b2936a2
    echo    'Loading Linux 2.6.35-22-generic ...'
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=7cbc126b-605a-46fa-ab2d-cdc83b2936a2 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-22-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/11_Windows ###
menuentry “Windows 7&#8243; {
set root=(hd0,2)
chainloader +1
}
### END /etc/grub.d/11_Windows ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 7cbc126b-605a-46fa-ab2d-cdc83b2936a2
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 7cbc126b-605a-46fa-ab2d-cdc83b2936a2
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
if [ "x${timeout}" != "x-1" ]; then
  if keystatus; then
    if keystatus --shift; then
      set timeout=-1
    else
      set timeout=0
    fi
  else
    if sleep --interruptible 3 ; then
      set timeout=0
    fi
  fi
fi
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

=============================== sda1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/sda1       /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=ef09e135-8a03-4f19-a745-f88c7e3fdfb8 none            swap    sw              0       0

=================== sda1: Location of files loaded by Grub: ===================


  59.2GB: boot/grub/grub.cfg
  59.2GB: boot/grub/menu.lst
  59.2GB: boot/initrd.img-2.6.35-22-generic
  59.2GB: boot/initrd.img-2.6.35-24-generic
  59.2GB: boot/vmlinuz-2.6.35-22-generic
  59.2GB: boot/vmlinuz-2.6.35-24-generic
  59.2GB: initrd.img
  59.2GB: initrd.img.old
  59.2GB: vmlinuz
  59.2GB: vmlinuz.old
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda1

00000000  eb 63 90 00 00 00 00 00  00 00 00 00 00 00 00 00  |.c..............|
00000010  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
00000050  00 00 00 00 00 00 00 00  00 00 00 80 50 63 69 10  |............Pci.|
00000060  00 00 00 00 ff fa 90 90  f6 c2 80 75 02 b2 80 ea  |...........u....|
00000070  74 7c 00 00 31 c0 8e d8  8e d0 bc 00 20 fb a0 64  |t|..1....... ..d|
00000080  7c 3c ff 74 02 88 c2 52  bb 17 04 80 27 03 74 06  ||<.t...R....'.t.|
00000090  be 88 7d e8 1c 01 be 05  7c f6 c2 80 74 48 b4 41  |..}.....|...tH.A|
000000a0  bb aa 55 cd 13 5a 52 72  3d 81 fb 55 aa 75 37 83  |..U..ZRr=..U.u7.|
000000b0  e1 01 74 32 31 c0 89 44  04 40 88 44 ff 89 44 02  |..t21..D.@.D..D.|
000000c0  c7 04 10 00 66 8b 1e 5c  7c 66 89 5c 08 66 8b 1e  |....f..\|f.\.f..|
000000d0  60 7c 66 89 5c 0c c7 44  06 00 70 b4 42 cd 13 72  |`|f.\..D..p.B..r|
000000e0  05 bb 00 70 eb 76 b4 08  cd 13 73 0d f6 c2 80 0f  |...p.v....s.....|
000000f0  84 d0 00 be 93 7d e9 82  00 66 0f b6 c6 88 64 ff  |.....}...f....d.|
00000100  40 66 89 44 04 0f b6 d1  c1 e2 02 88 e8 88 f4 40  |@f.D...........@|
00000110  89 44 08 0f b6 c2 c0 e8  02 66 89 04 66 a1 60 7c  |.D.......f..f.`||
00000120  66 09 c0 75 4e 66 a1 5c  7c 66 31 d2 66 f7 34 88  |f..uNf.\|f1.f.4.|
00000130  d1 31 d2 66 f7 74 04 3b  44 08 7d 37 fe c1 88 c5  |.1.f.t.;D.}7....|
00000140  30 c0 c1 e8 02 08 c1 88  d0 5a 88 c6 bb 00 70 8e  |0........Z....p.|
00000150  c3 31 db b8 01 02 cd 13  72 1e 8c c3 60 1e b9 00  |.1......r...`...|
00000160  01 8e db 31 f6 bf 00 80  8e c6 fc f3 a5 1f 61 ff  |...1..........a.|
00000170  26 5a 7c be 8e 7d eb 03  be 9d 7d e8 34 00 be a2  |&Z|..}....}.4...|
00000180  7d e8 2e 00 cd 18 eb fe  47 52 55 42 20 00 47 65  |}.......GRUB .Ge|
00000190  6f 6d 00 48 61 72 64 20  44 69 73 6b 00 52 65 61  |om.Hard Disk.Rea|
000001a0  64 00 20 45 72 72 6f 72  0d 0a 00 bb 01 00 b4 0e  |d. Error........|
000001b0  cd 10 ac 3c 00 75 f4 c3  00 00 00 00 00 00 00 00  |...<.u..........|
000001c0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200

```

---

### Post by karthick87 on 2010-12-23
To restore Windows 7 ,you must first boot off your 7 installation DVD.When you get to the Regional settings, select your Location/Keyboard setting then click next. On the next page you must click on Repair your computer.On the next page, if it finds your Windows Vista/7 installation, make sure it is UNSELECTED before clicking next.Then click on Command prompt,

From there, type in the folowing,
```
bootrec.exe /fixboot
```
```
bootrec.exe /fixmbr
```
Now close the two windows and click Restart.

---

### Post by xionlander on 2010-12-23
Thanks for the quick answer...I was hoping not do that because I have a netbook as I said and I have no CD device...Windows 7 came installed with the netbook...I will try to find a way to get Windows 7 installed in a USB drive. If there is a suggestion for another solution to this problem I would love to hear it...Thanks again

---

### Post by karthick87 on 2010-12-23
Wait for another user for a better solution :)

---

### Post by xionlander on 2010-12-23
I will...thanks a lot for your time

---

### Post by garvinrick4 on 2010-12-23
If you had windows and then installed Ubuntu I do not know how you got ubuntu in sda1 and Windows in sda2
 and then grub-legacy and grub2 installed also when grub-legacy does not come with 10.10 and no boot files in Windows.
Is there anything else you should tell us?

---

### Post by xionlander on 2010-12-23
> **garvinrick4 said:**
> If you had windows and then installed Ubuntu I do not know how you got ubuntu in sda1 and Windows in sda2
 and then grub-legacy and grub2 installed also when grub-legacy does not come with 10.10 and no boot files in Windows.
Is there anything else you should tell us?

I had to use Advance Options during partitioning to install both operative system...that's maybe the reason for the sda1 and sda2 installations.
During re installation process of the Grub I have read some solutions where they suggested to try installing grub-legacy...
I also tried to "sudo apt-get install grub2" to see what can I get...
I truly don't know why I have no boot files in Windows...any suggestions?

---

### Post by garvinrick4 on 2010-12-23
> **xionlander said:**
> I had to use Advance Options during partitioning to install both operative system...that's maybe the reason for the sda1 and sda2 installations.
During re installation process of the Grub I have read some solutions where they suggested to try installing grub-legacy...
I also tried to "sudo apt-get install grub2" to see what can I get...
I truly don't know why I have no boot files in Windows...any suggestions?
It looks like Windows once had a boot partition that is now gone. Windows starts at 206,000 
and linux took over sda1 but behind windows on the drive nothing from 0 to 206,000. We have to 
go to a live cd and remove grub grub-common and grub2 then install a windows bootloader
 and install grub2 then install grub2 to mbr looking in sda1 for boot files.
Give me a minute to write code.
#Thanks for telling what happened sure makes easier.

---

### Post by garvinrick4 on 2010-12-23
In a live cd with internet connection. (ubuntu install cd using try ubuntu)

```
sudo apt-get install lilo
``````
sudo lilo -M /dev/sda
```will give errors ignore.
Now boot into windows to make sure she boots windows and then go back to live cd and rest of code.
```
 
[code]sudo mount /dev/sda1 /mnt
``````
sudo mount -o bind /dev /mnt/dev
``````
sudo mount -o bind /dev/pts /mnt/dev/pts
``````
sudo mount -o bind /proc /mnt/proc
``````
 sudo mount -o bind /sys /mnt/sys
``````
sudo cp /etc/resolv.conf /mnt/etc/resolv.conf
``````
sudo chroot /mnt
``````
apt-get purge grub grub-common grub-pc
``````
apt-get install grub-common grub-pc
``````
apt-get grub-install --recheck --root-directory=/mnt /dev/sda
``````
exit
``````
sudo umount /mnt/dev/pts
``````
sudo umount /mnt/dev
``````
sudo umount /mnt/proc
``````
sudo umount /mnt/sys
``````
sudo umount /mnt
``` (not a typo)
Boot into Ubuntu on HDD and
```
sudo update-grub
```[/code]Let me know might have to mnt/proc and mnt/dev and /dev/pts and /mnt/sys -do not think so in this situation.
Not a problem do your thing.

---

### Post by xionlander on 2010-12-24
> **garvinrick4 said:**
> In a live cd with internet connection. (ubuntu install cd using try ubuntu)

```
sudo apt-get install lilo
``````
sudo lilo -M /dev/sda
```will give errors ignore.
Now boot into windows to make sure she boots windows and then go back to live cd and rest of code.
```
 
[code]sudo mount /dev/sda1 /mnt
``````
sudo mount -o bind /dev /mnt/dev
``````
sudo mount -o bind /dev/pts /mnt/dev/pts
``````
sudo mount -o bind /proc /mnt/proc
``````
 sudo mount -o bind /sys /mnt/sys
``````
sudo cp /etc/resolv.conf /mnt/etc/resolv.conf
``````
sudo chroot /mnt
``````
apt-get purge grub grub-common grub-pc
``````
apt-get install grub-common grub-pc
``````
apt-get grub-install --recheck --root-directory=/mnt /dev/sda
``````
exit
``````
sudo umount /mnt/dev/pts
``````
sudo umount /mnt/dev
``````
sudo umount /mnt/proc
``````
sudo umount /mnt/sys
``````
sudo umount /mnt
``` (not a typo)
Boot into Ubuntu on HDD and
```
sudo update-grub
```[/code]Let me know might have to mnt/proc and mnt/dev and /dev/pts and /mnt/sys -do not think so in this situation.
Not a problem do your thing.

Sorry for answering quite late...I've tried what you said but without any results...even some errors came out... I had to reinstall all the OS and delete everything to start over. Thanks for all your support and quick answering...:)

---

### Post by garvinrick4 on 2010-12-24
Sorry it did not work for you most all the time you can purge and reinstall grub, disk starts at 206,000 but should not be a problem.
Never no I guess.

---

