---
title: "How to clone an installed partition?"
date: 2005-08-10
forum: Installation &amp; Upgrades
---

### Post by Offset on 2005-08-10
Peace, users!

I tried to clone an installed Kubuntu, for a backup, thusly:

```

# mount /dev/hda7 /mnt
# nice cp --verbose --recursive --no-dereference --one-file-system \
   /bin /boot /etc /home /lib /media /root /sbin /topics /usr /var \
   /cdrom /initrd.img /vmlinuz /mnt

```

/initrd.img and /vmlinuz are symlinks into /boot, and /cdrom symlinked media/cdrom. 

Did not copy "special" directories: /.dev, /dev, /proc, /sys, /tmp:

```

# cd /mnt
# mkdir .dev dev data initrd mnt opt proc srv sys tmp

```

And updated GRUB.

(What's the initrd.img story? Never mind, different question.)

OK, question: the system did boot, but when trying to login (in KDM), something goes wrong, I don't know what, it just goes back to the login screen.

/var/log/kdm.log contains all sorts of nonsense (several repetitions of):

```

Error: Can't open display: :0
FATAL: Module via not found.
[drm] failed to load kernel module "via"
(EE) VIA(0): [dri] DRIScreenInit failed.  Disabling DRI.
Could not init font path element unix/:7100, removing from list!
QImage::convertDepth: Image is a null image
QImage::smoothScale: Image is a null image
Xsession: unable to create X session log/error file; aborting.
AUDIT: Sat Aug  6 07:12:30 2005: 7535 X: client 2 rejected from local host
Xlib: connection to ":0.0" refused by server
Xlib: No protocol specified

```

but KDM did start, did let me login. 

Any ideas? The systems (partitions) ought to be identical, by my thinking, hmm?

Thanks!

---

### Post by johanvdw on 2005-08-10
For backup purposes, the easiest way to copy a complete partition is using:

```
 sudo  dd if=/dev/hda1 of=/dev/hdb1
```
(if = input, of = output)

---

### Post by transactionlogfiller on 2005-08-10
Have you tried dd?

Something like

dd if=/dev/hda1 of=/dev/hda2

to clone the partition on hda1 to hda2.

---

### Post by Offset on 2005-08-11
dd? Come on...

Ah, I didn't mention: I copied the system while _mounted_! Logged into it! 
From my avoiding the mount-point directories you could have guessed.

dd won't do.
(And it will copy the entire 8G partition instead of just 1.7G files I did with cp.)

Better ideas?

---

### Post by wrtrdood on 2005-08-11
tar cf - * | ( cd /target; tar xfp -)

...where /target is the destination

---

