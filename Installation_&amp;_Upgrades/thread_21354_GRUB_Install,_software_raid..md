---
title: "GRUB Install, software raid."
date: 2005-03-21
forum: Installation &amp; Upgrades
---

### Post by CrayMk7 on 2005-03-21
Hi all  :smile: 

After trying the ubuntu live cd and finding that even my lexmark z602 was detected and all modules loaded, I decided I would install it and give it a try.

The only problem is...

I have two sata HDs, who are setup with software raid where swap=/dev/md0 /=dev/md1 & home=/dev/md2.

The problem is when its time to install GRUB or LILO both will fail giving me : unable to install GRUB in /dev/md1

I did try different versions of /dev/sdxx too but none would work.

I'm still a newb and can't really figure out what's wrong.

BTW, I downloaded the latest hoary-preview-install-i386.iso, could it be a bug?

Thanks.

---

