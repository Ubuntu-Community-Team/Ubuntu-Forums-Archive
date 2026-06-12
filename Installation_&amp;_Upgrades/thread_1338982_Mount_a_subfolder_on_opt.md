---
title: "Mount a subfolder on /opt"
date: 2009-11-27
forum: Installation &amp; Upgrades
---

### Post by Sanix on 2009-11-27
Hi guys,
I have a partition mounted under /mnt/data, which contains a folder named "opt".
Now I want, that my /opt is pointing to this folder. Or is it only possible, that /opt is pointing to a partition?

I don't know if I described it exactly, so some examples:
If I create a folder in /opt, it will be created in /mnt/data/opt and reverse. Since it should be the same partition.

---

### Post by lloyd_b on 2009-11-27
> **Sanix said:**
> Hi guys,
I have a partition mounted under /mnt/data, which contains a folder named "opt".
Now I want, that my /opt is pointing to this folder. Or is it only possible, that /opt is pointing to a partition?

I don't know if I described it exactly, so some examples:
If I create a folder in /opt, it will be created in /mnt/data/opt and reverse. Since it should be the same partition.

The simplest way to handle that is with a "symlink" (symbolic link).  In a terminal window:```
sudo mv /opt /oldopt
sudo ln -s /mnt/data/opt /opt
```(I'm having you backup the existing /opt directory because I don't know if there's anything in there on your system.  If it's empty, you can just 'rmdir' it instead of moving it to a new name).

Lloyd B.

---

