---
title: "can't open / boot grub (from mbr)"
date: 2008-03-21
forum: Installation &amp; Upgrades
---

### Post by belowen on 2008-03-21
Hello
I have an interesting problem.I was using Linux Pardus and I only used Linux without windows xp.I could boot grub from local hard disk (mbr) and it automatically selected Linux pardus for me.
But two days ago I tried to install Ubuntu linux.After I installed it,I realized that I couldn't boot it from my hard disk automatically.I tried everything on ubuntu forums.For example, setup grub again from terminal,I reinstall ubuntu for many times.I tried to install ubuntu 7.04 (it gives the same thing) and 7.10.Now I'm using 7.10 and I can't boot it from local harddisk ,I can only boot grub from ubuntu setup cd.I want to tell this again I have only one linux partition (ubuntu) and a ntfs for my normal documents,files etc. and I haven't got a windows xp.
Today I tried super grub cd and I selected "fix grub" option but it didn't work for me.I'm searching for days to solve that problem.But I found nothing.Is there a problem about my mbr of my harddisk? or Is that a problem about hardware?I hope I can tell my problem properly.I need some help.

I want to give some technical information about my notebook,
I'm using toshiba tecra A4 109 and I have one harddisk.I said I have 2 partitions,first one is ubuntu 7.10 and second one is my ntfs (it has my documents and files etc.) .I don't use windows xp.
Thank you for reading and for your support.

---

### Post by Pumalite on 2008-03-21
If you can boot an Ubuntu Live CD, from the Terminal, post:
sudo fdisk -lu

---

### Post by belowen on 2008-03-21
Disk /dev/sda: 80.0 GB, 80026361856 bytes
77 heads, 63 sectors/track, 32220 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x4d8c28d0

   Device Boot      Start         End      Blocks   Id  System
/dev/sda2   *          63   156296384    78148161    f  W95 Ext'd (LBA)
/dev/sda5        39086208   156296384    58605088+   7  HPFS/NTFS
/dev/sda6             189      498014      248913   82  Linux swap / Solaris
/dev/sda7          498078    39086144    19294033+  83  Linux

Thank you for your interest.

---

### Post by Pumalite on 2008-03-21
Tell me what you have in sda2 and sda5

---

### Post by belowen on 2008-03-21
I have documents and files ,I mean my backup files on sda 5. But I can't see any partition about sda 2 on x window.I can only see it from terminal.I didn't see it on install  too.

---

### Post by Pumalite on 2008-03-21
Get Gparted Live CD: [http://gparted-livecd.tuxfamily.org/](http://gparted-livecd.tuxfamily.org/)
Burn to disk and boot from it.
Post screenshot
Use camera icon at the bottom.

---

### Post by belowen on 2008-03-21
ok I'm downloading now.I will write here after I'll do.

---

### Post by Pumalite on 2008-03-21
Ok.

---

### Post by belowen on 2008-03-21
Sorry for being late,I had some problems with internet speed.
I attached the screenshot.Thank you.

---

### Post by Pumalite on 2008-03-21
Use Gparted to move the boot flag to sda7 and lets see your menu.lst
Boot your Ubuntu Live CD. At the Terminal:
sudo mkdir /media/sda7
sudo mount -t ext3 /dev/sda7 /media/sda7
cat /media/sda7/boot/grub/menu.lst
Post it here.

---

### Post by belowen on 2008-03-21
**Here it is:**

# menu.lst - See: grub( 8 ), info grub, update-grub( 8 ) 
#            grub-install( 8 ), grub-floppy( 8 ), 
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
# kopt=root=UUID=a1eeaf19-2ba9-4b82-bd57-2fe00ec2fa38 ro 

## Setup crashdump menu entries 
## e.g. crashdump=1 
# crashdump=0 

## default grub root device 
## e.g. groot=(hd0,0) 
# groot=(hd0,6) 

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
root            (hd0,6) 
kernel          /boot/vmlinuz-2.6.22-14-generic root=UUID=a1eeaf19-2ba9-4b82-bd57-2fe00ec2fa38 vga=788 irqpoll 
initrd          /boot/initrd.img-2.6.22-14-generic 


title           Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode) 
root            (hd0,6) 
kernel          /boot/vmlinuz-2.6.22-14-generic root=UUID=a1eeaf19-2ba9-4b82-bd57-2fe00ec2fa38 ro single 
initrd          /boot/initrd.img-2.6.22-14-generic 

title           Ubuntu 7.10, memtest86+ 
root            (hd0,6) 
kernel          /boot/memtest86+.bin 
quiet 

### END DEBIAN AUTOMAGIC KERNELS LIST

---

### Post by Pumalite on 2008-03-21
With the boot flag removed from where it was and placed on sda7, your system should boot now.

---

### Post by belowen on 2008-03-21
It is the last screenshot about the situation,boot is on sda7 but I still can't boot it from local harddisk.What should I do ?

---

### Post by Pumalite on 2008-03-21
I would start from scratch save your data. Use Gparted to delete your hard drive and make new partitions:
10 GB for '/'
1 GB for /swap
The rest for /home
Install Ubuntu.
Restore your data to /home.

---

### Post by belowen on 2008-03-21
ok I'll try but I need to backup my data first.

---

### Post by Pumalite on 2008-03-21
Good luck.

---

### Post by belowen on 2008-03-21
I don't know if it is interested with this problem but I remembered one thing.
I installed ubuntu 7.04** before **my bios update for about a year ago.And I could boot it from my local hard disk.But I tried to install ubuntu 7.04 again the other day,I hoped I could boot it again but I couldn't.
Can it be about a bios conflict with ubuntu? 
I wanted to write this because I thought we need to know everything to solve this problem.

---

### Post by Pumalite on 2008-03-21
Check your BIOS and fiddle with it if you think it will save you a reinstall.

---

### Post by torgrot on 2008-03-21
Can you boot Ubuntu from an extended partition?  I didn't think that you could.  

torgrot

---

### Post by Pumalite on 2008-03-21
I didn't think so either, but now we have the proof

---

### Post by belowen on 2008-03-21
I didn't try booting from an extended partition.I'm trying to find an information about my bios and ubuntu.Do you think can this problem be from my bios?

---

### Post by Pumalite on 2008-03-21
If you look at the screenshot from Gparted, you'll see that everything (visible at least) is within an extended partition. Better to start again and follow my previous instructions.

---

### Post by belowen on 2008-03-21
I don't know how I did this mistake ,ok I'll get my backups and I will do what you've said.

---

