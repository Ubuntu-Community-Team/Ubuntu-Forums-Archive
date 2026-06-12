---
title: "[SOLVED] Partition"
date: 2008-11-16
forum: Installation &amp; Upgrades
---

### Post by adamant715 on 2008-11-16
Ok, Im wondering. Is the NTFS partition my windows partition and EXT3 my ubuntu partition?

---

### Post by Pumalite on 2008-11-16
Yes

---

### Post by adamant715 on 2008-11-16
What do i put for the file system on it? FAT32?

---

### Post by Pumalite on 2008-11-16
You said it yourself: ext3
For data you can make it ntfs. Ubuntu natively reads and writes to ntfs. Just have to install ntfs-3g if it doen't come with your package.

---

### Post by adamant715 on 2008-11-17
Thank you, and I'm guessing the mount point is /home?

---

### Post by psusi on 2008-11-17
> **adamant715 said:**
> Thank you, and I'm guessing the mount point is /home?

No, if you only have one one linux partition it will be the root ( / ).

---

### Post by adamant715 on 2008-11-18
Thank you . ;)

---

