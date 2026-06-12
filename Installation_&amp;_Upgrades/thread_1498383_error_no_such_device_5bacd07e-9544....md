---
title: "error: no such device: 5bacd07e-9544..."
date: 2010-05-31
forum: Installation &amp; Upgrades
---

### Post by Kodpoet on 2010-05-31
So I tried installing crunchbang and got startled by the following when booting up grub: :(

```

error: no such device: 5bacd07e-9544-4099-bd83-9c14e067f1a4.
grub rescue> _

```I reinstalled and changed iso-file and so on until I gave up and decided to reinstall ubuntu. This time I used the net-install version and everything went great, just as before, untill I tried booting up after installation and once again got greeted by the same mesage. :P

Having wrestled with this for quite a while I'd really like to know what's going on :P :D

Do you have an idea? ;)

---

### Post by darkod on 2010-05-31
Because you reinstalled, I can't be sure right now. That long string is UUID, an identifier allocated to ext2/ext3/ext4 partition upon formatting.
The reinstall would have created new UUID for the root partition, so it might just be message from grub on the MBR looking for its "old" root.
The best is to reinstall grub/grub2 on the MBR. Can you do that from live mode?

If the error is there despite the UUID being correct, you might be hit by this:
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:search](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:search)

---

