---
title: "Gutsy: is ntfs-3g == ntfs now?"
date: 2008-01-05
forum: Installation &amp; Upgrades
---

### Post by Finch75 on 2008-01-05
Hi everybody,

last year, I installed Feisty with ntfs-3g and "played around a little".

Now I'm installing Gutsy and ntfs rw-support is available "out of the box". So far so good.

However, I need to mount additional partitions and I am slightly confused by the new fstab. Is "ntfs" now officially the same as "ntfs-3g"? In Feisty, "ntfs" was read-only.

I have tried to do searches and find some information, but haven't found anything mentioning this change...

On a related note... how can I find out if "ntfs" and "ntfs-3g" mean the same? (I mean some command that shows me if they load the same filesystem driver...) I am still new to Linux and would just like to know how to find out stuff like this in the future :-)

Thanks,

Finch

P.S.: Is there any place I could've / should've found this information myself?

---

### Post by LaRoza on 2008-01-05
I don't know what fstab was like before, but ntfs in fstab allows write support on my end.

[http://ubuntuforums.org/showthread.php?t=283131](http://ubuntuforums.org/showthread.php?t=283131)

---

### Post by Finch75 on 2008-01-05
yes, I know it does... but that still doesn't answer my question... is "ntfs" and "ntfs-3g" the same now? (when used in fstab)

Synaptic shows that ntfs-3g is installed. Is "ntfs" just something like an alias now? In Feisty ntfs and ntfs-3g were different.
If I install an updated version of ntfs-3g, will it be used if I refer to it by using "ntfs"?

And still: How do I "find out" (other than asking here) if the two mean the same?

---

