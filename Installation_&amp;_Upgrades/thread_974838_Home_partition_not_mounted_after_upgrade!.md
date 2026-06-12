---
title: "Home partition not mounted after upgrade!"
date: 2008-11-07
forum: Installation &amp; Upgrades
---

### Post by theShaggy on 2008-11-07
Hey guys,

I just upgraded from 8.04.1 to Ibex 64-bit.  It gave me some difficulty and errors installing both Samba and Upgrade Manager, apparently (but using the command line seems to work fine).

However, it won't load up for me, as it will not read my seperate HOME partition.  I don't know why this is, but when I try to load up in a Failsafe I get the new Ibex background and no interface loads.

I've not rolled back to Hardy, but I can't find any help on how to solve this?

UPDATE - so it turns out that it's an FSCK thing... it's telling me that my /dev/hda4 is not a valid "ext2" device and refuses to mount it, saying "special device /dev/hda4 does not exist."

But it exists when I roll back the kernel.  Any help?

---

### Post by kidders on 2008-11-09
Hi there,

> **theShaggy said:**
> "special device /dev/hda4 does not exist."The newer kernel may be mapping it to a different /dev node. Depending on your chipset, it could now be called something in the sd[n] range.

Try going through all your filesystems and verifying that their corresponding entries in /etc/fstab are still current. You may have to change one or two things for compatibility with newer kernels. One way to get a list of detected filesystems is ...```
ls -l /dev/[hs]d*[0-9]
```

---

### Post by theShaggy on 2008-11-12
Oh hi, managed to get it working, forgot to update the forums. There was a post elsewhere here that gave me the answer.

Turns out that during the upgrade from 8.04 -> 8.10 they renamed all my /dev/hda* mounts to /dev/sda*, so I just had to rename them in my fstab.  Works like a charm now.

Thank you, though.

---

### Post by psusi on 2008-11-12
I'm pretty sure that was actually done back in like 7.10 or 7.04.  Weird.

---

