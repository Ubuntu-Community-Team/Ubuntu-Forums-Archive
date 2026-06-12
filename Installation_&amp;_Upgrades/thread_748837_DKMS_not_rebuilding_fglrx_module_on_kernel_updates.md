---
title: "DKMS not rebuilding fglrx module on kernel updates"
date: 2008-04-07
forum: Installation &amp; Upgrades
---

### Post by macaholic on 2008-04-07
I am currently running hardy with the latest updates, yes this was in the hardy forum, but no one responded. I have a bit large issue with DKMS and fglrx (8-3 from hardy repositories). Whenever there is a kernel update, DKMS does not rebuild the kernel module for fglrx as it should. This leaves me without graphics. In order to workaround this, I must build the driver manually, and install the kernel source from that package. Doing such forces DKMS to rebuild the kernel module, and after restart the module is installed and I must reinstall the driver and kernel source from the repositories and everything works. This issue is getting more and more annoying every time it happens, especially since o accomplish the workaround I hate to drop to a tty1 terminal and type in the commands. Any help would be greatly appreciated.

---

### Post by macaholic on 2008-04-09
No one has any ideas? i would really like to get this resolved.

---

### Post by eriksallstrom on 2008-06-04
I think I solved the problem by removing all old fglrx driver directories in the directory /var/lib/dkms/fglrx. Before I did that, I got error messages for all old drivers when I ran the command

```
sudo dkms status
```

but now I don't get any errors.

---

### Post by h3rt3q on 2008-06-13
i had the same problem too

---

