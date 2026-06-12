---
title: "Oh oH Just installed ubuntu 7.10"
date: 2008-02-19
forum: Installation &amp; Upgrades
---

### Post by babybash on 2008-02-19
Hi Ive just installed ubuntu on my pc ive split the hard so i was supposed to be able to run windows if needed... i didnt have any probs for the first couple of hours untill i shut down the pc and tried to access windows xp then the probs started windows wouldnt boot, nor will it boot to safe mode or last know good config i cant even boot from the xp disc to try and repair the install im really at a bit of a loss.
When i first installed linux i could access the windows section of my hard drive through linux, now it just gives me this message (unable to mount volume) i could probably find a couple of error codes aswell but i will have to shut down and dont know if i dare lol!!!
Please please can anyone help oh i also need to not loose all my stuff on windows. Ahhhh i feel like such a tool lol.

---

### Post by PmDematagoda on 2008-02-19
I am not able to help much on the Windows problem, but I can help with the mount problem.

Post the output of:-
```
sudo fdisk -l
```
```
cat /etc/mtab
```
and
```
cat /etc/fstab
```

---

### Post by babybash on 2008-02-19
Ok im not too good at this!! i think you may need to run me through this step by step if you can as i know enough to be a hazard to my pc and not quite enough to repair it!!
I reckon if i can mount the xp partition i can retreve my photos ect!!

---

### Post by PmDematagoda on 2008-02-19
Yes, that is what I am trying to help you with:).

Just enter the commands I gave in a terminal which can be brought up through Applications>Accessories>Terminal, just post the outputs of the commands here:).

---

### Post by babybash on 2008-02-19
anthony@anthony-desktop:~$ sudo fdisk -1
[sudo] password for anthony:
thats the first one i know the password but it wont let me enter it.

The second one.
anthony@anthony-desktop:~$ cat /etc/mtab
/dev/sda2 / ext3 rw,errors=remount-ro 0 0
proc /proc proc rw,noexec,nosuid,nodev 0 0
/sys /sys sysfs rw,noexec,nosuid,nodev 0 0
varrun /var/run tmpfs rw,noexec,nosuid,nodev,mode=0755 0 0
varlock /var/lock tmpfs rw,noexec,nosuid,nodev,mode=1777 0 0
udev /dev tmpfs rw,mode=0755 0 0
devshm /dev/shm tmpfs rw 0 0
devpts /dev/pts devpts rw,gid=5,mode=620 0 0
lrm /lib/modules/2.6.22-14-generic/volatile tmpfs rw 0 0
securityfs /sys/kernel/security securityfs rw 0 0
anthony@anthony-desktop:~$ 

The third one.
anthony@anthony-desktop:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda2
UUID=fc8e48af-e821-4e80-9962-09b56a314187 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=b3dfe413-ce12-4efa-9215-49a3eca461ca none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/scd1       /media/cdrom1   udf,iso9660 user,noauto,exec 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0
anthony@anthony-desktop:~$

---

### Post by PmDematagoda on 2008-02-19
I need the output for the first command as well, and in any case you can enter the password in the terminal only you cannot see it. So just enter the password as normal and press Enter once done.

---

### Post by babybash on 2008-02-19
Hi got it this time lol. Thankyou for the patience.
anthony@anthony-laptop:~$ sudo fdisk -1
[sudo] password for anthony:
fdisk: invalid option -- 1

Usage: fdisk [-b SSZ] [-u] DISK     Change partition table
       fdisk -l [-b SSZ] [-u] DISK  List partition table(s)
       fdisk -s PARTITION           Give partition size(s) in blocks
       fdisk -v                     Give fdisk version
Here DISK is something like /dev/hdb or /dev/sda
and PARTITION is something like /dev/hda7
-u: give Start and End in sector (instead of cylinder) units
-b 2048: (for certain MO disks) use 2048-byte sectors
anthony@anthony-laptop:~$

---

### Post by PmDematagoda on 2008-02-19
Actually sudo fdisk -l is simple L not number 1. Can you please fix that and post the command again.

---

### Post by babybash on 2008-02-19
Yep i will do as soon as i get back on line my flat mate has decided to spill coke over the router so im at a friends house on the laptop, i will get onto it in an hour or so.
Thankyou once again

---

### Post by babybash on 2008-02-20
Ok ive run the whole thing again and i think i got it right this time lol.

anthony@anthony-desktop:~$ sudo fdisk -l
[sudo] password for anthony:

Disk /dev/sda: 120.0 GB, 120000000000 bytes
255 heads, 63 sectors/track, 14589 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x9dc96e9e

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9868    79264678+   7  HPFS/NTFS
/dev/sda2            9869       14389    36314932+  83  Linux
/dev/sda3           14390       14589     1606500    5  Extended
/dev/sda5           14390       14589     1606468+  82  Linux swap / Solaris
anthony@anthony-desktop:~$ cat /etc/mtab
/dev/sda2 / ext3 rw,errors=remount-ro 0 0
proc /proc proc rw,noexec,nosuid,nodev 0 0
/sys /sys sysfs rw,noexec,nosuid,nodev 0 0
varrun /var/run tmpfs rw,noexec,nosuid,nodev,mode=0755 0 0
varlock /var/lock tmpfs rw,noexec,nosuid,nodev,mode=1777 0 0
udev /dev tmpfs rw,mode=0755 0 0
devshm /dev/shm tmpfs rw 0 0
devpts /dev/pts devpts rw,gid=5,mode=620 0 0
lrm /lib/modules/2.6.22-14-generic/volatile tmpfs rw 0 0
securityfs /sys/kernel/security securityfs rw 0 0
anthony@anthony-desktop:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda2
UUID=fc8e48af-e821-4e80-9962-09b56a314187 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=b3dfe413-ce12-4efa-9215-49a3eca461ca none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/scd1       /media/cdrom1   udf,iso9660 user,noauto,exec 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0
anthony@anthony-desktop:~$

---

### Post by babybash on 2008-02-23
Please is  anyone helping me on this one..........

---

### Post by PmDematagoda on 2008-02-23
I am terribly sorry for replying late. 

Try this(Post any and all error messages you get):-

1) Make a new folder in the /media directory using:-
```
sudo mkdir /media/force
```

2) Mount the drive on the folder using:-
```
sudo ntfs-3g /dev/sda1 /media/force
```

---

### Post by babybash on 2008-02-23
Hi ive put in the commands and this is what its come up with...
anthony@anthony-desktop:~$ sudo mkdir /media/force
[sudo] password for anthony:
anthony@anthony-desktop:~$ sudo ntfs-3g /dev/sda1 /media/force
$LogFile indicates unclean shutdown (0, 1)
Failed to mount '/dev/sda1': Operation not supported
Mount is denied because NTFS is marked to be in use. Choose one action:

Choice 1: If you have Windows then disconnect the external devices by
          clicking on the 'Safely Remove Hardware' icon in the Windows
          taskbar then shutdown Windows cleanly.

Choice 2: If you don't have Windows then you can use the 'force' option for
          your own responsibility. For example type on the command line:

            mount -t ntfs-3g /dev/sda1 /media/force -o force

    Or add the option to the relevant row in the /etc/fstab file:

            /dev/sda1 /media/force ntfs-3g defaults,force 0 0
anthony@anthony-desktop:~$

---

### Post by PmDematagoda on 2008-02-23
Ok, now mount the Windows partition using:-
```
sudo ntfs-3g /dev/sda1 /media/force -o force
```
and after that open up fstab for editing using:-
```
gksudo gedit /etc/fstab
```
and add the following line:-
```
/dev/sda1 /media/sda1 ntfs-3g defaults 0 1
```
keep in mind that after you save the file you would have to create the sda1 folder in /media, do that using:-
```
sudo mkdir /media/sda1
```
That should solve the problem with the Windows partition not mounting at boot-up.

For your Windows problem, post the output of:-
```
cat /boot/grub/menu.lst
```

---

### Post by babybash on 2008-02-24
Hi thankyou, Ive posted everything i did and lisred it just so you can see if i did it right but i dont think i did, im going to reboot after this post to see if it has worked if it doesnt ill let you know, Thankyou so much for your help so far.
anthony@anthony-desktop:~$ sudo ntfs-3g /dev/sda1 /media/force -o force
[sudo] password for anthony:
$LogFile indicates unclean shutdown (0, 1)
WARNING: Forced mount, reset $LogFile.
anthony@anthony-desktop:~$ gksudo gedit /etc/fstab
/dev/sda1 /media/sda1 ntfs-3g defaults 0 1
anthony@anthony-desktop:~$ /dev/sda1 /media/sda1 ntfs-3g defaults 0 1
bash: /dev/sda1: Permission denied
anthony@anthony-desktop:~$ sudo mkdir /media/sda1
anthony@anthony-desktop:~$ 
anthony@anthony-desktop:~$ cat /boot/grub/menu.lst
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
# kopt=root=UUID=fc8e48af-e821-4e80-9962-09b56a314187 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,1)

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

title           Ubuntu 7.10, kernel 2.6.22-14-generic
root            (hd0,1)
kernel          /boot/vmlinuz-2.6.22-14-generic root=UUID=fc8e48af-e821-4e80-9962-09b56a314187 ro quiet splash
initrd          /boot/initrd.img-2.6.22-14-generic
quiet

title           Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root            (hd0,1)
kernel          /boot/vmlinuz-2.6.22-14-generic root=UUID=fc8e48af-e821-4e80-9962-09b56a314187 ro single
initrd          /boot/initrd.img-2.6.22-14-generic

title           Ubuntu 7.10, memtest86+
root            (hd0,1)
kernel          /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title           Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title           Microsoft Windows XP Home Edition
root            (hd0,0)
savedefault
makeactive
chainloader     +1

anthony@anthony-desktop:~$

---

### Post by PmDematagoda on 2008-02-24
> **babybash said:**
> 
anthony@anthony-desktop:~$ /dev/sda1 /media/sda1 ntfs-3g defaults 0 1
bash: /dev/sda1: Permission denied


About that, you have to insert that line to the document that is opened up and then save it.

---

### Post by PmDematagoda on 2008-02-24
About your Windows install, I honestly believe that you may have to reinstall it since the GRUB entry looks fine. But you could wait for someone else to offer help.

---

### Post by babybash on 2008-02-24
Hi i kinda figured i had to enter into the document so i did lol, i Can accsess the docs on windows now so im not that bothered but i cant rip my music from there to disc using serpentine is there anyhing i can do coz that and the pics are the only reason i want to access windows once i get them i will reformat the hard drive to all be linux!!
Thankyou for all your help i couldnt have sorted this without people like you, Thankyou.:popcorn::)

---

