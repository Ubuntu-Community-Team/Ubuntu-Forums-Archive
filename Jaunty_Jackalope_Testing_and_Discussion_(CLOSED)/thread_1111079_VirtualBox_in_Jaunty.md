---
title: "VirtualBox in Jaunty"
date: 2009-03-30
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by john@ukgillies.com on 2009-03-30
Hello everyone,
Anyone get VirtualBox to install?
I cannot get it to install

Errors look like attached.

Many thanks,

John

---

### Post by cariboo on 2009-03-30
I installed VirtualBox from virtualbox.org yeasterday and it installed with zero problem. Virtualbox.org seems to be down right now, so sorry no proper links.

Edit: The site is back up again. Go [here]("http://www.virtualbox.org/wiki/Downloads") for downloads.

Jim

---

### Post by bapoumba on 2009-03-30
Moved to Jaunty, thanks!
(and to forestpixie too ;))

---

### Post by Wraith's Hand on 2009-03-30
Edit.  Never mind, I think I misunderstood the original post.

---

### Post by zevans on 2009-03-31
> **john@ukgillies.com said:**
> Hello everyone,
Anyone get VirtualBox to install?
I cannot get it to install

Errors look like attached.


Can't see your screenshot attachment, sorry. 

Is it a DKMS problem by any chance?

---

### Post by loomsen on 2009-03-31
Can't see it neither (or don't want to more likely, why spammin myelf?)
but most likely you just have to compile your module (usual procedure after upgrading your kernel.)

Make sure u have your kernel-source installed, usually located here:
```

ls /usr/src/linux-headers-`uname -r`

```

and compile it manually with:

```
sudo /etc/init.d/vboxdrv setup
```

---

