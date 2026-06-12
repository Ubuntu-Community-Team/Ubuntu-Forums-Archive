---
title: "Some sort of driver problem"
date: 2008-11-10
forum: Installation &amp; Upgrades
---

### Post by emobrad on 2008-11-10
So, I recently got a new motehrboard due to my old one being fried and whatnot. But when I installed ubuntu on my HDD (Upgrading to ibex), it told me that something is not a correct driver and I should try the "8139too" driver. I tried installing it and stuff but it wasn't found. And it really seems as if it messed my install up right off the bat. Any suggestions? This is all happening as my computer boots up.

---

### Post by cariboo on 2008-11-10
The 8139too is a driver for the network adapter on your new motherboard. The best thing to do is to remove the driver for the nic from your old mb and then install the realtek driver for your new motherboard. If you know what driver your old mb was using it is just a matter of entering in a terminal:


```
sudo rmmod <nic_driver>
```

then inserting the new module:

```
sudo modprobe 8139too
```

Jim

---

### Post by emobrad on 2008-11-10
Thank you so much dude. That helps a lot

---

