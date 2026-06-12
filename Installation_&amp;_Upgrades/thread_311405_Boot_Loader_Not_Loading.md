---
title: "Boot Loader Not Loading"
date: 2006-12-02
forum: Installation &amp; Upgrades
---

### Post by EvilBob on 2006-12-02
I'm trying to get Ubuntu up and running and I'm pretty sure it's installed and happy, I just can't get to it.

The problem is that my computer starts and Windows XP loads right up. There's no selection screen or hint that grub is anywhere on my computer. I've found other threads that mentioned trouble other people have had with grub but they seem to mostly deal with grub screwing up, not being missing entirely.

I did try the steps given here by the original poster: [http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351) but with no joy. I received no error messages, no suggestion that grub didn't install or did so in a corrupt manner. I even tried reinstalling once just to be sure.

I had three hard drives that are now four. I was running just XP on this machine prior to the partition shift. My partitions now look like this:
Drive0 (NTFS)((/)(swap))
Drive1 (NTFS)
Drive2 (NTFS)

If there's any other information you need let me know (and how to get it, if applicable) and I'll include that as well. I have a sneaking suspicion I'm overlooking something simple but, then again, I always have that feeling.

Thanks for any help.

---

### Post by bulldog on 2006-12-02
You have to find out on which disk GRUB is installed.
Now it boots direct into windows,so this disk doesn't have GRUB.

Try to boot from every disk by selecting it in the BIOS to find out on which GRUB is installed.

It's possible that what you called drive0,is seen by GRUB as drive1.

You can also boot the live cd and type in your terminal```
sudo fdisk -l {l as in like}
```to find out some info about your disk ordering. 

By mounting your ubuntu partition [found by the previous command] you can enter the menu.lst.
```
sudo mkdir /mnt/rescue
```
This makes a mountpoint.
Now to actual mount```
sudo mount /dev/hd? /mnt/rescue
```where hd? stands for the partition you found with the fdisk command.

If the mounting was succes full,you can enter the menu.lst by the following command```
gksudo gedit /mnt/rescue/boot/grub/menu.lst
```

If you can put the outcome of the fdisk command and the menu.lst on the forum,we can have a look at your problems.

---

### Post by EvilBob on 2006-12-02
You are very good.

I opened up my BIOS, I had peeked quickly earlier but nothing seemed amiss, this time paying close attention to the drive models.
I got the order of the drives right insofar as they were displayed in windows. That, of course, had little bearing on reality. It wasn't far off from what the BIOS showed, the system drive was still the first one, but the "boot sequence" part only let me pick the drive type order (CD/Floppy/HDD).
It was then I found that the drive it was picking to boot from was, in fact, the third one. I switched it to the one I had mistakenly believed it to be earlier and, lo, grub greets me.

It just leaves me a little curious as to how windows was able to boot at all, unless it can load from any drives MBR or something.

Thanks!

Edit:
I spoke too soon it seems. I tried selecting windows from grub and it tossed an error that it couldn't find a file. I can, however, still switch drives in BIOS to pick what I want to boot. I'll probably have to live with that until I reinstall windows?

---

### Post by bulldog on 2006-12-03
LOL,nope, that won't work.:D 

Some things to understand.
You can boot every hard disk which has an OS on it's own by selecting it in your BIOS,so it boots with it's own loader.
So you did with windows.

Now you have found GRUB on another hard disk and this should be the disk you have to set to boot from in the future.
Now we have to get sorted out your menu.lst and fstab to set every thing to point at the right disk.

If you can boot to ubuntu give us the outcome of```
sudo fdisk -l (l as in like)
``` and your menu.lst as well```
cat /boot/grub/menu.lst
```
Copy this to the forum and we can get sorted things out.

---

### Post by EvilBob on 2006-12-03
Haha, on a positive note, following the guide to install the ATi drivers worked well and than means no more 800x600 for me.

The output you requested from *sudo fdisk -l*
```

Disk /dev/hda: 40.0 GB, 40016019456 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1               1        2167    17406396    7  HPFS/NTFS
/dev/hda2   *        2168        4717    20482875   83  Linux
/dev/hda3            4718        4865     1188810    5  Extended
/dev/hda5            4718        4865     1188778+  82  Linux swap / Solaris

Disk /dev/sda: 300.0 GB, 300069052416 bytes
255 heads, 63 sectors/track, 36481 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       36481   293033601    7  HPFS/NTFS

Disk /dev/sdb: 163.9 GB, 163928604672 bytes
255 heads, 63 sectors/track, 19929 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       19928   160071628+   7  HPFS/NTFS

```

and here is *cat /boot/grub/menu.lst*
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
#      password --md5 $1$LqhU0/$aW78HqK1QfV3P2b2zqUoe/
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
# kopt=root=UUID=fa6076b2-6b3d-4057-a65d-c83b8347746b ro
# kopt_2_6=root=/dev/hda2 ro

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

title           Ubuntu, kernel 2.6.17-10-generic
root            (hd0,1)
kernel          /boot/vmlinuz-2.6.17-10-generic root=/dev/hda2 ro quiet splash
initrd          /boot/initrd.img-2.6.17-10-generic
quiet
savedefault
boot

title           Ubuntu, kernel 2.6.17-10-generic (recovery mode)
root            (hd0,1)
kernel          /boot/vmlinuz-2.6.17-10-generic root=/dev/hda2 ro single
initrd          /boot/initrd.img-2.6.17-10-generic
boot

title           Ubuntu, memtest86+
root            (hd0,1)
kernel          /boot/memtest86+.bin
quiet
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title           Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb1
title           Microsoft Windows XP Professional
root            (hd2,0)
savedefault
makeactive
map             (hd0) (hd2)
map             (hd2) (hd0)
chainloader     +1

```

Note to self: Pay more attention to BIOS in future, buy it flowers, etc.
Thanks again.

---

### Post by bulldog on 2006-12-03
```
## ## End Default Options ##

title           Ubuntu, kernel 2.6.17-10-generic
root            (hd0,1)
kernel          /boot/vmlinuz-2.6.17-10-generic root=/dev/hda2 ro quiet splash
initrd          /boot/initrd.img-2.6.17-10-generic
quiet
savedefault
boot

title           Ubuntu, kernel 2.6.17-10-generic (recovery mode)
root            (hd0,1)
kernel          /boot/vmlinuz-2.6.17-10-generic root=/dev/hda2 ro single
initrd          /boot/initrd.img-2.6.17-10-generic
boot

title           Ubuntu, memtest86+
root            (hd0,1)
kernel          /boot/memtest86+.bin
quiet
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title           Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb1
title           Microsoft Windows XP Professional
map             (hd0) (hd2)
map             (hd2) (hd0)
rootnoverify    (hd2,0)
makeactive
chainloader     +1
```
Change your menu.lst according to this windows entry.
If you now boot from the disk with GRUB it should work fine I think.
I must admit however I loose a little what's the problem again :D 
I've been busy with multiple topic's and don't know who had which problem again ](*,) 
Let me know if things aren't working like they should be.

---

### Post by EvilBob on 2006-12-03
Thanks, I'll give that a try as soon as I can and update the results.

This was the "stupid man wasn't looking what drive was being booted to when he installed windows and now has the windows MBR setup on the wrong drive while linux/grub are on the right one" problem. ;)

Edit:
I made the changes to the *menu.lst* but there was no change. When I select Windows to boot I get the same error message as before - this time I wrote it down though!
```

Windows could not start because the following file is missing or corrupt:
<Windows root>\system32\hal.dll
Please re-install a copy of the above file.

```

---

### Post by EvilBob on 2006-12-04
If I set the correct drive to boot from (the one Linux is now using) and popped in the Windows CD to 'fix' the MBR. Would that then allow Windows to boot from that drive? 

Then all I would have to do is reinstall grub... in theory, right?

---

### Post by bulldog on 2006-12-04
Simply find the hal.dll on the windows install disk and copy it to windows/system32,and see if you get somewhere.

---

### Post by EvilBob on 2006-12-04
Sorry, I should have mentioned *hal.dll* is already there.

As far as I can tell both installs are fine, I can boot into both still by switching the boot drive in my BIOS. The fact that grub gets Windows going far enough along to even think there is a file missing would seem to suggest it was trying to load.

I was reading up a bit on the grub manual but all that did for me was confirm what you gave me should be throwing me right into Windows. The right drives are mapped, there's only the one partition on every drive except the one that's already working right. ](*,) 

The only thing I can think of is: since the MBR for Windows is on a drive that doesn't actually contain the Windows install and without the BIOS forcing it to look in the right spot - could the Windows MBR itself be what's confused and not grub? I don't know if that even makes sense, I've never played around with any of this stuff before.

Sorry for taking up so much of your time with this, it's appreciated.

---

### Post by bulldog on 2006-12-04
> **EvilBob said:**
> Sorry, I should have mentioned *hal.dll* is already there.

The only thing I can think of is: since the MBR for Windows is on a drive that doesn't actually contain the Windows install and without the BIOS forcing it to look in the right spot - could the Windows MBR itself be what's confused and not grub? I don't know if that even makes sense, I've never played around with any of this stuff before.

You mean GRUB as [windows MBR]?
I boot windows more than a year with GRUB and it's installed on another hard disk as well :D 

The options are limited because all should work well now,and it refuses to do so ](*,) 
We try two more options and if that won't work,I'll trow the towl.:D 

First we are trying too refresh GRUB```
sudo update-grub
```
If this has not the desired fix,you have to try and boot windows of course,we're reinstalling GRUB again.
Boot into the live Ubuntu cd. 

When you get to the desktop open a terminal and enter. 
```
sudo grub
```
This will get you a grub> prompt 
```
find /boot/grub/stage1
```
This will return a location which you have to use in the next command. 
```
root (hd?,?)
```
Next enter the command to install grub to the mbr
```
setup (hd0)  <---Watch this one please!!
```
Exit the grub shell
```
quit
```
Now Grub will be installed to the mbr. 

We have to take a look with ```
sudo fdisk -l
```we're not making a mistake here,and install GRUB on the wrong disk,this kind of things happen you know :D 

If this is not getting us the result we're after,I call it a day.
I should really not know what is wrong with it.

---

### Post by EvilBob on 2006-12-04
Still no joy :cry: 

I can only think of one other thing to try, apart from reinstalling Windows, but I'd like to know why you think the chances of Success vs Nuking Windows are and to make sure I understand what I'd doing right:

According to *sudo fdisk -l* the other booting drive is sdb1. This is the drive that the BIOS was unfortunately set to when I installed it.

What if I setup grub to write itself to that drives (*setup (hd2)* ?) MBR instead of using *setup (hd0)*?

Windows seems attached to that spot so would Linux be happy there too?
If you think it's worth trying can you just confirm that the following commands would be the right way to go about doing it...

```
sudo grub
find /boot/grub/stage1
root (hd0,1)                   [I assume this isn't going to change unless I move the Ubuntu install]
setup (hd2)
quit

```


Edit:
Woops, almost forgot the *sudo fdisk -l* output you asked for. You'll be disappointed though, I don't think it's changed:
```

Disk /dev/hda: 40.0 GB, 40016019456 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1               1        2167    17406396    7  HPFS/NTFS
/dev/hda2   *        2168        4717    20482875   83  Linux
/dev/hda3            4718        4865     1188810    5  Extended
/dev/hda5            4718        4865     1188778+  82  Linux swap / Solaris

Disk /dev/sda: 300.0 GB, 300069052416 bytes
255 heads, 63 sectors/track, 36481 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       36481   293033601    7  HPFS/NTFS

Disk /dev/sdb: 163.9 GB, 163928604672 bytes
255 heads, 63 sectors/track, 19929 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       19928   160071628+   7  HPFS/NTFS

```

---

### Post by bulldog on 2006-12-04
Well,you can boot windows now by switching your boot device.
Can't promise it will be so if you put GRUB on the windows disk.

And the boot order would change and you have to unmap windows,but that is easy and GRUB will do the most of it by reinstalling.

My concern is that if it **not** works,you can't boot windows anymore.

The only thing GRUB has to do to fire up windows is pointing it to the right hard disk and partition,then windows takes over and should boot.

Now it will boot if you start it on it's own disk,no error what so ever,but when you do it with GRUB you get a hal.dll is missing error.
That part beats me,because GRUB has nothing to do with that as far as I know.

If it was my computer I shouldn't change anything and if you want windows just change the boot order.
Maybe you can put up another thread with this problem and maybe someone with more knowledge can give you a hint.

**EDIT:**

Looking at your previous post,did you install GRUB again?
Did you the update-grub command [don't think this help]
Given you boot from the disk with Ubuntu you have to use setup (hd0) in reinstalling GRUB

---

### Post by EvilBob on 2006-12-04
I did do the reinstall and the update, from what you've told me and how it's behaving I don't think it's grub's fault but rather a by-product of my sloppy Windows install. 

I see your point though, it maybe be a backwards way to get into Windows but if it works, it works. I usually reformat Windows about once a year anyway to get its performance back. Amongst other things, I'm hoping Linux doesn't have the same slow deterioration - although I've used Linux systems before, it's almost always been as a client. Before the next time I format I might try a few more daring things and see what happens but I'm in no hurry.

I'll leave it how it is. Thanks for your time and the help, at least I understand a little more about Linux's boot methods.

Now, let just see if I can get wine to work... :twisted:

---

