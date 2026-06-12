---
title: "Setting up and testing Software RAID 5"
date: 2007-09-16
forum: Installation &amp; Upgrades
---

### Post by un_dave on 2007-09-16
Hey all, here's my first post to the ubuntu forums, so i hope this is in the right place.

I've just brought a new system, with the intent of setting it up as a file server and home workstation. I've successfully installed 7.04 desktop, and have had no major hassles, and am throughly enjoying myself fiddling around. 

I currently have 1 320gb hard drive installed, which i was planning to use as my system drive. However i plan to buy 3 x 1tb drives, and install these in a raid 5 software configuration. I was hoping to use lvm2 on top of the raid to allow me to expand the array at some later point by simply inserting another 1tb hard drive.

My question is first, should, or can i even, boot the system off my raid 5 software array?

Secondly, is this a good idea? Or would i be better to keep my system on a single separate disk (and maybe raid 0 this later?)

Cheers,

Dave.

---

### Post by kidders on 2007-09-17
Hi there & welcome,

> **un_dave said:**
> would i be better to keep my system on a single separate disk (and maybe raid 0 this later?)If you're considering not using RAID at all, then you most likely don't need it, imo. If RAID 0 (aka ticking time bomb) is an option for you, then you *certainly* won't want RAID 5.

> **un_dave said:**
> should, or can i even, boot the system off my raid 5 software array?You can, but whether you *should* is up to you, really. Personally, I tend not to, mostly because I've come to think of server boxs' operating systems as "dispensable". By putting only the data that *needs* the added redundancy on an array, I end up with...

[LIST]
[*]Operating systems I can configure almost without thinking, because their installation processes never involve any disks with critically important data on them.
[*]An array I can freely swap out of one server & plug into another.
[*]Simple initial setup of arrays. Since no part of the OS is stored on them, I can create, destroy & manipulate them while the server is live.
[/LIST]

People mostly only use RAID with disaster in mind ... they are thinking about what would happen should one of their hard disks suddely crash & burn in a blaze of glory. So, when you're deciding how to organise your box, the goal is to make recovering from something like a hardware failure as quick & simple as possible, so your data losses are zero, and your downtime is as close to it as you can get. So, whether you choose to configure your system the way *I* would do it doesn't really matter ... what's important is to do it in a way that *you* feel confident you can manipulate in a crisis without making mistakes.

In any case, as I mentioned before, I'm not so sure RAID 5 is for you, based purely on the failure probabilities of the two alternative configurations you seemed to suggest. All things being equal, and compared to a simple single-disk install...
[LIST]
[*]Putting everything (including the OS) on RAID 5 is extremely robust. On a typical 4-device array, two of them would have to fail almost simultaneously to cause data loss.
[*]A five-disk system without any RAID would (obviously) be five times more likely to fail, but failures would only result in partial data loss.
[*]With a RAID-less OS + 4-disk RAID 5 array, the OS's failure probability is unaffected, but your important data is hundreds of thousands of times less likely to fail.
[*]A RAID-less OS + 4-disk RAID 0 array has a failure probability about 5 times *greater* than a single-disk install. 80% of the time, the data loss will essentially be total.
[/LIST]

Anyhow, I hope that helps answer your questions.

---

### Post by un_dave on 2007-09-20
Thanks heaps for all the info kidders.

I think i may have needlessly confused the issue by saying raid 0, when i meant raid 1 (mirrored).  Basically, the two options you discussed that are looking good to me at the moment are:
- unraided system disk + raid 5 data array 
or 
- raid 5 array, bootable. 

Over the past two days, with the help of the awesome people on irc, i've managed to mount some images as 'pretend' drives, and i've been playing with raiding these drives, failing them and rebuilding to see what happens, and 'growing' the array, and related filesystems, to add more space. 

I'm now pretty confident i wont have any issues with the RAID 5 process, so if we assume that i do want raid, how would i go about booting from raid 5 array?

Really, the only reason i would go with the first option is if the second is overly complex, and would prove harder for later maintenance. However, my main concern was 'growing' an array, and this seems to be fine running while the disk is online. It's also unlikely that i would be doing this very frequently, so 'growing' while the raid is offline using a live cd, or something similar wouldn't be out of the question. 

 I hope this is all making sense!

Thanks again for your time, 

Dave.

---

### Post by psusi on 2007-09-20
You can put / on the raid, but /boot must be on a single disk standard partition.  That can either be on a stand alone disk, or a small partition on one of the raid drives.

---

### Post by un_dave on 2007-09-20
How big would this partition need to be?

Based on the fact that my current /boot folder is 36mb, i imagine 50mb would be sufficient for this partition? This size is a little more of an issue because obviously if i make this partition on one of the drives, in a raid 5 array i'll lose that spaces on all drives.

If this partition can indeed be that small, and assuming that it's not impossible to setup, then i think i would go with that option. Only downside is that this /boot folder would not be part of the raid, so if the disk it was residing on failed, then the system wouldn't boot. However, such a small size could easily be backed up, so this shouldn't be and issue.

---

### Post by psusi on 2007-09-20
You should go with 100 MB so you have room for 2-3 kernels with some room to spare.  You can also copy the whole partition ( with dd ) to the other drives in the array, and if the primary drive fails, unplug it and the next drive in line will become the primary and boot.

---

### Post by un_dave on 2007-09-20
Thanks psusi, that sounds ideal!

One last thing. I've been setting up this distro over the last few days, so if possible, i'd prefer not to have to reinstall ubuntu once i get the raid 5 setup. 
Would it be possible to move the whole install from my current drive to the new raid 5 array?

I assume the answer is yes... because nothing seems to be impossible around here. But is it worth the effort, or should i start from scratch?

I would assume that the best way to do it would be to boot to a live cd, setup the raid 5, then mount my current system drive, and copy everything across. Then i'd just need to setup the boot process, and i'd be away!

Obviously won't quite be that simple... but am i on the right track?

---

### Post by kidders on 2007-09-20
> **un_dave said:**
> One last thing. I've been setting up this distro over the last few days, so if possible, i'd prefer not to have to reinstall ubuntu once i get the raid 5 setup.If you're careful with your Linux system files, you should be able to hold onto the same install for quite some time. :-) Personally, I'd be very resistant to reinstalling if I didn't *need* to.

> **un_dave said:**
> I would assume that the best way to do it would be to boot to a live cd, setup the raid 5, then mount my current system drive, and copy everything across. Then i'd just need to setup the boot process, and i'd be away!

Obviously won't quite be that simple.Actually, it kind of *is* that simple! In theory, I suppose you could do it without a live CD if you really wanted to, but I wouldn't recommend it.

My suggestions:[LIST]
[*]Stay away from graphical interfaces. Doing everything in a terminal window means you get to see every single error message, and gives you far better control over what's happening.
[*]For example, check out "man cp" for an idea of the number of different ways something can be copied. I would suggest something like **cp -dpR /mnt/old /mnt/new** ... a recursive, permissions-preserving, symlink-preserving copy. By comparison, drag & drop would most likely ruin your system.
[*]If at all possible, copy (ie don't move) things. It's just not worth the risk.
[*]It's easy to forget about things like /etc/fstab and /boot/grub/menu.lst ... files like these may need explicit references to /dev/sd?? changed to /dev/md??.
[*]The last step, as you rightly mentioned, is to reinstall your bootloader.[/LIST]Psusi's advice about the size of /boot is well worth taking. Personally, I would...[LIST]
[*] Go with at least double what you think would be sensible.
[*]Use Ext2 or Ext3, for the sake of stability.
[*]It's common practice to symlink /boot to itself ... **cd /boot && ln -s . boot **... to make auto-generated grub configurations more tolerant of inaccuracies.
[*]It's also commonplace to make an effort to protect your /boot from accidental damage, by adding "ro" or "noauto" to its /etc/fstab mount options. That way, any attempt to write to it will fail, unless you execute **mount -o remount,rw /boot** (in the case of "ro") or **mount /boot** (in the case of "noauto") first.[/LIST]Of course, you don't *have* to do any of the above ... they're just some conventions FYI.

Anyhow, I'm sure Psusi will have some things to add to (or take away from) this post, so hold off for a few hours before doing anything. The way I see it, you should be able to reboot your computer exactly the way it *used* to be, right up until you reinstall your bootloader, so if you suspect you might've made mistakes, there's no panic. :-)

**Edit:**

> **un_dave said:**
> I think i may have needlessly confused the issue by saying raid 0, when i meant raid 1 (mirrored).Oops... If I were awake, I might've spotted that hehe. Sorry. RAID 1 can have certain advantages, but is a bit wasteful (for lack of a better way of putting it!).

---

### Post by psusi on 2007-09-20
Yep, that's pretty much it.  Just cp -a ( -a is short for -dpR ) the old filesystem to the new one, install grub, and tweak fstab and menu.lst.  

You can do it without a livecd too; just boot into recovery mode.  You also will want to add -x to cp so it only copies the root filesystem, not things like /tmp, /boot, /proc, /sys, and doesn't get into an infinite loop trying to copy the files you have already copied to /mnt into /mnt again.  

If you have a /home partition or others, you will need to copy those as well.

---

### Post by un_dave on 2007-09-20
Great, this sounds ideal. 

I'm about to order 3 x 1tb drives online, so they probably wont be here for a week or so. (They're not in stock until next week, and they have to get shipped from one side of Australia to the other.) 

But knowing I can keep my install means I can happily tweak things to my hearts content with my current version, and put some time into reading up on this file system copy process. 

I guess the plus here is that because my current 320 gb drive isn't going to be part of the array, if the setup of the new raid drive goes horribly wrong, i can happily wipe it clean, and start again. 

Out of curiosity, as an alternative to using the cp command, can you somehow just copy the entire partition in one go?

Thanks for all the help!

---

### Post by kidders on 2007-09-20
> **un_dave said:**
> Out of curiosity, as an alternative to using the cp command, can you somehow just copy the entire partition in one go?Ordinarily yes, but not in this case.

If, for instance, you wanted to take a snapshot of your current 320GiB drive (or perhaps one of the filesystems on it), you could use something like "dd" to take a byte-for-byte copy of it. I wouldn't recommend doing it with RAID though, unless only the source location (or *both* the source and destination locations) were RAID arrays.

In theory, even if you *did* do some sort of "partition copy", you'd be copying something designed to work as a single-disk filesystem to a multi-disk device, which would have performance implications. It's much nicer to give yourself the opportunity to tailor your new filesystem(s) to your needs as you're creating them, rather than winding up stuck with something that doesn't perform as well as it could.

---

### Post by psusi on 2007-09-20
cp -a will make an exact copy of everything important, save the boot loader.  One of the nice things about Linux is you don't run into stupid crap like not being able to copy files because they are in use like on windows.

---

### Post by un_dave on 2007-10-29
Well, the drives have finally arrived, and the raid5 is setup as described. 
I have each drive partitioned with the first 100mb as ext3 (where 'll put the boot stuff) and the rest as part of the raid. 

Only point of note is that i skipped the lvm, and put the ext3 partition straight onto the raid, as i could see no reason to use lvm.

So, my next step is to move the filesystem across from my existing drive, which i assume i will do using something along the lines of:

cp -a -x /* /mnt/raid

Then you've mentioned installing grub, and tweaking the fstab. I've messed with fstab before, but what specifically will i need to do? And how do I install Grub? Will this allow me to setup the /boot on the 100mb partition?

Thanks for all the help along the way guys, this i'll be looking to writeup a how-to on this when i'm done!

For the moment, I'm about to go on holiday for a week, but I'm looking forward to setting this up when I get back.

---

### Post by psusi on 2007-10-30
Post your fstab and /boot/grub/menu.lst

---

### Post by un_dave on 2007-11-06
menu.lst:
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
# kopt=root=UUID=dd7f1c10-ce84-48a5-bf92-26524796a5c7 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

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

title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=dd7f1c10-ce84-48a5-bf92-26524796a5c7 ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=dd7f1c10-ce84-48a5-bf92-26524796a5c7 ro single
initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu 7.10, kernel 2.6.20-16-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=dd7f1c10-ce84-48a5-bf92-26524796a5c7 ro quiet splash
initrd		/boot/initrd.img-2.6.20-16-generic
quiet

title		Ubuntu 7.10, kernel 2.6.20-16-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=dd7f1c10-ce84-48a5-bf92-26524796a5c7 ro single
initrd		/boot/initrd.img-2.6.20-16-generic

title		Ubuntu 7.10, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

```

fstab:
```

# /etc/fstab: static file system information.
#
#  -- This file has been automaticly generated by ntfs-config -- 
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc /proc proc defaults 0 0
# Entry for /dev/sda1 :
UUID=dd7f1c10-ce84-48a5-bf92-26524796a5c7 / ext3 defaults,errors=remount-ro 0 1
# Entry for /dev/sda5 :
UUID=544540d3-cf22-4823-9fba-15d3fb114ac6 none swap sw 0 0
/dev/scd0 /media/cdrom0 udf,iso9660 user,noauto 0 0
# Entry for /dev/md0 :
/dev/md0 /mnt/raid ext3 rw,user 0 0

```

Note that the only bit I've edited manually is the # Entry for /dev/md0 ... Everything else is default.

---

### Post by un_dave on 2007-11-07
So assuming I want to leave the swap disk on the old 320gb drive for now, I figure this is how my new fstab should look. Basically, I've mounted the old root partition as /mnt/olddrive, and made the raid root.

fstab:
```

# /etc/fstab: static file system information.
#
#  -- This file has been automaticly generated by ntfs-config -- 
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc /proc proc defaults 0 0
# Entry for /dev/md0 :
/dev/md0 / defaults,errors=remount-ro 0 1
# Entry for /dev/sda5 :
UUID=544540d3-cf22-4823-9fba-15d3fb114ac6 none swap sw 0 0
/dev/scd0 /media/cdrom0 udf,iso9660 user,noauto 0 0
# Entry for /dev/sda1 :
UUID=dd7f1c10-ce84-48a5-bf92-26524796a5c7 /mnt/olddrive ext3 defaults,errors=remount-ro 0 1

```

And, I should add a new entry into menu.lst with the 'root' parameter changed, to point at one of my 100mb boot partitions. I've guessed (hd1,0), how do I actually know which it is?

menu.lst:
```

title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=dd7f1c10-ce84-48a5-bf92-26524796a5c7 ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

```

Now, I'm guessing once I have my file system moved to the raid, I update the fstab, and menu.lst as I've described, I will still need one last thing... the /boot folder setup, in one of the 100mb partitions. This is the one last thing I'm unsure of, how I get that /boot folder to initialize the raid?

Cheers again!

---

### Post by psusi on 2007-11-07
root= needs to point to your root partition, not your boot partition... i.e. /dev/md0.

---

### Post by un_dave on 2007-11-08
Ok, so assuming it should point to my raid5, how do i do that if it's not a physical drive?

```

root		(md0)

```

Would that work?

And, back to the grub stuff, should i be running grub-install?

Sorry about all the questions, but i'm really struggling to find any information on this topic. If you have a link that would help me out, feel free to post it.

---

### Post by psusi on 2007-11-09
Grub does not know what (md0) is.  The root command to grub needs to be (hd0,n) where n is the partition number of your /boot partition, where the kernel will be for grub to load.  I don't see a /boot partition in your fstab though.  

The root= kernel command line parameter needs to be /dev/md0 because that is what you want the kernel to use as the root filesystem.

---

### Post by un_dave on 2007-11-09
Ok, cool, progress :)

So my fstab should look like this, with /boot mounted as ro:

fstab:
```

proc /proc proc defaults 0 0
# Entry for /dev/md0 :
/dev/md0 / defaults,errors=remount-ro 0 1
# Entry for /dev/sdb1 :
/dev/sdb1 /boot ro 0 1

# Entry for /dev/sda5 :
UUID=544540d3-cf22-4823-9fba-15d3fb114ac6 none swap sw 0 0

/dev/scd0 /media/cdrom0 udf,iso9660 user,noauto 0 0

# Entry for /dev/sda1 :
UUID=dd7f1c10-ce84-48a5-bf92-26524796a5c7 /mnt/olddrive ext3 defaults,errors=remount-ro 0 1

```

And menu.lst should look like this:
menu.lst
```

title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd1,0) 
kernel		/boot/vmlinuz-2.6.22-14-generic root=/dev/md0 ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

```

How does that look?

---

### Post by Trillian1138 on 2007-11-10
Sorry for jumping on this thread, but I have a similar issue - just received my 3 500GB drives and am ready to make a RAID5 array. I've decided I'd like to boot from the array, rather than have a separate boot disk, and have a couple questions.

First, how did you actually create your array? I've seen some pages talk about using mdadm and some seem to imply you can do it straight through GParted on the Ubuntu LiveCD. Any help would be appreciated.

I am also more generally torn between a software and hardware array.

It seems to me that the pros of a software array are that  if/when i switch motherboards (which has the on-board RAID utility I'd be using) or the motherboard dies, I'm not tied to the same board. Hardware pros seeming to be a slight speed increase and less headache creating, since i'll be doing it through the board's built-in utility and not futzing with convincing an Ubuntu LiveCD to do it. Again, any help or thoughts would be appreciated.

Thanks for your time!
-Trillian

---

### Post by un_dave on 2007-11-10
Like I said somewhere in there, I intend to make up a tutorial when I've finished. But until then, I'll summarise my steps. Keep in mind that I'm not doing a fresh install, simply trying to shift my current install from it's current single disk setup.

You're pros/cons for software raid are right on the money, it seems to me that unless you have a lot of money to spend on a hardware raid controller, software raid is the way to go.

I did use mdadm, which seems to be the newer, and cooler, software raid tool out there, allowing things like raid 5 growing. 

Anyway, the steps:
 **1)formatting in GParted. **
Each of the drives was partitioned, giving a 100mb boot partition (ext3) and the remainder as unformatted. 

**Result is:** (including my current system disk)
```
dave@hades:~$ sudo fdisk -l

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0004ae8c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       38157   306496071   83  Linux
/dev/sda2           38158       38913     6072570    5  Extended
/dev/sda5           38158       38913     6072538+  82  Linux swap / Solaris

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000e7401

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1          13      104391   83  Linux
/dev/sdb2              14      121601   976655610   83  Linux

Disk /dev/sdc: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00074a9a

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1          13      104391   83  Linux
/dev/sdc2              14      121601   976655610   83  Linux

Disk /dev/sdd: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000111a9

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1               1          13      104391   83  Linux
/dev/sdd2              14      121601   976655610   83  Linux

```

**2) Create the array:**
```

dave@hades:~$ sudo mdadm --create /dev/md0 --level=5 --raid-devices=3 /dev/sdb2 /dev/sdc2 /dev/sdd2
mdadm: array /dev/md0 started.
```

**3) Checking the array:**
```

dave@hades:~$ sudo mdadm --detail /dev/md0
/dev/md0:
        Version : 00.90.03
  Creation Time : Mon Oct 29 23:57:38 2007
     Raid Level : raid5
     Array Size : 1953310976 (1862.82 GiB 2000.19 GB)
  Used Dev Size : 976655488 (931.41 GiB 1000.10 GB)
   Raid Devices : 3
  Total Devices : 3
Preferred Minor : 0
    Persistence : Superblock is persistent

    Update Time : Mon Oct 29 23:59:37 2007
          State : clean, degraded, recovering
 Active Devices : 2
Working Devices : 3
 Failed Devices : 0
  Spare Devices : 1

         Layout : left-symmetric
     Chunk Size : 64K

 Rebuild Status : 0% complete

           UUID : 0b915fb6:3b238a62:5d7d955a:8812843f (local to host hades)
         Events : 0.44

    Number   Major   Minor   RaidDevice State
       0       8       18        0      active sync   /dev/sdb2
       1       8       34        1      active sync   /dev/sdc2
       3       8       50        2      spare rebuilding   /dev/sdd2

```

**4) Creating the ext3 filesystem on the raid. **
Note that at this point, I had the choice of installing an LVM on top of the raid to allow for easier and more flexible partitioning. Because I only want one partition, I didn't bother. 
```

dave@hades:~$ sudo mkfs.ext3 /dev/md0 
mke2fs 1.40.2 (12-Jul-2007)
Filesystem label=
OS type: Linux
Block size=4096 (log=2)
Fragment size=4096 (log=2)
244170752 inodes, 488327744 blocks
24416387 blocks (5.00%) reserved for the super user
First data block=0
Maximum filesystem blocks=0
14903 block groups
32768 blocks per group, 32768 fragments per group
16384 inodes per group
Superblock backups stored on blocks: 
        32768, 98304, 163840, 229376, 294912, 819200, 884736, 1605632, 2654208, 
        4096000, 7962624, 11239424, 20480000, 23887872, 71663616, 78675968, 
        102400000, 214990848

Writing inode tables: done                            
Creating journal (32768 blocks): done
Writing superblocks and filesystem accounting information: done

This filesystem will be automatically checked every 37 mounts or
180 days, whichever comes first.  Use tune2fs -c or -i to override.
```
[B]
5) Mounting the drive:[/B]
```
	dave@hades:~$ sudo mount /dev/md0 /mnt/raid/
```

**6) Test. **
With judicious use of mdadm --detail /dev/md0, it's a good idea to make sure the raid can handle a failed drive. If you're using SATA, and don't mind getting your hands dirty, you can simply unplug a drive while the system is online. 
Once you're satisfied with the testing, *then* you can use the raid. 

Now, here's where it starts getting hazy for me... Also, this is quite specific to what I want to do, boot from the raid 5. So, bearing that in mind...

**7) Copy the filesystem: **
```
cp -a -x /* /mnt/raid

```
**8) Setup the menu.lst, and fstab**

See the current discussion in this thread...

**9) Setup the /boot partitions**

See the current discussion in this thread...

Hope that helps!

---

### Post by un_dave on 2007-11-29
Well, I've now admitted defeat.

After trying everything i could think of, and more. I've ended up not being able to get the root partition to reside on the raid 5. I can get everything to work right up to the grub bootloader, but then it doesn't seem to want to mount the raid, and the boot halts.

I've fallen back on having a raid 5 /home, and / living on a single disk.

The frustrating thing is that at no point has anyone said that this can't be done. It's just that no-one seems to be able to tell me how to do it!

Again, for more info on my boot struggles, see this thread: [http://ubuntuforums.org/showthread.php?p=3862865](http://ubuntuforums.org/showthread.php?p=3862865)

---

### Post by TrapMakeR on 2007-12-26
Hi,

Were you able to find a solution till now?

I have just set up a machine. /boot is on RAID1, / on RAID5
and the rest on RAID5+LVM. I just did not want to play with
initrd (no time at all), otherwise I would put / on LVM.

---

### Post by un_dave on 2008-01-03
Nope. No solution. I've ended up with much the same situation as you, but without the LVM. It's frustrating, but it works.

---

