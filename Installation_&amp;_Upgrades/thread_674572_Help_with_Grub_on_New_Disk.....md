---
title: "Help with Grub on New Disk...."
date: 2008-01-21
forum: Installation &amp; Upgrades
---

### Post by rompstar420 on 2008-01-21
Ok, my hobby server came with a 80GB hard-drive and I have bought a 500GB at Fry's, it was only $89, and since I run a gallery I want to upload lots of high-def pictures and video, so 80GIG wasn't going to cut it.

So the 80 Gig is currently set as:

/dev/hda1 and swap is /dev/hda2

I also have have an external USB hard-drive, but when I plugged in the new 500GB to transfer the OS that is coming up as /dev/hdd so I setup the partitions for now as:

/dev/hdd1 Linux
/dev/hdd2 Swap

I have successfully followed a Howto in making a copy of the old drive to the new, but the Howto was written to use LILO and Ubuntu uses Grub for the boot loader.

I have currently mounted the new 500GB drive as /new-drive and in /new-drive/etc/fstab
I am poiting to /dev/hda1 and /dev/hda2, even tho' the new drive is currently as /dev/hdd, I figure once I switch them, it will be /dev/hda, is this correct thinking ?

Anyways, the last steps that I have left are:

1. Install Grub on /dev/hdd
2. Turn off machine, remove old /dev/hda
3. switch jumper to primary on the new drive and install the 500GB
4 Boot machine

Help would be appreciated, thanks!!!!

I love Ubuntu.

---

### Post by jerrykenny on 2008-01-21
ah well . . . . your 2nd drive is currently showing as

hdd

because its on the second ide controller . . . . . but when you remove your original drive, you can probably unplug your cable that goes with it, . . . and plug the second cable into the first ide controller . . . 

that aught to make it hda again. . . . 

when you want to boot the thing . . . . 

put your installation disk in, and type

[SIZE="4"]rescue[/SIZE]

at the boot prompt,then hit enter . . . 

tel it you want to boot the partition /dev/hda1 ( i reckon thats your root file system ? )

When you get it booted type

[SIZE="4"]grub-install  /dev/hda[/SIZE]

---

### Post by rompstar420 on 2008-01-21
Ahhh that makes sense about the hdd, so if I simply unplug the 500GB drive and plug it into the existing ribbon that connects the current 80GB drive, that should be /dev/hda, right ?

I will do what you recommended and report any problems

---

### Post by jerrykenny on 2008-01-21
yes, I hope so . . . . . you havent altered your  /etc/fstab have you ?  if any entries for /dev/hdd is in fstab, possibly cos you were mounting that new drive from within ubuntu, then your boot might fail, with a message that that the filesystem could not be found . . . . . otherwise good luck . . . 

Its no ways st8forward so you might need some more forum posts, fingers crossed :)

---

### Post by rompstar420 on 2008-01-21
I see, well, the Air, let's go and hit it and try it out.

:)

In /newdisk/etc/fstab I have edited that to point to

/dev/hda1

and

/dev/hda2

so it should work once I plug it into the other first eide channel, thanks! for reminding me, have been away from Linux for a good 6 years, and before I used Slackware, so it's a "little" different, I like it a lot!

---

### Post by jerrykenny on 2008-01-21
SIX  years  !   omg,  i cant even remember breakfast

---

### Post by rompstar420 on 2008-01-21
Ok before I proceed here is my ./fstab does it look good ?


```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0

# /dev/hda1
UUID=c6f75e7a-6fe0-4f21-b3e9-dee7a9720499 /               ext3    defaults,errors=remount-ro 0       1

# /dev/hda2
/dev/hda2       swap    swap    defaults        0 0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0

# External USB Backup Drive
# /dev/sda1 /mount/backup ext3 defaults 0 0
# currently mounted out - not using it.
```

What is that UUID reference ?

---

