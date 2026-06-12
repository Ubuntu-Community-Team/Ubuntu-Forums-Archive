---
title: "grub error 18 after upgrade, help!"
date: 2008-05-27
forum: Installation &amp; Upgrades
---

### Post by Simstud on 2008-05-27
I have an old Gateway with Ubuntu 7.10 that I use as a network backup for a dozen office computers and as a 'guest' machine that random people use. I ran apt-get upgrade remotely yesterday as I do from time to time just to keep on top of things. I think I got upgraded to kernel 2.6.22-14. Now I get grub error 18: selected cylinder exceeds maximum supported by BIOS. I can still boot into the old kernel 2.6.20-16 but if I do X won't start (error msg about a NVIDIA kernel mismatch). My question is if I apt-get remove vmlinuz-2.6.22-14-generic will that solve my problems? Will X change back to the old kernel? Or is there a better way to fix the bootsector problem so that the machine boots into the new kernel? I know nothing about this stuff, but I guess that if I could move the new kernel to the right physical spot on the hard drive the BIOS would be able to access it and my problems would be solved. Right? There is a lot of data on this machine so I can't really afford to experiment. Thanks in advance for any ideas.

---

### Post by dstew on 2008-05-27
If the error 18 is due to the old BIOS cylinder limit, you can fix it by making a /boot partition at the front of the drive, which is contained withing the limit. However, if you did not re-partition during the upgrade, it is probable that the error is from something else. See [Herman's grub error 18 page]("http://users.bigpond.net.au/hermanzone/p15.htm#18") for other reasons.

Probably, the upgrade gave you a new display driver along with the kernel. You can remove the new kernel using Synaptic, but you will probably still have problems with your display. You can reconfigure the display to use the older driver using the command```
sudo dpkg-reconfigure xserver-xorg
```That command re-creates the xorg.conf file, in light of whatever kernel is currently being used. It should give you a useable display. You can chose the **vesa** driver if you still can't get it to work with the nv driver, or with the restricted driver.

---

### Post by meierfra. on 2008-05-27
> However, if you did not re-partition during the upgrade, it is probable that the error is from something else. 

I believe that not only the location of the partition matters, but where on the partition the kernel is located. The new kernel might just  be further down the hard drive, outside the reach of the bios.

---

### Post by Simstud on 2008-05-28
> **meierfra. said:**
> I believe that not only the location of the partition matters, but where on the partition the kernel is located. The new kernel might just  be further down the hard drive, outside the reach of the bios.

That's what I think happened. Is there a way to swap the physical positions of the two kernels?

---

### Post by thschiavo on 2008-06-25
I'm having this problem too... After my upgrade from 7.10 to 8.04, this messages after the grub screen started. But when I try again the Ubuntu option, it starts normaly... :confused: 
I ill ready the suggested guide. 

And there's another post exposing one way to fix it.
[http://ubuntuforums.org/showthread.php?t=836825](http://ubuntuforums.org/showthread.php?t=836825)

---

