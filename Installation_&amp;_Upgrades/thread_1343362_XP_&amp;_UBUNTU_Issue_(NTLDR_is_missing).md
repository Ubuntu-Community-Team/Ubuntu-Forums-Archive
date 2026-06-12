---
title: "XP &amp; UBUNTU Issue (NTLDR is missing)"
date: 2009-12-01
forum: Installation &amp; Upgrades
---

### Post by USB 3.0 on 2009-12-01
[B][COLOR=Red]EDIT:
SOLVED: [solution]("http://newyork.ubuntuforums.org/showpost.php?p=8425862&postcount=8")[/COLOR][/B]

Hello,
I have been using Ubuntu under wubi for a long time and I found it so good that I wanted to move it into a dedicated HDD, so I used LVPM to do it.
I have 2 HDDs in my PC:
The 1st one has two partitions (sda1 and sda2):
          (one with XP system & the other one is used to store other files)
The 2nd one (sdb) was not used so I moved Ubuntu to it.
But it seems that I can't run neither Ubuntu nor XP after this. All I get is an error saying "NTLDR is missing. Press CTRL+ALT+DEL to restart.". I can't even proceed to the old Choose an OS interface.
So I didn't have any choice but to restart. And I'm now posting from the LiveCD after changing BIOS to boot from CDROM.
This is the output of sudo fdisk -l:

> Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x15dee5da

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        9728    78140128+   7  HPFS/NTFS
/dev/sda2   *        9729       19457    78148192+   7  HPFS/NTFS

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xd2c4ac58

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       19457   156288321   83  LinuxThis is the menu.lst file located in /dev/sdb/boot/grub (I have done some tweaks with it):

> # menu.lst - See: grub(8), info grub, update-grub(8)
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
default        0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout        3

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
## password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
# password topsecret

#
# examples
#
# title        Windows 95/98/NT/2000
# root        (hd0,0)
# makeactive
# chainloader    +1
#
# title        Linux
# root        (hd0,1)
# kernel    /vmlinuz root=/dev/hda2 ro
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
# kopt=root=UUID=  ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=()/ubuntu/disks

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

title        Ubuntu 9.10, kernel 2.6.31-15-generic
root        ()/ubuntu/disks
kernel        /boot/vmlinuz-2.6.31-15-generic root=UUID=  ro quiet splash 
initrd        /boot/initrd.img-2.6.31-15-generic

title        Ubuntu 9.10, kernel 2.6.31-15-generic (recovery mode)
root        ()/ubuntu/disks
kernel        /boot/vmlinuz-2.6.31-15-generic root=UUID=  ro  single
initrd        /boot/initrd.img-2.6.31-15-generic

title        Ubuntu 9.10, kernel 2.6.31-14-generic
root        ()/ubuntu/disks
kernel        /boot/vmlinuz-2.6.31-14-generic root=UUID=  ro quiet splash 
initrd        /boot/initrd.img-2.6.31-14-generic

title        Ubuntu 9.10, kernel 2.6.31-14-generic (recovery mode)
root        ()/ubuntu/disks
kernel        /boot/vmlinuz-2.6.31-14-generic root=UUID=  ro  single
initrd        /boot/initrd.img-2.6.31-14-generic

title        Ubuntu 9.10, kernel 2.6.28-16-generic
root        ()/ubuntu/disks
kernel        /boot/vmlinuz-2.6.28-16-generic root=UUID=  ro quiet splash 
initrd        /boot/initrd.img-2.6.28-16-generic

title        Ubuntu 9.10, kernel 2.6.28-16-generic (recovery mode)
root        ()/ubuntu/disks
kernel        /boot/vmlinuz-2.6.28-16-generic root=UUID=  ro  single
initrd        /boot/initrd.img-2.6.28-16-generic

title        Ubuntu 9.10, kernel 2.6.28-15-generic
root        ()/ubuntu/disks
kernel        /boot/vmlinuz-2.6.28-15-generic root=UUID=  ro quiet splash 
initrd        /boot/initrd.img-2.6.28-15-generic

title        Ubuntu 9.10, kernel 2.6.28-15-generic (recovery mode)
root        ()/ubuntu/disks
kernel        /boot/vmlinuz-2.6.28-15-generic root=UUID=  ro  single
initrd        /boot/initrd.img-2.6.28-15-generic

title        Ubuntu 9.10, kernel 2.6.28-11-generic
root        ()/ubuntu/disks
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=  ro quiet splash 
initrd        /boot/initrd.img-2.6.28-11-generic

title        Ubuntu 9.10, kernel 2.6.28-11-generic (recovery mode)
root        ()/ubuntu/disks
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=  ro  single
initrd        /boot/initrd.img-2.6.28-11-generic

title        Ubuntu 9.10, memtest86+
root        ()/ubuntu/disks
kernel        /boot/memtest86+.bin

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title        Microsoft Windows XP Professional
rootnoverify    (hd0,0)
savedefault
chainloader    +1


# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root


title UnknownOS
root (hd0,1)
makeactive
chainloader +1
boot


title Microsoft Windows XP Professional
root (hd?,?)
makeactive
chainloader +1
map (hd0) (hd1)
map (hd1) (hd0)


# title Microsoft Windows XP Professional
# root (hd0,0)
# makeactive
# chainloader +1
# boot


---

### Post by phillw on 2009-12-01
As you're already on the Live CD - re-initialing Grub2 is covered over here -->  [http://ubuntuforums.org/showthread.php?t=1195275&highlight=drs305](http://ubuntuforums.org/showthread.php?t=1195275&highlight=drs305)

Yeah, it seems scary - but i can assure that it works - from personal experiance !!

Regards,

Phill.

---

### Post by USB 3.0 on 2009-12-02
Thank you Phill,
But from the link you provided, it seems what I have is GRUB and not GRUB2. Is there a guide for it?

---

### Post by darkod on 2009-12-02
Grub2 is much better than grub anyway. But another thing I'm worried about.
You can see from your menu.lst in the listing of the kernels has
root ()/ubuntu/disks

I guess this is because of moving actualy wubi installation. Have no experience with this procedure but that looks like you're asking for trouble long term. Unless you have some specific setup on your ubuntu that you will need days to recreate, I would seriously consider just reinstalling 9.10 over everything (sdb).

Wubi in fact is only to try ubuntu, it is not recommended to get at a stage that you want to save/move wubi installation. Not to sound like I'm telling you what to do but in case you really wanted to save your installation you should have moved away from wubi ages ago.

Repairing the windows MBR to get windows booting is easy. Just use an XP disc and fix the MBR.
After that you might try this: first set in BIOS your ubuntu drive to be first in boot order. Then reinstall grub2 to the MBR of the ubuntu disk and because it will be first in boot order grub2 will start from there. Your windows disk MBR is intact.
Note: I can't guarantee this would work because of the wubi moving you made. On standard ubuntu installations works perfectly. You might need more tweaking in your case.

---

### Post by darkod on 2009-12-02
Looking more closely it doesn't seem grub reinstall can help you at all.
Using the LiveCD open the sdb1 partition. It seems moving wubi actually formatted the whole drive as one single big partition, and I guess puts an image file sort of like virtual machine that will run wubi.
Open sdb1 and look inside. If you get the standard folder structure, that's means I'm wrong. But if all you see is onr or few big image files, that have your wubi installation actually packed inside, I can't see how standard grub configuration can read them. I don't know of a way, at least.

---

### Post by USB 3.0 on 2009-12-02
Hello, darkod
Actually sdb1 has the standard linux file structure (i.e. boot, usr, home ..etc). not those wubi .disk files. It's filesystem is ext3.
I managed to get XP to boot with no problems (unless you consider not showing the Ubuntu partition a problem) after a quick search in the forum. I also changed root ()/ubuntu/disks to root (hd1,0) and got the ubuntu splash logo to appear (the first white one in Karmic) and then It kept showing nothing black and an error screen appears if you press any key saying something like:

> usplash: Setting mode 1152x864 failed
usplash: Using mode 1024x768
Gave up waiting for root device. Common problems:
- boot args (cat /proc/cmdline)
 - Check rootdelay= (did the system wait long enough?)
 - Check root= (did the system wait for the right device?)
- Missing modules (cat /proc/modules; ls /dev)
ALERT! /dev/disk/by-uuid/ does not exist. Droppingto a shell!


BusyBox v1.13.3 (Ubuntu 1:1.13.3-1ubuntu7) built-in shell (ash)
Enter 'help' for a list of built-in commands.

(initramfs) _

---

### Post by darkod on 2009-12-02
If the process actually "unpacked" wubi into standard installation even better.
You might actually try installing grub2 then. Because it will be missing grub.cfg file (you never had grub2 before), try this procedure in terminal booted from LiveCD:
[http://ubuntuguide.net/how-to-restore-grub-2-after-reinstalling-windows-xpvistawin7](http://ubuntuguide.net/how-to-restore-grub-2-after-reinstalling-windows-xpvistawin7)

Look under number 2) Using Ubuntu 9.10 LiveCD

The first few lines reinstall grub2 but since you never had grub.cfg you will need the additional 5-6 lines as per the article. Make sure you install it on /dev/sdb and your root should be /dev/sdb1. Switch the BIOS order of the drives before that if you already didn't.

---

### Post by USB 3.0 on 2009-12-02
> **darkod said:**
> Switch the BIOS order of the drives before that if you already didn't.
Thank you darkod, but how to do this? I'm not really familiar with these places.
EDIT: [SOLVED]
Oh, never mind. I managed to get it to work by changing "root ()/ubuntu/disks" into "root (hd1,0)" and then adding "/dev/sdb1" (no quotes) after "root=UUID=" in menu.lst
These variables depend on your system. Do a "sudo fdisk -l" to see your values.
darkod, Phill, Thank you very much for your help. :D

---

### Post by phillw on 2009-12-02
> **USB 3.0 said:**
> Thank you darkod, but how to do this? I'm not really familiar with these places.

As you computer boots up- you will quickly see, Press xxx for Setup/BIOS, xxx can be esc, F2, F12 etc. - you need to keep your wits about you, as it flashes by pretty quick !!

Once in BIOS, go to the drives boot priority area, and you will see the Boot order of devices. If you don't mind the couple of second delay, set you CD/DVD drive as boot #1, and your SECOND disk as boot#2. The methods of doing so differ - but there will be instructions on that screen as to how to (typically using the + button to move a device up and - to move it down).
Then select Save & exit. (Again typically F10 - but it may be different)

Regards,

Phill.

---

