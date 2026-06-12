---
title: "[SOLVED] enable secondary Marvell 88SE61xx sata controller in 8.10"
date: 2008-10-26
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by cresny on 2008-10-26
My motherboard is an Intel D975XBX2. It has a 4-port AHCI sata controller, plus another "fakeraid" 88SE61xx 4-port controller that I have enabled with a couple of drives, used mostly for media files.

In 8.04 Hardy, I saw all six of my drives. In 8.10 Ibex, I couldn't even boot up the LiveCD with the secondary controller enabled, ending up in busybox with initramfs errors. So I disabled it to install, but when I re-enabled it I was back in busybox. 

I suspect the reason it failed was that there was a recent fix in the ahci module detailed in this thread:

[http://lkml.org/lkml/2008/9/8/205](http://lkml.org/lkml/2008/9/8/205)

This fix is not enabled by default, possibly because it could have a conversely bad effect if it was. But if you, too, are stuck in busybox, here's how to get out:

Add the following ahci module option to /etc/modprobe.d/options:
```

#have ahci handle marvell sata
options ahci marvel_enable=1

```

That will let you boot, but if you want to actually use the controller you need to use another module, sata_mv which I read about ins this pretty useful page: [http://linuxmafia.com/faq/Hardware/sata.html]("http://linuxmafia.com/faq/Hardware/sata.html")

To do this, add 'sata_mv' (without quotes of course) to the file /etc/initramfs-tools/modules, then run update-initramfs.

```

sudo update-initramfs -u

```

Also, your controller must be set to AHCI in your bios, not IDE emulation.

This solved my problem, so I never did try to get this working directly from the LiveCD. Anyone know how that could be done?

---

