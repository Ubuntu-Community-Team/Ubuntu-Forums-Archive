---
title: "Kernel upgrade frustrations (Error 17)"
date: 2007-06-09
forum: Installation &amp; Upgrades
---

### Post by phredduk on 2007-06-09
This is really annoying!

When I initially installed Feisty, the install went smoothly until I came to boot for the first time - grub showed the frustrating 'Error 17 cannot mount selected partition' message.

This had me confused for a while, until i booted the LiveCD and dug out the /boot/grub/menu.lst. For some reason the installer had pointed to a hd0 drive instead of a sd0 drive (I'm running a partitioned 500GB SATA drive, with Ubuntu installed on the 2nd partition). No bother - I simply corrected the grub menu.lst pointing it to sd0 instead of hd0 and it booted nicely. Great.

What's bothering me now is that every time there's a kernel update it molests my grub config!

e.g.

 Update Kernel -> Please restart -> Reboot -> Error 17 cannot mount selected partition -> WTF?!

The first time this happened the update manager added a reference in /boot/grub/device.map which just mapped the alias hd0 to /dev/sda so that menu.lst could refer to the kernel location as (hd0,0) - which would have been fine except it should have been (hd0,1) as my root is on the 2nd partition. Easily fixed - except for it had also added a 'UUID' reference to the root partition

```
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=4febb449-3296-4f7a-8687-f8031e3faca2 ro quiet splash
```

Why did it add this?? after correcting the menu.lst to point to (hd0,1) and rebooting i then got the message:

```
fsck.ext3: Unable to resolve 'UUID=4febb449-3296-4f7a-8687-f8031e3faca2' 
fsck died with exit status 8
```

So I LiveCD boot again, and change the menu.lst config line to :

```
kernel		/boot/vmlinuz-2.6.20-16-generic root=/dev/sda2 ro quiet splash
```

and now I'm back in business! I don't really want to go through this every time there's a kernel upgrade - ahhhhg! I'm an intermediate user and managed to figure it out but a novice would surely go running back to windows!

Questions:

1) Is this a bug and if so where/how do I report it?
2) Why the hell does the update manager feel the need to assume that my kernel will be located on the first partition of the first harddrive and b0rk my grub config?
3) What's the point in using the UUID reference? It made my system unbootable until I changed it explicitly to /dev/sda2. This seems a more intuitive and equally effective method so why bother with that weird UUID hash?

Thanks! ;)

---

### Post by confused57 on 2007-06-09
You need to change the #kopt line to /dev/sda2:
[http://users.bigpond.net.au/hermanzone/p15.htm#kopt](http://users.bigpond.net.au/hermanzone/p15.htm#kopt)
otherwise a kernel update will use the kopt entry & use root UUID in your menu.lst kernel line.

The command:
```
blkid
```
will show the UUID's for your partitions, you'd need to check that the correct UUID was used in your menu.lst kernel root and your /etc/fstab...if you use UUID's to boot your root partition.

---

