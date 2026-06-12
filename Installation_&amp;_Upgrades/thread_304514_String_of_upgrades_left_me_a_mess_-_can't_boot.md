---
title: "String of upgrades left me a mess - can't boot"
date: 2006-11-21
forum: Installation &amp; Upgrades
---

### Post by stereth on 2006-11-21
I've been bringing up my Linux box again over the last few weeks. It was running Hoary, and I left it there for a while, then started to upgrade. I pored over the wiki articles and linked threads at each step. I ran apt-get, update manager, and synaptic whenever I could to make sure there was nothing else to update. I believe I actually upgraded to Edgy last night, but I'm still confused at the kernel stuff below.

Now, at boot, I get the error```
Booting 'Ubuntu, kernel 2.6.15-27-386'

root(hd0,0)
Filesystem type is ext2fs, partition type 0x83
kernel /boot/vmlinuz-2.6.15-27-386 root=/dev/hdb1 ro quiet splash

Error 13: Invalid or unsupported executable format

Press any key to continue...
```
Pressing a key brings me to a GRUB menu with nine options: kernels 2.6.15-27-386, 2.6.12-10-386, 2.6.10-6-386, and 2.6.10-5-386, each with a normal and recovery mode, and memtest86+.

The first two kernels, in both modes, give me the above error again. The second two kernels, in normal mode, freeze at```
Uncompressing Linux...Ok, booting the kernel.
audit(...): initialized
Starting Ubuntu...
```
In recovery mode, they freeze at```
[hda info, DVD]
[hdb info, HDD]
Stopping tasks
Freeing memory...done
Restarting tasks...done
EXT3-fs: mounted filesystem with ordered data mode.
kjournald starting. Commit interval 5 seconds
```
I actually had the first error when most everything was working. Only the first kernel gave me the error though; the rest seemed to work.

My system is a Mini-ITX board with everything Via integrated. 1ghz Nehemiah, 512mb RAM, 160gb hard drive with default Ubuntu partitions.

Where do I go from here? I've used my Hoary live CD to run fsck after I had some problems as I got to Breezy. If an Edgy live/install CD is my best bet, I'll do that.

I hit a problem at Dapper where most of my modules weren't loaded, and I booted without USB, network, or sound. (This is fun when you're using a USB keyboard and mouse.) All I corrected from there was adding my networking module to /etc/modules. I used the recommended method to get to Edgy.

Also, why do I have all of these kernels loaded, and should I clean them up after things work? How would I do that?

---

### Post by ingo on 2006-11-22
hi, 

try this

[http://www.smop.co.uk/node/43](http://www.smop.co.uk/node/43)

to find your kernel

---

### Post by stereth on 2006-11-22
Nope, no help. That all seems to be set up correctly. And the command line just tells me which partition the kernel is on - and I only have one partition to choose from. Those instructions don't list multiple kernels.

Also the article is a bit incorrect in mapping device names. It says the kernel is on (hd0,0), which maps to hdb1, not hda1, in my machine.

---

### Post by ingo on 2006-11-22
right, you need to identify the latest kernel using the link I've given you. If Grub says its on (hd0,0) then so be it. If you doubt it please give more info on what else you have on your system. Do the same to the root path.

Now compare both kernel path and root path with what is in your

/boot/grub/menu.lst

there is bound to be some discrepancy (at least if you search the forums for grub error 13 that is what you will find).

HTH

---

### Post by stereth on 2006-11-22
I don't understand how to identify the latest kernel with that article. All the command line seems to tell me is that important stuff is on (hd0,0). None of the commands use or return anything related to different kernels.

The boot entries look like the text of the first error. If I change /boot/vmlinuz-## to (hd0,0)/vmlinuz , I still have error 13.

And what about the root path needs to be changed?

Is there a way to search for "error 13" on the forums? It drops the 13 however I try.

---

### Post by ingo on 2006-11-22
hm, ok. can you post the following outputs please (using the live cd or knoppix or whatever). The first command has to be done as root.

$ fdisk -l

this will give us a run-down of your disks and partitions and

$ cat  /boot/grub/menu.lst

I know it seems silly to go through the basics, but it has happened so often to me that I thought everything was configured correctly when it actually wasn't. The different naming conventions of linux and grub don't help :( and often serve to confuse.

---

### Post by stereth on 2006-11-22
I appreciate it, even if you do have to get basic. I'm learning by experience and don't have much depth in a lot of areas.

Partitions are pretty simple:```
ubuntu@ubuntu:/mnt/hdb1$ sudo fdisk -l

Disk /dev/hdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1       19281   154874601   83  Linux
/dev/hdb2           19282       19457     1413720    5  Extended
/dev/hdb5           19282       19457     1413688+  82  Linux swap / Solaris
```
Here's menu.lst:
```
ubuntu@ubuntu:/mnt/hdb1/boot/grub$ cat menu.lst
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
# kopt=root=/dev/hdb1 ro

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

title           Ubuntu, kernel 2.6.15-27-386
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.15-27-386 root=/dev/hdb1 ro quiet splash
initrd          /boot/initrd.img-2.6.15-27-386
savedefault
boot

title           Ubuntu, kernel 2.6.15-27-386 (recovery mode)
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.15-27-386 root=/dev/hdb1 ro single
initrd          /boot/initrd.img-2.6.15-27-386
boot

title           Ubuntu, kernel 2.6.12-10-386
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.12-10-386 root=/dev/hdb1 ro quiet splash
initrd          /boot/initrd.img-2.6.12-10-386
savedefault
boot

title           Ubuntu, kernel 2.6.12-10-386 (recovery mode)
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.12-10-386 root=/dev/hdb1 ro single
initrd          /boot/initrd.img-2.6.12-10-386
boot

title           Ubuntu, kernel 2.6.10-6-386
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.10-6-386 root=/dev/hdb1 ro quiet splash
initrd          /boot/initrd.img-2.6.10-6-386
savedefault
boot

title           Ubuntu, kernel 2.6.10-6-386 (recovery mode)
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.10-6-386 root=/dev/hdb1 ro single
initrd          /boot/initrd.img-2.6.10-6-386
boot

title           Ubuntu, kernel 2.6.10-5-386
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.10-5-386 root=/dev/hdb1 ro quiet splash
initrd          /boot/initrd.img-2.6.10-5-386
savedefault
boot

title           Ubuntu, kernel 2.6.10-5-386 (recovery mode)
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.10-5-386 root=/dev/hdb1 ro single
initrd          /boot/initrd.img-2.6.10-5-386
boot

title           Ubuntu, memtest86+
root            (hd0,0)
kernel          /boot/memtest86+.bin
boot

### END DEBIAN AUTOMAGIC KERNELS LIST
```
/boot also has vmlinuz and System.map entries for 2.6.17-10-386, but no corresponding initrd.img.

---

### Post by ingo on 2006-11-22
thanks for posting that stuff, me still thinks what happened to hda? is hdb your one and only hard drive? 

questions, questions, questions, I know... :)

EDIT: just noticed hda is your DVD set up as master and your hard disk as slave. weird, don't you find it slows you down when you need to access both (just interested as one does not see that kind of configuration very often)

---

### Post by stereth on 2006-11-22
hda is my DVD drive, I think. I'm not sure why it's set up like that. hdb is my only hard drive.

edit: It may well be slow, but it works. I don't demand too much from this machine.

---

### Post by ingo on 2006-11-22
ok, quickly checked the grub manual and they aren't really too clear about it either:     > (hd0,1)

   Here, `hd' means it is a hard disk drive. The first integer `0' indicates the drive number, that is, the first hard disk, while the second integer, `1', indicates the partition number (or the pc slice number in the BSD terminology). Once again, please note that the partition numbers are counted from *zero*, not from one. This expression means the second partition of the first hard disk drive. In this case, GRUB uses one partition of the disk, instead of the whole disk. 

So my guess (and it really is no more than that) is to change the first entry from (hd0,0) to (hd1,0) and then try to boot that. 

As for > I'm learning by experience and don't have much depth in a lot of areas. - same here :) [FONT=monospace][/FONT]

---

### Post by stereth on 2006-11-22
But they're all (hd0,0), and some of them work more than others. If that were the problem, none of the options would get past the kernel line. And hdb is still my first hard drive.

---

### Post by ingo on 2006-11-22
I understand your hesitation. However, I have seen error 13 happen only when GRUB is pointing at the wrong disk/partition - regardless how far it goes! My experience tells me that that is they way forward...

Even if it doesn't work, you are free to change it back :)

---

### Post by stereth on 2006-11-22
Nope.
```
Booting command-list

root(hd1,0)

Error 21: Selected disk does not exist

Press any key to continue...
```

---

### Post by ingo on 2006-11-22
just as you predicted... bummer. well, here is a link to a rescue grub cd

[http://supergrub.forjamari.linex.org/](http://supergrub.forjamari.linex.org/)

as I don't know what to do next (and I'm tired).

best of luck :)

---

### Post by stereth on 2006-11-22
Thanks, I'll try it. My next step may be burning an Edgy CD.

---

### Post by phines on 2006-11-28
I am having a similar problem.  I upgraded from Dapper to Edgy. In recovery mode my boot dies at:

kjournald starting. Commit interval 5 seconds
Done.

In standard mode, after mounting the root filesystem, I get a blank screen with a cursor.

Any suggestions?

---

### Post by stereth on 2006-12-03
Grub rescue CD and live CD didn't help. All of my attempts to reinstall and reconfigure grub just made it worse. Eventually the machine would just loop the BIOS startup sequence if there wasn't a boot CD in the drive. I ended up installing Edgy from a CD.

However, there's a bug in Edgy that keeps it from installing over an older version. I was worried because I had a few gigs of data I wanted to keep, and it was all on the same partition. Fortunately, the Edgy live CD has a partition manager that can work on unmounted drives. I resized the partition down, moved stuff to a new partition, and reinstalled Ubuntu on the old partition.

phines, your problem is similar, but it actually doesn't sound related. Have you tried poking around with a live CD?

---

