---
title: "Ubuntu 8.10.1 LTS Disk Partition Booting - Expert Mode?"
date: 2008-11-12
forum: Installation &amp; Upgrades
---

### Post by dmfh on 2008-11-12
Ubunter's:

I have an older SuperMicro chassis that has a TEAC CD-224E CD-ROM coupled with a motherboard that has that "classic" CD-ROM DMA problem, preventing the installation CD from completely booting, hanging when it starts to load some of the installer files.

Fortunately, the system had an existing Linux installation on it with a large enough swap partition that was easily able to turn into an ext2 file system, and instruct GRUB to boot to, putting vmlinuz and initrd.gz in /boot along with the alternate ISO image file. 

This boots successfully into the install process, however, what I really want to be doing is not to do the automated-type install, but I want to be able to tell the install process to run in Expert mode - what do I need to do this? Is it a boot-line switch, or do I need to copy more file to /boot and more boot-line switches to get the option to switch to Expert mode?

Thanks in advance for any / all responses.

/dmfh

---

### Post by cariboo on 2008-11-12
What are you trying to install? The desktop or the server. The server installation allows you to select what serivces you want to run, but doesn't by default install a gui. While the desktop installs the default gui setup. If you really want to control the setup, use the mini.iso this only installs the basic system, either server or cli, and you can then install only the packages you want. the mini iso is available here:

[https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD)

Jim

---

