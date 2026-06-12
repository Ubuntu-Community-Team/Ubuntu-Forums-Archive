---
title: "uuids for the windows partitions?"
date: 2007-04-29
forum: Installation &amp; Upgrades
---

### Post by undecidable on 2007-04-29
When I installed Feisty (clean install)
it recognized the W fat32 partitions and put entries for them in fstab.

However the uuids are only 8 chars instead of the usual 32 chars for the ext3 uuids.
I believe the W does not support uuids,
so my question is:
 where did these uuids for the fat32 partitions come from?
Did Ubuntu installer assign them?

2.  Now I have added a 2nd hdd.  
But fstab has not been updated.
so how do I generate these 8 digit uuids so I can manually add these partitions to fstab?

any help appreciated.

---

### Post by kidders on 2007-05-01
Hi there,

> **undecidable said:**
> where did these uuids for the fat32 partitions come from?The application used to create the filesystems (perhaps your Windows installer?) set them.

> **undecidable said:**
> Did Ubuntu installer assign them?No. Linux absolutely never alters filesystems without being told to do so.

> **undecidable said:**
> Now I have added a 2nd hdd. But fstab has not been updated.Similarly, Ubuntu generally won't alter /etc/fstab without being told to. In general, there is no way for Ubuntu to guess what you'd like to do with a new hard disk it's never seen before, so you should make any required changes yourself.

> **undecidable said:**
> how do I generate these 8 digit uuids so I can manually add these partitions to fstab?The length of a filesystem UUID is irrelevant. As long as no two UUIDs are the same, what they are makes no difference, so you needn't worry.

I hope that helps.

[COLOR=Silver][[SIZE=1]*[UAResolved]*[/SIZE]]("http://ubuntuforums.org/showthread.php?t=377083")[/COLOR]

---

### Post by undecidable on 2007-05-01
Kidders

It does help, thanks.
I assume the uuids are generated when the filesystem is created  (ie partition formatted).

Do you have any idea how to find out the uuids of a fat32 or ntfs partition so I can use them in the fstab?

"tune2fs - l" won't do it as it says there is no superblock.

google search only tells me how to assign - just can't find anywhere that tells me how to find/read them. 

thanks
MC

---

### Post by kidders on 2007-05-01
> **undecidable said:**
> Do you have any idea how to find out the uuids of a fat32 or ntfs partition so I can use them in the fstab?

"tune2fs - l" won't do it as it says there is no superblock.Yeah... **tune2fs** (as its name suggests) expects an Ext2 filesystem, so "no superblock" just means "Aagh... something's not right".

You can find a filesystem's UUID by typing **sudo vol_id /dev/whatever**. Also, you may notice udev creating symbolic links at **/dev/disk/by-uuid** that you can also use to associate a UUID with its underlying device node.

---

### Post by Churnd on 2007-05-01
You can generate (and check) labels using e2label:
```
sudo e2label dev
```

---

### Post by undecidable on 2007-05-01
kidders

thanks very much.  Two perfectly satisfactory ways of getting the answer.
As my father used to say "your blood is worth bottling".

(Churnd - I think e2label only works on ext2/3)

mc

---

### Post by kidders on 2007-05-01
> **undecidable said:**
> As my father used to say "your blood is worth bottling".Lol!

---

