---
title: "Restoring GRUB"
date: 2008-05-09
forum: Installation &amp; Upgrades
---

### Post by Archel on 2008-05-09
Greetings,
I recently installed Ubuntu 8.04 and everything worked out fine. I was dual-booting with XP. Then one day Ubuntu decided to check the disk before booting and after that I got error 13 everytime I chose XP.

So I eliminated GRUB with FIXMBR and now it loads directly to XP. 

I want to either restore GRUB loader or add the Linux option to boot.ini somehow. I could use some help since the guides on google are pretty cryptic.

Thanks.

---

### Post by unutbu on 2008-05-09
Try this:

[http://www.dedoimedo.com/computers/grub.html#mozTocId928352](http://www.dedoimedo.com/computers/grub.html#mozTocId928352)

---

### Post by Pumalite on 2008-05-09
You can reinstall Grub:
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)
Or modify your boot.ini:
Boot from the LiveD.




 Mount your Windows partition:

Code:

sudo mount  -t ntfs-3g  /dev/sda2 /windows

(Here replace sda2 by whatever partition Windows is on)

 Copy the first sector of the Ubuntu partition to a file on the Windows partition:

Code:

sudo dd if=/dev/sda3 of=/windows/ubuntu.bin bs=512 count=1

(Be very careful when using "dd". Info on dd)

 Add ubuntu to the windows boot loader:

Open "boot.ini" from the Windows partition via
Code:

sudo gedit /windows/boot.ini

Add this line to the end of the file:
c:\ubuntu.bin="Ubuntu"

Save the file.

Reboot and you get should get a menu with a Windows and Ubuntu choice.
__________________

---

### Post by Archel on 2008-05-09
> **Pumalite said:**
> You can reinstall Grub:
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)
Or modify your boot.ini:
Boot from the LiveD.




 Mount your Windows partition:

Code:

sudo mount  -t ntfs-3g  /dev/sda2 /windows

(Here replace sda2 by whatever partition Windows is on)

 Copy the first sector of the Ubuntu partition to a file on the Windows partition:

Code:

sudo dd if=/dev/sda3 of=/windows/ubuntu.bin bs=512 count=1

(Be very careful when using "dd". Info on dd)

 Add ubuntu to the windows boot loader:

Open "boot.ini" from the Windows partition via
Code:

sudo gedit /windows/boot.ini

Add this line to the end of the file:
c:\ubuntu.bin="Ubuntu"

Save the file.

Reboot and you get should get a menu with a Windows and Ubuntu choice.
__________________

Apparently I'm getting problems trying to mount. When I type in: 
"sudo mount  -t ntfs-3g  /dev/sda2 /windows"

I get a huge list of all the mount commands.

---

### Post by Reg Editor on 2008-05-09
Here's a link to the method i used to fix the problem
[http://www.howtogeek.com/howto/ubuntu/reinstall-ubuntu-grub-bootloader-after-windows-wipes-it-out/](http://www.howtogeek.com/howto/ubuntu/reinstall-ubuntu-grub-bootloader-after-windows-wipes-it-out/)

---

### Post by Pumalite on 2008-05-09
You may have to make the dir first:
sudo mkdir /windows

---

### Post by Archel on 2008-05-10
> **Pumalite said:**
> You may have to make the dir first:
sudo mkdir /windows

This made it work but when I rebooted it went straight to XP. I went into C: and found the ubuntu.bin and the boot.ini modified but for some reason it did not work.

---

### Post by Pumalite on 2008-05-10
Ubuntu's Grub is a better boot loader.

---

### Post by Archel on 2008-05-15
Just re-installed GRUB. I get the same error when I try to boot windows.

---

### Post by unutbu on 2008-05-15
Please post your menu.lst.

And just to double check: Currently you can boot into Ubuntu fine, but you get GRUB error 13 when you try to boot Windows?

---

### Post by Archel on 2008-05-15
```
#
# Sample boot menu configuration file
#

# Boot automatically after 30 secs.
timeout 30

# By default, boot the first entry.
default 0

# Fallback to the second entry.
fallback 1

# For booting GNU (also known as GNU/Hurd)
title  GNU (also known as GNU/Hurd)
root   (hd0,0)
kernel /boot/gnumach.gz root=device:hd0s1
module /hurd/ext2fs.static --multiboot-command-line=${kernel-command-line} --host-priv-port=${host-port} --device-master-port=${device-port} --exec-server-task=${exec-task} -T typed ${root} $(task-create) $(task-resume)
module /lib/ld.so.1 /hurd/exec $(exec-task=task-create)

# For booting GNU/Linux
title  GNU/Linux
root (hd1,0)
kernel /vmlinuz root=/dev/hdb1
#initrd /initrd.img

# For booting GNU/kFreeBSD
title  GNU/kFreeBSD
root   (hd0,2,a)
kernel /boot/loader.gz

# For booting GNU/kNetBSD
title  GNU/kNetBSD
root   (hd0,2,a)
kernel --type=netbsd /boot/knetbsd.gz

# For booting Mach (getting kernel from floppy)
title  Utah Mach4 multiboot
root   (hd0,2)
pause  Insert the diskette now!!
kernel (fd0)/boot/kernel root=hd0s3
module (fd0)/boot/bootstrap

# For booting FreeBSD
title  FreeBSD
root   (hd0,2,a)
kernel /boot/loader

# For booting NetBSD
title  NetBSD
root   (hd0,2,a)
kernel --type=netbsd /netbsd

# For booting OpenBSD
title  OpenBSD
root   (hd0,2,a)
kernel --type=netbsd /bsd

# For booting OS/2
title OS/2
root  (hd0,1)
makeactive
# chainload OS/2 bootloader from the first sector
chainloader +1
# This is similar to "chainload", but loads a specific file
#chainloader /boot/chain.os2

# For booting Windows NT or Windows95
title Windows NT / Windows 95 boot menu
rootnoverify (hd0,0)
makeactive
chainloader  +1
# For loading DOS if Windows NT is installed
# chainload /bootsect.dos

# For installing GRUB into the hard disk
title Install GRUB into the hard disk
root    (hd0,0)
setup   (hd0)

# Change the colors.
title Change the colors
color light-green/brown blink-red/blue
```

---

### Post by unutbu on 2008-05-15
Please post

```
sudo fdisk -l
```

---

### Post by Archel on 2008-05-16
> **unutbu said:**
> Please post

```
sudo fdisk -l
```

I run this from where? and why?

---

### Post by unutbu on 2008-05-16
Your menu.lst looks very complicated, and probably contains many boot stanza which are not going to work with your setup. Before we can comment on what you need to do to fix your menu.lst, we need to see what OSs you actually have on your system. The 

```
sudo fdisk -l
```

will produce output that looks something like this:
```
% sudo fdisk -l
Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x48000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1           7       56196   de  Dell Utility
/dev/sda2               8         660     5245222+   b  W95 FAT32
/dev/sda3   *         661       38536   304238970   83  Linux
/dev/sda4           38537       38913     3028252+   5  Extended
/dev/sda5           38537       38913     3028221   82  Linux swap / Solaris
```

Using info from this output we can at least start to guess what your menu.lst should look like.

It's good that you are careful. For more info on the command, read the man page

```
man sudo
man fdisk
```

To run the commands, go to Applications>Accessories>Terminal. Type the commands in the terminal window.

---

### Post by Archel on 2008-05-17
```
Disk /dev/sda: 60.0 GB, 60011642880 bytes
255 heads, 63 sectors/track, 7296 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xab1dab1d

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        6072    48773308+   7  HPFS/NTFS
/dev/sda2            6073        7227     9277537+  83  Linux
/dev/sda3            7228        7296      554242+  82  Linux swap / Solaris

```

---

### Post by unutbu on 2008-05-17
Archel, please boot your Ubuntu OS from the hard drive. Log in. Open a terminal and type

```
cat /boot/grub/menu.lst
```

Please post the output here. The menu.lst you posted is not the one you are actually using to boot your machine.

---

### Post by Archel on 2008-05-18
> **unutbu said:**
> Archel, please boot your Ubuntu OS from the hard drive. Log in. Open a terminal and type

```
cat /boot/grub/menu.lst
```

Please post the output here. The menu.lst you posted is not the one you are actually using to boot your machine.

```
default 0
timeout 10

title Ubuntu 8.04, kernel 2.6.24-16-generic
root (hd0,1)
kernel /boot/vmlinuz-2.6.24-16-generic root=UUID=7d7688bd-f44c-459b-8960-bbff6751b4a2 ro quiet splash
initrd /boot/initrd.img-2.6.24-16-generic
quiet

title Ubuntu 8.04, kernel 2.6.24-16-generic (recovery mode)
root (hd0,1)
kernel /boot/vmlinuz-2.6.24-16-generic root=UUID=7d7688bd-f44c-459b-8960-bbff6751b4a2 ro single
initrd /boot/initrd.img-2.6.24-16-generic

title Ubuntu 8.04, memtest86+
root (hd0,1)
kernel /boot/memtest86+.bin
quiet

title Other operating systems:
root 

title Microsoft Windows XP Professional
root (hd0,1)
chainloader +1
savedefault
makeactive
```

---

### Post by unutbu on 2008-05-18
Boot Ubuntu. Open a terminal. Type

```
gksudo gedit /boot/grub/menu.lst
```
Go to the bottom and change

```
title Microsoft Windows XP Professional
root (hd0,1)
chainloader +1
savedefault
makeactive
```

to

```
title Microsoft Windows XP Professional
root (hd0,**0**)
chainloader +1
savedefault
makeactive
```

(Change the 1 to a 0.)
Reboot, get to the GRUB menu, and you should be able to boot XP.

---

### Post by Archel on 2008-05-18
> **unutbu said:**
> Boot Ubuntu. Open a terminal. Type

```
gksudo gedit /boot/grub/menu.lst
```
Go to the bottom and change

```
title Microsoft Windows XP Professional
root (hd0,1)
chainloader +1
savedefault
makeactive
```

to

```
title Microsoft Windows XP Professional
root (hd0,**0**)
chainloader +1
savedefault
makeactive
```

(Change the 1 to a 0.)
Reboot, get to the GRUB menu, and you should be able to boot XP.

Thanks it finally solved my problem.

---

