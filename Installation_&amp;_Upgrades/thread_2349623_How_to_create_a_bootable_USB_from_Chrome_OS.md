---
title: "How to create a bootable USB from Chrome OS"
date: 2017-01-16
forum: Installation &amp; Upgrades
---

### Post by sduverge on 2017-01-16
So I made a huge mistake and deleted the linux image I was using (didn't do the uname -r check before).
I'm currently downloading 16.10 to upgrade via USB but I need to create the USB on my chromebook since the one I'm trying to fix lost internet access and can't mount any external drive. I do have another partition for /home so I'll try to fix boot before losing all hope and my files.
How do I make the bootable drive from my chromebook?

---

### Post by spjackson on 2017-01-18
Ubuntu isos are hybrid which means that all you need to do is copy the image to the device using dd:
```

sudo dd if=image.iso of=/dev/theDevice

```
where image.iso is the name of the 16.10 image and theDevice is whatever the device is (e.g. sdb). **N.B.** Be careful that you don't choose the device from which your Chromebook boots.

---

