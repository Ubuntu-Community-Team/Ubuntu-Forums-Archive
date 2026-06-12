---
title: "Regenerate grub.conf?"
date: 2010-03-26
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by sgage on 2010-03-26
Somehow, my grub.conf was destroyed. I was booting into my nicely tuned Lucid install, and nothing happened after the grub menu. I booted the LiveCD, and found that my grub.conf was 0 bytes. WTF? How did I even have a grub menu?

How can I regenerate it from the LiveCD or whatever? I am not in the mood to reinstall from scratch and set everything up again. If I have to do that, I'm just going to wait until final release. I wish I had more time, but that's just the way it is.

So, does anyone have an easy recipe?

TIA...

---

### Post by philinux on 2010-03-26
Ignore the title of this just follow it.

[http://www.ubuntu-inside.me/2009/06/howto-recover-grub2-after-windows.html](http://www.ubuntu-inside.me/2009/06/howto-recover-grub2-after-windows.html)

I use this script from my karmic install if I need to chroot in to lucid.

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

---

