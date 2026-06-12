---
title: "Grub and Vista"
date: 2008-08-07
forum: Installation &amp; Upgrades
---

### Post by garnie on 2008-08-07
Hey

So i just installed Ubuntu on my main PC but i have troubles getting it to boot.

Grub starts up fine and gives me the option of Ubuntu and Vista, which is also on this PC, but none of them will boot gives "wrong path" or something.

Vista and Ubuntu are located on the same Hard drive, but different partitions.

Vista is located on /dev/sdb1 

while Ubuntu is on /dev/sdb2

```

title           Ubuntu 8.04, kernel 2.6.24-16-generic
root            (hd1,1)
kernel          /boot/vmlinuz-2.6.24-16-generic root=UUID=764dc7d7 e024-4951-892f-3ac19aec7a2d ro single
initrd          /boot/initrd.img-2.6.24-16-generic
quiet

```

This is for Ubuntu, and here is the one for Vista

```

title           Windows Vista/Longhorn (loader)
root            (hd1,0)
savedefault
makeactive
map             (hd0) (hd1)
map             (hd1) (hd0)
chainloader     +1

```

so i ask what can be wrong, since i really have no idea of how grub works

Thanks in advance :)

---

### Post by cdtech on 2008-08-07
Since your booting off of that drive you need to set the device as hd0,0 hd0,1.

Vista:
root            (hd0,0)
Ubuntu:
root            (hd0,1)

---

### Post by garnie on 2008-08-07
Thank you that did the trick :)

---

