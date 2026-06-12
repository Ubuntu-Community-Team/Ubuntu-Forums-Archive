---
title: "Software updater hanging on grub-efi-amd64...."
date: 2015-05-28
forum: Installation &amp; Upgrades
---

### Post by Shugs81 on 2015-05-28
right.. will it screw up my install if i reboot with this? been stuck about an hour now so not just slow...

in the details it shows :
[ATTACH=CONFIG]262256[/ATTACH]

sorry for the pic... couldn't copy and paste and wasn't typing it all out....

any ideas? plus the fact that i'm using an intel processor.... why would it be installing amd stuff? (nvidia gfx card too)

---

### Post by grahammechanical on 2015-05-28
It is not installing AMD stuff. The Linux 64 bit kernel is called amd64. The Linux 32 bit kernel is called i386. That is just the way it is. Actually, what you are seeing is the installation of Grub 2 and the installation finished successfully.
> Installation finished No error reported.

When we get an upgrade to the Linux kernel Grub has to be re-installed  and its configuration file re-generated or we will not be able to load  Ubuntu with the new kernel from the Grub boot menu.

It is the part where a new grub configuration file is generated that the process has paused or even stopped. The process quickly finds all the Linux kernels on the partition that the update is being run from. It then looks for other operation systems and depending on how many other operating systems, including Linux ones, there are this can take a bit of time. But I have never known it to take an hour to complete this part of the process.

There may be problems with the file system/partition that another OS is installed on. And that is forcing grub os-prober to repeated check for a boot loader.

Regards.

---

### Post by Shugs81 on 2015-05-28
it has actually just finished... no idea why it took so long to do whatever it was doing but it's done now...

but thanks for clearing that up with the AMD thing...didn't know that was the difference!!

---

### Post by Khaldoon_Mansour on 2015-10-27
How long did you wait for that hanging on until it was resolved ? ive been waiting for an hour now !

---

