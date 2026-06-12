---
title: "Ibex Upgrade Disaster - Kernel Panic"
date: 2008-10-28
forum: Installation &amp; Upgrades
---

### Post by zobcat on 2008-10-28
I upgraded to 8.10 Intrepid Ibex and now I get this error when I try to boot from kernel 2.6.27-7:

[1.204117] Kernel panic - not syncing: VFS: unable to mount root fs on unknown-block (0,0)

I tried booting from the older kernels and it takes me all the way to the login screen, but my keyboard and mouse are unresponsive.

Any ideas?

---

### Post by epictetus on 2008-10-30
Mostly same thing here.  I had issues during the upgrade with packages appearing `to be not working' and the upgrade itself failed and said it would revert to the previous installation (I don't have access anymore to the exact wording).  Upon rebooting, I get 

[     0.892158] Kernel panic - not syncing: VFS: unable to mount root fs on unknown-block(0,0)

The only (recovery) kernel option that works is

``Ubuntu 8.10, kernel 2.6.22-15-generic (recovery mode)''

and it only takes me to the human-coloured screen right before login whereupon the little circly in-progress animated cursor twitches and the keyboard/mouse do not respond.

Any help/advice/respects/card&flowers would be greatly appreciated.

---

### Post by Aenima99x on 2008-10-30
Had the exact same issue and found that my Grub Menu was partially corrupted. Here's what I did to fix the problem -
1. Boot up up using a Live CD or any way that you can use to access your Grub Menu (located at /boot/grub/menu.lst)
2. Open menu.lst with any editor and scroll all the way to the bottom and find the Kernel list. 
3. Here's the part that was corrupted on mine - the line beginning with initrd was completely missing from the 2.6.27-7 Kernel. If this is missing for you, then add in the following  
```
initrd		/initrd.img-2.6.27-7-generic
```

So your full entry for the 2.6.27-7 kernel should be similar to this - 
```
title		Ubuntu 8.10, kernel 2.6.27-7-generic
root		(hd0,0)
kernel		/vmlinuz-2.6.27-7-generic root=UUID=f7180814-9e85-4548-9816-a54f052dc2a3 ro
initrd		/initrd.img-2.6.27-7-generic
quiet
```

Edit - Your root and kernel lines may look a little different, that is ok. You just nmeed to make sure the initrd line is there.
Hope this helps.

---

### Post by TheWama on 2008-10-31
Thanks Aenima99x, but that should be:

```
initrd		/boot/initrd.img-2.6.27-7-generic
```

Except that in my case, the above file doesn't exist.  All the other 2.6.27-7 files (config, system.map, vmcoreinfo, &c) are there but not initrd...

---

### Post by Lightstar on 2008-10-31
I had the same problem, and I also didn't have the init file in my /boot folder

I was able to log into the 8.10 2.6.24-16
did a 
sudo dpkg --configure -a

after reconfiguring alot of stuff, that actually generated the initrd.img-2.6.27-7-generic

I don't think this would work from a livecd, need to be logged in the actual linux you need to repair.

I  used to always delete old kernel entries from my grub menu...  I guess now I learned to keep a few old "working" ones.. just in case.

---

### Post by Aenima99x on 2008-11-03
> **TheWama said:**
> Thanks Aenima99x, but that should be:

```
initrd		/boot/initrd.img-2.6.27-7-generic
```

Except that in my case, the above file doesn't exist.  All the other 2.6.27-7 files (config, system.map, vmcoreinfo, &c) are there but not initrd...
Actually, no it shouldn't. Although the file does exist in that path, the entry in the menu.lst should be exactly as I have it.

---

### Post by florus on 2008-11-03
Kernel panic can be caused by the Intrepid driver for the Intel 4965 chipset. See 'known issues' on the 8.10 release notes on the Ubuntu website.

---

