---
title: "Grub replaced my windows bootloader:"
date: 2007-05-17
forum: Installation &amp; Upgrades
---

### Post by Jambhavan on 2007-05-17
I installed Ubuntu successfully in my system, with a dual boot setup (Windows XP). It works good, I could choose which OS to boot into. Thats fine, but its not my windows boot loader.

For me, Ubuntu installation procedure never asked me, where to install GRUB tool. This is my first linux installation, GRUB is not previously installed.

Now GRUB is my default bootloader. Does that mean it got installed in MBR, and my windows bootloader gone?

I dont want that to happen. Is there any way to get my windows boot loader to determine which OS to boot into instead of GRUB.

Thanks,

Jambhavan

---

### Post by louieb on 2007-05-18
The boot loader is still there. But the MBR now points to the GRUB program. There are plenty of post on using the [Super Grub Disk  ]("http://supergrub.forjamari.linex.org/") to make the MBR code point back to ntloader. Or you can use your windows install disk to get the MBR pointing back to ntloader.

And here is one on how to get ntloader to boot Ubuntu. 
[ Booting Kubuntu Using NTloader]("http://ubuntuforums.org/showthread.php?t=351692")

---

### Post by Jambhavan on 2007-05-18
Thanks Louie.

I understood now. So my /ext3 is made active primary partition so that MBR points to the bootloader in the active partition. I guess so. If I reassign C:\ partition as active (by using some bootcd), then I got to follow the second link you gave me.

But I am able to use both Linux as well as boot into Windows, So GRUB is good enough for me, atleast until I update to Vista.

Thanks again.
J

---

