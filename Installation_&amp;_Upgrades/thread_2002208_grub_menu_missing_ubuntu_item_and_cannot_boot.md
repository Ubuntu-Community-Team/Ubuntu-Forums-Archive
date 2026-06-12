---
title: "grub menu missing ubuntu item and cannot boot"
date: 2012-06-12
forum: Installation &amp; Upgrades
---

### Post by chentaocuc on 2012-06-12
[SIZE="4"]Hello!
I am using ubuntu 10.04 LTS.
Now I cannot boot. The grub menu missing ubuntu item, remaining only test memory.
How to fix this problem?[/SIZE]

---

### Post by wilee-nilee on 2012-06-12
> **chentaocuc said:**
> [SIZE=4]Hello!
I am using ubuntu 10.04 LTS.
Now I cannot boot. The grub menu missing ubuntu item, remaining only test memory.
How to fix this problem?[/SIZE]

Sounds like you have used the grub customizer is this correct? Or some grub tweaker let us know if and what it is if you have. In other words what got you here.

Run this command set from a booted ubuntu live cd. In home will be a results.txt copy and paste all the text from it to a reply.

While the reply is still open highlight all the text and click on the # in the reply panel, then submit reply.
```
wget -O bootinfoscript 'http://bootinfoscript.git.sourceforge.net/git/gitweb.cgi?p=bootinfoscript/bootinfoscript;a=blob_plain;f=bootinfoscript;hb=HEAD'
chmod a+x bootinfoscript
sudo bash bootinfoscript
```

---

### Post by chentaocuc on 2012-06-12
> **wilee-nilee said:**
> Sounds like you have used the grub  customizer is this correct? Or some grub tweaker let us know if and what  it is if you have. In other words what got you here.

Run this command set from a booted ubuntu live cd. In home will be a results.txt copy and paste all the text from it to a reply.

While the reply is still open highlight all the text and click on the # in the reply panel, then submit reply.
```
wget -O bootinfoscript  'http://bootinfoscript.git.sourceforge.net/git/gitweb.cgi?p=bootinfoscript/bootinfoscript;a=blob_plain;f=bootinfoscript;hb=HEAD'
chmod a+x bootinfoscript
sudo bash bootinfoscript
```
wilee-nilee,
The Linux system on my PC is Ubuntu 10.04 LTS 64-bit, the Grub 1.98.
I began to use Ubuntu 10.04 LTS 64-bit about two month ago. Everything  seems to be OK, until yesterday,  I used synaptic to update one package,  amd64-libc6. When the update finished, the PC rebooted  by itself and  enter a command-line mode, then I found there were a lot of errors  showed on the screen and the program stopped running. The last three  lines of errors are posted as follows:
[COLOR=Red]udevd[552]: can not read '/lib/udev/rules.d/keyboard-force-release'
udevd[552]: can not read '/lib/udev/rules.d/95-keymap.rules'
udevd[552]: can not read '/lib/udev/rules.d/95-udev-late.rules'[/COLOR]
I turned off the power as the PC stopped running anymore and restart the  PC, then the start menu of grub missed the Ubuntu item, remaining only  test memory. So, I can boot Ubuntu now.
At first, I tried some solutions on the forums, for example, install  grub from the LiveCD, modify the file /boot/grub/menu.lst, but all of  them didn't work.

I have followed you instruction to generate the RESULT.txt file, and post it as follows. 
```

------------------------------------------------------------------------------------------------------
RESULT.txt
                  Boot Info Script 0.61      [1 April 2012]


============================= Boot Info Summary: ===============================

 => Grub2 (v1.97-1.98 ) is installed in the MBR of /dev/sda and looks at sector 
    1 of the same hard drive for core.img. core.img is at this location and 
    looks in partition 8 for /boot/grub.
 => Windows is installed in the MBR of /dev/sdb.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /Boot/BCD

sda2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files:        /Windows/System32/winload.exe

sda3: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info: 

sda5: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Grub2 (v1.97-1.98 )
    Boot sector info:  Grub2 (v1.97-1.98 ) is installed in the boot sector of 
                       sda5 and looks at sector 1414131840 of the same hard 
                       drive for core.img. core.img is at this location and 
                       looks in partition 256 for /boot/grub. According to 
                       the info in the boot sector, sda5 starts at sector 63.
    Operating System:  
    Boot files:        

sda6: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  According to the info in the boot sector, sda6 starts 
                       at sector 2048.
    Operating System:  
    Boot files:        

sda7: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info: 

sda8: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Ubuntu 10.04.4 LTS
    Boot files:        /boot/grub/menu.lst /boot/grub/grub.cfg /etc/fstab 
                       /boot/grub/core.img

sda4: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  According to the info in the boot sector, sda4 has 
                       62916607 sectors, but according to the info from 
                       fdisk, it has 63069615 sectors.
    Operating System:  
    Boot files:        /bootmgr /boot/bcd

sdb1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  FAT16
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *          2,048       206,847       204,800   7 NTFS / exFAT / HPFS
/dev/sda2             206,896   211,431,464   211,224,569   7 NTFS / exFAT / HPFS
/dev/sda3         211,431,526 1,890,453,503 1,679,021,978   5 Extended
/dev/sda5         211,431,528   716,997,014   505,565,487   7 NTFS / exFAT / HPFS
/dev/sda6         717,010,944 1,331,410,943   614,400,000   7 NTFS / exFAT / HPFS
/dev/sda7       1,331,412,992 1,350,942,719    19,529,728  82 Linux swap / Solaris
/dev/sda8       1,350,944,768 1,890,453,503   539,508,736  83 Linux
/dev/sda4       1,890,455,552 1,953,525,167    63,069,616  12 Compaq diagnostics


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 530 MB, 530972672 bytes
255 heads, 63 sectors/track, 64 cylinders, total 1037056 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1    *             63     1,028,159     1,028,097   6 FAT16


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        8640073340072A0F                       ntfs       System Reserved
/dev/sda2        6E04096204092EA1                       ntfs       
/dev/sda4        30D4AEF0D4AEB80C                       ntfs       LENOVO_PART
/dev/sda5        204EF98A4EF958CC                       ntfs       
/dev/sda6        264205074204DE05                       ntfs       
/dev/sda7        939d7b99-dbce-499d-97d0-644f12e39e9a   swap       
/dev/sda8        53113478-2443-4097-9572-8b6eae277d48   ext4       
/dev/sdb1        BC27-24A0                              vfat       CHEN TAO

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sda8        /media/53113478-2443-4097-9572-8b6eae277d48 ext4       (rw,nosuid,nodev,uhelper=udisks)
/dev/sdb1        /media/CHEN TAO          vfat        (rw,nosuid,nodev,uhelper=udisks,uid=999,gid=999,shortname=mixed,dmask=0077,utf8=1,flush)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)


=========================== sda8/boot/grub/menu.lst: ===========================

--------------------------------------------------------------------------------
debug off
hiddenmenu
default 0
timeout 0
fallback 1

title      Ubuntu 10.04, kernel 2.6.32-34-generic
root      ()/ubuntu/disks
kernel      /boot/vmlinuz-2.6.32-34-generic  root=UUID=53113478-2443-4097-9572-8b6eae277d48  loop=/ubuntu/disks/root.disk ro quiet splash
initrd      /boot/initrd.img-2.6.28-12-generic

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title      Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title      Windows 7
rootnoverify   (hd0,0)
savedefault
chainloader   +1
--------------------------------------------------------------------------------

=========================== sda8/boot/grub/grub.cfg: ===========================

--------------------------------------------------------------------------------
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
set default="8"
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
set root='(hd0,8 )'
search --no-floppy --fs-uuid --set 53113478-2443-4097-9572-8b6eae277d48
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
set root='(hd0, 8 )'
search --no-floppy --fs-uuid --set 53113478-2443-4097-9572-8b6eae277d48
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
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd0,8 )'
    search --no-floppy --fs-uuid --set 53113478-2443-4097-9572-8b6eae277d48
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd0,8 )'
    search --no-floppy --fs-uuid --set 53113478-2443-4097-9572-8b6eae277d48
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###
--------------------------------------------------------------------------------

=============================== sda8/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/sda8       /               ext4    errors=remount-ro 0       1
/dev/sda7       none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sda8: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

 674.310634613 = 724.035530752  boot/grub/core.img                             1
 674.307628632 = 724.032303104  boot/grub/grub.cfg                             1
 674.383792877 = 724.114083840  boot/grub/menu.lst                             1
 646.546779633 = 694.224318464  boot/initrd                                    1
 646.561748505 = 694.240391168  boot/initrd.gz                                 1
 674.748901367 = 724.506116096  boot/vmlinuz                                   1

=============================== StdErr Messages: ===============================

mdadm: No arrays found in config file or automatically

```

---

### Post by drs305 on 2012-06-12
Let's try this quick attempt to boot from the Grub menu.

Press 'c' to get to the grub prompt, then:
```
set prefix=(hd0,8)/boot/grub
set root=(hd0,8)
linux (hd0,8)/vmlinuz root=/dev/sda8 ro
initrd (hd0,8)/initrd.img
boot
```

If it boots, try running 
```
sudo update-grub
```
and rerun the boot info script.

---

### Post by chentaocuc on 2012-06-12
> Let's try this quick attempt to boot from the Grub menu.

Press 'c' to get to the grub prompt, then:
Code:
set prefix=(hd0,8 )/boot/grub
set root=(hd0,8 )
linux (hd0,8 )/vmlinuz root=/dev/sda8 ro
initrd (hd0,8 )/initrd.img
boot
If it boots, try running 
Code:
sudo update-grub
and rerun the boot info script.
I have tried this method, it doesn't work.
First, I found that there was only memorytest.bin in (hd0,8 )/boot/. The file vmlinuz you see now was copied from LiveCD, and also the initrd.
After I copy the files from LiveCD, I tried the method you mentioned, the system began to boot, but also failed to boot, terminated by the error: 
[COLOR="Red"]ALERT! does not exist. Dropping to a shell.[/COLOR]

---

### Post by drs305 on 2012-06-12
> **chentaocuc said:**
> I have tried this method, it doesn't work.
First, I found that there was only memorytest.bin in (hd0,8 )/boot/. The file vmlinuz you see now was copied from LiveCD, and also the initrd.
After I copy the files from LiveCD, I tried the method you mentioned, the system began to boot, but also failed to boot, terminated by the error: 
[COLOR="Red"]ALERT! does not exist. Dropping to a shell.[/COLOR]


Copying the initrd image isn't going to work, as you discovered.

If you didn't have the kernel in /boot, you have more issues than just grub. If your system *only* needs to reinstall the kernel, we can do that via 'chrooting' into your installation from the LiveCD. If lots of other system files are missing this won't work.

If you want to try chrooting, the instructions are in the "Chroot" link in my signature line. You would mount and chroot into sda8. 

*Once in the chroot*, let's install the kernel AND purge/reinstall grub. In 'chroot' you don't need to use sudo since you are running the terminal as root:

```

apt-get update # Make sure your internet connection is working
apt-get install linux-image linux-headers-generic
apt-get purge grub-common # Don't run this if your internet is broken
apt-get install grub-pc # More information in the Purge/Reinstall chroot thread
```

Then continue with the chroot instructions for unmounting/exiting.

---

### Post by chentaocuc on 2012-06-12
Thank you very much for your help!
I have re-install the Ubuntu system at last last night.
I am so confused that why my system damaged and I have tried lots of methods posted on the forums, but all of them didn't work. Many errors displayed in the command-line mode, and I tried to write them down on the paper, but there so many, and I don't known how to post them on the forums.
I just wanted to update the amd64-libc6, but the result turned out to be system ruined. 
[COLOR="red"]How to avoid such mistakes next?[/COLOR]

---

### Post by drs305 on 2012-06-12
> **chentaocuc said:**
> 
[COLOR="red"]How to avoid such mistakes next?[/COLOR]

Often it's nothing that the user did. Despite widespread testing to ensure a reliable operating system there is no guarantee an update is going to work for every user.

You can help by using only 'official' or trusted repositories, and not running a command until you understand what it is going to do (if you don't, just ask on the UF).

I've found the best course for me is to keep all my data on a separate partition and to make a backup of the system when it is working correctly. There are a variety of backup apps and commands that can ensure you can restore your system to working order even when an update makes the system unusable. There are plenty of backup options available - just search these forums as I don't have a specific link handy.

---

