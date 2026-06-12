---
title: "Other versions on boot screen?"
date: 2009-12-08
forum: Installation &amp; Upgrades
---

### Post by biohazardhm on 2009-12-08
I updated ubuntu and now when I open my pc, i see 3 linux boot options. (all of these are ubuntu) If i want to delete this boot options, how can i do it ?
If i delete these files, will I lose any data?

If I remove these files, will GRUB's list decrease? (I don't want to face with a problem and i want to ask because of this):

/boot/abi-2.6.31-14-generic
/boot/initrg.img-2.6.31-14-generic
/boot/vmcoreinfo-2.6.31-14-generic
/boot/vmlinuz-2.6.31-14-generic
/boot/systemmap-2.6.31-14-generic
/boot/config-2.6.31-14-generic

Thanks in advance

Note: I see these file's other versions
If you approve it i'll remove them also...
they are "2.6.31-15-generic" files
I already have "2.6.31-16-generic" files. I ask to remove 14. and 15. version's files.

---

### Post by darkod on 2009-12-08
The 3 boot options you are talking about are 2.6.31-14 -15 and -16 kernels?

---

### Post by darkod on 2009-12-08
It's recommended to keep at least one "older" kernel because if for any reason 31-16 stops working 31-15 should work for you.
You can probably remove 31-14 if you really want to. The best way is Synaptics in System - Administration.
I think if you type linux in the filter it will show them. You can remove them there and you need to do in terminal:
sudo update-grub

after.

---

### Post by biohazardhm on 2009-12-10
> **darkod said:**
> It's recommended to keep at least one "older" kernel because if for any reason 31-16 stops working 31-15 should work for you.
You can probably remove 31-14 if you really want to. The best way is Synaptics in System - Administration.
I think if you type linux in the filter it will show them. You can remove them there and you need to do in terminal:
sudo update-grub

after.

so i don't have to remove files. thx to everyone...

---

