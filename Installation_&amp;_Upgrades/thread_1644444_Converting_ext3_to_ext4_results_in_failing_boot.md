---
title: "Converting ext3 to ext4 results in failing boot"
date: 2010-12-13
forum: Installation &amp; Upgrades
---

### Post by materthron on 2010-12-13
Hi all,

I tried to convert my filesystem from ex3 to ext4 by following the [community docs]("https://help.ubuntu.com/community/ConvertFilesystemToExt4") for it.

When changing the fstab entry, my machine would say the filesystem is corrupted and boot into the maintenance console.
Running e2fsck -f always resulted in a "fs is clean" message.
After uncommenting the entry again (via Knoppix), my system would boot again.

My questions:

Is this is a "normal" fstab file?
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
#/dev/sda1
UUID=639fdfe7-cbee-414b-828b-e1d91b8df7f5 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=976a8f6b-d91c-421b-ba37-028f437b5ffe none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

```

I find it curious that my system boots with the crucial line (/dev/sda1) being commented out.

How can I convert to ext4?

As I used GRUB 1.5 before, I upgraded to GRUB2 (via installing the grub2 package and the upgrade-from-grub-legacy command).

Thanks!

Philipp

---

### Post by dabl on 2010-12-13
That /etc/fstab looks pretty normal. Some installers comment out the "/dev/sdxx" partition ID during setup, when they set up UUID mounting. UUID is way superior, since plugging in USB drives can change the /dev/sdxx numbers randomly, but UUIDs don't change (unless you reformat).

The community docs guidance for conversion of ext3 ---> ext4 are supposed to be very solid, but I admit I never did it.  If you really want to change to ext4 (assuming desktop user here), I would just back up everything essential, and repartition and reinstall.  Not sure it's worth it ....  but it will get the job done safely if that's what you want.

---

### Post by coffeecat on 2010-12-13
If you've converted sda1 to ext4, here is your problem:

> **materthron said:**
> ```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
#/dev/sda1
UUID=639fdfe7-cbee-414b-828b-e1d91b8df7f5 /               [COLOR=Red]ext3[/COLOR]    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=976a8f6b-d91c-421b-ba37-028f437b5ffe none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

```

You have to change that to 'ext4'. Make sure the UUID is still correct  after the filesystem modification. I see no reason why it shouldn't be,  but it's worth checking. Use:

```
sudo blkid
```> **materthron said:**
> I find it curious that my system boots with the crucial line (/dev/sda1) being commented out.

That is not a crucial line, just a comment line. The one following is the one that does the work. You'll find that the UUID that starts the line is that for sda1 - but see my comment above.

---

