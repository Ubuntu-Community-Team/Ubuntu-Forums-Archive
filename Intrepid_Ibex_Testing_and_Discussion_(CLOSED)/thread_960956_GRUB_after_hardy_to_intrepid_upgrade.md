---
title: "GRUB after hardy to intrepid upgrade"
date: 2008-10-27
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by jepong on 2008-10-27
Hello... i just upgraded my hardy desktop to intrepid desktop last weekend. I just notice that upon pressing ESC to see menu.lst is not updated with the latest kernel.

Then I tried system cleaner and delete unnecessary package which includes the old kernel and boom! I can't boot anymore.

Is this a intrepid bug?

Thanks

---

### Post by panda726 on 2008-10-28
Someone else just had a similar issue, and there does seem to be a bug here.  Please post the output of "sudo fdisk -lu" (sans quotes, of course) and your menu.lst which should be in /boot/grub of the partition to which Intrepid is supposed to be installed.

Someone else will hopefully take it from here, as it will be a bit before I can get back, but that information is what anyone will need to help you.

Tor

---

