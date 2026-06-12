---
title: "Kernel 2.6.24-16 won't boot properly"
date: 2008-05-26
forum: Installation &amp; Upgrades
---

### Post by smelloscope on 2008-05-26
I upgraded from Gutsy to Hardy a few weeks ago, and when I try to boot the newest kernel in GRUB, the screen goes black and my monitor gives me the "No Signal Detected" message.  When I boot into recovery mode, I get the following messages:

```
Driver 'sd' needs updating - please use bus_type methods
```

and then it repeats this section continuously

```
ata2.00: status { DRDY }
ata2: soft resetting link
ata2.00: configured for UDMA/33
ata2: EH complete
ata2.00: exception Emask <something in hex that I didn't write down>
ata2.00: cmd <lots more hex codes>
```


I have absolutely no idea what is going on, or where to start fixing it.  If I try to stop the repeating messages with <ctrl-c>, it briefly shows the prompt "initramfs" and then continues printing that repeating message.

I can still run Ubuntu under the old kernel (2.6.22-14), and as far as I can tell, Hardy is running fine except for the out-of-date kernel.

Here's a brief description of my setup:
-Dual-booted with Vista
-Dell Inspiron 530, Intel Core2 Duo processor E6420 (2.13GHz 1066FSB) w/Dual Core Technology and 4MB cache
-320GB Serial ATA 2 Hard Drive (7200RPM)

Thanks in advance for any help people can give me!

---

