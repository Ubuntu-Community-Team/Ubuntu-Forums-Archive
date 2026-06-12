---
title: "can't mount my system this morning"
date: 2006-10-16
forum: Installation &amp; Upgrades
---

### Post by viniosity on 2006-10-16
This morning when I try to load my system I get an error like:

```

mounting dev/mapper/ubuntu-root /root failed



```

It eventually dumps me into busybox.. from where I have no idea what to do.

I can boot from the live cd but it does not mount my hard disk.  The output of fstab -l is:

Device Boot    Start    End    Blocks   ID  System
/dev/hda1       1        9729 781481161  5   Extended
/dev/hda5 *     1        31    248944+   83  Linux
/dev/hda6       32       9729   77899153+ 8e Linux LVM

I ran e2fsck on hda5 and it came out ok but on hda6 I get an error saying:

e2fsck:  Bad magic number in super-block while trying to open /dev/hda6
/dev/hda6:
The superblock could not be read or does not describe a correct ext2 filesystem. If the device is valid and it really contains an ext2 filesystem (and is not swap or ufs or something else), then the superblock is corrupt, and you might try running e2fsck with an alternate superblock
e2fsck -b 8193 <device>

I then tried e2fsck -b 9730 /dev/hda6 but got the same error..

Any ideas out there?  This is my mail server and I'd really love to get my data back!

---

### Post by taurus on 2006-10-16
What's your /etc/fstab look like then?

---

### Post by viniosity on 2006-10-16
I can't see my fstab, but booting off the live CD the fstab is:

unionfs / unionfs rw 0 0
tmpfs /tmp tmpfs nosuid,nodev 0 0

---

### Post by taurus on 2006-10-16
Mount your root, /, partition somewhere and have a look at your /etc/fstab!!!  

```

sudo mkdir /mnt/ubuntu
sudo mount -t ext3 /dev/hda6 /mnt/ubuntu
(assuming that you use ext3 and your / is on /dev/hda6!!!)
more /mnt/ubuntu/etc/fstab

```

---

### Post by viniosity on 2006-10-16
I had tried that already.. sorry, maybe I should have made that clear.  

sudo mount -t ext3 /dev/hda6 /media

gives

mount: /dev/hda6 already mounted or /media busy

doesn't matter which directory I try to mount /dev/hda6/

So, one thing I did forget is to type the full error on boot:

```

2 logical volume(s) in volume group "Ubuntu" now active
[   29.353451] EXT3-fs: journal inode is deleted.
mount: Mounting /dev/mapper/Ubuntu-root on /root failed: Invalid argument
mount: Mounting /root/dev on /dev/.static/dev failed: No such file or directory
mount: Mounting /sys on /root/sys failed: No such file or directory
mount: Mounting /proc on /root/proc failed: No such file or directory
Target filesystem doesn't have /sbin/init

```

And then it drops me into busybox.  So I think I need to fix this deleted journal inode thing somehow or else chroot into my drive from busybox and fix something.

So that's the situation.. hope you can help me out because I'm pretty lost on this one.

---

### Post by viniosity on 2006-10-16
Ok, this problem is solved.  How you ask?  By a large snapping sound followed by billowing smoke coming out of my computer case.  Yes, Jim, the hard disk is toast.

No recovering from that regardless of how well you chroot..

Anyway, thanks for the time and attention.  May that box rest in peace.. (or else not mind that it's totally getting gutted)

---

### Post by taurus on 2006-10-16
It's time for shopping!!!  ](*,)

---

