---
title: "How to restore Grub 2?"
date: 2009-10-19
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by Sealbhach on 2009-10-19
Hi,
I was wondering if the routine of 

[B]find /boot/grub/stage1
[/B]
      [B]setup (hd0)
[/B] 
That we have used up until now has changed with Grub 2? [B]

.
[/B]

---

### Post by philinux on 2009-10-19
Sure has. You need chroot now.

[http://www.ubuntu-inside.me/2009/06/howto-recover-grub2-after-windows.html](http://www.ubuntu-inside.me/2009/06/howto-recover-grub2-after-windows.html)

You can do this from another install on same machine. I use the script below to chroot from jaunty on sda1.
```

#!/bin/sh

##sudo mkdir /mnt/karmic
sudo mount /dev/sdb1 /mnt/karmic/
sudo mount -o bind /proc /mnt/karmic/proc
sudo mount -o bind /dev /mnt/karmic/dev
sudo mount -o bind /dev/pts /mnt/karmic/dev/pts
sudo mount -o bind /sys /mnt/karmic/sys
sudo cp /etc/resolv.conf /mnt/karmic/etc/resolve.conf
sudo chroot /mnt/karmic /bin/bash

fi
```

[edit] grub2 complains if you install to a partition instead of mbr but it still works.

---

### Post by VMC on 2009-10-19
> **Sealbhach said:**
> Hi,
I was wondering if the routine of 

[B]find /boot/grub/stage1
[/B]
      [B]setup (hd0)
[/B] 
That we have used up until now has changed with Grub 2? [B]

.
[/B]

find command has been replaced with search. Go [here]("http://grub.enbug.org/CommandList") for comparisons.

---

### Post by Sealbhach on 2009-10-19
Thanks guys, looks a little more complicated.

.

---

### Post by ranch hand on 2009-10-19
It is much simpler if all you want to do is change the OS that you are using for boot/root.  For that all you haveto do is be able to boot to the chosen OS and run;
```

sudo grub-install /dev/sda

```
with the "sda" edited to match your box conditions.

---

