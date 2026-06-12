---
title: "System can't mount partition after yesterdays update"
date: 2007-09-01
forum: Installation &amp; Upgrades
---

### Post by mindless1973 on 2007-09-01
Hi,

After the standard update of some packages yesterday, I am not able to boot Ubuntu again. During the update I recognized some kernel files and so it asked me to reboot after the update. 

Unfortually it did not boot. I see the GRUB menu, but when selecting any entry the message

Error 17: Cannot mount selected partition
Press any key to continue...

apears and that's it :-(

any ideas?

bye
me.

Ubuntu 7.04 AMD64

---

### Post by loell on 2007-09-01
me too :(  , in fact if you search for thread title "update" , many are expiriencing this one too.

ranging from sound problems to xorg problems, then the modification of menu.lst :(

---

### Post by Pumalite on 2007-09-01
[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html#17](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html#17)

---

### Post by loell on 2007-09-01
> **Pumalite said:**
> [http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html#17](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html#17)

throwing an entire doc of grub won't actually help, thanks though.

---

### Post by loell on 2007-09-01
basically what i did, is edit menu.lst, by pressing e

then change hd(0,1) to hd(0,0) 

we have different cases here so what i did is guess the partition number, for it to correctly mount and the boot

---

### Post by Pumalite on 2007-09-01
Good for you!

---

### Post by Mike-97470 on 2007-09-02
As I now recall I had a similar problem when I did a clean install of 7.04.  This time I didn't remember until I saw this thread.  I fixed the Linux stuff by changing hd(0,0) to hd(1,0).
Good Job!

---

