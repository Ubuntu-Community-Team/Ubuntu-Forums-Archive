---
title: "Multi-Ubuntu Install"
date: 2006-07-14
forum: Installation &amp; Upgrades
---

### Post by ChrisMalarky on 2006-07-14
Hi,

I have a new hard drive that I'm about to install in my laptop.

I'd quite like to be able to multi-boot two or three different versions of Ubuntu so that I can have, for example, a 'live' and 'test' environment.  Initially, 'live' would be my current hoary-upgraded-to-breezy install and 'test' would be a fresh install of dapper.  Once I'm happy that I've got dapper set up right for daily use then then I'll switch the breezy install for some testing of edgy eft.

So, assuming I can get my current install transferred over to the new drive, I just have to decide on the partitioning scheme.

I'll be sharing the swap space.

I'll also use the same /home partition for each install.  Am I likely to run in to any problems with different versions of applications sharing the same config files?

Obviously I'll have one root partition per install.

The only bit I'm not sure about is the /boot partition - is it feasible for multiple installs to share the same /boot space?  I'd have to be careful and keep an eye on the Grub config whenever there's a kernel change/upgrade, but I'm guessing that it is do-able.

Any comments or suggestions?

Cheers,
Chris

---

### Post by cotcot on 2006-07-14
Check "partimage" for transferring your install. Partimage is a partition cloning tool such as Ghost. I use it to backup my partitions and set them back in case of fatal error.  

You can use the same boot partition as long as the vmlinuz and initrd files from the different ubuntu installs have different names. If you have the same kernel on more then one install the oldest install will not be bootable. 

Be careful with the /boot/grub/menu.lst you use.

---

### Post by ChrisMalarky on 2006-07-14
Thanks for that.

Yeah, moving partitions around is no problem - I use partimage at work a fair amount.

I'll keep an eye on the /boot partition and kernel versions.

C

---

