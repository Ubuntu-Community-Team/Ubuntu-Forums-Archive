---
title: "Modify GRUB to boot QNX"
date: 2006-06-12
forum: Installation &amp; Upgrades
---

### Post by Keith_Beef on 2006-06-12
I've just installed QNX onto a disc in my Ubuntu box, and want to boot it from GRUB.

I've modified the /boot/grub/menu.lst to add the following stanza:
```

# This entry added 12 June 2006
# to boot QNX
# inspired by http://www.gnu.org/software/grub/manual/html_node/QNX.html#QNX
title           QNX
rootnoverify    (hd2,0)
chainloader     +4
```

Does it look right?

What's the right way to test this, before writing to the MBR?

I used to be on Mandrake/Mandrive, and had got used to the Webmin GRUB configuration module; doing this by hand is a pain.


Beef.

---

