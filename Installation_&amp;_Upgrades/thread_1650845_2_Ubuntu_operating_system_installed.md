---
title: "2 Ubuntu operating system installed?"
date: 2010-12-22
forum: Installation &amp; Upgrades
---

### Post by Jerry786 on 2010-12-22
Hi all, i noticed something very strange today. In the GRUB menu it shows ubuntu twice

Is this normal or a problem?

---

### Post by Rubi1200 on 2010-12-22
Hi,
does it say _exactly_ the same thing twice or two entries with different numbers?

If you recently upgraded or there was a kernel upgrade then these will show up in the menu.

It  is advisable to keep at least one spare entry for troubleshooting purposes in the event an upgrade goes wrong.

If you want us to take a closer look:
```
gksu gedit /boot/grub/grub.cfg
```

Paste the contents here and we can confirm for you.

---

### Post by Jerry786 on 2010-12-22
> **Rubi1200 said:**
> Hi,
does it say _exactly_ the same thing twice or two entries with different numbers?

If you recently upgraded or there was a kernel upgrade then these will show up in the menu.

It  is advisable to keep at least one spare entry for troubleshooting purposes in the event an upgrade goes wrong.

If you want us to take a closer look:
```
gksu gedit /boot/grub/grub.cfg
```Paste the contents here and we can confirm for you.

Thanks for the reply. Its showing two entries with different numbers
Cause for concern or is it all ok?

---

### Post by tgalati4 on 2010-12-22
I think by default GRUB holds on the last 7 kernels.  So after 7, some will start to drop off.  You can change the value in grub.cfg to 3 or 1 or 20.  Think of them as spare tires.  You really only need 1 backup, but your trunk can hold 4 or 5.

What is the purpose of these backup kernels?  Let's say you have a PowerShift digital camera.  You plug it in and a file browser opens up so you can see your pictures.  All is well with the world.  You upgrade your system and apply a bunch of updates.  Then a month later you plug in your PowerShift camera and nothing happens.  What happened?  Don't know.  Sometimes updates can break things (even though they are supposed to fix things).  This is called a regression.  Something that is common in an operating system as complex as gnu/linux.  So in the GRUB menu, you try the previous kernel and boot up.  Now your PowerShift camera works again.  Obviously something changed between the old kernel and the newer, updated kernel that borked your camera.  So now you can file a bug and say "My PowerShift camera works under Kernel 2.36.22-18 but does not work under Kernel 2.36.22-23.  What changed?"

So you really need only 1 or 2 backup kernels.  The default of 7 is perhaps excessive, but then this is linux that we are talking about.

---

### Post by Jerry786 on 2010-12-23
Thanks for the response. I really am not too fussed about it showing up twice in the GRUB menu, as long as the system is working fine, its all good :)

Though, i could do with hiding it, because when i did select the old kernel, it came up with an error message of some sort? Something like udevalam trigger not recognised?

---

