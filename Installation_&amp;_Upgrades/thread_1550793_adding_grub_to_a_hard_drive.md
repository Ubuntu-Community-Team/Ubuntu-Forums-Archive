---
title: "adding grub to a hard drive"
date: 2010-08-11
forum: Installation &amp; Upgrades
---

### Post by cong06 on 2010-08-11
I recently purchased a Thinkpad T410.
With the thinkpad came windows 7.

Soon I decided that I wanted to use a solid state hard drive, and just this morning I recieved and managed to copy all my files over.

I ran dd to copy the partitions:
dd if=/dev/sda2 of=/dev/sdb2  (windows)
dd if=/dev/sda5 of=/dev/sdb3  (ubuntu)

Now the problem is that this new hard drive doesn't appear to have grub on it.

How do I install grub? Can I do it with a live disk?


(Partitions below: sda being the old, sdb being the new)
```

The original hard drive was like this:
/dev/sda1 SYSTEM_DRV
/dev/sda2 Windows7_OS
/dev/sda4 extended
-> /dev/sda5 Ubuntu ext4
-> /dev/sda6 SWAP
/dev/sda3 Recovery partition

The new hard drive is now like this
/dev/sdb2 Windows7_OS
/dev/sdb3 Ubuntu
/dev/sdb1 extended
-> /dev/sda5 SWAP

```

---

### Post by dabl on 2010-08-11
Probably you need to review this:  [http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

---

### Post by cong06 on 2010-08-11
sweet! I need to bookmark that link.


I did have some problem, but that's cause I didn't read it correctly.
For reference this command is what finally worked for me:
```

sudo grub-install --root-directory=/media/drive/ /dev/sda

```

---

