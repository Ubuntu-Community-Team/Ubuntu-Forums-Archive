---
title: "FSCK Error!"
date: 2006-11-04
forum: Installation &amp; Upgrades
---

### Post by tuxy on 2006-11-04
I got this error message while my PC was booting:
----------------
Log of fsck -C -R -A -a 
Sat Nov  4 14:52:46 2006

fsck 1.39 (29-May-2006)
/: Superblock last mount time is in the future.  FIXED.
/: clean, 150896/1221600 files, 2044545/2441376 blocks
fsck.ext3: Unable to resolve 'UUID=1c27a699-e034-4ab1-bf6a-6c6ac452f29a'

fsck died with exit status 8

Sat Nov  4 14:52:47 2006
----------------

I tried fixing the issue by running 
$fsck.ext3 UUID=1c27a699-e034-4ab1-bf6a-6c6ac452f29a

But I had no luck it says "fsck.ext3 unable to resolve UUID=1c27a699-e034-4ab1-bf6a-6c6ac452f29a" 

Any of you guys know whats the error and why it is caused? In fact, I got this error after I installed Fedora Core 5 on different partition.
I get this error whenever I boot into Ubuntu Edgy partition. I can boot into the Ubuntu parition but I get this awful message everytime! 

Any suggestions will be greately regarded.

---

### Post by kidders on 2006-11-04
Hi there,

Does a filesystem with that UUID actually exist? One possibility is that your Fedora install reformatted a previously unused partition, changing its UUID in the process.

---

### Post by tuxy on 2006-11-04
If you check the man pages for fsck it says there is.

---

### Post by bsussman on 2006-11-04
> **tuxy said:**
> If you check the man pages for fsck it says there is.

The man page is doc for the utility - in what way would it know whether that particular UUID exists?

do:

```
dumpe2fs /dev/<eachofyorpartitions>
```

and see if that UUID exists.

---

