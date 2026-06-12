---
title: "After Mint install Ubuntu won't boot gives file error"
date: 2007-09-28
forum: Installation &amp; Upgrades
---

### Post by mschilling on 2007-09-28
I had both Mint 3.0 and Ubuntu installed and running  along with XP on my laptop. After installing Mint 3.1 overtop of the older 3.0, both XP and Mint work fine, but Ubuntu starts booting and then gives a file system check error and stops booting before the desktop comes up. Do I have to reinstall Ubuntu to fix this problem? Thanks for any help.

Device Boot Start End Blocks Id System 
/dev/sda1 * 1 7944 63810148+ 7 HPFS/NTFS 
/dev/sda2 7945 8187 1951897+ 82 Linux swap / Solaris 
/dev/sda3 8188 8958 6193057+ 83 Linux 
/dev/sda4 8959 9687 5855692+ 83 Linux 
martin@martin-laptop:~$

sda3 is mint, and sda4 is ubuntu

---

### Post by Pumalite on 2007-09-28
Post(from Mint):
sudo fdisk -lu
cat /boot/grub/menu.lst

---

### Post by mschilling on 2007-09-28
ok, here it is


   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   127620359    63810148+   7  HPFS/NTFS
/dev/sda2       127620360   131524154     1951897+  82  Linux swap / Solaris
/dev/sda3       131524155   143910269     6193057+  83  Linux
/dev/sda4       143910270   155621654     5855692+  83  Linux
martin@martin-laptop:~$ cat /boot/grub/menu.lst

---

### Post by Pumalite on 2007-09-28
Where is the menu.lst?

---

### Post by mschilling on 2007-09-29
OK, I see this now:


   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   127620359    63810148+   7  HPFS/NTFS
/dev/sda2       127620360   131524154     1951897+  82  Linux swap / Solaris
/dev/sda3       131524155   143910269     6193057+  83  Linux
/dev/sda4       143910270   155621654     5855692+  83  Linux
martin@martin-laptop:~$ cat /boot/grub/menu.lst
# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
default         0

gfxmenu=/etc/grub/message.mint

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout         10

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
# kopt=root=/dev/sda3 ro

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

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery mode) single
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

## ## End Default Options ##

title           Linux Mint, kernel 2.6.20-15-generic
root            (hd0,2)
kernel          /boot/vmlinuz-2.6.20-15-generic root=/dev/sda3 ro quiet splash
initrd          /boot/initrd.img-2.6.20-15-generic
boot

title           Linux Mint, kernel 2.6.20-15-generic (recovery mode)
root            (hd0,2)
kernel          /boot/vmlinuz-2.6.20-15-generic root=/dev/sda3 ro single
initrd          /boot/initrd.img-2.6.20-15-generic
boot

title           Linux Mint, kernel memtest86+
root            (hd0,2)
kernel          /boot/memtest86+.bin 
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title           Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title           Windows NT/2000/XP (loader)
root            (hd0,0)
savedefault
makeactive
chainloader     +1


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda4.
title           Ubuntu, kernel 2.6.20-16-generic (on /dev/sda4)
root            (hd0,3)
kernel          /boot/vmlinuz-2.6.20-16-generic root=UUID=7afc0f45-1f5b-4d5c-9f62-f056fd714bed ro quiet splash 
initrd          /boot/initrd.img-2.6.20-16-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda4.
title           Ubuntu, kernel 2.6.20-16-generic (recovery mode) (on /dev/sda4)
root            (hd0,3)
kernel          /boot/vmlinuz-2.6.20-16-generic root=UUID=7afc0f45-1f5b-4d5c-9f62-f056fd714bed ro single 
initrd          /boot/initrd.img-2.6.20-16-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda4.
title           Ubuntu, kernel 2.6.20-15-generic (on /dev/sda4)
root            (hd0,3)
kernel          /boot/vmlinuz-2.6.20-15-generic root=UUID=7afc0f45-1f5b-4d5c-9f62-f056fd714bed ro quiet splash 
initrd          /boot/initrd.img-2.6.20-15-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda4.
title           Ubuntu, kernel 2.6.20-15-generic (recovery mode) (on /dev/sda4)
root            (hd0,3)
kernel          /boot/vmlinuz-2.6.20-15-generic root=UUID=7afc0f45-1f5b-4d5c-9f62-f056fd714bed ro single 
initrd          /boot/initrd.img-2.6.20-15-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda4.
title           Ubuntu, memtest86+ (on /dev/sda4)
root            (hd0,3)
kernel          /boot/memtest86+.bin  
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda4.
title           Linux Mint, kernel 2.6.20-15-generic (on /dev/sda3) (on /dev/sda4)
root            (hd0,3)
kernel          /boot/vmlinuz-2.6.20-15-generic root=UUID=c4e64726-41b0-4bbb-8b15-0fca91985fa2 ro quiet splash 
initrd          /boot/initrd.img-2.6.20-15-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda4.
title           Linux Mint, kernel 2.6.20-15-generic (recovery mode) (on /dev/sda3) (on /dev/sda4)
root            (hd0,3)
kernel          /boot/vmlinuz-2.6.20-15-generic root=UUID=c4e64726-41b0-4bbb-8b15-0fca91985fa2 ro single 
initrd          /boot/initrd.img-2.6.20-15-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda4.
title           Linux Mint, memtest86+ (on /dev/sda3) (on /dev/sda4)
root            (hd0,3)
kernel          /boot/memtest86+.bin  
savedefault
boot

martin@martin-laptop:~$

---

### Post by Pumalite on 2007-09-29
Try reinstalling Grub first: [http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

---

### Post by mschilling on 2007-09-29
I'll check into reintalling GRUB. I tried booting again and the error is "unable to resolve UUID...
it says to repair file system manually
then when I tried the suggested control D, it continued to boot normally into Ubuntu. I haven't tried rebooting to see if the problem is still there. What is the best strategy now that it has booted? Thanks for any help.

---

### Post by Pumalite on 2007-09-29
Eventually you will have to check the output of:
blkid
And compare it with the UUID's in:
cat /etc/fstab
Make the changes necessary, if any.
At this point I would consider myself lucky and leave it at that.

---

### Post by floke on 2007-09-29
At grub - press 'e' to edit your mint line - then delete the UUID and replace with /dev/hda (ol sda) whatever - eg /dev/sda3 - and press enter to return to menu to try - if it works then edit the /boot/grub/menu.list file to make change permanent.

---

### Post by mschilling on 2007-09-29
not sure if this new grub that mint installed is different, but typing e didn't do anything at the grub screen. is there another way to try deleting the uuid? the grub shows that long hex code when selecting ubuntu, and not mint.

---

### Post by Pumalite on 2007-09-29
What is the error message and where?

---

### Post by mschilling on 2007-09-29
The error message is : 
unable to resolve UUID...
it says to repair file system manually
This happens after the Ubuntu boot up progress bar gets about 1/3 the way.

---

### Post by Pumalite on 2007-09-29
See post # 8

---

### Post by mschilling on 2007-09-29
So are you suggesting that I shouldn't bother trying to fix it? Is it that difficult? If so, how about a fresh install of Ubuntu from CD? Would that be a guaranteed fix? I'd rather fix the uuid, and learn more about how the grub works. Is the uuid stored in the mbr of the hd?

---

### Post by Pumalite on 2007-09-29
No, I'm saying that you should fix it following my instructions in post # 8. It's quite easy.

---

### Post by mschilling on 2007-09-30
Great, now I see what you mean. Here are the two screens, and I see where the uuid is different. Where do I make the change and how do I save it?
[IMG]http://img.photobucket.com/albums/v415/mschilling/Screenshot3.png[/IMG]

---

### Post by Pumalite on 2007-09-30
First backup:
sudo cp /etc/fstab /etc/fstab.back
gksudo gedit /etc/fstab
Make the changes where it corresponds.
Save, exit, reboot.

---

### Post by MetalMusicAddict on 2007-09-30
Honestly as Mint created the issue I think this is a issue for [their forums]("http://linuxmint.com/forum"). At the very least this should be moved to the "Other OS" section.

---

### Post by raul_ on 2007-09-30
why don't you replace the UUID with the /dev/sdx lines?

---

### Post by mschilling on 2007-10-02
Thanks for the command lines Pumalite, that worked very easily. So the original file list is backed up with the first command? If it didn't work, I could then replace the file with the original, correct? Now I see the advantage to using the terminal, nice indeed!

---

### Post by Pumalite on 2007-10-02
You are welcome. Happy Ubuntuing!

---

