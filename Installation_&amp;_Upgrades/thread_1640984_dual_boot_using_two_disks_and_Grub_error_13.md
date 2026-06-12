---
title: "dual boot using two disks and Grub error 13"
date: 2010-12-08
forum: Installation &amp; Upgrades
---

### Post by karaluh on 2010-12-08
HDD setup:
Primary master PATA - Windows
1st and 2nd SATA - Ubuntu software raid 0. Boot partition outside raid, Grub installed on 2nd SATA MBR.

When I was installing Windows I had to disconnect both SATA drives because of some Windows installer bug.

Both systems boot fine when I set appropriate HDD to boot from in BIOS. However, I would like to boot Windows from Grub.

menu.lst:
title Windows
root (hd0,0)
makeactive
chainloader +1

Grub gives error 13 whenever I try to boot Windows. How should Windows entry look like to be bootable?

---

### Post by DocEsq on 2010-12-08
When I had set up my dual boot system (two disks) a few years ago I used the information posted here:
[http://ubuntuforums.org/showthread.php?t=179902&highlight=dualboot](http://ubuntuforums.org/showthread.php?t=179902&highlight=dualboot)

A quick look at what you posted seems that you need to modify Grub to chainload properly.  From the link I posted it should be something like:

title              Windows XP
root               (hd1,0)
savedefault
makeactive
map                (hd0) (hd1)
map                (hd1) (hd0)
chainloader        +1

Note that this was for Grub and not Grub 2 which is what the latest Ubuntu is running by default.

This is something that could have been set up by default with 10.10 if that is what you had installed as per
[http://members.iinet.net.au/~herman546/p24.html](http://members.iinet.net.au/~herman546/p24.html)

Good luck

---

### Post by karaluh on 2010-12-08
> **DocEsq said:**
> When I had set up my dual boot system (two disks) a few years ago I used the information posted here:
[http://ubuntuforums.org/showthread.php?t=179902&highlight=dualboot](http://ubuntuforums.org/showthread.php?t=179902&highlight=dualboot)

Thank you for a quick answer. I've modified menu.lst and now the error 13 is gone. However, some garbage is displayed instead and the system freezes. Any ideas? BTW: I'm using grub legacy.

---

### Post by DocEsq on 2010-12-08
This appears to be a Grub issue you have.  Off the top of my head I am thinking that you need to place Grub on the first part of the drive that has Ubuntu and have your system boot into that.  You should be able to find additional information on the web or in this forum.

Good Luck

DocEsq

---

### Post by karaluh on 2010-12-09
> **DocEsq said:**
> This appears to be a Grub issue you have.  Off the top of my head I am thinking that you need to place Grub on the first part of the drive that has Ubuntu and have your system boot into that.

This is exactly how it is configured right now. I didn't made myself clear: the garbage and the error 13 are displayed only after I choose Windows from the Grub boot menu.

---

### Post by sikander3786 on 2010-12-09
Grub error 13 comes from Grub Legacy. We need to know more about your setup and bootinfoscript does exactly that.

Boot an Ubuntu Live CD/USB and download and run the script found here.

[http://bootinfoscript.sourceforge.net](http://bootinfoscript.sourceforge.net)

It would generate a Results.txt on your Desktop. Copy paste all data from that in your post.

While posting, click the # icon in post menu and paste your text in between the generated code tags.

---

### Post by karaluh on 2010-12-09
> **sikander3786 said:**
> Grub error 13 comes from Grub Legacy. We need to know more about your setup and bootinfoscript does exactly that.

I allready tried that, so I hope youre smarter than me :)

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda
 => No boot loader is installed in the MBR of /dev/sdb
 => Grub 0.97 is installed in the MBR of /dev/sdc and looks on the same drive 
    in partition #1 for /grub/stage2 and /grub/menu.lst.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe

sdb1: _________________________________________________________________________

    File system:       linux_raid_member
    Boot sector type:  -
    Boot sector info:  

sdb2: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb3: _________________________________________________________________________

    File system:       linux_raid_member
    Boot sector type:  -
    Boot sector info:  

sdb4: _________________________________________________________________________

    File system:       linux_raid_member
    Boot sector type:  -
    Boot sector info:  

sdc1: _________________________________________________________________________

    File system:       linux_raid_member
    Boot sector type:  -
    Boot sector info:  

sdc2: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdc3: _________________________________________________________________________

    File system:       linux_raid_member
    Boot sector type:  -
    Boot sector info:  

sdc4: _________________________________________________________________________

    File system:       linux_raid_member
    Boot sector type:  -
    Boot sector info:  

md2: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

md1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.1 LTS
    Boot files/dirs:   /etc/fstab

md0: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   /grub/menu.lst

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Dysk /dev/sda: 320.1 GB, bajtów: 320072933376
g&#322;owic: 255, sektorów/&#347;cie&#380;k&#281;: 63, cylindrów: 38913, w sumie sektorów: 625142448
Jednostka = sektorów, czyli 1 * 512 = 512 bajtów
Rozmiar sektora (logiczny/fizyczny) w bajtach: 512 / 512

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048   625,139,711   625,137,664   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Dysk /dev/sdb: 250.1 GB, bajtów: 250059350016
g&#322;owic: 255, sektorów/&#347;cie&#380;k&#281;: 63, cylindrów: 30401, w sumie sektorów: 488397168
Jednostka = sektorów, czyli 1 * 512 = 512 bajtów
Rozmiar sektora (logiczny/fizyczny) w bajtach: 512 / 512

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63       979,964       979,902  fd Linux raid autodetect
/dev/sdb2             979,965     1,959,929       979,965  82 Linux swap / Solaris
/dev/sdb3           1,959,930    21,494,969    19,535,040  fd Linux raid autodetect
/dev/sdb4          21,494,970   488,392,064   466,897,095  fd Linux raid autodetect


Drive: sdc ___________________ _____________________________________________________

Dysk /dev/sdc: 250.1 GB, bajtów: 250059350016
g&#322;owic: 255, sektorów/&#347;cie&#380;k&#281;: 63, cylindrów: 30401, w sumie sektorów: 488397168
Jednostka = sektorów, czyli 1 * 512 = 512 bajtów
Rozmiar sektora (logiczny/fizyczny) w bajtach: 512 / 512

Partition  Boot         Start           End          Size  Id System

/dev/sdc1    *             63       979,964       979,902  fd Linux raid autodetect
/dev/sdc2             979,965     1,959,929       979,965  82 Linux swap / Solaris
/dev/sdc3           1,959,930    21,494,969    19,535,040  fd Linux raid autodetect
/dev/sdc4          21,494,970   488,392,064   466,897,095  fd Linux raid autodetect


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/etherd/e0.0 5afe126c-6268-49e1-89a2-5e0feb21ef0c   ext3                                     
/dev/loop0                                              iso9660    STARCRAFT                     
/dev/loop1                                              iso9660    BROODWAR_UK                   
/dev/loop2                                              iso9660    DIABLO                        
/dev/loop3                                              iso9660    HELLFIRE                      
/dev/loop4                                              udf        SC2-L100-D1                   
/dev/md0         85fe053d-aac8-431f-93b1-6b1c5c17c9a0   ext3                                     
/dev/md1         9d1fc4ff-e587-4c28-a8dd-87e3a87f81dd   ext3                                     
/dev/md2         fe93fccd-2eee-48b4-b842-9f7be7c1c76b   ext3                                     
/dev/sda1        8A6CD51F6CD5073B                       ntfs                                     
/dev/sda         62c22f8c-69d2-4d46-878d-c47b08b102d0   ext3                                     
/dev/sdb1        bbaba355-758c-bedf-e422-ab6ed7ca0eb1   linux_raid_member                               
/dev/sdb2        2a58ff5f-3cb7-4377-b093-8ebb1074964b   swap                                     
/dev/sdb3        ff8b000f-974b-e8db-5b1b-afefddfd28f9   linux_raid_member                               
/dev/sdb4        242e707f-c979-43d8-8f89-6a686b280eae   linux_raid_member                               
/dev/sdb                                                promise_fasttrack_raid_member                               
/dev/sdc1        bbaba355-758c-bedf-e422-ab6ed7ca0eb1   linux_raid_member                               
/dev/sdc2        803b2cda-7a18-48ac-9d7d-0ee89d5e4467   swap                                     
/dev/sdc3        ff8b000f-974b-e8db-5b1b-afefddfd28f9   linux_raid_member                               
/dev/sdc4        242e707f-c979-43d8-8f89-6a686b280eae   linux_raid_member                               
/dev/sdc                                                promise_fasttrack_raid_member                               
error: /dev/sde: No medium found
error: /dev/sdf: No medium found
error: /dev/sdg: No medium found
error: /dev/sdh: No medium found
error: /dev/sdi: No medium found

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/md1         /                        ext3       (rw,relatime,errors=remount-ro)
/dev/md0         /boot                    ext3       (rw,relatime)
/dev/md2         /home                    ext3       (rw,relatime)
/dev/loop0       /mnt/starcraft           iso9660    (rw,noexec,nosuid,nodev)
/dev/loop1       /mnt/broodwar            iso9660    (rw,noexec,nosuid,nodev)
/dev/loop2       /mnt/diablo              iso9660    (rw,noexec,nosuid,nodev)
/dev/loop3       /mnt/hellfire            iso9660    (rw,noexec,nosuid,nodev)
/dev/loop4       /mnt/starcraft_ii        udf        (rw,noexec,nosuid,nodev)
/dev/etherd/e0.0 /mnt/backup              ext3       (rw,relatime)


================================ md1/etc/fstab: ================================

# /etc/fstab: static file system information.
#
# <file system> 					<mount point>   <type>  	<options>       		<dump>  <pass>
proc            					/proc           	proc    	defaults        		0       0
# /dev/md1
UUID=9d1fc4ff-e587-4c28-a8dd-87e3a87f81dd 		/               	ext3    	relatime,errors=remount-ro 	0       1
# /dev/md0
UUID=85fe053d-aac8-431f-93b1-6b1c5c17c9a0 		/boot           	ext3    	relatime        		0       2
# /dev/md2
UUID=fe93fccd-2eee-48b4-b842-9f7be7c1c76b 		/home           	ext3    	relatime        		0       2
# /dev/sda2
UUID=803b2cda-7a18-48ac-9d7d-0ee89d5e4467 		none            	swap    	sw              		0       0
# /dev/sdb2
UUID=2a58ff5f-3cb7-4377-b093-8ebb1074964b 		none            	swap    	sw              		0       0
/dev/scd0       					/media/cdrom0   	udf,iso9660 	user,noauto,exec,utf8 		0       0
/dev/etherd/e0.0 					/mnt/backup/		ext3		relatime			0	0
/home/karaluh/Linux/starcraft/starcraft.iso		/mnt/starcraft  	udf,iso9660 	user,loop    			0       0
/home/karaluh/Linux/starcraft/broodwar.iso		/mnt/broodwar		udf,iso9660 	user,loop    			0       0
/home/karaluh/Linux/diablo/diablo.iso			/mnt/diablo		udf,iso9660 	user,loop    			0       0
/home/karaluh/Linux/diablo/hellfire.iso			/mnt/hellfire		udf,iso9660 	user,loop    			0       0
/home/karaluh/Linux/starcraft_ii/starcraft_ii.iso	/mnt/starcraft_ii	udf,iso9660	user,loop			0	0

==================== md1: Location of files loaded by Grub: ====================


    .3GB: initrd.img
    .2GB: initrd.img.old
    .2GB: vmlinuz
    .2GB: vmlinuz.old

============================== md0/grub/menu.lst: ==============================

# Splashimage line added by kubuntu-grub-splashimages package
splashimage=(hd0,0)/grub/splashimages/KUBUNTU_splashscreen_blue_neon_logo_03.xpm.gz

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
default		1

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

title		Windows
rootnoverify (hd2,0)
map                (hd0) (hd2)
map                (hd2) (hd0)
makeactive
chainloader +1


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
# kopt=root=/dev/md1 ro

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

title		Ubuntu 10.04.1 LTS, kernel 2.6.32-26-generic
root		(hd0,0)
kernel		/vmlinuz-2.6.32-26-generic root=/dev/md1 ro quiet splash 
initrd		/initrd.img-2.6.32-26-generic
quiet

title		Ubuntu 10.04.1 LTS, kernel 2.6.32-26-generic (recovery mode)
root		(hd0,0)
kernel		/vmlinuz-2.6.32-26-generic root=/dev/md1 ro  single
initrd		/initrd.img-2.6.32-26-generic

title		Ubuntu 10.04.1 LTS, kernel 2.6.32-25-generic
root		(hd0,0)
kernel		/vmlinuz-2.6.32-25-generic root=/dev/md1 ro quiet splash 
initrd		/initrd.img-2.6.32-25-generic
quiet

title		Ubuntu 10.04.1 LTS, kernel 2.6.32-25-generic (recovery mode)
root		(hd0,0)
kernel		/vmlinuz-2.6.32-25-generic root=/dev/md1 ro  single
initrd		/initrd.img-2.6.32-25-generic

title		Ubuntu 10.04.1 LTS, kernel 2.6.32-24-generic
root		(hd0,0)
kernel		/vmlinuz-2.6.32-24-generic root=/dev/md1 ro quiet splash 
initrd		/initrd.img-2.6.32-24-generic
quiet

title		Ubuntu 10.04.1 LTS, kernel 2.6.32-24-generic (recovery mode)
root		(hd0,0)
kernel		/vmlinuz-2.6.32-24-generic root=/dev/md1 ro  single
initrd		/initrd.img-2.6.32-24-generic

title		Ubuntu 10.04.1 LTS, kernel 2.6.32-23-generic
root		(hd0,0)
kernel		/vmlinuz-2.6.32-23-generic root=/dev/md1 ro quiet splash 
initrd		/initrd.img-2.6.32-23-generic
quiet

title		Ubuntu 10.04.1 LTS, kernel 2.6.32-23-generic (recovery mode)
root		(hd0,0)
kernel		/vmlinuz-2.6.32-23-generic root=/dev/md1 ro  single
initrd		/initrd.img-2.6.32-23-generic

title		Ubuntu 10.04.1 LTS, kernel 2.6.32-22-generic
root		(hd0,0)
kernel		/vmlinuz-2.6.32-22-generic root=/dev/md1 ro quiet splash 
initrd		/initrd.img-2.6.32-22-generic
quiet

title		Ubuntu 10.04.1 LTS, kernel 2.6.32-22-generic (recovery mode)
root		(hd0,0)
kernel		/vmlinuz-2.6.32-22-generic root=/dev/md1 ro  single
initrd		/initrd.img-2.6.32-22-generic

title		Ubuntu 10.04.1 LTS, kernel 2.6.31-21-generic
root		(hd0,0)
kernel		/vmlinuz-2.6.31-21-generic root=/dev/md1 ro quiet splash 
initrd		/initrd.img-2.6.31-21-generic
quiet

title		Ubuntu 10.04.1 LTS, kernel 2.6.31-21-generic (recovery mode)
root		(hd0,0)
kernel		/vmlinuz-2.6.31-21-generic root=/dev/md1 ro  single
initrd		/initrd.img-2.6.31-21-generic

title		Ubuntu 10.04.1 LTS, kernel 2.6.24-27-generic
root		(hd0,0)
kernel		/vmlinuz-2.6.24-27-generic root=/dev/md1 ro quiet splash 
initrd		/initrd.img-2.6.24-27-generic
quiet

title		Ubuntu 10.04.1 LTS, kernel 2.6.24-27-generic (recovery mode)
root		(hd0,0)
kernel		/vmlinuz-2.6.24-27-generic root=/dev/md1 ro  single
initrd		/initrd.img-2.6.24-27-generic

title		Ubuntu 10.04.1 LTS, kernel 2.6.24-26-generic
root		(hd0,0)
kernel		/vmlinuz-2.6.24-26-generic root=/dev/md1 ro quiet splash 
initrd		/initrd.img-2.6.24-26-generic
quiet

title		Ubuntu 10.04.1 LTS, kernel 2.6.24-26-generic (recovery mode)
root		(hd0,0)
kernel		/vmlinuz-2.6.24-26-generic root=/dev/md1 ro  single
initrd		/initrd.img-2.6.24-26-generic

title		Ubuntu 10.04.1 LTS, kernel 2.6.24-25-generic
root		(hd0,0)
kernel		/vmlinuz-2.6.24-25-generic root=/dev/md1 ro quiet splash 
initrd		/initrd.img-2.6.24-25-generic
quiet

title		Ubuntu 10.04.1 LTS, kernel 2.6.24-25-generic (recovery mode)
root		(hd0,0)
kernel		/vmlinuz-2.6.24-25-generic root=/dev/md1 ro  single
initrd		/initrd.img-2.6.24-25-generic

title		Ubuntu 10.04.1 LTS, kernel 2.6.24-24-generic
root		(hd0,0)
kernel		/vmlinuz-2.6.24-24-generic root=/dev/md1 ro quiet splash 
initrd		/initrd.img-2.6.24-24-generic
quiet

title		Ubuntu 10.04.1 LTS, kernel 2.6.24-24-generic (recovery mode)
root		(hd0,0)
kernel		/vmlinuz-2.6.24-24-generic root=/dev/md1 ro  single
initrd		/initrd.img-2.6.24-24-generic

title		Ubuntu 10.04.1 LTS, kernel 2.6.24-23-generic
root		(hd0,0)
kernel		/vmlinuz-2.6.24-23-generic root=/dev/md1 ro quiet splash 
initrd		/initrd.img-2.6.24-23-generic
quiet

title		Ubuntu 10.04.1 LTS, kernel 2.6.24-23-generic (recovery mode)
root		(hd0,0)
kernel		/vmlinuz-2.6.24-23-generic root=/dev/md1 ro  single
initrd		/initrd.img-2.6.24-23-generic

title		Ubuntu 10.04.1 LTS, memtest86+
root		(hd0,0)
kernel		/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

==================== md0: Location of files loaded by Grub: ====================


    .4GB: grub/menu.lst
    .4GB: grub/stage2
    .0GB: initrd.img-2.6.24-21-generic
    .0GB: initrd.img-2.6.24-22-generic
    .1GB: initrd.img-2.6.24-23-generic
    .1GB: initrd.img-2.6.24-23-generic.bak
    .1GB: initrd.img-2.6.24-24-generic
    .1GB: initrd.img-2.6.24-24-generic.bak
    .1GB: initrd.img-2.6.24-25-generic
    .1GB: initrd.img-2.6.24-25-generic.bak
    .1GB: initrd.img-2.6.24-26-generic
    .1GB: initrd.img-2.6.24-26-generic.bak
    .0GB: initrd.img-2.6.24-27-generic
    .3GB: initrd.img-2.6.24-27-generic.bak
    .0GB: initrd.img-2.6.31-21-generic
    .1GB: initrd.img-2.6.32-22-generic
    .1GB: initrd.img-2.6.32-23-generic
    .2GB: initrd.img-2.6.32-24-generic
    .2GB: initrd.img-2.6.32-25-generic
    .3GB: initrd.img-2.6.32-26-generic
    .1GB: vmlinuz-2.6.24-23-generic
    .1GB: vmlinuz-2.6.24-24-generic
    .0GB: vmlinuz-2.6.24-25-generic
    .1GB: vmlinuz-2.6.24-26-generic
    .1GB: vmlinuz-2.6.24-27-generic
    .0GB: vmlinuz-2.6.31-21-generic
    .0GB: vmlinuz-2.6.32-22-generic
    .0GB: vmlinuz-2.6.32-23-generic
    .1GB: vmlinuz-2.6.32-24-generic
    .2GB: vmlinuz-2.6.32-25-generic
    .2GB: vmlinuz-2.6.32-26-generic
=======Devices which don't seem to have a corresponding hard drive==============

sde sdf sdg sdh sdi 

```

---

### Post by oldfred on 2010-12-09
I do not know how RAID may affect it, but I boot sdc and if I want to chainload to the grub in sda, I have to refer to it as hd1 not hd0 as I would expect. The boot drive seems to be hd0 in all cases then the drives come in order. 

I would try changing the [COLOR=Red]2[/COLOR] to 1.

title        Windows
rootnoverify (hd[COLOR=Red]2[/COLOR],0)
map                (hd0) (hd[COLOR=Red]2[/COLOR])
map                (hd[COLOR=Red]2[/COLOR]) (hd0)
makeactive
chainloader +1

---

### Post by karaluh on 2010-12-10
> **oldfred said:**
> I do not know how RAID may affect it, but I boot sdc and if I want to chainload to the grub in sda, I have to refer to it as hd1 not hd0 as I would expect. The boot drive seems to be hd0 in all cases then the drives come in order. 

I would try changing the [COLOR=Red]2[/COLOR] to 1.


RAID doesn't affect it at all, Grub doesn't understand it, so boot partition has to be outside of it. As for the hdX, I tried everything from 0 to even 3 to no avail. Whatever I set, I get either error 13 or freeze.

---

### Post by oldfred on 2010-12-10
This says it may be more related to a kernel issue.
[http://members.iinet.net.au/~herman546/p15.html#13](http://members.iinet.net.au/~herman546/p15.html#13)

Speaking of kernels you have not housecleaned for a while, once upgraded the old kernels do not do anything but take up space.

8.04     2.6.24 
8.10     2.6.27 
9.04     2.6.28 
9.10     2.6.31 
10.04     2.6.32 
Go to Synaptic Package Manager and search for linux-image.
More info in post #8
[http://ubuntuforums.org/showthread.php?t=1283521](http://ubuntuforums.org/showthread.php?t=1283521)

---

### Post by karaluh on 2010-12-11
> **oldfred said:**
> This says it may be more related to a kernel issue.
[http://members.iinet.net.au/~herman546/p15.html#13](http://members.iinet.net.au/~herman546/p15.html#13)


Yes, and no. When error 13 appears while booting Windows, the page says it's a coruppted boot sector. However, the bootsector is ok, because Windows boots fine when I change boot order in bios.

> **oldfred said:**
> 
Speaking of kernels you have not housecleaned for a while, once upgraded the old kernels do not do anything but take up space.


I know, I'm just to lazy to do that :)

---

### Post by oldfred on 2010-12-11
I boot sdc and chainload back to the MBR of sda or sdb. I do the same with grub2.

These were old entries that I saved. If booting sdc then hd1 should be sda.

title      Chainload hd1 @ sda
root        (hd1)
chainloader +1

title       Chainload hd2 @ sdb
root        (hd2)
chainloader +1

---

### Post by karaluh on 2010-12-11
> **oldfred said:**
> I boot sdc and chainload back to the MBR of sda or sdb. I do the same with grub2.


I've deceided to upgrade Grub. The install went fine, it picked the Windows MBR and added it to the grub2 menu. On reboot I chainloaded grub2 and tried to run Windows from there - successfully. I then finished the upgrade and installed grub2 on both of the Linux drives. Since then I'm no longer able to boot Windows again. When I choose to, I get some garbage on the screen and Grub freezes.

---

### Post by oldfred on 2010-12-11
Rerun the boot info script. If you run it again it will make a results1.txt or results2.txt etc.

Then we may be able to see what the issue is.

---

### Post by karaluh on 2010-12-12
> **oldfred said:**
> Rerun the boot info script. If you run it again it will make a results1.txt or results2.txt etc.

Then we may be able to see what the issue is.

This is the output:
```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks for (md0)/grub.
 => Grub 2 is installed in the MBR of /dev/sdb and looks for (md0)/grub.
 => Windows is installed in the MBR of /dev/sdc

sda1: _________________________________________________________________________

    File system:       linux_raid_member
    Boot sector type:  -
    Boot sector info:  

sda2: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda3: _________________________________________________________________________

    File system:       linux_raid_member
    Boot sector type:  -
    Boot sector info:  

sda4: _________________________________________________________________________

    File system:       linux_raid_member
    Boot sector type:  -
    Boot sector info:  

sdb1: _________________________________________________________________________

    File system:       linux_raid_member
    Boot sector type:  -
    Boot sector info:  

sdb2: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb3: _________________________________________________________________________

    File system:       linux_raid_member
    Boot sector type:  -
    Boot sector info:  

sdb4: _________________________________________________________________________

    File system:       linux_raid_member
    Boot sector type:  -
    Boot sector info:  

sdc1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe

md1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.1 LTS
    Boot files/dirs:   /etc/fstab

md0: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   /grub/menu.lst /grub/grub.cfg /grub/core.img

md2: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Dysk /dev/sda: 250.1 GB, bajtÃ³w: 250059350016
gÅ‚owic: 255, sektorÃ³w/Å›cieÅ&#338;kÄ™: 63, cylindrÃ³w: 30401, w sumie sektorÃ³w: 488397168
Jednostka = sektorÃ³w, czyli 1 * 512 = 512 bajtÃ³w
Rozmiar sektora (logiczny/fizyczny) w bajtach: 512 / 512

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63       979,964       979,902  fd Linux raid autodetect
/dev/sda2             979,965     1,959,929       979,965  82 Linux swap / Solaris
/dev/sda3           1,959,930    21,494,969    19,535,040  fd Linux raid autodetect
/dev/sda4          21,494,970   488,392,064   466,897,095  fd Linux raid autodetect


Drive: sdb ___________________ _____________________________________________________

Dysk /dev/sdb: 250.1 GB, bajtÃ³w: 250059350016
gÅ‚owic: 255, sektorÃ³w/Å›cieÅ&#338;kÄ™: 63, cylindrÃ³w: 30401, w sumie sektorÃ³w: 488397168
Jednostka = sektorÃ³w, czyli 1 * 512 = 512 bajtÃ³w
Rozmiar sektora (logiczny/fizyczny) w bajtach: 512 / 512

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63       979,964       979,902  fd Linux raid autodetect
/dev/sdb2             979,965     1,959,929       979,965  82 Linux swap / Solaris
/dev/sdb3           1,959,930    21,494,969    19,535,040  fd Linux raid autodetect
/dev/sdb4          21,494,970   488,392,064   466,897,095  fd Linux raid autodetect


Drive: sdc ___________________ _____________________________________________________

Dysk /dev/sdc: 320.1 GB, bajtÃ³w: 320072933376
gÅ‚owic: 255, sektorÃ³w/Å›cieÅ&#338;kÄ™: 63, cylindrÃ³w: 38913, w sumie sektorÃ³w: 625142448
Jednostka = sektorÃ³w, czyli 1 * 512 = 512 bajtÃ³w
Rozmiar sektora (logiczny/fizyczny) w bajtach: 512 / 512

Partition  Boot         Start           End          Size  Id System

/dev/sdc1    *          2,048   625,139,711   625,137,664   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/etherd/e0.0 5afe126c-6268-49e1-89a2-5e0feb21ef0c   ext3                                     
/dev/loop0                                              iso9660    STARCRAFT                     
/dev/loop1                                              iso9660    BROODWAR_UK                   
/dev/loop2                                              iso9660    DIABLO                        
/dev/loop3                                              iso9660    HELLFIRE                      
/dev/loop4                                              udf        SC2-L100-D1                   
/dev/md0         85fe053d-aac8-431f-93b1-6b1c5c17c9a0   ext3                                     
/dev/md1         9d1fc4ff-e587-4c28-a8dd-87e3a87f81dd   ext3                                     
/dev/md2         fe93fccd-2eee-48b4-b842-9f7be7c1c76b   ext3                                     
/dev/sda1        bbaba355-758c-bedf-e422-ab6ed7ca0eb1   linux_raid_member                               
/dev/sda2        2a58ff5f-3cb7-4377-b093-8ebb1074964b   swap                                     
/dev/sda3        ff8b000f-974b-e8db-5b1b-afefddfd28f9   linux_raid_member                               
/dev/sda4        242e707f-c979-43d8-8f89-6a686b280eae   linux_raid_member                               
/dev/sda                                                promise_fasttrack_raid_member                               
/dev/sdb1        bbaba355-758c-bedf-e422-ab6ed7ca0eb1   linux_raid_member                               
/dev/sdb2        803b2cda-7a18-48ac-9d7d-0ee89d5e4467   swap                                     
/dev/sdb3        ff8b000f-974b-e8db-5b1b-afefddfd28f9   linux_raid_member                               
/dev/sdb4        242e707f-c979-43d8-8f89-6a686b280eae   linux_raid_member                               
/dev/sdb                                                promise_fasttrack_raid_member                               
/dev/sdc1        8A6CD51F6CD5073B                       ntfs                                     
/dev/sdc         62c22f8c-69d2-4d46-878d-c47b08b102d0   ext3                                     
error: /dev/sdd: No medium found
error: /dev/sde: No medium found
error: /dev/sdf: No medium found
error: /dev/sdg: No medium found
error: /dev/sdh: No medium found

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/md1         /                        ext3       (rw,relatime,errors=remount-ro)
/dev/md0         /boot                    ext3       (rw,relatime)
/dev/md2         /home                    ext3       (rw,relatime)
/dev/loop0       /mnt/starcraft           iso9660    (rw,noexec,nosuid,nodev)
/dev/loop1       /mnt/broodwar            iso9660    (rw,noexec,nosuid,nodev)
/dev/loop2       /mnt/diablo              iso9660    (rw,noexec,nosuid,nodev)
/dev/loop3       /mnt/hellfire            iso9660    (rw,noexec,nosuid,nodev)
/dev/loop4       /mnt/starcraft_ii        udf        (rw,noexec,nosuid,nodev)
/dev/etherd/e0.0 /mnt/backup              ext3       (rw,relatime)


================================ md1/etc/fstab: ================================

# /etc/fstab: static file system information.
#
# <file system> 					<mount point>   <type>  	<options>       		<dump>  <pass>
proc            					/proc           	proc    	defaults        		0       0
# /dev/md1
UUID=9d1fc4ff-e587-4c28-a8dd-87e3a87f81dd 		/               	ext3    	relatime,errors=remount-ro 	0       1
# /dev/md0
UUID=85fe053d-aac8-431f-93b1-6b1c5c17c9a0 		/boot           	ext3    	relatime        		0       2
# /dev/md2
UUID=fe93fccd-2eee-48b4-b842-9f7be7c1c76b 		/home           	ext3    	relatime        		0       2
# /dev/sda2
UUID=803b2cda-7a18-48ac-9d7d-0ee89d5e4467 		none            	swap    	sw              		0       0
# /dev/sdb2
UUID=2a58ff5f-3cb7-4377-b093-8ebb1074964b 		none            	swap    	sw              		0       0
/dev/scd0       					/media/cdrom0   	udf,iso9660 	user,noauto,exec,utf8 		0       0
/dev/etherd/e0.0 					/mnt/backup/		ext3		relatime			0	0
/home/karaluh/Linux/starcraft/starcraft.iso		/mnt/starcraft  	udf,iso9660 	user,loop    			0       0
/home/karaluh/Linux/starcraft/broodwar.iso		/mnt/broodwar		udf,iso9660 	user,loop    			0       0
/home/karaluh/Linux/diablo/diablo.iso			/mnt/diablo		udf,iso9660 	user,loop    			0       0
/home/karaluh/Linux/diablo/hellfire.iso			/mnt/hellfire		udf,iso9660 	user,loop    			0       0
/home/karaluh/Linux/starcraft_ii/starcraft_ii.iso	/mnt/starcraft_ii	udf,iso9660	user,loop			0	0

==================== md1: Location of files loaded by Grub: ====================


    .3GB: initrd.img
    .3GB: initrd.img.old
    .3GB: vmlinuz
    .2GB: vmlinuz.old

============================== md0/grub/menu.lst: ==============================




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

title		Windows
root (hd0,0)
chainloader +1


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
# kopt=root=/dev/md1 ro

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

title		Chainload into GRUB 2
root		(hd0,0)
kernel		/grub/core.img

title		ÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄ
root
		
title		When you have verified GRUB 2 works, you can use this command to
root

title		complete the upgrade:  upgrade-from-grub-legacy
root

title		ÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄ
root

title		Ubuntu 10.04.1 LTS, kernel 2.6.32-27-generic
root		(hd0,0)
kernel		/vmlinuz-2.6.32-27-generic root=/dev/md1 ro quiet splash
initrd		/initrd.img-2.6.32-27-generic
quiet

title		Ubuntu 10.04.1 LTS, kernel 2.6.32-27-generic (recovery mode)
root		(hd0,0)
kernel		/vmlinuz-2.6.32-27-generic root=/dev/md1 ro single
initrd		/initrd.img-2.6.32-27-generic

title		Ubuntu 10.04.1 LTS, kernel 2.6.32-26-generic
root		(hd0,0)
kernel		/vmlinuz-2.6.32-26-generic root=/dev/md1 ro quiet splash
initrd		/initrd.img-2.6.32-26-generic
quiet

title		Ubuntu 10.04.1 LTS, kernel 2.6.32-26-generic (recovery mode)
root		(hd0,0)
kernel		/vmlinuz-2.6.32-26-generic root=/dev/md1 ro single
initrd		/initrd.img-2.6.32-26-generic

title		Ubuntu 10.04.1 LTS, kernel 2.6.32-25-generic
root		(hd0,0)
kernel		/vmlinuz-2.6.32-25-generic root=/dev/md1 ro quiet splash
initrd		/initrd.img-2.6.32-25-generic
quiet

title		Ubuntu 10.04.1 LTS, kernel 2.6.32-25-generic (recovery mode)
root		(hd0,0)
kernel		/vmlinuz-2.6.32-25-generic root=/dev/md1 ro single
initrd		/initrd.img-2.6.32-25-generic

title		Ubuntu 10.04.1 LTS, kernel 2.6.32-24-generic
root		(hd0,0)
kernel		/vmlinuz-2.6.32-24-generic root=/dev/md1 ro quiet splash
initrd		/initrd.img-2.6.32-24-generic
quiet

title		Ubuntu 10.04.1 LTS, kernel 2.6.32-24-generic (recovery mode)
root		(hd0,0)
kernel		/vmlinuz-2.6.32-24-generic root=/dev/md1 ro single
initrd		/initrd.img-2.6.32-24-generic

title		Ubuntu 10.04.1 LTS, kernel 2.6.32-23-generic
root		(hd0,0)
kernel		/vmlinuz-2.6.32-23-generic root=/dev/md1 ro quiet splash
initrd		/initrd.img-2.6.32-23-generic
quiet

title		Ubuntu 10.04.1 LTS, kernel 2.6.32-23-generic (recovery mode)
root		(hd0,0)
kernel		/vmlinuz-2.6.32-23-generic root=/dev/md1 ro single
initrd		/initrd.img-2.6.32-23-generic

title		Ubuntu 10.04.1 LTS, kernel 2.6.32-22-generic
root		(hd0,0)
kernel		/vmlinuz-2.6.32-22-generic root=/dev/md1 ro quiet splash
initrd		/initrd.img-2.6.32-22-generic
quiet

title		Ubuntu 10.04.1 LTS, kernel 2.6.32-22-generic (recovery mode)
root		(hd0,0)
kernel		/vmlinuz-2.6.32-22-generic root=/dev/md1 ro single
initrd		/initrd.img-2.6.32-22-generic

title		Ubuntu 10.04.1 LTS, kernel 2.6.31-21-generic
root		(hd0,0)
kernel		/vmlinuz-2.6.31-21-generic root=/dev/md1 ro quiet splash
initrd		/initrd.img-2.6.31-21-generic
quiet

title		Ubuntu 10.04.1 LTS, kernel 2.6.31-21-generic (recovery mode)
root		(hd0,0)
kernel		/vmlinuz-2.6.31-21-generic root=/dev/md1 ro single
initrd		/initrd.img-2.6.31-21-generic

title		Ubuntu 10.04.1 LTS, kernel 2.6.24-27-generic
root		(hd0,0)
kernel		/vmlinuz-2.6.24-27-generic root=/dev/md1 ro quiet splash
initrd		/initrd.img-2.6.24-27-generic
quiet

title		Ubuntu 10.04.1 LTS, kernel 2.6.24-27-generic (recovery mode)
root		(hd0,0)
kernel		/vmlinuz-2.6.24-27-generic root=/dev/md1 ro single
initrd		/initrd.img-2.6.24-27-generic

title		Ubuntu 10.04.1 LTS, kernel 2.6.24-26-generic
root		(hd0,0)
kernel		/vmlinuz-2.6.24-26-generic root=/dev/md1 ro quiet splash
initrd		/initrd.img-2.6.24-26-generic
quiet

title		Ubuntu 10.04.1 LTS, kernel 2.6.24-26-generic (recovery mode)
root		(hd0,0)
kernel		/vmlinuz-2.6.24-26-generic root=/dev/md1 ro single
initrd		/initrd.img-2.6.24-26-generic

title		Ubuntu 10.04.1 LTS, kernel 2.6.24-25-generic
root		(hd0,0)
kernel		/vmlinuz-2.6.24-25-generic root=/dev/md1 ro quiet splash
initrd		/initrd.img-2.6.24-25-generic
quiet

title		Ubuntu 10.04.1 LTS, kernel 2.6.24-25-generic (recovery mode)
root		(hd0,0)
kernel		/vmlinuz-2.6.24-25-generic root=/dev/md1 ro single
initrd		/initrd.img-2.6.24-25-generic

title		Ubuntu 10.04.1 LTS, kernel 2.6.24-24-generic
root		(hd0,0)
kernel		/vmlinuz-2.6.24-24-generic root=/dev/md1 ro quiet splash
initrd		/initrd.img-2.6.24-24-generic
quiet

title		Ubuntu 10.04.1 LTS, kernel 2.6.24-24-generic (recovery mode)
root		(hd0,0)
kernel		/vmlinuz-2.6.24-24-generic root=/dev/md1 ro single
initrd		/initrd.img-2.6.24-24-generic

title		Ubuntu 10.04.1 LTS, kernel 2.6.24-23-generic
root		(hd0,0)
kernel		/vmlinuz-2.6.24-23-generic root=/dev/md1 ro quiet splash
initrd		/initrd.img-2.6.24-23-generic
quiet

title		Ubuntu 10.04.1 LTS, kernel 2.6.24-23-generic (recovery mode)
root		(hd0,0)
kernel		/vmlinuz-2.6.24-23-generic root=/dev/md1 ro single
initrd		/initrd.img-2.6.24-23-generic

title		Ubuntu 10.04.1 LTS, memtest86+
root		(hd0,0)
kernel		/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

============================== md0/grub/grub.cfg: ==============================

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
set default="0"
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
insmod raid
insmod mdraid
insmod ext2
set root='(md1)'
search --no-floppy --fs-uuid --set 9d1fc4ff-e587-4c28-a8dd-87e3a87f81dd
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
insmod raid
insmod mdraid
insmod ext2
set root='(md0)'
search --no-floppy --fs-uuid --set 85fe053d-aac8-431f-93b1-6b1c5c17c9a0
set locale_dir=($root)/grub/locale
set lang=pl.UTF-8
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
menuentry 'Ubuntu, with Linux 2.6.32-27-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod raid
	insmod mdraid
	insmod ext2
	set root='(md0)'
	search --no-floppy --fs-uuid --set 85fe053d-aac8-431f-93b1-6b1c5c17c9a0
	linux	/vmlinuz-2.6.32-27-generic root=UUID=9d1fc4ff-e587-4c28-a8dd-87e3a87f81dd ro   quiet splash
	initrd	/initrd.img-2.6.32-27-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-27-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod raid
	insmod mdraid
	insmod ext2
	set root='(md0)'
	search --no-floppy --fs-uuid --set 85fe053d-aac8-431f-93b1-6b1c5c17c9a0
	echo	'Loading Linux 2.6.32-27-generic ...'
	linux	/vmlinuz-2.6.32-27-generic root=UUID=9d1fc4ff-e587-4c28-a8dd-87e3a87f81dd ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/initrd.img-2.6.32-27-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-26-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod raid
	insmod mdraid
	insmod ext2
	set root='(md0)'
	search --no-floppy --fs-uuid --set 85fe053d-aac8-431f-93b1-6b1c5c17c9a0
	linux	/vmlinuz-2.6.32-26-generic root=UUID=9d1fc4ff-e587-4c28-a8dd-87e3a87f81dd ro   quiet splash
	initrd	/initrd.img-2.6.32-26-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-26-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod raid
	insmod mdraid
	insmod ext2
	set root='(md0)'
	search --no-floppy --fs-uuid --set 85fe053d-aac8-431f-93b1-6b1c5c17c9a0
	echo	'Loading Linux 2.6.32-26-generic ...'
	linux	/vmlinuz-2.6.32-26-generic root=UUID=9d1fc4ff-e587-4c28-a8dd-87e3a87f81dd ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/initrd.img-2.6.32-26-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod raid
	insmod mdraid
	insmod ext2
	set root='(md0)'
	search --no-floppy --fs-uuid --set 85fe053d-aac8-431f-93b1-6b1c5c17c9a0
	linux16	/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod raid
	insmod mdraid
	insmod ext2
	set root='(md0)'
	search --no-floppy --fs-uuid --set 85fe053d-aac8-431f-93b1-6b1c5c17c9a0
	linux16	/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" {
	insmod ntfs
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set 8a6cd51f6cd5073b
	chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

==================== md0: Location of files loaded by Grub: ====================


    .4GB: grub/core.img
    .4GB: grub/grub.cfg
    .4GB: grub/menu.lst
    .0GB: initrd.img-2.6.24-21-generic
    .0GB: initrd.img-2.6.24-22-generic
    .3GB: initrd.img-2.6.32-26-generic
    .3GB: initrd.img-2.6.32-27-generic
    .2GB: vmlinuz-2.6.32-26-generic
    .3GB: vmlinuz-2.6.32-27-generic
=======Devices which don't seem to have a corresponding hard drive==============

sdd sde sdf sdg sdh 

```

---

### Post by oldfred on 2010-12-12
I do not know how all the RAID setup may change things.

The search by UUID should find the windows install as it has the correct UUID, but the set root thinks it is sda1, but now it is sdc1. That should not stop it from booting windows, but may be something to experiment with.

What drive do you actually boot with? I find grub considers that hd0 and then the rest of the drives are hd1, hd2. Do not know if md0 is considered a drive or not.

With win7 the script does not parse the BCD hive to know what drive windows thinks it is. If it thinks it is drive0 it may boot ok when booting from sdc, but when booting from sda or sdb, then sdc is not drive 0.

You could try several alternate boot stanzas in 40_custom for booting windows to see if it makes any difference. I do not see anything but these are just experiments.

menuentry "Windows 7 (loader) (on /dev/sdc1)" {
insmod ntfs
set root=(hd2,1)
chainloader +1
}

I just noticed that I only see the drivemap with XP stanzas that I have saved. I do not have 7, and only have XP on sda. This is just to have the drivemap command, the title does not matter.

menuentry "Windows NT/2000/XP (loader) (on /dev/sdc1)" {
    insmod ntfs
    set root=(hd2,1)
    drivemap -s (hd2) ${root}
    chainloader +1
}


title Windows 7 , chainloader (on /dev/sdc1)
rootnoverify (hd2,1)
savedefault
chainloader +1

Another alternative is to move  your windows drive back to sda?

---

### Post by karaluh on 2010-12-20
> **oldfred said:**
> I do not know how all the RAID setup may change things.

It shouldn't. md devices are invisible to grub, while /boot being raid1 is visible as ext3.

> **oldfred said:**
> 
The search by UUID should find the windows install as it has the correct UUID, but the set root thinks it is sda1, but now it is sdc1. That should not stop it from booting windows, but may be something to experiment with.

I have no idea why the script "moved" Windows drive to sdc. It is and always was sda.

> **oldfred said:**
> 
What drive do you actually boot with? I find grub considers that hd0 and then the rest of the drives are hd1, hd2. Do not know if md0 is considered a drive or not.


I boot with sdc. md are not considered as drives.

> **oldfred said:**
> 
You could try several alternate boot stanzas in 40_custom for booting windows to see if it makes any difference. I do not see anything but these are just experiments.


I tried every sane drive number in "set root" and "drivemap" to no avail. Either I get garbage and freeze - that's probably linux drives, or the comuter just resets - that's probably Windows failing to load. The funny thing is, it worked when chainloadnig Grub2 from legacy.

---

### Post by oldfred on 2010-12-20
We have seen where mixed PATA & SATA drives sometimes change order. Something about powering up and when BIOS sees drive. Does it make a difference between cold boot & warm boot?

I might just try a sudo update-grub  and warm reboot to see if it found a good windows boot stanza. But that may not thne work with every cold boot.

---

