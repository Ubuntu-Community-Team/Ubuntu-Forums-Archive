---
title: "Multi Boot problem"
date: 2007-10-25
forum: Installation &amp; Upgrades
---

### Post by scy1192 on 2007-10-25
If at any time I say something wrong, please correct me.

Running an x86...

So earlier I tied Ubuntu 7.04, and didn't like it. Just recently (Yesterday) I decided to give it another go and install it on my system, because I'd be safe if I multi-boot, right?

Well, I had Windows XP and Windows Vista set up in the Vista bootloader to dual boot. I install Ubuntu (everything goes smooth), and when I go to restart, Ubuntu loads by itself, giving me no option for Vista or XP. Reading some dual boot guides, I see this is not how it should go.

So I bring up the GRUB menu before it loads up, and sure enough all it has registered is Ubuntu.

I figure, no problem, I can reinstall the Vista bootloader and be on my way again. Vista didn't recognize its own bootloader was missing, so the repair option was a no. About to give up, I realise that all my files are safe and sound and weren't erased. "DRIVE COULD NOT BE MOUNTED". Great, all my stuff is inaccessible.

So what I need:

A way to reinstall the Vista bootoader, or modify GRUB to include my Vista and XP installations.

---

### Post by scy1192 on 2007-10-25
bump

I know you probably don't like me ditching your OS for Windows, but this is definitely going to leave a sour taste in my mouth if I can't do anything about it.

---

### Post by Pumalite on 2007-10-25
At the Terminal post:
sudo fdisk -lu

---

### Post by scy1192 on 2007-10-25
EDIT: I guess I didn't have a password, even tough I set one..
Disk /dev/sda: 61.4 GB, 61492838400 bytes
255 heads, 63 sectors/track, 7476 cylinders, total 120103200 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x143e654c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048    51202047    25600000    7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sda2        51202048   120101939    34449946    7  HPFS/NTFS

Disk /dev/sdb: 100.0 GB, 100030242816 bytes
255 heads, 63 sectors/track, 12161 cylinders, total 195371568 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x02d06120

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1              63    52291574    26145756    7  HPFS/NTFS
/dev/sdb2       118286595   195366464    38539935    7  HPFS/NTFS
/dev/sdb3   *    52291575   115475219    31591822+  83  Linux
/dev/sdb4       115475220   118286594     1405687+   5  Extended
/dev/sdb5       115475283   118286594     1405656   82  Linux swap / Solaris

Partition table entries are not in disk order
josh@josh-desktop:~$

---

### Post by Pumalite on 2007-10-25
Now we need:
cat /boot/grub/menu.lst

---

### Post by scy1192 on 2007-10-25
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
timeout         3

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
# kopt=root=UUID=5a6c780a-549a-467c-a8f4-29e54e95fe04 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd1,2)

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
root            (hd1,2)
kernel          /boot/vmlinuz-2.6.22-14-generic root=UUID=5a6c780a-549a-467c-a8f4-29e54e95fe04 ro quiet splash
initrd          /boot/initrd.img-2.6.22-14-generic
quiet

title           Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root            (hd1,2)
kernel          /boot/vmlinuz-2.6.22-14-generic root=UUID=5a6c780a-549a-467c-a8f4-29e54e95fe04 ro single
initrd          /boot/initrd.img-2.6.22-14-generic

title           Ubuntu 7.10, memtest86+
root            (hd1,2)
kernel          /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

---

### Post by cowrecked on 2007-10-25
> **scy1192 said:**
> So what I need:

A way to reinstall the Vista bootoader, or modify GRUB to include my Vista and XP installations.

1. Put the Windows Vista installation disc in the disc drive, and then start the computer.
2. Press a key when you are prompted.
3. Select a language, a time, a currency, a keyboard or an input method, and then click Next.
4. Click Repair your computer.
5. Click the operating system that you want to repair, and then click Next.
6. In the System Recovery Options dialog box, click Command Prompt.
7. Type Bootrec.exe /FixMbr, and then press ENTER.

This will restore the Vista boot manager to at least allow you to access your Vista OS

(from [http://quainttech.blogspot.com/2007/05/how-to-remove-ubuntu-from-vista-dual.html](http://quainttech.blogspot.com/2007/05/how-to-remove-ubuntu-from-vista-dual.html))

---

### Post by Pumalite on 2007-10-25
Backup first:
sudo cp /boot/grub/menu.lst /boot/grub/menu.lst.back, then
gksudo gedit /boot/grub/menu.lst
Add this after memtest
title Windows 
rootnoverify (hd0,0)
map (hd0,0) (hd1,0)
map (hd1,0) (hd0,0)
makeactive
chainloader +1
Save, exit and reboot
Let's see what happens

---

### Post by scy1192 on 2007-10-25
> **Pumalite said:**
> Backup first:
sudo cp /boot/grub/menu.lst /boot/grub/menu.lst.back, then
gksudo gedit /boot/grub/menu.lst
Add this after memtest
title Windows 
rootnoverify (hd0,0)
map (hd0,0) (hd1,0)
map (hd1,0) (hd0,0)
makeactive
chainloader +1
Save, exit and reboot
Let's see what happens
sorry, how do I add that stuff after memtest? actually, I think I'll just go with cowrecked's idea, I don't really have any reason to keep ubuntu and I can always put it in a Virtual Machine back in Windows, shall I ever need it. Thanks for the hlp :)

---

### Post by cowrecked on 2007-10-28
You're using multiple hard drives, correct?  If so, try this.  If you still want to try to get Ubuntu AND Vista to work, try unplugging your vista (and any other drives) before installing Ubuntu.  This will force you to manually select which hard drive to boot from as your BIOS loads.  

Worst case scenario, this means a few keystrokes and a soft reboot.  Your motherboard might have a boot menu that you can load separate of your BIOS settings that will allow you to choose which HDD to boot from.  You can also set in your BIOS which HDD you want to be the default booting device, usually...

Try this, it worked for me, and it doesnt interfere with your other hard drive(s) at all, so there's no risk.

---

### Post by skompier on 2007-10-28
> **scy1192 said:**
> 
I know you probably don't like me ditching your OS for Windows, but this is definitely going to leave a sour taste in my mouth if I can't do anything about it.

You're free to use whatever OS that is right for you. If that's Windows, then excellent. Linux is not for everyone and conversely, Windows isn't for everyone. Linux isn't Windows and Windows isn't Linux. It's the way it is. I hope that you can take the help given here and get your Windows working.

---

### Post by Pumalite on 2007-10-28
I doubt he could get it from Microsoft.

---

