---
title: "Feisty on HP Pavilion dv6049ea"
date: 2007-06-10
forum: Installation &amp; Upgrades
---

### Post by johatte on 2007-06-10
Hi,
Has anyone succeeded in installing Feisty on HP Pavilion dv 6059ea? I would like to have Feisty on my laptop. I've tried several times to install, tried even an network installation without success. Starting the system begins with following error messages: Found a bios bug etc. and Failed to allocate memory resources etc.. Startup process continues a while but after that everything hangs. Have even tried other Linuxes: Mandriva, Suse. The only distro which functions without errors is PXLinuxOS 2007. 
Is there a remedy for this mysterious behavior:?

---

### Post by johatte on 2007-06-10
There is error in the title. The laptop is HP Pavilion dv 6059ea.

---

### Post by foopirata on 2007-06-11
Unfortunately the bios OEM'd by HP has a very buggy BIOS. You'll need to add "noapic" to have it boot.

---

