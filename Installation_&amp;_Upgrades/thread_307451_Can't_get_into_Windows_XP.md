---
title: "Can't get into Windows XP"
date: 2006-11-26
forum: Installation &amp; Upgrades
---

### Post by welshboy on 2006-11-26
Hi guys,

I installed Edgy, and I now can't boot Windows.  Yet I can see the hard disk on my desktop, so I know that all my data is safe waiting for me to back it up.

I have altered my menu.lst file to have the proper boot options, however I get an error whenever I try and get into Windows.

Something like "invalid device"

The windows partition is on hda5 for some reason, I'm not sure why.

Any help would be fantastic

welshboy

---

### Post by taurus on 2006-11-26
Paste the output of these two commands from a terminal, Applications -> Accessories -> Terminal.

```

sudo fdisk -l
cat /boot/grub/menu.lst
(you only have to include the last section regarding an entry for Windows.  No need to send the whole thing...)
```

---

### Post by welshboy on 2006-11-26
Hi there,

I read elsewhere on the forum that Grub wouldn't see windows unless it was on the first partition, so I backed up my data and did a re-install of Windows, and made sure I partitioned the drive properly.

All now works, but many thanks for the reply.  Much obliged.

welshboy

---

