---
title: "grub2 sets drives ro"
date: 2009-08-24
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by dimeotane on 2009-08-24
I'm using Ubuntu Netbook Remix, and I keep having to edit my /boot/grub/grub.cfg so that ro isn't added to every entry. 

Every time my grub.cfg is updated the ro is added back.  I know grub.cfg is generated, but what do I edit so that ro doesn't keep getting added to each drive entry.   I've ran fsck and there are no errors.
Thanks in advance.

---

### Post by mattduckman on 2009-08-24
the root partition is supposed to be mounted ro from grub. once the computer boots, though, the partitions should be set up like they are in fstab.

if root is staying ro, that makes me think there's an error since one of the default options is errors=remount-ro

have you checked dmesg for any errors?

---

