---
title: "[SOLVED] grub boots vista &amp;amp; not ubuntu"
date: 2007-09-04
forum: Installation &amp; Upgrades
---

### Post by Bethrine on 2007-09-04
Hey all,

I have finally got grub on the mbr and properly configured to boot either vista or the linux kernal. I used this...

sudo grub
find /boot/grub/stage1
root (hdx,y)
setup (hdx)
quit

Now, however, linux won't finish booting. Please help! I am using the live CD.

---

### Post by thelocust on 2007-09-04
does it give you any errors or just freezes? Also try booting in recovery mode.

---

### Post by Bethrine on 2007-09-04
I think it gives me errors during the boot cycle, something about the kernal? I don't know how to do a boot into recovery mode on linux. Vista is fine...it's the linux I'm having the problem with.

I'll try rebooting now to see what the error is...I feel silly .

---

### Post by Bethrine on 2007-09-04
okay, I restarted in "safe" mode (found it) and got this error...

'bin/sh: can't access tty :  job control turned off

by the way, I have a SATA II drive and vista boots at (hd0,0) and ubuntu at (hd0,1)

---

### Post by thelocust on 2007-09-04
Hey Grubs a whore. One of the option when selecting which OS to boot should have (Recovery Mode) at the end.

---

### Post by Bethrine on 2007-09-04
lol, I used the recovery mode and I got the...

'bin/sh: can't access tty : job control turned off

---

### Post by thelocust on 2007-09-04
Can you boot a previous kernel. There should be a couple options in grub. also check out [this thread]("http://ubuntuforums.org/showthread.php?t=292533"), looks like post #7 is your answer.

---

### Post by Bethrine on 2007-09-04
that looks good to me but now I can't get into grub, I tried...

gksudo gedit /boot/grub/menu.lst

It opens a menu.lst, but it is empty

I can't boot a previous kernal either and I also get these when I try to boot the first one (the one that's been booting..er or not booting) so I am trying to use the live cd...

cannot read /etc/fstab:no such file order

and

target file system doesn't have /sbin/init 

followed by the 'bin/sh stuff. I'm a newb, but could this be because grub is now in the mbr? Correct me if I am wrong, definately.

---

### Post by rsambuca on 2007-09-04
You will be able to edit your files from the liveCD, if you have one handy.

---

### Post by Bethrine on 2007-09-04
I'm in it now..

I got this far...

grub> root
 (fd0): Filesystem type unknown, partition type 0x0

if that's getting anywhere.

In terminal, Where it usually has my computer and user name it just has ubuntu@ubuntu:$~  does that make a difference?

---

### Post by Bethrine on 2007-09-04
bump

---

### Post by Bethrine on 2007-09-04
Aside: Hi rambusca, thanks for getting me my pics last time!

---

### Post by Bethrine on 2007-09-04
:~$ sudo fdisk -l

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        7699    61842186    7  HPFS/NTFS
/dev/sda2            7700       14408    53890042+  83  Linux
/dev/sda3           14409       14593     1486012+   5  Extended
/dev/sda5           14409       14593     1485981   82  Linux swap / Solaris
ubuntu@ubuntu:~$ sudo mount /dev/sda/1
mount: can't find /dev/sda/1 in /etc/fstab or /etc/mtab
ubuntu@ubuntu:~$ sudo mount /dev/sda1 /mnt
mount: /dev/sda1 already mounted or /mnt busy
mount: according to mtab, /dev/sda2 is already mounted on /mnt
ubuntu@ubuntu:~$ gksudo gedit /boot/grub/menu.lst

<groan> help please??

(gedit:9416): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.
ubuntu@ubuntu:~$ sudo mount /dev/sda/2 /mnt
mount: special device /dev/sda/2 does not exist
       (a path prefix is not a directory)

ubuntu@ubuntu:~$ sudo mount /root /mnt
mount: /root is not a block device
ubuntu@ubuntu:~$ sudo mount /vista /mnt
mount: special device /vista does not exist
ubuntu@ubuntu:~$

---

### Post by Bethrine on 2007-09-04
Okay! I got into my ubuntu! I restarted and in the boot menues, temporarily edited the kernal to start with (hd0,1) as (hd0,0) is the vista partition. Then I edited to start /dev/sda/2 and it worked! So now, can anyone tell me how to permanently configure grub with these settings in the menu so I can just tell it where to boot linux on startup instead of having to edit every single time for linux?  Here is my menu.lst...

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
default		0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		25

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

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## ## End Default Options ##

title		Ubuntu, kernel 2.6.15-29-386
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.15-29-386 root=/dev/sda3 ro quiet splash
initrd		/boot/initrd.img-2.6.15-29-386
savedefault
boot

title		Ubuntu, kernel 2.6.15-29-386 (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.15-29-386 root=/dev/sda3 ro single
initrd		/boot/initrd.img-2.6.15-29-386
boot

title		Ubuntu, kernel 2.6.15-28-386
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.15-28-386 root=/dev/sda3 ro quiet splash
initrd		/boot/initrd.img-2.6.15-28-386
savedefault
boot

title		Ubuntu, kernel 2.6.15-28-386 (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.15-28-386 root=/dev/sda3 ro single
initrd		/boot/initrd.img-2.6.15-28-386
boot

title		Ubuntu, kernel 2.6.15-26-386
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.15-26-386 root=/dev/sda3 ro quiet splash
initrd		/boot/initrd.img-2.6.15-26-386
savedefault
boot

title		Ubuntu, kernel 2.6.15-26-386 (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.15-26-386 root=/dev/sda3 ro single
initrd		/boot/initrd.img-2.6.15-26-386
boot

title		Ubuntu, memtest86+
root		(hd0,2)
kernel		/boot/memtest86+.bin 
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title           Other operating systems:
root
# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title           Windows Vista
root            (hd0,1)
savedefault
makeactive
chainloader     +1


and here is my fdisk -l

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        7699    61842186    7  HPFS/NTFS
/dev/sda2            7700       14408    53890042+  83  Linux
/dev/sda3           14409       14593     1486012+   5  Extended
/dev/sda5           14409       14593     1485981   82  Linux swap / Solaris

I really want grub properly configured! Please see my first post too! And thanks all! I am REALLY looking forward to marking this one solved!

---

### Post by thelocust on 2007-09-04
This should do it i think. 

title		Ubuntu, kernel 2.6.15-29-386
root		(hd0,[COLOR=Red]**1**[/COLOR])
kernel		/boot/vmlinuz-2.6.15-29-386 root=/dev/sda3 ro quiet splash
initrd		/boot/initrd.img-2.6.15-29-386
savedefault
boot

title		Ubuntu, kernel 2.6.15-29-386 (recovery mode)
root		(hd0,[COLOR=Red]**1**[/COLOR])
kernel		/boot/vmlinuz-2.6.15-29-386 root=/dev/sda3 ro single
initrd		/boot/initrd.img-2.6.15-29-386
boot

title		Ubuntu, kernel 2.6.15-28-386
root		(hd0,[COLOR=Red]**1**[/COLOR])
kernel		/boot/vmlinuz-2.6.15-28-386 root=/dev/sda3 ro quiet splash
initrd		/boot/initrd.img-2.6.15-28-386
savedefault
boot

title		Ubuntu, kernel 2.6.15-28-386 (recovery mode)
root		(hd0,[COLOR=Red]**1**[/COLOR])
kernel		/boot/vmlinuz-2.6.15-28-386 root=/dev/sda3 ro single
initrd		/boot/initrd.img-2.6.15-28-386
boot

title		Ubuntu, kernel 2.6.15-26-386
root		(hd0,[COLOR=Red]**1**[/COLOR])
kernel		/boot/vmlinuz-2.6.15-26-386 root=/dev/sda3 ro quiet splash
initrd		/boot/initrd.img-2.6.15-26-386
savedefault
boot

title		Ubuntu, kernel 2.6.15-26-386 (recovery mode)
root		(hd0,[COLOR=Red]**1**[/COLOR])
kernel		/boot/vmlinuz-2.6.15-26-386 root=/dev/sda3 ro single
initrd		/boot/initrd.img-2.6.15-26-386
boot

title		Ubuntu, memtest86+
root		(hd0,[COLOR=Red]**1**[/COLOR])
kernel		/boot/memtest86+.bin 
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title           Other operating systems:
root
# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title           Windows Vista
root            (hd0,[COLOR=Red]**0**[/COLOR])
savedefault
makeactive
chainloader     +1


Make the changes in red. Can somebody else check this so I don't screw it up!

---

### Post by thelocust on 2007-09-04
[Also this is a really great page that explains all the option in grub.]("http://users.bigpond.net.au/hermanzone/p15.htm#groot")

---

### Post by Bethrine on 2007-09-04
Oh, thank you! I thought so, but didn't know if I should change them all. :)) I'm going to try it now...

---

### Post by thelocust on 2007-09-04
you can also delete some of the older ones and change the names. If your feeling frisky.

---

### Post by rsambuca on 2007-09-04
> **Bethrine said:**
> Aside: Hi rambusca, thanks for getting me my pics last time!

Hey no problem!  I was gonna ask if you were keeping out of trouble, but from the thread I guess not :wink:

Anyways, it appears that thelocust has you well taken care of.

See ya round the forums!

---

### Post by Bethrine on 2007-09-04
AWESOME! I also had to change my...

root=/dev/sda3

to 

root=/dev/sda2 

for all of them and it boots beautifully! Thank you, thank you! I'm going to look into "cleaning" grub up tomorrow. Been spending too much time on it today, but my problem is fixed! At least until grub updates :)), I may have to go back and change that "root=" thing in the file mentioned in the thread you gave me much earlier to make it permanently boot at /dev/sda2. If so I will update this thread at that time. Awesome! Thanks thelocust!

---

### Post by Bethrine on 2007-09-04
> **rsambuca said:**
> Hey no problem!  I was gonna ask if you were keeping out of trouble, but from the thread I guess not :wink:

Anyways, it appears that thelocust has you well taken care of.

See ya round the forums!

LOL I'm always driving the family nuts! :)) Thanks!

---

### Post by rsambuca on 2007-09-05
I looked at your grub/menu.lst a little closer.  I think that you will want to change your menu.lst as follows, otherwise this will happen again at the next kernel update.```
## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,[COLOR="Red"]1[/COLOR])
```

---

### Post by Bethrine on 2007-09-09
Oops, just got this! I made the change. Thanks!

---

### Post by Bethrine on 2007-09-09
Okay, here is my grub now...

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
default		0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		25

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
# kopt=root=/dev/sda3 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,1)

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

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## ## End Default Options ##

title		Ubuntu, kernel 2.6.15-29-386
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.15-29-386 root=/dev/sda2 ro quiet splash
initrd		/boot/initrd.img-2.6.15-29-386
savedefault
boot

title		Ubuntu, kernel 2.6.15-29-386 (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.15-29-386 root=/dev/sda2 ro single
initrd		/boot/initrd.img-2.6.15-29-386
boot

title		Ubuntu, kernel 2.6.15-28-386
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.15-28-386 root=/dev/sda2 ro quiet splash
initrd		/boot/initrd.img-2.6.15-28-386
savedefault
boot

title		Ubuntu, kernel 2.6.15-28-386 (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.15-28-386 root=/dev/sda2 ro single
initrd		/boot/initrd.img-2.6.15-28-386
boot

title		Ubuntu, kernel 2.6.15-26-386
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.15-26-386 root=/dev/sda2 ro quiet splash
initrd		/boot/initrd.img-2.6.15-26-386
savedefault
boot

title		Ubuntu, kernel 2.6.15-26-386 (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.15-26-386 root=/dev/sda2 ro single
initrd		/boot/initrd.img-2.6.15-26-386
boot

title		Ubuntu, memtest86+
root		(hd0,1)
kernel		/boot/memtest86+.bin 
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title           Other operating systems:
root
# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title           Windows Vista
root            (hd0,0)
savedefault
makeactive
chainloader     +1

---

