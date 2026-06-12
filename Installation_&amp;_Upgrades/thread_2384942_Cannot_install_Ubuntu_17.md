---
title: "Cannot install Ubuntu 17"
date: 2018-02-14
forum: Installation &amp; Upgrades
---

### Post by sweeten.jacob on 2018-02-14
First, Grub fails during install with "The grub-efi-amd64-signed" package failed to install.

If I try to follow any instructions/solutions on forums, I get nothing but errors, like "failed to get canonical path of /cow" or missing files.

I accidentally uninstalled Grub from my live installation, and I cannot reinstall it due to apt-get errors. 

So basically everything I do ends up with errors. Is my computer just entirely borked?

---

### Post by oldfred on 2018-02-14
/cow is copy on write. Or you are trying to run commands on the live installer which cannot be updated.

       May be best to see details, you can run from your Ubuntu live installer or any working install, use ppa version not older Boot-Repair ISO:
Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info) and:
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

---

