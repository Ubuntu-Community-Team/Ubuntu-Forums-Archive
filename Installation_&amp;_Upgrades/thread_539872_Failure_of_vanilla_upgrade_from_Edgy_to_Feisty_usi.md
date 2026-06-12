---
title: "Failure of vanilla upgrade from Edgy to Feisty using Update Manager"
date: 2007-08-31
forum: Installation &amp; Upgrades
---

### Post by pcalnon on 2007-08-31
Hi all,

I've been running Edgy on a pretty vanilla system (Intel P4 1.5Ghz, 256M ram, 75G hd) for the past several months without any problems.  Two days ago, I attempted to upgrade the distro to Feisty using the Update Distro button in the Update Manager.  The upgrade went smoothly through the download and install process until after the initial reboot.  

At this point, things started getting weird.  The system appeared to boot into the login screen of some alternate windows manager (looked vaguely like openwin from my unix days but was definitely not gnome with the default Ubuntu settings that I had been using) and displayed a blank (light grey) screen after login.  At this point, mouse and keyboard worked, and ctrl-alt-del called up the system monitor, but no menus or desktops were displayed.  I restarted X (ctrl-alt-bksp) and got the default Ubuntu login.  I then restarted the machine by selecting restart from the options menu from the Ubuntu login dialog box.

Then all hell broke loose.  The os load hung almost immediately and then, after a suitably nerve-wracking delay, dropped me into the busybox shell and gave me the good news that the hard drive /dev/hda couldn't be found.  I rebooted and selected the recovery kernel from grub to try to see what was going on.  The additional output confirmed the problem.  Everything worked until the attempt to start up hda.  Again, /dev/hda could not be found; the startup aborted and dropped me into the busybox shell.

Much googling later, it appears that there was a well-know and apparently similar problem for breezy to dapper upgrades.  At least as far as i could discover, however, this hasn't been observed for edgy to feisty upgrades.  My system is about as vanilla as they come--no exotic hardware, no strange lvm or raid stuff, no bleeding edge code at all.  The Feisty live cd does boot flawlessly and allows me to access the hard drive.  So if anyone has any solutions or ideas about how to proceed, I should be able to get system up and running.  Also, I'd rather not wipe the drive and do a clean install unless I have to.  There's enough data on the hd that backing it up prior to the clean install would be cumbersome.  Has anyone else seen this?  Any ideas about how to fix this?  Worth a bug report?

Thanks in advance,
Paul Calnon

---

### Post by Pumalite on 2007-08-31
The upgrade changed your menu.lst
Get in with the live CD, mount your partition ( filesystem) and post:
sudo fdisk -l
cat /boot/grub/menu.lst
blkid

---

### Post by pcalnon on 2007-08-31
Thanks for the quick response, Pumalite.

Ran the commands you mentioned in your previous e-mail.  The results are included below.  

At first glance, it looks like menu.lst refers to my hd partitions as /dev/**h**da1, etc. while fdisk and blkid see my hd partitions as /dev/**s**da1, etc.  Is this what's causing the problem?  And how could this have only happened during my install and not anyone else's?  Is the fix as simple as editing menu.lst, or is there more to it?

Thanks in advance,
Paul Calnon


**sudo fdisk -l**

root@ubuntu:/home/ubuntu# fdisk -l
Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9636    77401138+  83  Linux
/dev/sda2            9637        9729      747022+   5  Extended
/dev/sda5            9637        9729      746991   82  Linux swap / Solaris


**blkid**

root@ubuntu:/media/disk/boot/grub# blkid
/dev/sda1: UUID="3ffe6293-45d3-4064-9725-b37204e29573" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda5: UUID="cfc8e01d-5534-47ae-88e6-987321f53f29" TYPE="swap" 


**cat /boot/grub/menu.lst**

root@ubuntu:/media/disk/boot/grub# cat menu.lst
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
# WARNING: If you are using dmraid do not change this entry to 'saved' or your
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
# kopt=root=UUID=3ffe6293-45d3-4064-9725-b37204e29573 ro
# kopt_2_6=root=/dev/hda1 ro

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

title           Ubuntu, kernel 2.6.17-12-generic
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.17-12-generic root=/dev/hda1 ro quiet splash
initrd          /boot/initrd.img-2.6.17-12-generic
quiet
savedefault
boot

title           Ubuntu, kernel 2.6.17-12-generic (recovery mode)
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.17-12-generic root=/dev/hda1 ro single
initrd          /boot/initrd.img-2.6.17-12-generic
boot

title           Ubuntu, kernel 2.6.17-11-generic
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.17-11-generic root=/dev/hda1 ro quiet splash
initrd          /boot/initrd.img-2.6.17-11-generic
quiet
savedefault
boot

title           Ubuntu, kernel 2.6.17-11-generic (recovery mode)
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.17-11-generic root=/dev/hda1 ro single
initrd          /boot/initrd.img-2.6.17-11-generic
boot

title           Ubuntu, kernel 2.6.17-10-generic
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.17-10-generic root=/dev/hda1 ro quiet splash
initrd          /boot/initrd.img-2.6.17-10-generic
quiet
savedefault
boot

title           Ubuntu, kernel 2.6.17-10-generic (recovery mode)
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.17-10-generic root=/dev/hda1 ro single
initrd          /boot/initrd.img-2.6.17-10-generic
boot

title           Ubuntu, memtest86+
root            (hd0,0)
kernel          /boot/memtest86+.bin
quiet
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

---

### Post by merlinus on 2007-08-31
All this looks good, but your UUIDs may have changed.

Check entries in /etc/fstab with results from blkid.

-merlin

---

### Post by pcalnon on 2007-09-01
Hi merlinus,

I compared the UUIDs from blkid to the ones in fstab, and it looks like they're the same.  

Is it a problem that fstab refers to the root partition as hda1 while blkid sees the root partition as sda1?

Thanks,
Paul Calnon


root@ubuntu:/media/disk/etc# blkid
/dev/sda1: UUID="3ffe6293-45d3-4064-9725-b37204e29573" SEC_TYPE="ext2" TYPE="ext3"
/dev/sda5: UUID="cfc8e01d-5534-47ae-88e6-987321f53f29" TYPE="swap"


root@ubuntu:/media/disk/etc# cat ./fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda1
UUID=3ffe6293-45d3-4064-9725-b37204e29573 /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda5
UUID=cfc8e01d-5534-47ae-88e6-987321f53f29 none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/           /media/floppy0  auto    rw,user,noauto  0       0

# Generated by Automatix
## End of Automatix mounted partitions

---

### Post by merlinus on 2007-09-01
It should not matter because /etc/fstab is using UUIDs, not hdas nor sdas.

But it would not hurt to change the entries and restart.

-merlin

---

### Post by merlinus on 2007-09-01
Also, if you are using Feisty, do the upgrades, which will install the latest -16 kernel.

That may solve the problems.

If not, I suggest a reinstall using the Alternate text-based cd, of course after backing up your data!

-merlin

---

### Post by pcalnon on 2007-09-01
Hello all,

I tried modifying the menu.lst entries that referred to hda1 and hda5 to sda1 and sda5, but as merlin predicted this didn't solve the problem.

How do I go about updating the kernel used by the os on my hd after booting from live cd?  As I mentioned earlier, I can mount the partitions on my hd and access them from the live cd boot, but I'm not sure how to do the kernel update manually.

Is there anything else that I can do that might fix this problem?

Thanks in advance,
Paul Calnon

---

### Post by merlinus on 2007-09-01
You can search for the -16 kernel using Synaptic, but I wonder if it will install correctly even if your ubuntu partition is mounted via the live cd.

No harm in trying, at this point.

BUt why not do as I suggested?  Back up data, and reinstall via Alternate cd.

FWIW, a goodly number of folks have problems with upgrading to a new version versus a fresh install.

-merlin

---

### Post by pcalnon on 2007-09-02
Thanks for the help, merlin and Pumalite.

Took merlin's advice, backed up, and performed a clean install.  System seems to be working flawlessly now.

Thanks again,
Paul Calnon

---

### Post by merlinus on 2007-09-02
Glad to hear that you are up-and-running.  Enjoy!

-merlin

---

