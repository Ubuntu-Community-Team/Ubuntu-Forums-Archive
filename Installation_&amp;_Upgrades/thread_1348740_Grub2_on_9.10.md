---
title: "Grub2 on 9.10"
date: 2009-12-07
forum: Installation &amp; Upgrades
---

### Post by skendza on 2009-12-07
I have Ubuntu and Vista(hey! it came with laptop,not my fault)

I wasn't lazy, i googled around, perhaps i'm just stupid.
I want to change grub(edit it's menu) - (read that part don't change grub.cfg)
to show me like this
1.Ubuntu(without that generic linux bla blah)
2.Vista

so no memory test, and when i click ubuntu, latest generic version to be loaded.
Please don't redirect me to other thread, i read them...almost all, and i don't get it.
Step by step

Thanks for patience
greetings from Serbia

---

### Post by darkod on 2009-12-07
You can get rid of memtest by making the file unexecutable with:
sudo chmod -x /etc/grub.d/20_memtest86+

Then run
sudo update-grub

to update the menu. You can also disable the recovery mode entry but I recommend keeping it because it can help if the normal mode entry can't work out of what ever reason.
As for the older kernels, I don't know how to remove them because it's also recommended to keep at least one older kernel in case you have a problem with the latest one.

---

### Post by QIII on 2009-12-07
Easiest way to get rid of the old kernels and keep them from showing in the GRUB2 boot list is to use Synaptic to uninstall them (jot down the kernel and versions you want to get rid of) and then run sudo update-grub2.

However, it is always a good idea to keep at least the most recent working previous kernel in case the most recent on gives you problems.

As above, I HIGHLY recommend that you keep the ability to use the recovery mode.

---

