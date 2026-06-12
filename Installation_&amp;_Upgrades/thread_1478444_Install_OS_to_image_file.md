---
title: "Install OS to image file"
date: 2010-05-09
forum: Installation &amp; Upgrades
---

### Post by Neds Moar Salt on 2010-05-09
Can I install ubuntu to an image file?  I am using GRUB to boot my live cd, so is there a way to trick the installer into picking up an image file as another hard disk, like it is in wubi?  (I am using mac)

Really what I am looking for is a way to use an image file as a hard disk.

---

### Post by Bachstelze on 2010-05-09
You can mount the image file and do a debootstrap to it.

---

### Post by Neds Moar Salt on 2010-05-09
> **Bachstelze said:**
> You can mount the image file and do a debootstrap to it.

Hmmm...  I don't know what that means.  Could you explain please?

---

### Post by Bachstelze on 2010-05-09
In a nutshell, boot your Live CD, mount your image file like this

```
sudo mount -o loop /path/to/image.img /mnt
```

Then install the base system like this:

```
sudo debootstrap lucid /mnt http://archive.ubuntu.com/ubuntu
```

However, I don't really know how you could boot such a system...

---

### Post by Jay Car on 2010-05-09
> Really what I am looking for is a way to use an image file as a hard disk.

I think this is something that Virtualbox can do...could that be what you're looking for?

---

