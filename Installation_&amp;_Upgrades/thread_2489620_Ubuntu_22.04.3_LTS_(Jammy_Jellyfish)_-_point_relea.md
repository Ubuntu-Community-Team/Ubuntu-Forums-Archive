---
title: "Ubuntu 22.04.3 LTS (Jammy Jellyfish) - point release arrived"
date: 2023-08-05
forum: Installation &amp; Upgrades
---

### Post by corradoventu on 2023-08-05
```
corrado@corrado-n12-jammy:~$ inxi -SNxc
System:
  Host: corrado-n12-jammy Kernel: 6.2.0-26-generic x86_64 bits: 64
    compiler: N/A Desktop: GNOME 42.9
    Distro: Ubuntu 22.04.3 LTS (Jammy Jellyfish)

```
Attention: The update installs the new kernel 6.2.0-26-generic. If you have RTL810xE PCI Express Fast Ethernet controller
you risk this problem: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/2015670](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/2015670)
The loop is slow, so it doesn't fill the log quickly but you can see it easily from the journal, for example ```
journalctl -n 100
```

---

