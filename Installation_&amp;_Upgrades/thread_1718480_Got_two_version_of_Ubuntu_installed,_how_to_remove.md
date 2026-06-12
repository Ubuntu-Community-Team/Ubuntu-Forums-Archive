---
title: "Got two version of Ubuntu installed, how to remove one of them"
date: 2011-03-31
forum: Installation &amp; Upgrades
---

### Post by hanz_the_legend on 2011-03-31
Hello there,
I am new to linux and I recently installed Ubuntu on my laptop. Thing is, I have both Ubuntu and Windows 7 running and everything was fine. But there was an update that Ubuntu did on the system, and now when my pc boots, I have 2 series ( 2 times Ubuntu, 2 times Ubunti safemode, 2 times memory test, 2 times memory test safemode) of choices for Ubuntu and one for windows 7.

Is it normal??
how do I revert back?

thanks

---

### Post by coffeecat on 2011-03-31
Are you sure you have all of these?

> **hanz_the_legend said:**
> I have 2 series ( 2 times Ubuntu, 2 times Ubunti safemode, 2 times memory test, 2 times memory test safemode) of choices for Ubuntu and one for windows 7.

The seeming duplication of the normal Ubuntu and recovery mode menu entries is because the update installed a newer version of the kernel, but didn't uninstall the older kernel. This is normal. If you look at the figures, you'll see different kernel version numbers. It's a good idea to keep the immediately previous version of the kernel installed in case the newer one has problems with your hardware. 

But if you really have 4 entries for memtest, then something is odd. If you do, post the contents of your /boot/grub/grub.cfg file in code tags (you can use the # icon on the message toolbar) for us to have a look at.

---

