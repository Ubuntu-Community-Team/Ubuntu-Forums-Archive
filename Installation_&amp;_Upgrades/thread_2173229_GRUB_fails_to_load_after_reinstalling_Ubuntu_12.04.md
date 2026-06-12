---
title: "GRUB fails to load after reinstalling Ubuntu 12.04"
date: 2013-09-08
forum: Installation &amp; Upgrades
---

### Post by sleepfuriously on 2013-09-08
I'm a Linux newby so any help is appreciated.

Dual booting Windows 8 and Ubuntu 12.04. I just reinstalled Ubuntu and now the GRUB boot menu does not appear (was working before). Instead is this screen:

> Minimal BASH-like line editing is supported. For the first word,  TAB lists possible command completions. Anywhere else TAB lists possible  device or file completions.

GRUB>

I can get to the GRUB menu by going to Boot Device Options --> Ubuntu before this screen appears, but I would prefer not to have to do this every time. How can I get it to come up automatically?

---

### Post by oldfred on 2013-09-08
Was this pre-installed Windows 8 with UEFI and secure boot, or your own install?

 Post the link to the BootInfo report that this creates. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.
LighterWeight (Lubuntu based) Boot-RepairCD
[http://sourceforge.net/projects/boot-repair-cd/files/](http://sourceforge.net/projects/boot-repair-cd/files/)
Full Ubuntu 13.04 liveDVD or USB Flash drive Installer with Boot-Repair included (for newer computers) 
[https://help.ubuntu.com/community/LinuxSecureRemix](https://help.ubuntu.com/community/LinuxSecureRemix)

---

