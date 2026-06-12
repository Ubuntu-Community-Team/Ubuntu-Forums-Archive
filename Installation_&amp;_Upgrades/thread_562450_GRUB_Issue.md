---
title: "GRUB Issue"
date: 2007-09-28
forum: Installation &amp; Upgrades
---

### Post by sgtbob on 2007-09-28
I had a PC crash on windows last week -  so, in re-installing both OS's, I thought that  with a master HDD and a slave HDD, 'Why not put Ubuntu on **hda** and Windows on **hdb**?'  But after installation  of both OS's and re-boot, no Windows at all [COLOR="Red"](I know - some would say why bother, but I need some stuff on Windows and am afraid to give it up completely)[/COLOR], just the Ubuntu 7.04!  I know Windows is there, so how do I get it to appear in the GRUB boot file so that I  can choose? I had a similar issue when the roles were reversed, i.e., Windows on hda and Ubuntu on hdb, and was able to control the startup OS; however, I don't seem to be able to correctly set this up now.

Here is what my menu.lst looks like.  How to change so I can choose either Ubuntu or Windows?

'...# menu.lst - See: grub(8), info grub, update-grub(8) [COLOR="Red"] Note that these little 'smiley' faces are included in Ubuntu 7.04, not something I entered - although they are kinda neat.)[/COLOR]
#            grub-install(8), grub-floppy(8), 
#            grub-md5-crypt, /usr/share/doc/grub 
#            and /usr/share/doc/grub-doc/. 

## default num 
# Set the default entry to the entry number NUM. Numbering starts from 0, and 
# the entry number 0 is the default if the command is not used. 
# 
# You can specify 'saved' instead of a number. In this case, the default entry 
# is the entry saved with the command 'savedefault'. 
# WARNING: If you are using dmraid do not change this entry to 'saved' or your 
# array will desync and will not let you boot your system. 
default		1  [COLOR="Red"]Note: this was initially 0, but I have been changin numbers trying to see what would work and after entering 1, 2, 3, 4, 5, 6 and restarting, I get no change in booting - Ubuntu is the default boot.[/COLOR] 

## timeout sec 
# Set a timeout, in SEC seconds, before automatically booting the default entry 
# (normally the first entry defined). 
timeout		10 

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
# kopt=root=UUID=f0b768a8-0633-4447-b15f-89949d02660f ro 

## Setup crashdump menu entries 
## e.g. crashdump=1 
# crashdump=0 

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

## ## End Default Options ## 

title		Ubuntu, kernel 2.6.20-16-generic 
root		(hd0,0) 
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=f0b768a8-0633-4447-b15f-89949d02660f ro quiet splash 
initrd		/boot/initrd.img-2.6.20-16-generic 
quiet 
savedefault 

title		Ubuntu, kernel 2.6.20-16-generic (recovery mode) 
root		(hd0,0) 
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=f0b768a8-0633-4447-b15f-89949d02660f ro single 
initrd		/boot/initrd.img-2.6.20-16-generic 

title		Ubuntu, kernel 2.6.20-15-generic 
root		(hd0,0) 
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=f0b768a8-0633-4447-b15f-89949d02660f ro quiet splash 
initrd		/boot/initrd.img-2.6.20-15-generic 
quiet 
savedefault 

title		Ubuntu, kernel 2.6.20-15-generic (recovery mode) 
root		(hd0,0) 
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=f0b768a8-0633-4447-b15f-89949d02660f ro single 
initrd		/boot/initrd.img-2.6.20-15-generic 

title		Ubuntu, memtest86+ 
root		(hd0,0) 
kernel		/boot/memtest86+.bin 
quiet 

### END DEBIAN AUTOMAGIC KERNELS LIST...'.

Bob:confused: :oops:

---

### Post by Pumalite on 2007-09-28
Post:
sudo fdisk -lu

---

### Post by sgtbob on 2007-09-28
Could you elaborate on what I will see if using this?  I've always been leery of using fdisk....

Bob

---

### Post by Pumalite on 2007-09-28
It will show how your system is arranged, so I can help you edit your menu.lst

---

### Post by sgtbob on 2007-09-28
Lost my head there for a bit.  Here are the results:

Disk /dev/sda: 123.5 GB, 123522416640 bytes
255 heads, 63 sectors/track, 15017 cylinders, total 241254720 sectors
Units = sectors of 1 * 512 = 512 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1              63   235191599   117595768+  83  Linux
/dev/sda2   *   235191600   241232039     3020220    7  HPFS/NTFS

Disk /dev/sdb: 30.0 GB, 30020272128 bytes
255 heads, 63 sectors/track, 3649 cylinders, total 58633344 sectors
Units = sectors of 1 * 512 = 512 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1              63    58605119    29302528+   7  HPFS/NTFS

---

### Post by Pumalite on 2007-09-28
Disk /dev/sda: 123.5 GB, 123522416640 bytes
255 heads, 63 sectors/track, 15017 cylinders, total 241254720 sectors
Units = sectors of 1 * 512 = 512 bytes

Device Boot Start End Blocks Id System
/dev/sda1 63 235191599 117595768+ 83 Linux
/dev/sda2 * 235191600 241232039 3020220 7 HPFS/NTFS

Disk /dev/sdb: 30.0 GB, 30020272128 bytes
255 heads, 63 sectors/track, 3649 cylinders, total 58633344 sectors
Units = sectors of 1 * 512 = 512 bytes

Device Boot Start End Blocks Id System
/dev/sdb1 63 58605119 29302528+ 7 HPFS/NTFS 

Which one is your Windows system; sda2 or sdb1?

---

### Post by sgtbob on 2007-09-28
I had hoped it was on sdb - that was my selection when installing Ubuntu.

---

### Post by Pumalite on 2007-09-28
We'll try sda2 first.
Backup first.
sudo cp /boot/grub/menu.lst /boot/grub/menu.lst.back, the:
gksudo gedit /boot/grub/menu.lst
Add the followig at the end (after the memtest entry)

title Windows 
rootnoverify (hd0,1)
makeactive
chainloader +1

Save, exit and reboot

---

### Post by sgtbob on 2007-09-28
That worked great - although I do have to hit the 'ESC' button to enable viewing of the various options - including Windows.  This I can live with.

Thank you so much.  I think I'll quit while I'm able to access Windows.


Bob):P):P

---

### Post by logos34 on 2007-09-28
> **sgtbob said:**
> although I do have to hit the 'ESC' button to enable viewing of the various options - including Windows

disable hiddenmenu:

**[COLOR="Red"]#[/COLOR]hiddenmenu**

---

### Post by Pumalite on 2007-09-28
> **sgtbob said:**
> That worked great - although I do have to hit the 'ESC' button to enable viewing of the various options - including Windows.  This I can live with.

Thank you so much.  I think I'll quit while I'm able to access Windows.


Bob):P):P

Your welcome. But logos34 finished the job.

---

### Post by sgtbob on 2007-09-28
That worked and looks like the startup I remember.

I really appreciate you help and will stop here - many thanks  from KS for the advice.

Bob

---

### Post by Pumalite on 2007-09-28
Good luck and happy Ubuntuing!

---

