---
title: "Dual Boot 6.10 and WinXP"
date: 2007-04-26
forum: Installation &amp; Upgrades
---

### Post by jbowman86 on 2007-04-26
Hi,
     I have just set up my hardrive with a partition for ubuntu, 1 for linux-swap and 1 for winXP. i installed ubuntu without any problems then installed winXP. i entered this information into the grub list

---------------------------------------------------------------------------------------------------------------------------------
default		0


timeout		10


title		Ubuntu, kernel 2.6.17-11-386
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.17-11-386 root=UUID=7c78387d-2701-4308-abff-191197ba51ea ro splash
initrd		/boot/initrd.img-2.6.17-11-386
savedefault
boot

title		Windows XP
root		(hd0,2)
boot

title		Ubuntu, kernel 2.6.17-11-386 (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.17-11-386 root=UUID=7c78387d-2701-4308-abff-191197ba51ea ro single
initrd		/boot/initrd.img-2.6.17-11-386
boot


title		Ubuntu, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
boot

### END DEBIAN AUTOMAGIC KERNELS LIST
-----------------------------------------------------------------------------------------------------------------------------------

But now when i try to choose WinXP from the grub selection screen its comes back with the following error message. 

-----------------------------------------------------------------------------------------------------------------------------------
Booting Windows XP

root (hd0,2)

filesystem type unknown partition type 0x7

boot

error 8: kernel must be loaded before booting.
----------------------------------------------------------------------------------------------------------------------------------

Ubuntu loads without any problems. If u can help me try to get windows booted please leave a reply.

THANKS

---

### Post by beaudoin996 on 2007-04-26
Does rootnoverify work ?

---

### Post by notwen on 2007-04-26
I'm no Grub expert, but I do have a last-resort proposition.  Install XP first, then go back and install Edgy afterwards, resizing your XP partition using GParted(default partitioner in the Edgy liveCD) to create your Ubuntu & swap partition.  Grub will automatically pick up your XP install and add it to it's boot options.  Hope someone can resolve your issue w/o having to re-install both Windoze and Ubuntu. =]

---

