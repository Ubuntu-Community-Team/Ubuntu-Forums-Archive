---
title: "[SOLVED] After apt-get upgrade, grub no longer boots (intrepid ibex)"
date: 2008-11-15
forum: Installation &amp; Upgrades
---

### Post by jimmyfredrick on 2008-11-15
I upgraded from 8.04 LTS to 8.10 on the day of its release and everything went smoothly (booting was fine).

After performing my first apt-get upgrade it downloaded a new kernel and grub (along with others). The installation of these appeared fine, but upon a reboot I am greeted with a grub boot error:


```
GRUB loading stage 1.5

GRUB loading please wait
ERROR 16
```

I have googled this error thoroughly and cannot find a solution.

I have tried changing the LBA mode of the disk in the bios - this did not fix the issue.

I have tried booting into a live cd and fsck'ing the partitions - this did not fix the issue.

Some information about the disk/partitions:

```
root@livecd % fdisk -ul

Disk /dev/sda: 300.0 GB, 300069052416 bytes
255 heads, 63 sectors/track, 36481 cylinders, total 586072368 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   584203724   292101831   83  Linux
/dev/sda2       584203725   586067264      931770    5  Extended
/dev/sda5       584203788   586067264      931738+  82  Linux swap / Solaris

```

/dev/sda1 is EXT3 and is the / (root) partition, grub resides on this partition and grub is installed into the MBR of /dev/sda

here is my /boot/grub/menu.lst

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
default         0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout         10

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu
#

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
# kopt=root=/dev/sda1 acpi=off ro

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

title           Ubuntu 8.10, kernel 2.6.27-7-server
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.27-7-server root=/dev/sda1 acpi=off ro quiet splash
initrd          /boot/initrd.img-2.6.27-7-server
quiet

title           Ubuntu 8.10, kernel 2.6.27-7-server (recovery mode)
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.27-7-server root=/dev/sda1 acpi=off ro  single
initrd          /boot/initrd.img-2.6.27-7-server

title           Ubuntu 8.10, kernel 2.6.24-19-server
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.24-19-server root=/dev/sda1 acpi=off ro quiet splash
initrd          /boot/initrd.img-2.6.24-19-server
quiet

title           Ubuntu 8.10, kernel 2.6.24-19-server (recovery mode)
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.24-19-server root=/dev/sda1 acpi=off ro  single
initrd          /boot/initrd.img-2.6.24-19-server

title           Ubuntu 8.10, kernel 2.6.22-14-server
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.22-14-server root=/dev/sda1 acpi=off ro quiet splash
initrd          /boot/initrd.img-2.6.22-14-server
quiet

title           Ubuntu 8.10, kernel 2.6.22-14-server (recovery mode)
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.22-14-server root=/dev/sda1 acpi=off ro  single
initrd          /boot/initrd.img-2.6.22-14-server

title           Ubuntu 8.10, memtest86+
root            (hd0,0)
kernel          /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

```

From the livecd I re-ran grub-install, verified my /boot/grub/menu.lst and even installed grub manually:

```
root@livecd % mkdir /mnt/system
root@livecd % mount /dev/sda1 /mnt/system
root@livecd % mount --bind /dev /mnt/system/dev
root@livecd % mount --bind /proc /mnt/system/proc
root@livecd % chroot /mnt/system /bin/bash
root@livecd % sudo /usr/sbin/grub

grub> root (hd0,0)

grub> find /boot/grub/stage2
 (hd0,0)

grub> setup (hd0)
 Checking if "/boot/grub/stage1" exists... yes
 Checking if "/boot/grub/stage2" exists... yes
 Checking if "/boot/grub/e2fs_stage1_5" exists... yes
 Running "embed /boot/grub/e2fs_stage1_5 (hd0)"...  16 sectors are embedded.
succeeded
 Running "install /boot/grub/stage1 (hd0) (hd0)1+16 p (hd0,0)/boot/grub/stage2
/boot/grub/menu.lst"... succeeded
Done.

grub> quit

root@livecd % exit
root@livecd % umount /mnt/system/proc
root@livecd % umount /mnt/system/dev
root@livecd % umount /mnt/system
root@livecd % reboot
```

This also, had no affect on the problem.

What is really bugging me about this is that all my research points to a hardware error or a bios setting yet the machine was booting just fine minutes before the apt-get upgrade and I can successfully mount the hard drive with no errors.

Anyone have any ideas ?

---

### Post by meierfra. on 2008-11-15
> GRUB loading stage 1.5

GRUB loading please wait
ERROR 16

This is an error message from stage1.5. So grub never reaches stage2 and hence neither tries to access the kernel.  So I doubt that your problem has anything to do with your kernel update. 


Grub error 16 is often caused by bad or loose cables. So I suggest to check out your cables.

Try another file system check:

```
sudo e2fsck -fy /dev/sda1
```

Could you also post the output of

```
sudo grub
```

and at the grub prompt:

```
blocklist (hd0,0)/boot/grub/stage2
```


Since grub cannot access stage2 you might also try to reinstall the stage2 files:

Chroot into /dev/sda1 just as you did to reinstall grub. Then

```
apt-get purge grub
apt-get install grub
grub-install --recheck /dev/sda
```

(This assumes that you have internet access in the chroot environment. If not, just try the last line.)

---

### Post by jimmyfredrick on 2008-11-15
Thanks for your reply but there has been some minor progress, and I am unable to try your instructions. Here are the details..

I removed (dpkg -r) grub_0.97-29ubuntu45.1_i386.deb and installed the original grub_0.97-29ubuntu21.1_i386.deb. Upon reboot I now receive grub boot error 18!

Googling this shows its a disk geometry issue which can be fixed by manually entering the C/H/S of the disk in the BIOS - this is where it gets interesting.

When set to auto detect, my BIOS only reports a 136GB disk when it is really 300GB (very old machine). As far as I know this has always been the case and it never used to stop grub from booting until now. When I set everything to manual and enter the C/H/S it correctly reports the drive as 300GB but when I reboot it loses these settings and reverts to 136GB. I am assuming grub can't read stage2 because of this.

After much fiddling around, I concluded that I would be better off creating a seperate /boot at the beginning of my disk so grub will not get confused about my disk geometry. Im using partimage to backup my data and restore it to the new partitions (sda1 as /boot and sda2 as /).

I will post again whether or not this yields success

---

### Post by jimmyfredrick on 2008-11-17
I can happily say this has fixed my issue.

What I did:

1. backup my partition with partimage, saving to a network drive.
2. delete partitions and start over with /dev/sda1 as /boot (150mb), /dev/sda2 as / and /dev/sda3 as swap.
3. use partimage to restore image to /dev/sda2 (it auto grows the fs to fill partition)
4. using my live cd (system rescue cd) I copied the contents of /boot from /dev/sda2 onto /dev/sda1.
5. edited /etc/fstab to include the new /dev/sda1 /boot partition and updated /boot/grub/menu.lst to reflect new root and file locations.
6. ran grub-update --no-floppy --recheck /dev/sda
7. rebooted
8. success!

---

