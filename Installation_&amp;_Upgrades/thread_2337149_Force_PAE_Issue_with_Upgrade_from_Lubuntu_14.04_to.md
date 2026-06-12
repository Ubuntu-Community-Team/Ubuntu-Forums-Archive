---
title: "Force PAE Issue with Upgrade from Lubuntu 14.04 to 16.04"
date: 2016-09-15
forum: Installation &amp; Upgrades
---

### Post by wjbmd48 on 2016-09-15
Hi:

I have an old, non-PAE Thinkpad that I installed Lubuntu 14.04 on using the forcePAE workaround. When I upgraded it to 16.04, it works well but won't upgrade the kernel beyond 3.13.0.9 to the 4.4 series, which download but don't install, because it's non-PAE.

Question: is there a way I can do a forcePAE install of a downloaded 4.4 kernel, say in synaptic, or am I stuck with having to do a complete reinstall of 16.04 with forcePAE, as I've been able to do with other non-PAE systems with 16.04?

Thanks,

Bill

---

### Post by sudodus on 2016-09-15
I suggest that you set the boot option forcepae in a persistent way. See the following link

[Grub2/Setup](https://help.ubuntu.com/community/Grub2/Setup)

> GRUB_CMDLINE_LINUX

    Entries on this line are added to the end of the 'linux' command line (GRUB legacy's "kernel" line) for both normal and recovery modes. It is used to pass options to the kernel.

So edit ```
GRUB_CMDLINE_LINUX=forcepae
``` into the file **/etc/default/grub** (and save it)

and run ```
sudo update-grub
``` and reboot. Then you will be able to install new kernels.

---

