---
title: "How to *properly* delete unwanted kernels?"
date: 2006-08-05
forum: Installation &amp; Upgrades
---

### Post by xp_newbie on 2006-08-05
After several updates, my /boot directory accumulated quite a few older kernel versions of which I would like to get rid. However, there are quite a few file types corresponding to each kernel version:

abi-2.6.x
config-2.6.x
initrd.img-2.6.x
System.map-2.6.x
vmlinuz-2.6.x

Do I need to delete all of them in order to get rid of that kernel version?

If so, are there special steps I need to follow before/after deleting those files?

Thanks,
Alex

---

### Post by orb9220 on 2006-08-05
Remove the linux-image packages you don't need using synaptic or any other package manager. 

I think that may remove them from the grub too. If not no biggie just edit grub.lst to remove the entries.

---

### Post by plexi50 on 2006-08-06
I usually keep only the last two updates. When I removed the oldest kernel with synaptic, it removed it from grub, too.

---

### Post by Benzorro on 2006-08-07
I'm very new but where do I find the linux-image package in the package manager?{synaptic}

---

### Post by xp_newbie on 2006-08-10
> **Benzorro said:**
> I'm very new but where do I find the linux-image package in the package manager?{synaptic}

It is name "linux-image-2.6.xx-yy-x86" (replace xx, yy, z with numbers)

For example, in my case I deleted the following two packages:

linux-image-2.6.15-23-386  (2.6.15-23.39)
linux-image-2.6.15-23-686  (2.6.15-23.39)

After being helped by so many good people here, I am glad to be able to give something back. :)

---

### Post by Benzorro on 2006-08-16
Thanks for your reply.  I finally got a chance to look for it.  It gave me an option to remove or complete removal.  What is the difference?

---

### Post by xp_newbie on 2006-08-17
> **Benzorro said:**
> Thanks for your reply.  I finally got a chance to look for it.  It gave me an option to remove or complete removal.  What is the difference?

"complete removal" does "removal" - plus removing any settings or profiles you may have created since that package install.

---

