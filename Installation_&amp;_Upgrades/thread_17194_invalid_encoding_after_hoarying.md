---
title: "invalid encoding after hoarying"
date: 2005-02-26
forum: Installation &amp; Upgrades
---

### Post by thnogueira on 2005-02-26
This is my very first message to this forum and I'd like to thank you guys for developing ubuntu. But as usual for somebody that is trying a new installation I got some problems...

Let me tell you whats wrong, I've installed a fresh warty dist for portuguese brazilian language and everything was ok including that the system recognized tipical brazilian characters (like: ã, ó, à, etc...) for filenames in all partitions I already have, witch includes ext3, fat32 and ntfs.

After a while I decided to go to hoary  and made a new fresh install with the iso provided in array-5. What happenend is that the system does not recognize this characters anymore and put (invalid encoding) at the end of the filenames that have this characters.

Do you know what happened?

Thanks,
thnogueira.

---

### Post by thnogueira on 2005-02-26
Well, I solved part of the problems:

**for NTFS**: added nls-utf8 option at fstab:
/dev/hda6	/progs		ntfs	ro,utf8,umask=0222	0	0

**for vfa**t: added iocharset=utf8 option:
/dev/hda5	/documentos	vfat	iocharset=utf8,umask=000	0	0

But the system warned me that this is not a good option for vfat because it will became case sentitive. I think this can be a problem if boot the other OS having in the same directory something like: nameoffile and NameOfFile.

**for ext3**: still having problems, since I haven't found how to add this option for this kind of partition

---

