---
title: "Error after upgrading kernel"
date: 2006-03-22
forum: Installation &amp; Upgrades
---

### Post by scratched on 2006-03-22
I recently uprgraded to the 2.6.12-10-386 kernel, and now when I try to boot I get this error:
```
 root (hd1,1)
Filesystem type unknown, partition type 0x7
kernel /boot/vmlinuz-2.6.12-10-386 root=/dev/sda2 ro quiet splash

Error 17: Cannont Mount Selected partition.
```

Anyone know what I have to do to fix this? I'm booting to an external hard drive on the second partition, so (hd1,1) should work as far as I know. I'm guessing I have to re-install grub but I'm sorta new to linux so this has me stumped:-k .

---

### Post by scratched on 2006-03-24
I installed GRUB using the method wernst gave on the [HOWTO: Restore GRUB Post #5]("http://www.ubuntuforums.org/showpost.php?p=121355&postcount=5"), and grub was correctly reinstalled (according to what was displayed after I finished at least...). I still have the same problem as before. I'm assuming this isn't a grub problem anymore, but I'm a newbie and I don't know where to go with this. Any ideas?

---

### Post by scratched on 2006-03-24
I asked around on a couple other linux forums. Apparently my GRUB menu.lst got screwed up. the root should have been on (hd0,1) instead of on (hd1,1) (which confuses me since ubuntu was installed on an external USB hard drive so it should have been (hd1,1)

For those having this problem, boot to GRUB, and then press 'e' when you have selected ubuntu. Then follow the prompts to change the root partition to the correct one. 

Hopefully this solution will help someone else out too.

---

