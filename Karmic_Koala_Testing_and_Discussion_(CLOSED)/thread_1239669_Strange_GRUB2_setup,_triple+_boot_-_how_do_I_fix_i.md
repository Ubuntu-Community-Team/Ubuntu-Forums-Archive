---
title: "Strange GRUB2 setup, triple+ boot - how do I fix it?"
date: 2009-08-13
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by trulan on 2009-08-13
Here's the deal:  My main OS is Jaunty, with Karmic on a separate partition, and Windows on another hd.  Grub2 is installed in Jaunty and works well, except:

When I run grub-config from Jaunty, it doesn't find the real-time kernels in Karmic (finds the generic kernels though).  When I run grub-config from Karmic, it finds all my kernels, but writes grub.cfg into the karmic partition instead of the Jaunty partition, so it doesn't get used.  If I write that file over the one in the Jaunty partition, it renders the system un-bootable.  I can manually edit the RT kernel into grub.cfg, but there would have to be a better way.  Any ideas?

---

### Post by Psicolonia on 2009-08-13
run grub from karmic
find /boot/grub/stage1
set hd(x,y) - with the output from the first line, the one corresponding to the karmic partition
quit grub
reboot.

should work... i think...
feels like i'm forgeting a step though... run, find, set, exit... yeah, that's it.

---

### Post by ranch hand on 2009-08-13
You won't find /boot/grub/stage1.  That is part of grub-legacy.

Boot into Karmic.  Run update-grub.

Then run grub-install /dev/sda or whatever your drive is known as.  This should fix it right up.

---

