---
title: "Installation to USB Boot Problem and Fix"
date: 2010-05-20
forum: Installation &amp; Upgrades
---

### Post by Blinding Mask on 2010-05-20
I encountered and interesting boot problem and resolved it.

Situation:

Created live USB on 8 GB flash drive, using Ubuntu 10.4 on sda. Booted to that flash drive and installed 10.4 onto another 8GB flash drive. 

Upon restart with both removed flash drive, Grub erred and stating that the stick name that had been installed to (which was at sdc) was missing. 

Plugged it back in, Grub works and lists bootables on sda, windows partition, and sdc.

Similar fate on just flash drive.

Resolved by booting to sda Ubuntu through flash Grub, removing USB, running: 

```
sudo update-grub
```

After restarting, booting into the USB grub again, and into sdc Ubuntu, I made /etc/grub.d/30_os-prober NOT executable and executed

```
sudo update-grub
```

Now stick and HD Grub are independent and can be differentiated and dissociated. 

Is this worth reporting as a bug?

---

