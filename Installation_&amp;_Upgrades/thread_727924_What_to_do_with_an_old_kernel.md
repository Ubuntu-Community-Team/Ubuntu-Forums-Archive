---
title: "What to do with an old kernel?"
date: 2008-03-18
forum: Installation &amp; Upgrades
---

### Post by revenant138 on 2008-03-18
Hi all,

I upgraded my distro and pulled down the 2.6.22 kernel. Now I have the old 2.6.20 laying around. I was wondering whats the 'correct' procedure for getting rid of it? I know how to edit it out of GRUB, but I want to remove it totally. Do I just go delete the thing or is there a 'best' way?

Thx ;-)

---

### Post by ittiam on 2008-03-18
You can remove the unwanted kernel image. 

```
sudo dpkg -r kernel_image_name
```

---

### Post by revenant138 on 2008-03-18
Wow, that was totally obvious. I feel awesome about myself. :lolflag:

Oh hey, will it work with Apt? My guess would be yes. I usually use apt to do everything.

---

### Post by ittiam on 2008-03-18
Well using apt i am not sure, it might say it has to remove some dependencies as well. Honestly I have not tried removing a kernel image using apt. dpkg just works fine for me.

---

### Post by revenant138 on 2008-03-19
Update: I did it, it worked fine, but a weird side effect occurred - I use an Nvidia 8600 and i have to install the driver with each kernel because it needs the kernel headers (or whatever is technically happening). I had this working for my new 2.6.22 kernel, but when i removed the old 2.6.20, i had to reinsall the driver for 2.6.22. How weird is that?

Thanks again for the help :)

---

### Post by chewearn on 2008-03-19
> **revenant138 said:**
> Update: I did it, it worked fine, but a weird side effect occurred - I use an Nvidia 8600 and i have to install the driver with each kernel because it needs the kernel headers (or whatever is technically happening). I had this working for my new 2.6.22 kernel, but when i removed the old 2.6.20, i had to reinsall the driver for 2.6.22. How weird is that?

Thanks again for the help :)

Usually, a device driver is part of the kernel. But because the proprietary nvidia driver is separate a binary blob, you have to link it separately to the kernel.  That's why, when the kernel changes, the binary blob has to be re-link.

---

### Post by revenant138 on 2008-03-21
> **AstalaVista said:**
> Usually, a device driver is part of the kernel. But because the proprietary nvidia driver is separate a binary blob, you have to link it separately to the kernel.  That's why, when the kernel changes, the binary blob has to be re-link.

I know - I relinked it to the new kernel and it was working fine, but when i removed the old one it stopped working in the new one, and i had to redo the driver install. Thats the part i think is so darn weird. :confused:

---

