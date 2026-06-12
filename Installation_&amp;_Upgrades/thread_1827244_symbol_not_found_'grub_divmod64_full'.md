---
title: "symbol not found: 'grub_divmod64_full'"
date: 2011-08-17
forum: Installation &amp; Upgrades
---

### Post by cyprys on 2011-08-17
Upgrade to 11.10 on my friends pc went bad and I ended up with grub rescue prompt with the following message:
> error: symbol not found: 'grub_divmod64_full'

Tried to load linux or normal modules but all I get is the above message. 

Found vmlinuz and initrd.img files on (hd0,msdos7)/ but (hd0,msdos7)/boot is empty. All the boot files and the grub directory are on (hd0,msdos5)/ partition. Calling **set** command shows:
> prefix=(hd0,msdos5)/grub
root=hd0,msdos5

Correcting the root variable to msdos7 doesn't help nor does loading modules from (hd0,msdos7)/usr/lib/i386-pc/.

Help? I have no other machine here and I post using smartphone (t9 is killing me, btw.). Need to fix it tonight, next time I'll be here is in five months.

---

