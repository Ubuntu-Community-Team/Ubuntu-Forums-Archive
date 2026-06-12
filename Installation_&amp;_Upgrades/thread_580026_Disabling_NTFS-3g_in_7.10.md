---
title: "Disabling NTFS-3g in 7.10"
date: 2007-10-18
forum: Installation &amp; Upgrades
---

### Post by victor_c26 on 2007-10-18
How can I disable/uninstall NTFS-3g upon installation of 7.10?

Quite frankly, I don't want my Vista NTFS hard drive to get corrupted. And yes I heard NTFS-3g has been mostly stable so far, but I just don't want to take the risk. Piece of Mind is very important for me.

---

### Post by kellemes on 2007-10-18
> **victor_c26 said:**
> How can I disable/uninstall NTFS-3g upon installation of 7.10?

Quite frankly, I don't want my Vista NTFS hard drive to get corrupted. And yes I heard NTFS-3g has been mostly stable so far, but I just don't want to take the risk. Piece of Mind is very important for me.

Just don't mount the disk.

---

### Post by logos34 on 2007-10-18
**sudo ntfs-config**

>disable write support

---

### Post by victor_c26 on 2007-10-18
Thanks logos.

I still want to transfer files from Vista to Ubuntu, but I don't want Ubuntu to modify the NTFS HDD in anyway. This is exactly what I needed.

---

### Post by szaka on 2007-11-04
Mount the disk read-only. You can do this by adding the 'ro' mount option in the /etc/fstab file. Maybe ntfs-config also supports this situation.

---

