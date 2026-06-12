---
title: "Qemu massive slowdown after 13.04 upgrade"
date: 2013-08-08
forum: Installation &amp; Upgrades
---

### Post by sorceror171 on 2013-08-08
Upgraded my system (Core i7-2600K, 16GB RAM, Geforce 560 Ti, P8Z68-V/Gen3 MB) from Xubuntu 12.10 to Xubuntu 13.04 just tonight.

So far everything seems okay, except for a Qemu virtual machine with 13.04. It's now horribly slow. It used to boot up in around a dozen seconds. Since the upgrade it's more like five minutes, and once up it runs like a 386.

The command I'm using to run it is:

```
qemu-system-x86_64 -localtime -m 2048 -soundhw all -vga vmware xubu-1304.qcow
```

No error messages or anything, just ridiculously slow performance. Anyone seen anything like this? Tips on how to debug it?

---

### Post by sorceror171 on 2013-08-08
Figured it out. Apparently now you need to have "-enable-kvm" in the command options or it defaults to pure software emulation.

---

