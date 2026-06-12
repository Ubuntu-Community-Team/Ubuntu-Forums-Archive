---
title: "Updating failure prevents upgrading"
date: 2010-05-27
forum: Installation &amp; Upgrades
---

### Post by ibates on 2010-05-27
Upgrade calls for ensuring latest updates to Karmic are installed before upgrading to 10.04 LTS.

Every attempt to update hangs, yielding the following dialogue:

W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY B152F042D246C25D

I guess I am sort of stuck in nowhere land here.

Any suggestions would be much appreciated.

Do I, in fact, need to complete the updating before upgrading?

---

### Post by dino99 on 2010-05-27
this error means that signature is missing, but in fact its only a warning not a error, so dont worry.

open synaptic repo to uncheck that ppa or update it, see how to do on the launchpad ppa page, be sure to only use lucid repo.

note: seem that link posted above use any ppa ( no address)

---

### Post by wilee-nilee on 2010-05-27
Untick that and any other ppa's they will be turned off anyway with a upgrade. Also make sure you have everything needed backed up and watch out for the grub gui that states install if you don't know in a partition, only install grub to the MBR where it resides as of now. For example if you only have one hard drive the mbr is in sda not a partition like sda1 or any other added numbers.

You may also need to go to software sources>updates and set it to long term support releases only and the do a update again.

---

### Post by kansasnoob on 2010-05-27
Check your software sources and disable any "added" repos, or if in doubt post the output of:

```
cat /etc/apt/sources.list
```

---

### Post by ibates on 2010-06-21
Thanks for all the assistance.

I don't know if I have actually solved the problem, but i have installed 10.04.  I simply removed the RAID array and have overcome the problem by backing up to discs in trayless enclosures.

Least line of resistance syndrome.

---

