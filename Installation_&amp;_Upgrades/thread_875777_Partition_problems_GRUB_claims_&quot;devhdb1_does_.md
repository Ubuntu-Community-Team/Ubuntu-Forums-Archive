---
title: "Partition problems: GRUB claims &quot;/dev/hdb1 does not exist&quot;"
date: 2008-07-31
forum: Installation &amp; Upgrades
---

### Post by LTsky on 2008-07-31
Hi everbody!
Wasn't sure exactly where to put this,but this seems an appropriate enough place.

About a week ago, I installed a Windows XP partition on my hard-drive with the aid of my Ubuntu 6.06 live cd, and I managed to get grub to recognise Windows and that boots just fine. Swell. Problem is, when I try to boot my Kubuntu 8.04 partition, the system hangs for a few seconds before dropping me into the BusyBox shell.

The error I get is: 
(initramfs)ALERT! /dev/hdb1 does not exist.
However, when I use "cat /proc/cmdline", it gives me this:
root=/dev/hdb1 ro single.

Any assistance would be greatly appreciated. I miss my Kubuntu partition :(

---

### Post by Pumalite on 2008-07-31
Post:
sudo fdisk -lu

---

### Post by LTsky on 2008-07-31
Here ya go:
```
ubuntu@ubuntu:~$ sudo fdisk -lu

Disk /dev/hdb: 81.9 GB, 81964302336 bytes
255 heads, 63 sectors/track, 9964 cylinders, total 160086528 sectors
Units = sectors of 1 * 512 = 512 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1              63   132520184    66260061   83  Linux
/dev/hdb2   *   132520185   155541329    11510572+   7  HPFS/NTFS
/dev/hdb3       155541330   160071659     2265165    5  Extended
/dev/hdb5       155541393   160071659     2265133+  82  Linux swap / Solaris

```

---

### Post by LTsky on 2008-07-31
Bumping for possible answer

---

### Post by logos34 on 2008-07-31
try substituting 'root=UUID=XXXX-XXXX...' for '/dev/hdb1'

run any of these commands to find uuid:

sudo blkid

sudo vol_id /dev/hdb1

ls -l /dev/disk/by-uuid (hdb1 needs to be mounted for this one)

---

### Post by LTsky on 2008-07-31
> **logos34 said:**
> try substituting 'root=UUID=XXXX-XXXX...' for '/dev/hdb1'

run any of these commands to find uuid:

sudo blkid

sudo vol_id /dev/hdb1

ls -l /dev/disk/by-uuid (hdb1 needs to be mounted for this one)

Alright: but what do I do once I find this? Do I append it to the /boot/grub/menu.lst?

---

### Post by Pumalite on 2008-07-31
Mount your partition:
sudo mkdir /media/sdb1
sudo mount -t ext3 /dev/sdb1 /media/sdb1
Post:
cat /media/sdb1/boot/grub/menu.lst

---

### Post by logos34 on 2008-07-31
> **LTsky said:**
> 
However, when I use "cat /proc/cmdline", it gives me this:
root=/dev/hdb1 ro single.

cat /proc/cmdline prints out the 'kernel' line in /boot/grub/menu.lst--that's where you replace the  'root=/dev/hdb1' with 'root=UUID=XXX...'.  Mount / like Pumalite suggested.

That may or may not solve the error you're getting

---

### Post by LTsky on 2008-07-31
Thank you both for your help. Here is my menu.lst

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
# WARNING: If you are using dmraid do not change this entry to 'saved' or your
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
# kopt=root=UUID=5508d276-7d92-414d-8364-fe58acb3ab02 ro

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
# howmany=1

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

title           Ubuntu 8.04.1, kernel 2.6.24-19-386
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.24-19-386 root=/dev/hdb1 ro quiet splash
initrd          /boot/initrd.img-2.6.24-19-386
quiet

title           Ubuntu 8.04.1, kernel 2.6.24-19-386 (recovery mode)
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.24-19-386 root=/dev/hdb1 ro single
initrd          /boot/initrd.img-2.6.24-19-386

title           Ubuntu 8.04.1, memtest86+
root            (hd0,0)
kernel          /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.

title Windows XP
root  (hd0,1)
makeactive
chainloader +1

```

---

### Post by Pumalite on 2008-07-31
Now post:
sudo blkid

---

### Post by LTsky on 2008-07-31
Righty-o.

```
ubuntu@ubuntu:~$ sudo blkid
/dev/hdb1: UUID="5508d276-7d92-414d-8364-fe58acb3ab02" SEC_TYPE="ext2" TYPE="ext3"
/dev/hdb2: TYPE="ntfs"
/dev/hdb5: TYPE="swap" UUID="a0150b78-e1e1-4458-9f57-0903bc00b413"
/dev/evms/hdb1: UUID="5508d276-7d92-414d-8364-fe58acb3ab02" SEC_TYPE="ext2" TYPE="ext3"
/dev/evms/hdb2: TYPE="ntfs"
/dev/evms/hdb5: TYPE="swap" UUID="a0150b78-e1e1-4458-9f57-0903bc00b413"

```

---

### Post by Pumalite on 2008-07-31
In menu.lst; substitute 'root=/dev/hdb1'
For this:
root=5508d276-7d92-414d-8364-fe58acb3ab02
I have a couple of comments: if Ubuntu is in hdb1; then 'root' should be (hd1,0); 2nd: you should use a -generic kernel

---

### Post by logos34 on 2008-07-31
> **LTsky said:**
> Righty-o.

```
ubuntu@ubuntu:~$ sudo blkid
/dev/hdb1: UUID="5508d276-7d92-414d-8364-fe58acb3ab02" SEC_TYPE="ext2" TYPE="ext3"
/dev/hdb2: TYPE="ntfs"
/dev/hdb5: TYPE="swap" UUID="a0150b78-e1e1-4458-9f57-0903bc00b413"
/dev/[COLOR=Red]evms[/COLOR]/hdb1: UUID="5508d276-7d92-414d-8364-fe58acb3ab02" SEC_TYPE="ext2" TYPE="ext3"
/dev/[COLOR=Red]evms[/COLOR]/hdb2: TYPE="ntfs"
/dev/[COLOR=Red]evms[/COLOR]/hdb5: TYPE="swap" UUID="a0150b78-e1e1-4458-9f57-0903bc00b413"

```

Oh, so you're running Evms--should have said so from the start, or maybe you didn't know.

Support for it has been officially dropped, and users are advised to unistall it.  You might want to read the problems associated with it here:
[https://wiki.ubuntu.com/Evms](https://wiki.ubuntu.com/Evms)

On the other hand it wouldn't hurt to try Pumalite's suggestion
'root (hd**1**,0)' instead of (hd0,0) -- I just noticed your 'groot' line doesn't match:

> ## default grub root device
## e.g. groot=(hd0,0)
**# groot=(hd[COLOR=Red]1[/COLOR],0)**Maybe changing that will fix it.  But you really should lose the Evms.

---

### Post by LTsky on 2008-08-01
Thanks for the suggestions guys: I'll get right on it!

Like I say, I didn't even know I had EVMS installed on my system, though if I re-call correctly, it did mention something about it when I was booting via my 6.06 Ubuntu Live CD. How would I go about removing it?

UPDATE: Just editing the root line in the menu.lst, now I'm getting this:

Begin: mounting root filesystem...
/init: /init: i60: Syntax error: 0x5508d276-7d92-414d-8364-fe58acb3ab02
[ 19.2777519] Kernel panic - not syncing: Attempting to kill init!
Any ideas?

---

### Post by logos34 on 2008-08-01
Are you still running Dapper or did you upgrade?  

If the former, I'd upgrade to gutsy or later release, and tell it to remove evms.  (see the wiki link I gave you)


see also:
[http://ubuntuforums.org/showpost.php?p=3976387&postcount=4http://ubuntuforums.org/showpost.php?p=3976387&postcount=4](http://ubuntuforums.org/showpost.php?p=3976387&postcount=4http://ubuntuforums.org/showpost.php?p=3976387&postcount=4)

[http://blog.andrewbeacock.com/2008_01_01_archive.html](http://blog.andrewbeacock.com/2008_01_01_archive.html)

[http://codepoets.co.uk/upgrade-ubuntu-gutsy-emvs-and-udevd-100-cpu-usage-aka-udevd-going-nuts](http://codepoets.co.uk/upgrade-ubuntu-gutsy-emvs-and-udevd-100-cpu-usage-aka-udevd-going-nuts)

---

### Post by LTsky on 2008-08-01
At present, I'm running Gutsy as my Linux partition. I'm using the Dapper Live CD because that was the one I used for my first CD install. I've upgraded to every version up till present.

---

### Post by logos34 on 2008-08-01
then I'd upgrade to Hardy and accept the option to remove evms.

[(--> 'But Evms is still installed')]("https://wiki.ubuntu.com/Evms")

---

### Post by LTsky on 2008-08-01
Wait, hang on, I think I've made a bit of a cock up. I meant to say that the my current Linux parition is **Hardy** rather than Gutsy. Sorry about the error

---

### Post by logos34 on 2008-08-01
then you'll have to manually uninstall the evms pkg

---

