---
title: "[SOLVED] Moving /home onto a separate HD"
date: 2007-04-03
forum: Installation &amp; Upgrades
---

### Post by apastuszak on 2007-04-03
Ok, here is what I have set up in my box.  I have 1 250 GB  SATA drive as /dev/sda.  I have a seperate 40 GB HD as /dev/sdb.  Right now sda has Edgy on it and sdb has Fesity beta on in.  I was to set up the machine so that /dev/sda1 automatically mount under /home in my filesystem.

Do I need to put a UUID into fstab?  How do I even find the UUID of the other HD?

I have already mount /dev/sda and copied my whole home drive over to the root of it, and set all proper permissions.

So now it's just a matter of editing fstab

sudo fdisk -l looks like this:

[FONT="Courier New"]Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       30216   242709988+  83  Linux
/dev/sda2           30217       30401     1486012+   5  Extended
/dev/sda5           30217       30401     1485981   82  Linux swap / Solaris

Disk /dev/sdb: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        4681    37600101   83  Linux
/dev/sdb2            4682        4865     1477980    5  Extended
/dev/sdb5            4682        4865     1477948+  82  Linux swap / Solaris[/FONT]

/etc/fstab looks like this:

[FONT="Courier New"]# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdb1
UUID=9bc060cb-a61c-48a3-b3b5-8550a95e6e99 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sdb5
UUID=256868a8-923a-4df2-806d-64a9a5dcb36e none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0
[/FONT]

Any help anyone can provide would be greatly appreciated.   I know the setup is kind of odd, but it works for me.

---

### Post by kidders on 2007-04-04
Hi there,

> **apastuszak said:**
>  Do I need to put a UUID into fstab?You don't *_need_* to, but you can if you like. Some people prefer to use filesystem UUIDs, others prefer the more traditional /dev node names. You can find your UUIDs with the **vol_id** tool, or by examining the symlinks in /dev/disk.

> **apastuszak said:**
> I know the setup is kind of odd, but it works for me.There's nothing even slightly odd about your setup (in theory), so don't worry about seeming strange! In practical terms though, I'm a little confused. Your post is a bit vague about exactly where your new /home is ... you referred to it as /dev/sda. :confused: Where exactly did you copy your files to? (Judging from your partition table dump,  you may have overwritten Edgy. Was that your intention?)

---

### Post by apastuszak on 2007-04-04
Edgy is still there.  I copied my home partition onto /dev/sda1.  My goal is to mount /dev/sda1 as /home and then pick files off /dev/sda1 and copy them into the new home drive and then delete edgy by simply rm -rf directory by directory.

I am trying to be as non-destructive as possible.

I was OK doing it myself, till I saw UUIDs.

Andy

---

### Post by kidders on 2007-04-04
Ah I see. Sorry... I was just afraid something weird was going on.

If you don't like using filesystem UUIDs, that's okay. (Linux survived for decades without them!) The only thing to be aware of is that referencing something using its /dev node name results in different behaviour, when things move around.

Essentially, UUID-style filesystem references in /etc/fstab are immune to rewiring ... ie you can suddenly decide to move your primary master IDE device to an SATA controller, and Ubuntu will not even notice the difference. On the other hand, a filesystem's UUID will change if you format it ... /dev-style filesystem references would remain unaffected.

In any case, go with what you understand, and like the "feel" of. :-) There is absolutely no reason not to mix & match (ie sometimes use UUID references, and sometimes use /dev paths), or change things around at some point in the future.

---

### Post by apastuszak on 2007-04-05
I got it all working without UUIDs.  I will probably switch to UUIDs sometime today.

Andy

---

### Post by kidders on 2007-04-05
Good news. :-)

If you need any further explanation, or run into any more trouble, feel free to post back.

---

### Post by louieb on 2007-04-05
list UUID
```
ls -l /dev/disk/by-uuid/
```

---

