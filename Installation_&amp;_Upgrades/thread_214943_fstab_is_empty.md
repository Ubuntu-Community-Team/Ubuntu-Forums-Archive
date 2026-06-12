---
title: "fstab is empty"
date: 2006-07-13
forum: Installation &amp; Upgrades
---

### Post by torypatnoe on 2006-07-13
I just installed a clean ubuntu-dapper box on a Dell laptop. I received a disk from a friend so I don't know if it was the official release.

I then applied all updates and upgraded to the linux-686 package (which runs slower). Most things work fine except the /etc/fstab contains only one line:

# UNCONFIGURED FSTAB FOR BASE SYSTEM

Commands like df -h do no return any reference to the root file system. I cannot determine the size of the / partition. I used the default installation with / and swap only / is mounted as xfs.

Is there a way to correct this problem?

Thanks
Tory

---

### Post by torypatnoe on 2006-07-14
I didn't have much installed on the system so I reinstalled with a root reisterfs partition. Things look much better now. After doing some checking it appears that grub doesn't like xfs too much, which is why the installation the 1st time used lilo.

I'm using grub now. And everything appears to be working fine.

Tory

---

