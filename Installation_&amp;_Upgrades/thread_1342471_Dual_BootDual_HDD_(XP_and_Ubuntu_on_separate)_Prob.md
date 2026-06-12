---
title: "Dual Boot/Dual HDD (XP and Ubuntu on separate) Problem"
date: 2009-11-30
forum: Installation &amp; Upgrades
---

### Post by HeLzWright on 2009-11-30
I have installed both separately with out the other connected until the now;

80g - Master IDE - Ubuntu 8.10

40g - Slave IDE - Windows XP

both on full partition of drive and grub is changed with;

sudo gedit /boot/grub/menu.lst

With the following inserted at the end of the list;

title        Windows XP
root        (hd1,0)
savedefault
makeactive
map        (hd0) (hd1)
map        (hd1) (hd0)
chainloader    +1


When I boot my comp with this set up my BIOS does not recognise the SLAVE drive at all, but if I switch the master and the slave creating;

40g - Master IDE - Windows XP

80g - Slave IDE - Ubuntu 8.10

My BIOS recognises both drives and boots XP.

I understand why XP boots in this situation but why the slave drive is not being recognised with the first set-up. I have dual booted with this set-up just a different 40g drive because the last is in a better place considering it doesn't have to be windows's slave any more. I can just plug in which ever one I want to use but I would rather not have to open my box every day (I have a DOS programs specifically programed for XP for my job). Any suggestions would be helpful. 

My computer knowledge and know how to most people on this site are considerably low so try to be patient.

P.S. I have just realized that I can "see" but not access the 40g drive... and I'm even more frustrated :x

---

### Post by presence1960 on 2009-11-30
If your BIOS does not recognize the original setup I would double check my connections both from PSU to HD and HD to mobo. If they are all correct and properly seated then it may be a BIOS issue.

Either way I want to see more info about your setup. Let's get a better look at your setup & boot process. Boot the Ubuntu Live CD/USB. Choose "try ubuntu without any changes", when the desktop loads come back here and use the link in my signature to download the Boot Info Script to the desktop. Once on desktop open a terminal and run this command ```
sudo bash ~/Desktop/boot_info_script*.sh
``` This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text.

---

### Post by Bucky Ball on 2009-11-30
From a terminal, what are the results of:

```
sudo blkid
```This will show what all the drives and partitions are actually allocated.

As for the master/slave mix up, you may need to change the jumpers on the drives around if they are IDE drives. Windows likes things better on a primary partition, preferably the first one, on the master drive, drive one.

---

### Post by HeLzWright on 2009-12-01
This is with the first set-up(not live cd) will post live cd if needed 


============================= Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 8.10
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x000d563a

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   150,255,944   150,255,882  83 Linux
/dev/sda2         150,255,945   156,296,384     6,040,440   5 Extended
/dev/sda5         150,256,008   156,296,384     6,040,377  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="0de7be22-1fc5-4925-9f2c-bd3de2469a93" TYPE="ext3" 
/dev/sda5: UUID="11490f39-9a49-41b5-a1e2-3e0b437de3b9" TYPE="swap" 

=============================== "mount" output: ===============================

/dev/sda1 on / type ext3 (rw,relatime,errors=remount-ro)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
/proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
lrm on /lib/modules/2.6.27-7-generic/volatile type tmpfs (rw,mode=755)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/thomas/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=thomas)
/dev/scd0 on /media/Ubuntu 9.10 i386 type iso9660 (ro,nosuid,nodev,uhelper=hal,uid=1000,utf8)


=========================== sda1/boot/grub/menu.lst: ===========================

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
timeout		3

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
# kopt=root=UUID=0de7be22-1fc5-4925-9f2c-bd3de2469a93 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=0de7be22-1fc5-4925-9f2c-bd3de2469a93

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
uuid		0de7be22-1fc5-4925-9f2c-bd3de2469a93
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=0de7be22-1fc5-4925-9f2c-bd3de2469a93 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		0de7be22-1fc5-4925-9f2c-bd3de2469a93
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=0de7be22-1fc5-4925-9f2c-bd3de2469a93 ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		0de7be22-1fc5-4925-9f2c-bd3de2469a93
kernel		/boot/memtest86+.bin
quiet

title        Windows XP
root        (hd1,0)
savedefault
makeactive
map        (hd0) (hd1)
map        (hd1) (hd0)
chainloader    +1


### END DEBIAN AUTOMAGIC KERNELS LIST

=============================== sda1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=0de7be22-1fc5-4925-9f2c-bd3de2469a93 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=11490f39-9a49-41b5-a1e2-3e0b437de3b9 none            swap    sw              0       0
/dev/scd1       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda1: Location of files loaded by Grub: ===================


  56.0GB: boot/grub/menu.lst
  56.0GB: boot/grub/stage2
  56.0GB: boot/initrd.img-2.6.27-7-generic
  56.0GB: boot/vmlinuz-2.6.27-7-generic
  56.0GB: initrd.img
  56.0GB: vmlinuz

---

### Post by darkod on 2009-12-01
First of all you have to figure out why your computer is not recognizing the 40GB drive when the 80GB is master. IDE drives usually had jumpers to select master/slave, are you adjusting that accordingly? Some of them were able to assign master/slave depending where on the ATA cable they are, but jumpers are much preferred.
This is a problem with your BIOS not seeing the drive, it has nothing to do with ubuntu.
If you do not manage to solve that problem, you can still use the option to install grub1 on the 40GB MBR, instead of current windows bootloader, because your BIOS can see both drives when the 40GB is master.

Also you might try buying another ATA cable and set both drives as master on the different IDE channels. And in some BIOSes after you make changes to the drives connections you need to enter the BIOS and see if they are recognized automatically, or sometimes even press Enter on some setting to auto detect them.

---

### Post by presence1960 on 2009-12-01
> **darkod said:**
> First of all you have to figure out why your computer is not recognizing the 40GB drive when the 80GB is master. IDE drives usually had jumpers to select master/slave, are you adjusting that accordingly? Some of them were able to assign master/slave depending where on the ATA cable they are, but jumpers are much preferred.
This is a problem with your BIOS not seeing the drive, it has nothing to do with ubuntu.
If you do not manage to solve that problem, you can still use the option to install grub1 on the 40GB MBR, instead of current windows bootloader, because your BIOS can see both drives when the 40GB is master.

Also you might try buying another ATA cable and set both drives as master on the different IDE channels. And in some BIOSes after you make changes to the drives connections you need to enter the BIOS and see if they are recognized automatically, or sometimes even press Enter on some setting to auto detect them.
I agree this has nothing to do with Ubuntu. Your other disk is not recognized in the script either. So it definitely is either a BIOS or a disk hook up issue. I would start with the disks. How are they hooked to mobo. Is each plugged into it's own IDE socket ? Are you using jumpers to set the master/slave relationship or are you using a master/slave IDE cable? It is time to open your case and dig in there. If all that checks out then it is time to look at BIOS.

---

### Post by HeLzWright on 2009-12-01
The hook up is correct and everything checks out in every other case but the way that I would want it (ubuntu-80g and XP-40g)

I'm am considering switching OSs and HDDs (ubuntu-40g and XP-80g) only because I would rather not mess with my BIOS. I've tried diff settings in BIOS but if I have to flash the BIOS I'm going to have to say no because this is the last comp I have,(the older one is being converted to a server, they are old it's old, and I dont have the money to buy another MOBO.

I have a 500g external that I store my info on anyway so its not like its a big deal I just use ubuntu more and moving files can get a little annoying.

If i can do anything without flashing my BIOS that would be optimal. Thanks so far tho.

---

### Post by darkod on 2009-12-02
You can connect the drives in the working order, first 40GB win, second 80GB ubuntu. If we understood you correctly this way both of them are recognized.
To avoid windows starting right away from the first disk, just install grub2 on that MBR too.

If you need help with the exact commands, connect the drives in the above order, then boot with the ubuntu cd, select Try Ubuntu, and do the thing with the script once more.
We need some data from it but when both drives are there.

And this time please make sure when you copy the text from the script, select the whole text once more and click the # icon in the toolbar when you write the posting, that will put CODE tags around the results. Much easier to read like that.

---

### Post by HeLzWright on 2009-12-03
Ok so I did all of my upgrades for ubuntu and the drive seems to magically work and everything is fine but.... My computer has eyes now... (the green moves back a forth)

---

### Post by HeLzWright on 2009-12-03
AHA!! I Win! Finally all updated and both ubuntu and xp are working and no more bars!

thx recovery mode!

Hey thanks everyone so f'n much! muahahahaha I love my computer now!:D

---

### Post by HeLzWright on 2009-12-03
Ok now my life sucks.... ubuntu won't load xp still can byitself I think it has something to do with nividia and grub I guess I need to do all of my upgrades before I try and Dual Boot... I'm going to try wipe and intall 9.10 first on the 80g and upgrade then try and boot up. If I can I will edit the menu.lst and try the dual boot option... I think part of it could be the external drive. Ill do everything with only ubuntu first since I know the windows drive works ill leave it unplugged and unused for now.

---

