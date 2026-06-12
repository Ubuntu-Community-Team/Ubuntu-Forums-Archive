---
title: "Netboot installation memory requirements"
date: 2024-08-05
forum: Installation &amp; Upgrades
---

### Post by red123nax on 2024-08-05
Hi all,

I've been using the netboot installation method successfully for for a while now and I'm pretty happy about it. The PXE boot server is used to automatically installs Ubuntu with the partition layout I like and the packages that I require.

There is only one issue that I'm having, and that is the amount of memory that's required to set up my VM. Most of my VMs run with about 2GB of memory, but to get a VM up and running with netboot my VM needs at least 8GB of memory. This is mainly due to the live iso being loaded into memory. Previously there used to be mini iso files that could be used to install my OS, but now all that's available is a 2,6GB live image, which is getting a bit out of hand.

Is anyone aware of plans to create smaller ISO files for use cases like mine? Or is anyone aware of a way to limit the memory consumption during installation? (I already applied the [FONT=courier new]cloud-config-url=/dev/null[/FONT] parameter)

---

