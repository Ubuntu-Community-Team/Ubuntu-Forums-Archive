---
title: "Grub fails during install"
date: 2008-09-02
forum: Installation &amp; Upgrades
---

### Post by MangledOne on 2008-09-02
Hey All

Im having some trouble installing ubuntu, I got a new graphics card (ATI) and done a full install of windows while partitioning space for linux later, however after formatting the partitions and installing ubuntu it fails on grub and doesn't start HAL

But the problem is that it works fine with the nvidia card, I really dont see how changing a graphics card should affect the OS installation.

If you need anything or any help would be great.

---

### Post by Pumalite on 2008-09-02
I'd stick to Nvidia. ATI does not support Linux.

---

### Post by kellemes on 2008-09-02
> **MangledOne said:**
> Hey All

Im having some trouble installing ubuntu, I got a new graphics card (ATI) and done a full install of windows while partitioning space for linux later, however after formatting the partitions and installing ubuntu it fails on grub and doesn't start HAL

But the problem is that it works fine with the nvidia card, I really dont see how changing a graphics card should affect the OS installation.

If you need anything or any help would be great.

And I expect you got the card running on Windows?
What's the message you're getting from Grub?

By the way, ATI **does** support Linux, it really depends on the model how hard it is to get it going..

---

### Post by Pumalite on 2008-09-02
The ATI drivers do WORSE than vesa.

---

### Post by MangledOne on 2008-09-03
> **kellemes said:**
> And I expect you got the card running on Windows?
What's the message you're getting from Grub?

By the way, ATI **does** support Linux, it really depends on the model how hard it is to get it going..

Yeah, windows works fine, as well as installing ubuntu on VMware which is really annoying running linux on vmware, Im going to try a bios update and see how that goes. I cant see how changing graphics cards would affect the installation but thats the only thing thats changed, if the bios update doesnt help I'll try the old card and see after that

The only error Im getting is that grub failed, then failed to initialise HAL then the it goes to the live CD

The installation is GUI and works fine up to the point of installing grub then bombs after that, I think that maybe the motherboard is faulty (new motherboard aswell) or the hard drive

Thanks

---

