---
title: "Increasing the size of root partition"
date: 2010-08-21
forum: Installation &amp; Upgrades
---

### Post by Mechanimal on 2010-08-21
The title should make it clear, because I'm having some trouble moving around partitions, and getting some extra space I've freed up from my extended partition, and don't know how to increase root with it. Here's a screenshot (I want the unallocated 12 gigs in the extended to increase the root partition at the top of the list):

[[IMG]http://img823.imageshack.us/img823/263/gparted.th.png[/IMG]](http://img823.imageshack.us/i/gparted.png/)]]

Thanks for any help!

---

### Post by Snark1994 on 2010-08-21
I'm no expert, but I don't think you can extend the root partition into that space because it can't be half-in half-out of the extended partition. I think what you want to do is to move /dev/sda5 and /dev/sda6 to the start of the extended partition, shrink the extended partition by 12 GBs then move it forward 12 GBs. That should then give you 12 GBs free after /dev/sda1 so that you can extend it :)

---

### Post by kansasnoob on 2010-08-21
Would you please also post the output from terminal of:

```
df -H
```

and:

```
cat /etc/fstab
```

---

### Post by Mechanimal on 2010-08-21
> **kansasnoob said:**
> Would you please also post the output from terminal of:

```
df -H
```

and:

```
cat /etc/fstab
``` I should also mention that I'm on Ubuntu from another drive now, and when I run the command you mentioned first, it shows information on this drive. I don't suppose that's the information you're looking for.

---

### Post by kansasnoob on 2010-08-21
> **Mechanimal said:**
> I should also mention that I'm on Ubuntu from another drive now, and when I run the command you mentioned first, it shows information on this drive. I don't suppose that's the information you're looking for.

True! If you can still boot into that Ubuntu OS it would be best to do so :)

If you can't boot into it that would also be nice to know.

---

### Post by Mechanimal on 2010-08-21
For df -H
```
Filesystem             Size   Used  Avail Use% Mounted on
/dev/sda1              6.9G   5.8G   783M  89% /
tmpfs                  1.1G      0   1.1G   0% /lib/init/rw
udev                   1.1G   238k   1.1G   1% /dev
tmpfs                  1.1G   541k   1.1G   1% /dev/shm
/dev/sda6              465G   115G   327G  26% /home

```

For cat /etc/fstab
```
# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda1 during installation
UUID=dff66502-0cc0-4455-89d4-a723d14abfa5 /               ext3    errors=remount-ro 0       1
# /home was on /dev/sda6 during installation
UUID=ced2b6f7-fa2e-46e0-8b64-b5f29e3e341a /home           ext3    defaults        0       2
# swap was on /dev/sda5 during installation
UUID=5db0d2e5-4ec7-4d7f-8e13-b5643837da9d none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto     0       0

```

This is while I'm booted on the debian-based distro on my other drive (this is the drive I want to change root with, but I figured I had to do it from my Ubuntu drive to make changes to it.)

I hope this is what you were looking for.

---

### Post by kansasnoob on 2010-08-21
Thanks. I just wanted to be certain that I identified the partitions properly. Now I can be sure:

/dev/sda1 = "/" (aka root)
/dev/sda2 = extended partition
/dev/sda5 = SWAP
/dev/sda6 = "/home"

So, boot a Live CD, go to Gparted, and first right click sda5, then click on "Swapoff".

Next right click on sda2 and select "Resize/Move", then resize the left edge as far to the right as possible. **[COLOR="Red"]Note: If done in this order you will only be resizing sda2! You DO NOT want to resize sda5 or sda6![/COLOR]** Click on apply.

That should leave about 13GB unallocated between sda1 and sda2, so you can now right click sda1 and use "Resize/Move" to grow it's right edge to the right as far as possible using the same process ;)

---

