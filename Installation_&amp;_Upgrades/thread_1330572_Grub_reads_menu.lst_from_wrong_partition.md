---
title: "Grub reads menu.lst from wrong partition"
date: 2009-11-18
forum: Installation &amp; Upgrades
---

### Post by woomatic on 2009-11-18
Hi!

I've got a problem with Grub since updating to 9.10.

I have ubuntu installed on one partition (sda5) and ubuntu studio on another (sda6). Before updating grub apparently read menu.lst from sda5 (or rather hd0,4))/boot/grub/menu.lst, as it should, but now after updating it uses the one on the ubuntu studio partition instead. 
The only way to boot with the correct menu.lst for now is to enter the grub console at startup and load the correct config manually :-/.

Is there some way to fix this without doing much damage to my current setup?

(This is not a Grub2 problem, as it was a regular update, no reinstall)

thanks,
woomatic

---

### Post by dstew on 2009-11-18
> Is there some way to fix this without doing much damage to my current setup?I am assuming you are using grub legacy (version 0.97 or earlier). If so, you need to re-install grub so that it gets its menu.lst file from the correct partition. If I misunderstood, and your bootloader is grub2 (version 1.97), then post back.

When you get the grub menu, press 'c' to get a command line. You should get the **grub>** prompt. If you are not completely sure that (hd0,4) is the correct root partition, you can use **find /boot/grub/menu.lst**, and you should get the locations of your two menu.lst files. You can use the grub **cat** command to view the files, to make sure you have the correct one. Then, reinstall grub. Assuming (hd0,4) is the correct partition (that is, has the correct /boot/grub/menu.lst file) the commands entered at the grub> prompt should be```
root (hd0,4)
setup (hd0)
quit
```Then reboot.

---

