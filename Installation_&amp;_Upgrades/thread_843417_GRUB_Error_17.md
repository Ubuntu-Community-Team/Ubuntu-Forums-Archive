---
title: "GRUB Error 17"
date: 2008-06-28
forum: Installation &amp; Upgrades
---

### Post by Cmdt_Carpenter on 2008-06-28
[CONFLICT RESOLVED!]

Yes, the dreaded Error 17. (Or at least for me it is)

So, let's start from the very beginning...

A few days ago, some of my friends recommended Ubuntu to me to try out, since it's so awesome. I thought, "Well, this might be kind of fun, I guess I'll go get it," and indeed I did. I burned the CD (At max speed) and installed Ubuntu without trying it out first. (Hey, I could just dual-boot) This is where the first snag comes into play: when I attempted to start Ubuntu, it would not work. I don't even think an error appeared, it was just nothing. So I rebooted into Windows and tried again. Still wouldn't work, but this time, when I tried to boot Windows, it flashed a blue screen of death and rebooted. So, long story short there, we reinstalled Windows. But I would not be defeated so easily. Oh no, I found my Ubuntu disc, reburned it at 4x, and I started the trial this time. So, kind of cool. I decided to install it inside the computer again, this time partitioned away from Windows so as not to kill it again. What happened? Windows was torched again. On top of that, Ubuntu does not work. At the moment I am writing this using the trail version of Ubuntu on the disc, and all I get when I try to boot up Ubuntu is the GRUB Error 17, cannot find selected partition. Though I have not exhausted every possibility of salvaging the thing yet, I thought posting something here would really help me in my search. Keep in mind that I have only the resources available on the trial disc.

I have downloaded GParted, cannot download Wine for some reason, set up my hard drives properly, and still have all my files on the second drive I use for games and such. (I am willing to try anything for the Ubuntu; all my programs are safe on another hard drive so I can screw up this one all I want) I do not know how to tell GRUB to change its root to hd#,# and I don't even know what my various drives are in the hd format. Basically, I'm flying blind. My first course of action for now is reinstall GRUB, but since I have no idea what I'm doing whatsoever, I just might screw that up.

Today I have been working since about 9:50 AM GMT -5 to get this working. That's about 6 hours so far, and I'm not much closer to my solution. If you need anything from the terminal on my computer, just tell me the command I need to use and I'll try to get it ASAP.

---

### Post by housam on 2008-06-28
Type in the terminal 
```
sudo fdisk -l
```
Where -l is the lower case of L . and post the results

---

### Post by Cmdt_Carpenter on 2008-06-28
```
Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x2ba06fcc

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         522     4192933+   5  Extended
/dev/sda2             523       38914   308374528    7  HPFS/NTFS
Partition 2 does not end on cylinder boundary.
/dev/sda5               1         522     4192902    b  W95 FAT32

Disk /dev/sdb: 74.3 GB, 74355769344 bytes
255 heads, 63 sectors/track, 9039 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xde96f2db

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        1300    10442218+  83  Linux
/dev/sdb2            8667        9039     2996122+   5  Extended
/dev/sdb3            1301        8666    59167395    b  W95 FAT32
/dev/sdb5            8667        9039     2996091   82  Linux swap / Solaris

Partition table entries are not in disk order

```

And I can't get GRUB reinstalled since the stuff for the disc is an exe.

And (again) am I right in assuming that one of those devices should be the one I need to tell GRUB to boot from?

---

### Post by housam on 2008-06-28
boot from the live cd
```
sudo grub
```
grub >
then type the following and press enter:
```
find /boot/grub/stage1
```
this will give where grub should be. in your case it should be (h1,0)
then type
```
root (hd1,0)
```
then type 
```
setup (hd1)
```
then type
```
quit
```
reboot . grub should be installed in the correct partition.

---

### Post by Cmdt_Carpenter on 2008-06-28
Oh my God, I love you.

EDIT: Okay, so I'm assuming that wasn't all I had to do? I still get the "Cannot mount selected partition" error.

---

### Post by housam on 2008-06-28
mount the selected partition sdb1. type in the terminal 
```
mkdir /mnt/root
```
then
```
mount -t ext3 /dev/hdb1 /mnt/root
```
then reinstall grub

---

### Post by Cmdt_Carpenter on 2008-06-28
```
mkdir: cannot create directory `/mnt/root': Permission denied
```

What I get when I type 

```
mkdir /mnt/root
```

EDIT: Wait a second. Now I get this:

```
mkdir: cannot create directory `/mnt/root': File exists

```

Hm...So maybe I just need to reinstall GRUB...

Wait...I'll check what happens when I try to mount the Linux drive again

When I try to mount the drive it says:

```
mount: only root can do that
```

I do believe I got the mkdir to work by adding sudo to the front...

EDIT: Adding sudo to the mount command gives me:

```
mount: special device /dev/hdb1 does not exist

```

EDIT: Did you mean sdb1, not hdb1?

---

### Post by housam on 2008-06-28
use sudo in front of each code line.
and you get nothing after entering the codes . if they have been accepted safely , reinstall grub.

---

### Post by housam on 2008-06-28
> **Cmdt_Carpenter said:**
> ```
mkdir: cannot create directory `/mnt/root': Permission denied
```

What I get when I type 

```
mkdir /mnt/root
```

EDIT: Wait a second. Now I get this:

```
mkdir: cannot create directory `/mnt/root': File exists

```

Hm...So maybe I just need to reinstall GRUB...

Wait...I'll check what happens when I try to mount the Linux drive again

When I try to mount the drive it says:

```
mount: only root can do that
```

I do believe I got the mkdir to work by adding sudo to the front...

EDIT: Adding sudo to the mount command gives me:

```
mount: special device /dev/hdb1 does not exist

```

EDIT: Did you mean sdb1, not hdb1?

Big sorry . it is a [COLOR="Red"]sdb1[/COLOR] not hdb1

---

### Post by Cmdt_Carpenter on 2008-06-28
Okay, thank you very much, I'm going to try this now and see if it works...

---

### Post by Cmdt_Carpenter on 2008-06-28
Okay, same error. I have no idea what kind of questions I could ask now, except reiterate a few facts.

GRUB is installed in (hd1,0) which I am assuming is the Linux system drive. Although the system drive is formatted properly to ext3, GRUB cannot mount it properly.

Whaaaaaaa?!

---

### Post by housam on 2008-06-28
we can check your grub menu . type in the terminal 
```
gksu gedit /boot/grub/menu.lst
``` and post the results.

---

### Post by Cmdt_Carpenter on 2008-06-28
Okay, when I put the command in the terminal, the text editor showed nothing when it came up. However, when I went to the Linux drive, opened boot/grub/menu.lst, I came up with this:

```
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
# kopt=root=UUID=0fbc8e14-6ef6-4667-9ad2-03753e7131bc ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd1,0)

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

title		Ubuntu 8.04, kernel 2.6.24-16-generic
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=0fbc8e14-6ef6-4667-9ad2-03753e7131bc ro quiet splash
initrd		/boot/initrd.img-2.6.24-16-generic
quiet

title		Ubuntu 8.04, kernel 2.6.24-16-generic (recovery mode)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=0fbc8e14-6ef6-4667-9ad2-03753e7131bc ro single
initrd		/boot/initrd.img-2.6.24-16-generic

title		Ubuntu 8.04, memtest86+
root		(hd1,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST
```

Man...I just want to say I appreciate all this help a lot. I know you've probably got better things to do than help a total n00b get this done...But I'm really, really grateful for all this...

I think I may actually take a break...8 solid hours of work can do that to a person...

---

### Post by housam on 2008-06-28
I only want you to get it working .Your menu .lst is fine .
try to reinstall grub using this code.
```
sudo grub-install --root-directory=/mnt/root /dev/sdb
```

---

### Post by housam on 2008-06-28
If the above code does not work . then you may have to readjust your Bios settings . as you may have a combination of SATA and IDE drives. 
Read [[COLOR="Red"]_this link_[/COLOR]]("http://users.bigpond.net.au/hermanzone/p15.htm#17") after a break .it may help

---

### Post by Cmdt_Carpenter on 2008-06-28
Okay...so...

It worked. Ubuntu started up with no errors. The only thing I think I have to do is choose the boot device myself whenever the computer starts up. Thank you so much.

I'm going to bookmark this in case I have any problems again and I can't remember what to do.

Now I have to figure out how to get sound and get Ubuntu to raise the resolution above 800x600.

---

