---
title: "[SOLVED] Boot hangs after creating a new /boot partition and upgrading to Intrepid"
date: 2008-11-01
forum: Installation &amp; Upgrades
---

### Post by bela83 on 2008-11-01
Hi everybody !

While upgrading to Intrepid, I did something I had long wanted to : I created a new partition (96 Mb ext2) for my /boot. I copy-pasted my old boot folder on the new partition, I upgraded and now I can't boot into my new system. The boot process hangs at 4 or 5 seconds, and I have no info. Please could you help me, I'm no newbie, I can boot on my computer using an old Knoppix Live CD, and I'm not afraid of the command-line :)

---

### Post by caljohnsmith on 2008-11-01
OK, how about first posting:
```
sudo fdisk -lu
```
For your main Ubuntu partition sdX (replace that with the actual partition):
```

sudo mkdir /mnt/Ubuntu
sudo mount /dev/sdX /mnt/Ubuntu
cat /mnt/Ubuntu/boot/grub/menu.lst
```
Also, for your /boot partition sdY:
```
sudo mkdir /mnt/Boot
sudo mount /dev/sdY /mnt/Boot
ls -lR /mnt/Boot
```
And lastly please post:
```
sudo blkid -c /dev/null
cat /mnt/Ubuntu/etc/fstab
```
And we can work from there. :)

---

### Post by bela83 on 2008-11-01
Thanks caljohnsmith for considering helping me !
I'm busy right now but I'll be back in 3 hours with the output of the commands...
Thanks again...

---

### Post by bela83 on 2008-11-01
> **caljohnsmith said:**
> OK, how about first posting:
```
sudo fdisk -lu
```
```
root@0[knoppix]# fdisk -lu

Disk /dev/hda: 40.0 GB, 40007761920 bytes
255 heads, 63 sectors/track, 4864 cylinders, total 78140160 sectors
Units = sectors of 1 * 512 = 512 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1              63      192779       96358+  83  Linux
/dev/hda2          192780    14329979     7068600   83  Linux
/dev/hda3        14329980    24370604     5020312+  83  Linux
/dev/hda4        24370605    78140159    26884777+   5  Extended
/dev/hda5        24370668    76565789    26097561   83  Linux
/dev/hda6        76565853    78140159      787153+  82  Linux swap / Solaris

```

> ```

sudo mkdir /mnt/Ubuntu
sudo mount /dev/sdX /mnt/Ubuntu
cat /mnt/Ubuntu/boot/grub/menu.lst
```


Note I have nothing in /boot but I backed up the old folder in /boot_old
```

root@0[knoppix]# cat /mnt/Ubuntu/**boot_old**/grub/menu.lst
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
default         0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout         2

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
# hiddenmenu

# Pretty colours
# color cyan/blue white/blue

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
# title         Windows 95/98/NT/2000
# root          (hd0,0)
# makeactive
# chainloader   +1
#
# title         Linux
# root          (hd0,1)
# kernel        /vmlinuz root=/dev/hda2 ro
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
# kopt=root=UUID=b412bf8d-bd1b-4f72-84d2-236d414c0c0e ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,2)

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

title           Ubuntu 8.04, kernel 2.6.24-19-generic
root            (hd0,1)
kernel          /boot/vmlinuz-2.6.24-19-generic root=UUID=b412bf8d-bd1b-4f72-84d2-236d414c0c0e ro
initrd          /boot/initrd.img-2.6.24-19-generic
quiet

title           Ubuntu 8.04, kernel 2.6.24-19-generic (recovery mode)
root            (hd0,1)
kernel          /boot/vmlinuz-2.6.24-19-generic root=UUID=b412bf8d-bd1b-4f72-84d2-236d414c0c0e ro single
initrd          /boot/initrd.img-2.6.24-19-generic

title           Ubuntu 8.04, kernel 2.6.22-15-generic
root            (hd0,1)
kernel          /boot/vmlinuz-2.6.22-15-generic root=UUID=b412bf8d-bd1b-4f72-84d2-236d414c0c0e ro quiet splash
initrd          /boot/initrd.img-2.6.22-15-generic
quiet

title           Ubuntu 8.04, kernel 2.6.22-15-generic (recovery mode)
root            (hd0,1)
kernel          /boot/vmlinuz-2.6.22-15-generic root=UUID=b412bf8d-bd1b-4f72-84d2-236d414c0c0e ro single
initrd          /boot/initrd.img-2.6.22-15-generic

title           Ubuntu 8.04, memtest86+
root            (hd0,1)
kernel          /boot/memtest86+.bin
quiet


### END DEBIAN AUTOMAGIC KERNELS LIST

```



> 
```
sudo mkdir /mnt/Boot
sudo mount /dev/sdY /mnt/Boot
ls -lR /mnt/Boot
```

```

root@0[knoppix]# ls -lR /mnt/Boot
/mnt/Boot:
total 14364
-rw-r--r--  1 root root 1029585 Oct 30 00:46 System.map-2.6.27-7-generic
-rw-r--r--  1 root root  507665 Oct 30 00:46 abi-2.6.27-7-generic
-rw-r--r--  1 root root   91364 Oct 30 00:46 config-2.6.27-7-generic
drwxr-xr-x  2 root root    1024 Nov  1 06:37 grub
-rw-r--r--  1 root root 2506714 Oct 31 15:20 initrd.img-2.6.22-14-generic
-rw-r--r--  1 root root 8121974 Oct 31 17:39 initrd.img-2.6.27-7-generic
drwx------  2 root root   12288 Oct 31 14:26 lost+found
-rw-r--r--  1 root root  124152 Sep 11 16:11 memtest86+.bin
-rw-r--r--  1 root root    1073 Oct 30 00:47 vmcoreinfo-2.6.27-7-generic
-rw-r--r--  1 root root 2244464 Oct 30 00:46 vmlinuz-2.6.27-7-generic

/mnt/Boot/grub:
total 173
-rw-r--r--  1 root root    197 Oct 31 15:20 default
-rw-r--r--  1 root root     15 Oct 31 15:20 device.map
-rw-r--r--  1 root root   8660 Oct 31 15:20 e2fs_stage1_5
-rw-r--r--  1 root root   8452 Oct 31 15:20 fat_stage1_5
-rw-r--r--  1 root root     15 Oct 31 15:20 installed-version
-rw-r--r--  1 root root   9152 Oct 31 15:20 jfs_stage1_5
-rw-r--r--  1 root root   4207 Nov  1 06:29 menu.lst
-rw-r--r--  1 root root   7860 Oct 31 15:20 minix_stage1_5
-rw-r--r--  1 root root  10132 Oct 31 15:20 reiserfs_stage1_5
-rw-r--r--  1 root root    512 Oct 31 15:20 stage1
-rw-r--r--  1 root root 110292 Oct 31 15:20 stage2
-rw-r--r--  1 root root   9980 Oct 31 15:20 xfs_stage1_5

/mnt/Boot/lost+found:
total 0


```
> And lastly please post:
```
sudo blkid -c /dev/null
cat /mnt/Ubuntu/etc/fstab
```
And we can work from there. :)

```

root@0[knoppix]# blkid -c /dev/null
/dev/hda1: UUID="8999fa39-30c2-497d-8018-05f8f6e1fed8" TYPE="ext2"
/dev/hda2: UUID="b412bf8d-bd1b-4f72-84d2-236d414c0c0e" SEC_TYPE="ext2" TYPE="ext3"
/dev/hda3: UUID="24fa1d40-15c3-4660-80f5-10a28e1570cf" SEC_TYPE="ext2" TYPE="ext3"
/dev/hda5: UUID="60a49342-af34-412b-afe8-92bfdf360cbe" SEC_TYPE="ext2" TYPE="ext3"
/dev/hda6: UUID="1cec4494-fe2e-4a92-83b9-baac9a9d235b" TYPE="swap"
/dev/cloop: TYPE="iso9660"


```
```

root@0[knoppix]# cat /mnt/Ubuntu/etc/fstab
# /etc/fstab: static file system information.
#
# <file system>                  <mount point>     <type>    <options>                <dump>  <pass>

proc                                       /proc   proc       defaults                       0     0

# /dev/sda1
UUID=8999fa39-30c2-497d-8018-05f8f6e1fed8  /boot   ext2       defaults,relatime              0     2

# /dev/sda2
UUID=b412bf8d-bd1b-4f72-84d2-236d414c0c0e  /       ext3  defaults,errors=remount-ro,relatime 0     1

# /dev/sda3
UUID=24fa1d40-15c3-4660-80f5-10a28e1570cf  /home   ext3       nodev,nosuid,relatime          0     2

# /dev/sda5
UUID=60a49342-af34-412b-afe8-92bfdf360cbe  /media/stockage ext3 noexec,relatime              0     2

# /dev/sda6
UUID=1cec4494-fe2e-4a92-83b9-baac9a9d235b  none    swap       sw                             0     0

/dev/scd0                                  /media/cdrom0   udf,iso9660   user,noauto,exec    0     0

################################# MEDIAS AMOVIBLES #################################################
# /dev/sdx5
UUID=32e73f41-94f0-4350-b6fc-5d6b20bb00c8 /media/dd_externe1   ext3   users,noauto,relatime  0     0

# /dev/sdx6
UUID=50021345-2063-49b0-8f2d-4fdb5df8b3b9 /media/dd_externe2   ext3   users,noauto,relatime  0     0

# /dev/sdx7
UUID=22a2c58e-e877-471a-b271-bbe2d75c7e31  /media/dd_externe3  ext3   users,noauto,relatime  0     0

# /dev/sdx8
UUID=2163B13C20009036  /media/dd_externe4  ntfs-3g   users,noauto,dmask=000,fmask=111        0     0

# /dev/sdx9
UUID=6B0797746F887BB6  /media/dd_externe5  ntfs-3g   users,noauto,dmask=000,fmask=111        0     0

# /dev/sdy1
UUID=F81B-3D35   /media/cle   vfat  users,noauto                                             0     0

# /dev/sdz2
UUID=4955-B286   /media/IPOD  vfat  users,noauto                                             0     0



```

---

### Post by caljohnsmith on 2008-11-01
OK, since you moved your /boot directory over to the sda1 /boot partition, you should move /boot in your main Ubuntu sda2 partition to a backup directory so you can mount the sda1 partition on /boot:
```
sudo mount /dev/sda2 /mnt
sudo mv /mnt/boot /mnt/boot.backup
sudo mkdir /mnt/boot
sudo mount /dev/sda1 /mnt/boot
gksudo gedit /mnt/boot/grub/menu.lst
```
in your menu.lst, first change the line that has "# groot=(hd0,2)" to be:
```
# groot=(hd0,0)
```
Save and quit gedit, next do:
```

sudo mount --bind /dev /mnt/dev
sudo mount --bind /proc /mnt/proc
sudo chroot /mnt /bin/bash
update-grub
exit

```
Next check your menu.lst and see if you have the following Ubuntu entry:
```
title           Ubuntu, kernel 2.6.27-7-generic
root            [COLOR="Red"](hd0,0)[/COLOR]
kernel          /vmlinuz-2.6.27-7-generic root=UUID=b412bf8d-bd1b-4f72-84d2-236d414c0c0e ro quiet splash
initrd          /initrd.img-2.6.27-7-generic
quiet
```
It might be that the update-grub script will use UUIDs instead of (hd0,0), so if it does, it should look like:
```
title           Ubuntu, kernel 2.6.27-7-generic
[COLOR="Red"]uuid            8999fa39-30c2-497d-8018-05f8f6e1fed8[/COLOR]
kernel          /vmlinuz-2.6.27-7-generic root=UUID=b412bf8d-bd1b-4f72-84d2-236d414c0c0e ro quiet splash
initrd          /initrd.img-2.6.27-7-generic
quiet
```
Note there should be no /boot in front of the kernel/initrd lines, so make sure it's not:
```
title           Ubuntu, kernel 2.6.27-7-generic
root            (hd0,0)
kernel          [COLOR="Red"]/boot[/COLOR]/vmlinuz-2.6.27-7-generic root=UUID=b412bf8d-bd1b-4f72-84d2-236d414c0c0e ro quiet splash
initrd          [COLOR="Red"]/boot[/COLOR]/initrd.img-2.6.27-7-generic
quiet
```
Next reinstall Grub to the MBR and have it point to your new boot partition:
```
sudo grub
grub> root (hd0,0)
grub> setup (hd0)
grub> quit
```
And I think you should be all set. Reboot, and let me know if you run into any problems. Otherwise let me know how it goes. :)

---

### Post by bela83 on 2008-11-01
Thanks ! I don't understand though your first advice, I already moved the old folder to /boot_old. May I skip this point ?

And also for the second point this is already (hd0,0). I go on...

---

### Post by bela83 on 2008-11-01
Bad news... Still not booting. So I think it's not a Grub problem... In fact, the boot sequence hangs after prompting 
```
Begin: Running /scripts/local-premount...
Begin: Waiting for resume device...
```

---

### Post by caljohnsmith on 2008-11-01
Yes, it does sound like that may be a booting problem with Intrepid and not a Grub problem. Can you boot some of your older Hardy kernels from the grub menu? Also, if you feel like posting the menu.lst from your /boot sda1 partition, I could look it over in case we missed something.

---

### Post by bela83 on 2008-11-01
This is the point, I was playing in Synaptic and I removed some linux-2.6.24... packages (not the base but the restricted or something like that). So I played with fire and I burnt ! I have to say I have no excuse...
When I tried to boot the 2.6.24 kernel, I got to the desktop and the system freezed before I could do anything.
Anyway here's the menu.lst :
```
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
timeout		2

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
hiddenmenu

# Pretty colours
color cyan/blue white/blue

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
# kopt=root=UUID=b412bf8d-bd1b-4f72-84d2-236d414c0c0e ro quiet splash

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,0)

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

title		Ubuntu 8.10, kernel 2.6.27-7-generic
root		(hd0,0)
kernel		/vmlinuz-2.6.27-7-generic root=UUID=b412bf8d-bd1b-4f72-84d2-236d414c0c0e ro quiet splash quiet splash 
initrd		/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
root		(hd0,0)
kernel		/vmlinuz-2.6.27-7-generic root=UUID=b412bf8d-bd1b-4f72-84d2-236d414c0c0e ro quiet splash  single
initrd		/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
root		(hd0,0)
kernel		/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

```

---

### Post by caljohnsmith on 2008-11-01
OK, how about doing this to install another kernel:
```
sudo mount /dev/sda2 /mnt
sudo mount /dev/sda1 /mnt/boot
sudo mount --bind /dev /mnt/dev
sudo mount --bind /proc /mnt/proc
sudo mount --bind /sys /mnt/sys
sudo chroot /mnt /bin/bash
apt-get install linux-headers-2.6.24-21-generic linux-image-2.6.24-21-generic linux-restricted-modules-2.6.24-21-generic linux-ubuntu-modules-2.6.24-21-generic
update-grub
exit
```
Then check your menu.lst to make sure it has the new kernel listed and everything is in order:
```
cat /mnt/boot/grub/menu.lst
```
Let me know how that goes.

---

### Post by bela83 on 2008-11-01
OK, I'm so glad you help me ! This "chroot" thing is just amazing. In fact, correct me if I'm wrong, it's as if I were in my system at the command-line ?
I did what you suggested and here's the answer 
```
root@Knoppix:/# apt-get install linux-headers-2.6.24-21-generic linux-image-2.6.24-21-generic linux-restricted-modules-2.6.24-21-generic linux-ubuntu-modules-2.6.24-21-generic
Reading package lists... Done
Building dependency tree
Reading state information... Done
Package linux-headers-2.6.24-21-generic is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package linux-headers-2.6.24-21-generic has no installation candidate

```
Did I forget to say I had played with my /etc/apt/sources.list ? But I'm surprised though, cause I thought I had put things back in order...

---

### Post by bela83 on 2008-11-01
```

root@Knoppix:/# apt-get update
Hit http://fr.archive.ubuntu.com intrepid Release.gpg
Hit http://fr.archive.ubuntu.com intrepid-updates Release.gpg
Hit http://fr.archive.ubuntu.com intrepid-security Release.gpg
Hit http://fr.archive.ubuntu.com intrepid-proposed Release.gpg
Hit http://fr.archive.ubuntu.com intrepid Release
Hit http://fr.archive.ubuntu.com intrepid-updates Release
Hit http://fr.archive.ubuntu.com intrepid-security Release
Hit http://fr.archive.ubuntu.com intrepid-proposed Release
Hit http://fr.archive.ubuntu.com intrepid/main Packages
Hit http://fr.archive.ubuntu.com intrepid/restricted Packages
Hit http://fr.archive.ubuntu.com intrepid/universe Packages
Hit http://fr.archive.ubuntu.com intrepid/multiverse Packages
Hit http://fr.archive.ubuntu.com intrepid-updates/main Packages
Hit http://fr.archive.ubuntu.com intrepid-updates/restricted Packages
Hit http://fr.archive.ubuntu.com intrepid-updates/universe Packages
Hit http://fr.archive.ubuntu.com intrepid-updates/multiverse Packages
Hit http://fr.archive.ubuntu.com intrepid-security/main Packages
Hit http://fr.archive.ubuntu.com intrepid-security/restricted Packages
Hit http://fr.archive.ubuntu.com intrepid-security/universe Packages
Hit http://fr.archive.ubuntu.com intrepid-security/multiverse Packages
Hit http://fr.archive.ubuntu.com intrepid-proposed/main Packages
Hit http://fr.archive.ubuntu.com intrepid-proposed/restricted Packages
Hit http://fr.archive.ubuntu.com intrepid-proposed/universe Packages
Hit http://fr.archive.ubuntu.com intrepid-proposed/multiverse Packages
Reading package lists... Done

```

---

### Post by bela83 on 2008-11-01
Should I revert my repos to hardy to ensure I can install this old kernel ?
Edit : I'm trying !

---

### Post by caljohnsmith on 2008-11-01
Yes, you could revert your sources.list (repos) back to Hardy, and I think that would solve the problem of installing those kernel packages. But I'm wondering if that 2.6.24-21 kernel is not available in Intrepid for a good reason; I don't know at this point. Another option is to download those 4 kernel packages from packages.ubuntu.com, and then install them with "dpkg -i <packages>.deb" instead of going through the repos. Let me know if you need more specifics, but that's the general idea. :)

---

### Post by bela83 on 2008-11-01
It works !! I mean the old kernel works so I'm back on my machine. So it's partly solved cause there's this new kernel 2.6.27 still not working...
But thanks anyway ! Do a "apt-get install" through a "chroot" is so... new to me ! And instructive of course :)

---

### Post by caljohnsmith on 2008-11-01
That's great news the old kernel works for you. And I agree, that "chroot" trick can really come in handy, because if you set up the environment right first by mounting some of the system directories (/dev, /proc, etc), then chrooting into your Ubuntu partition is basically like booting into it. 

And just for my own information, after you ran the "update-grub" after post #5, how accurate was your menu.lst? Did it get the kernel/initrd lines right about not having the /boot directory in front of them? Were there any other problems? And did the update-grub make a "uuid" line rather than the "root (hd0,0)" line? It would help me to know since I'm not yet running the Intrepid version of Grub. :)

---

### Post by bela83 on 2008-11-01
> **caljohnsmith said:**
> 
And just for my own information, after you ran the "update-grub" after post #5, how accurate was your menu.lst?
Quite good !
>  Did it get the kernel/initrd lines right about not having the /boot directory in front of them?
Yes there was no /boot in front of them.
>  Were there any other problems? And did the update-grub make a "uuid" line rather than the "root (hd0,0)" line? 
No it made the "root (hd0,0)" line, just like before. Grub is supposed to adopt the uuid too ?
> It would help me to know since I'm not yet running the Intrepid version of Grub. :)
Glad I can help back !

---

