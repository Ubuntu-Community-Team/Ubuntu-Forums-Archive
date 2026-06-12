---
title: "I did not update the grub menu, now I cannot boot to my desktop"
date: 2008-10-27
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by bcasanov on 2008-10-27
Hi,

I just upgraded to Ubuntu Intrepid.  Along the way, the update manager asked me if I wanted to keep my menu.lst or something like that (I think it deals with the Grub menu) or if I update it.  I decided to keep it.  The first restart I did worked; I was able to boot up into my desktop.  The second restart I did after I set the wireless switch on my laptop to on, which did not work.  There was a shrill high sound and the computer froze in the middle of shutting down, after the Ubuntu splash.  I had to do a cold shutdown and then tried to boot up my computer, but then, after the Grub menu, I got an error that said something like "Error 15.  File not found.  Press any key to continue."

Should I maybe get the updated version of the menu.lst?  How would I do that?  I am currently on the Hardy live CD.

This is what my menu.lst looks like currently:
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
#      password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
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
# kopt=root=UUID=927f2970-14be-4b98-b65f-286b6c23af23 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,5)

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

title        Ubuntu 8.04.1, kernel 2.6.24-21-generic
root        (hd0,5)
kernel        /boot/vmlinuz-2.6.24-21-generic root=UUID=927f2970-14be-4b98-b65f-286b6c23af23 ro quiet splash
initrd        /boot/initrd.img-2.6.24-21-generic
quiet

title        Ubuntu 8.04.1, kernel 2.6.24-21-generic (recovery mode)
root        (hd0,2)
kernel        /vmlinuz-2.6.24-21-generic root=UUID=927f2970-14be-4b98-b65f-286b6c23af23 ro single
initrd        /initrd.img-2.6.24-21-generic

title        Ubuntu 8.04.1, memtest86+
root        (hd0,2)
kernel        /memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

title Reinstall Operating System (WARNING: all Hard Drive data will be LOST!)
        root (hd0,1)
        kernel /vmlinuz debug boot=dellfactory quiet
        initrd /initrd.gz

```

---

### Post by ronacc on 2008-10-27
the shrill high sound and freeze sounds bad . You can mount the drive using the live cd and see if your menu.list looks ok and is pointing at the correct kernel and also that the kernel it is pointing at actualy exists . something that happened during that shutdown may have trashed something vital .

Edit: have you tried booting into recovery mode ?

---

### Post by bcasanov on 2008-10-27
Well, if I try booting to recovery mode, it might boot to the incorrect kernel or not at all, since the directory path might no longer exist.  I edited my post above so that you can see my menu.lst.

---

### Post by ronacc on 2008-10-27
the menu.list you posted is still pointing at the hardy kernel . the current intrepid kernel is 2.6.27-7 . try this , cut and paste this just above the first entry for 8.04

```

 title        Ubuntu 8.10., kernel 2.6.27-7-generic
root        (hd0,5)
kernel        /boot/vmlinuz-2.6.2-7-generic root=UUID=927f2970-14be-4b98-b65f-286b6c23af23 ro quiet splash
initrd        /boot/initrd.img-2.6.27-7-generic
quiet

```

it should appear as the first entry when grub comes up .

---

### Post by caljohnsmith on 2008-10-27
Your menu.lst indicates you have Ubuntu in both (hd0,2) and (hd0,5). Do you know which is correct? How about first posting:
```
sudo fdisk -lu
```
And let us know what your partitions are.

---

### Post by bcasanov on 2008-10-27
I tried ronacc's suggestion, but I still got the same error.  

The result of "sudo fdisk -lu" is:

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xf0000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda4              63   156296384    78148161    f  W95 Ext'd (LBA)
/dev/sda5             126     4289354     2144614+  82  Linux swap / Solaris
/dev/sda6         4289418   156296384    76003483+  83  Linux

---

### Post by caljohnsmith on 2008-10-27
OK, from your Live CD, try the following in order to automatically update your menu.lst with the kernel changes:
```
sudo mount /dev/sda6 /mnt
sudo mount --bind /dev /mnt/dev
sudo mount --bind /proc /mnt/proc
sudo chroot /mnt /bin/bash
update-grub
exit
```
Then reboot, and see if that is enough to correct your menu.lst. If not, I can help you manually fix your menu.lst if you want help. :)

---

### Post by ronacc on 2008-10-27
several things to check , using the live cd take a look at the /boot on the prtition where intrepid is and make sure that the menu.list entry is pointing at a kernel that is actualy there . also check the uuid for the partition and make sure that it is correct and is the one for the partition where intrepid actualy is ( I am assuming that it is sda6 which would be hd0,5 ) .

---

### Post by bcasanov on 2008-10-27
Thanks for your reply, both of you.  Caljohnsmith, I followed your instructions in your above post, and this is the result after putting in "update-grub":

Searching for GRUB installation directory ... found: /boot/grub
findfs: Unable to resolve 'UUID=95b5b7f2-95ec-4aaf-ae9f-d9ea528b30ec'
Searching for default file ... found: /boot/grub/default
Testing for an existing GRUB menu.lst file ... found: /boot/grub/menu.lst
Searching for splash image ... none found, skipping ...
Found kernel: /boot/vmlinuz-2.6.27-7-generic
Found kernel: /boot/memtest86+.bin
Updating /boot/grub/menu.lst ... done

After that, I rebooted, but I still have the same Grub error, and it seems that my Grub menu has not changed.  I would most certainly appreciate it if you could help me manually fix my menu.lst.

Regards,

bcasanov

---

### Post by caljohnsmith on 2008-10-27
> **bcasanov said:**
> Thanks for your reply, both of you.  Caljohnsmith, I followed your instructions in your above post, and this is the result after putting in "update-grub":

Searching for GRUB installation directory ... found: /boot/grub
[COLOR="Red"]findfs: Unable to resolve 'UUID=95b5b7f2-95ec-4aaf-ae9f-d9ea528b30ec'[/COLOR]
Searching for default file ... found: /boot/grub/default
Testing for an existing GRUB menu.lst file ... found: /boot/grub/menu.lst
Searching for splash image ... none found, skipping ...
Found kernel: /boot/vmlinuz-2.6.27-7-generic
Found kernel: /boot/memtest86+.bin
Updating /boot/grub/menu.lst ... done

After that, I rebooted, but I still have the same Grub error, and it seems that my Grub menu has not changed.  I would most certainly appreciate it if you could help me manually fix my menu.lst.

Regards,

bcasanov
OK, from the error above it looks like you might need to correct your UUID for the Ubuntu partition, but it still seems suspicious because I thought we had your UUIDs corrected before. How about doing:
```
sudo mount /dev/sda6 /mnt
sudo blkid -c /dev/null
gksudo gedit /mnt/boot/grub/menu.lst
```
From the blkid above, verify that the following "kopt" line in the menu.lst uses the correct UUID for sda6:
```
# kopt=root=UUID=927f2970-14be-4b98-b65f-286b6c23af23 ro
```
Let me know if the above line is correct or not, and please post the entire contents of the menu.lst again. Also post:
```
ls -l /mnt/boot
```
And we can work from there.

---

### Post by ronacc on 2008-10-27
I am going to let caljohnsmith take it alone for awhile so you aren't trying to listen to 2 of us at once , I'll chaeck back later to see if you get it resolved , If not I have a few more ideas .

---

### Post by bcasanov on 2008-10-27
I verified that the "# kopt" line" in the menu.lst has the correct UUID for sda6, and it seems to be okay.

My entire menu.lst is:
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
# kopt=root=UUID=927f2970-14be-4b98-b65f-286b6c23af23 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,5)

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

title          Ubuntu 8.10., kernel 2.6.27-7-generic
root           (hd0,5)
kernel         /boot/vmlinuz-2.6.2-7-generic root=UUID=927f2970-14be-4b98-b65f-286b6c23af23 ro quiet splash
initrd         /boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-21-generic
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.24-21-generic root=UUID=927f2970-14be-4b98-b65f-286b6c23af23 ro quiet splash
initrd		/boot/initrd.img-2.6.24-21-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-21-generic (recovery mode)
root		(hd0,2)
kernel		/vmlinuz-2.6.24-21-generic root=UUID=927f2970-14be-4b98-b65f-286b6c23af23 ro single
initrd		/initrd.img-2.6.24-21-generic

title		Ubuntu 8.04.1, memtest86+
root		(hd0,2)
kernel		/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

title Reinstall Operating System (WARNING: all Hard Drive data will be LOST!)
        root (hd0,1)
        kernel /vmlinuz debug boot=dellfactory quiet
        initrd /initrd.gz

```
(As an aside, the entry that says "Reinstall Operating System..." seems to be a remnant of the Dell Recovery Partition and might not actually point to anything.  Is it okay to delete it?)

The result of "ls -l /mnt/boot" is:

total 11915
-rw-r--r-- 1 root root  507665 2008-10-24 08:29 abi-2.6.27-7-generic
-rw-r--r-- 1 root root   91364 2008-10-24 08:29 config-2.6.27-7-generic
drwxr-xr-x 2 root root    1024 2008-10-27 14:51 grub
-rw-r--r-- 1 root root 8142691 2008-10-27 11:42 initrd.img-2.6.27-7-generic
drwx------ 2 root root    1024 2008-10-26 00:59 lost+found
-rw-r--r-- 1 root root  124152 2008-09-11 20:11 memtest86+.bin
-rw-r--r-- 1 root root 1029585 2008-10-24 08:29 System.map-2.6.27-7-generic
-rw-r--r-- 1 root root    1073 2008-10-24 08:31 vmcoreinfo-2.6.27-7-generic
-rw-r--r-- 1 root root 2244272 2008-10-24 08:29 vmlinuz-2.6.27-7-generic

---

### Post by caljohnsmith on 2008-10-27
> **bcasanov said:**
> 
```

title          Ubuntu 8.10., kernel 2.6.27-7-generic
root           (hd0,5)
kernel         /boot/[COLOR="Red"]vmlinuz-2.6.2-7-generic[/COLOR] root=UUID=927f2970-14be-4b98-b65f-286b6c23af23 ro quiet splash
initrd         /boot/initrd.img-2.6.27-7-generic
quiet

```

It looks like the reason why you get the Grub error 15 (file not found) is because as I've highlighted above, the kernel number is wrong. So first bring up your menu.lst again:
```
sudo mount /dev/sda6 /mnt
gksudo gedit /mnt/boot/grub/menu.lst
```
And yes, go ahead and delete the "Reinstalling Operating System..." entry as you obviously don't have that any more. Next change the "hiddenmenu" line to:
```
# hiddenmenu
```
So that you will see the Grub menu on start up. Next replace the first Ubuntu entry with:
```
title          Ubuntu 8.10., kernel 2.6.27-7-generic
root           (hd0,5)
kernel         /boot/vmlinuz-2.6.2[COLOR="Red"]7[/COLOR]-7-generic root=UUID=927f2970-14be-4b98-b65f-286b6c23af23 ro quiet splash
initrd         /boot/initrd.img-2.6.27-7-generic
quiet

```
And also, replace all the other Ubuntu entries with:
```
title          Ubuntu 8.10., kernel 2.6.27-7-generic (Recovery Mode)
root           (hd0,5)
kernel         /boot/vmlinuz-2.6.2-27-generic root=UUID=927f2970-14be-4b98-b65f-286b6c23af23 ro single
initrd         /boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.04.1, memtest86+
root		(hd0,5)
kernel		/memtest86+.bin
quiet
```
Reboot, and let me know if that works, or what errors you get if any. :)

---

### Post by bcasanov on 2008-10-27
Thank you very much caljohnsmith, your instructions worked!  I am now writing from my freshly booted-up Ubuntu Intrepid desktop.  Also, thanks to ronacc for your kind help as well.

---

### Post by kansasnoob on 2008-10-27
> **caljohnsmith said:**
> It looks like the reason why you get the Grub error 15 (file not found) is because as I've highlighted above, the kernel number is wrong. So first bring up your menu.lst again:
```
sudo mount /dev/sda6 /mnt
gksudo gedit /mnt/boot/grub/menu.lst
```
And yes, go ahead and delete the "Reinstalling Operating System..." entry as you obviously don't have that any more. Next change the "hiddenmenu" line to:
```
# hiddenmenu
```
So that you will see the Grub menu on start up. Next replace the first Ubuntu entry with:
```
title          Ubuntu 8.10., kernel 2.6.27-7-generic
root           (hd0,5)
kernel         /boot/vmlinuz-2.6.2[COLOR="Red"]7[/COLOR]-7-generic root=UUID=927f2970-14be-4b98-b65f-286b6c23af23 ro quiet splash
initrd         /boot/initrd.img-2.6.27-7-generic
quiet

```
And also, replace all the other Ubuntu entries with:
```
title          Ubuntu 8.10., kernel 2.6.27-7-generic (Recovery Mode)
root           (hd0,5)
kernel         /boot/vmlinuz-2.6.2-27-generic root=UUID=927f2970-14be-4b98-b65f-286b6c23af23 ro single
initrd         /boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.04.1, memtest86+
root		(hd0,5)
kernel		/memtest86+.bin
quiet
```
Reboot, and let me know if that works, or what errors you get if any. :)

**You rock!**

I call that awesome beyond belief!

---

### Post by caljohnsmith on 2008-10-27
> **bcasanov said:**
> Thank you very much caljohnsmith, your instructions worked!  I am now writing from my freshly booted-up Ubuntu Intrepid desktop.  Also, thanks to ronacc for your kind help as well.
That's great news, glad it's working. I'm a little concerned though that you may have uncovered a bug with the Intrepid update-grub command, because it didn't get the kernel number quite right. In the future, when you get a new kernel, if you run into similar problems, it would be great if you could take a few minutes to report the bug at bugs.launchpad.net if you have the time. That could help others in case they have the same problem.

Anyway, cheers and have fun with Intrepid. :)

---

### Post by caljohnsmith on 2008-10-27
> **kansasnoob said:**
> **You rock!**

I call that awesome beyond belief!
Thanks for the vote of confidence, Kansasnoob; sometimes I get it right, and sometimes I, well, err, have moments when my brain seems to be missing. I'm glad I didn't goof it this time. I'm sure ronacc would have helped him sort it out too. :)

---

### Post by ronacc on 2008-10-27
@ caljohnsmith glad you caught that , mybad I typo'd that line when I edited it for him .
@ bcasanov  sorry about that , if I had proofread what I typed I wouldn,t have put you through the extra grief .

---

### Post by ShirishAg75 on 2008-10-27
caljohnsmith: really cool. It would be nice if you could write a how-to for borked boots. Things which should be easily fixable if people put up their mind to it. What do you say?

---

### Post by caljohnsmith on 2008-10-27
> **ShirishAg75 said:**
> caljohnsmith: really cool. It would be nice if you could write a how-to for borked boots. Things which should be easily fixable if people put up their mind to it. What do you say?
Well, first of all, thanks for the vote of confidence, but really it probably isn't necessary to write a Grub/booting How-to since forum member Herman all ready has a website set up that gives alot of good info about Grub and troubleshooting tips:

[http://www.users.bigpond.net.au/hermanzone/p15.htm](http://www.users.bigpond.net.au/hermanzone/p15.htm)

And of course there is always the official Grub manual:

[http://www.gnu.org/software/grub/manual/](http://www.gnu.org/software/grub/manual/)

So I think the info is all ready available if the beginner wants to learn and try to sort out their booting issues themselves. I must admit though that I really wish there was some sort of GUI program that could help people sort out their Grub problems, because it really can get quite convoluted and complicated for beginners to do it all from the command line. And unfortunately, sometimes it takes quite a bit of learning about Grub/booting issues to effectively sort out some difficult and complicated booting problems I think; really the noob shouldn't be expected to become some sort of Grub expert just to get their setup booting correctly, so I can understand why some linux beginners get so frustrated with booting problems. But anyway, thanks for the words of encouragement. :)

---

### Post by bcasanov on 2008-10-27
Thanks for these web resources!  I just have one last question: in Intrepid, I heard that there was a "Last successful boot" option in the Grub menu.  I apparently don't have that entry on mine.  How can I get it?

---

### Post by bcasanov on 2008-10-27
Edited: Oops!  Double post.

---

### Post by bcasanov on 2008-10-27
Should I start a new thread topic with this new question, as it is not really relevant to the original issue of not being able to boot up to my desktop?

---

### Post by ronacc on 2008-10-27
another resource for dealing with a grub failure is here .
[http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)

---

