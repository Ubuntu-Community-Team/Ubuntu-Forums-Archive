---
title: "Clean install with /home Partitions?"
date: 2007-08-22
forum: Installation &amp; Upgrades
---

### Post by IronArjen on 2007-08-22
I am trying to upgrade my Dapper to Feisty, hence I need to do a clean install. I printed a document from the Ubuntu installation upgrade and set out to work. While installing the codes do not correspond to what I expect. Point 4 states Identify your root parttion.

I find an ntfs (Windows?) partition, the rest is all in dev\sda1, 2 ,3, 5 and 6. So which one is root, or which one I should set to root, which to swap?

The fact that I do not see a home partition, does this mean the guy who made my current OS work did make me a home partition? ( cannot find the guy!)

Tx IA

---

### Post by dreadlord_chris on 2007-08-22
```

cat /etc/fstab

```
this will list your partitions **as they are seen by your OS**

i.e. (from my fstab)
```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda2
UUID=88dca1de-72ab-4e0d-8579-89b31eb256aa /               ext3    defaults,errors=remount-ro 0       1
# /dev/hdd3
UUID=cd22e90e-d36a-4acd-8eda-282ddf2b69ed /home           ext3    defaults        0       2
# /dev/hda1
UUID=efe89fd9-58ab-456c-9881-528a9149e3c7 /media/DriveA   ext3    defaults        0       2
# /dev/hdd1
UUID=45eb76ed-6043-41ab-a272-6776dd6f1713 /media/DriveB   ext3    defaults        0       2
# /dev/hdd4
UUID=bb8c5625-c4e9-4f34-8bc7-9a9b9f86e651 /usr            ext3    defaults        0       2
# /dev/hdd2
UUID=7dee84b5-9573-432d-a827-99bb9fadba68 none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0

```
each line that starts with **#** is a comment (so it's ignored). The first partition listed in my fstab is the **root** partition
Each entry can be broken down into:
Filesystem: this is the UUID=xxxx.xxxx.... part of the line
```

_UUID=88dca1de-72ab-4e0d-8579-89b31eb256aa_  /       ext3    defaults,errors=remount-r  0       1

```
Mount Point: this is where your OS mounts the filesystem - it's the entry right after the UUID=...
```

UUID=88dca1de-72ab-4e0d-8579-89b31eb256aa   _/_       ext3    defaults,errors=remount-r  0       1

```
The next entry defines the type of filesystem to mount:
```

UUID=88dca1de-72ab-4e0d-8579-89b31eb256aa   /       _ext3_    defaults,errors=remount-r  0       1

```
I'll leave figuring out which one is SWAP to you...

btw.... if you don't see a seperate /home partition listed then that means that there wasn't a _seperate_ one set up...

---

