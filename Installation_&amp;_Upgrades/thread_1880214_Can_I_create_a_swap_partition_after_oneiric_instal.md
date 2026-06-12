---
title: "Can I create a swap partition after oneiric installation with LUKS"
date: 2011-11-13
forum: Installation &amp; Upgrades
---

### Post by newhotta on 2011-11-13
Hi,

I've installed Oneiric over LUKS encrypted partitions, I couldn't find my swap partition working.

Tried running
```
sudo swapon -a
```
The output was
```
swapon: /dev/mapper/XXXXXX-swap_1: read swap header failed: Invalid argument
```

Can i setup my swap partition again without re-installing the whole system?

Thanks

---

### Post by BillyBoa on 2011-11-13
Booting from a live CD and using Gparted you can arrange the partitions without problem.

---

### Post by newhotta on 2011-11-13
Thanks for the quick reply.

GParted doesn't support LUKS(Linux Unified Key Setup) encryption

---

### Post by newhotta on 2011-11-13
Thank you BillyBoa, I managed to create it.

[LIST=1]
[*]Installed LVM (Logical Volume Management).
[*]Created a Logical Volume in the Logical group i have
[*]From the terminal executed the following:
[/LIST]
[INDENT]a-
```
sudo mkswap /dev/XXXXXXXX/swap_1
```
where /dev/XXXXXXXX/swap_1 is the full path of the logical volume.

b-
```
sudo swapon -a
```
[/INDENT]

---

