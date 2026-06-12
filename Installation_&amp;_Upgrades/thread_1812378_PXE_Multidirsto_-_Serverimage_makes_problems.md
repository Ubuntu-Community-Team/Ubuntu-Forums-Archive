---
title: "PXE Multidirsto - Serverimage makes problems?"
date: 2011-07-26
forum: Installation &amp; Upgrades
---

### Post by SeaKing on 2011-07-26
I've installed an [PXEInstallMultiDistro-Server]("https://help.ubuntu.com/community/PXEInstallMultiDistro") now I also want to have the possibility to boot and install Ubuntu Server Edition. But the server image has a different structure than a desktop cd. I have to fill in the kernel (vmlinuz) and initrd.**[COLOR=black]lz[/COLOR]** path which are usually both in the root-directory / but not on the server cd. There I can find the vmlinuz in /install/ as well as the initrd but as a packed initrd**.gz** file.

And if I use the paths:
/install/vmlinuz
/install/initrd.gz

it's not booting, I even doesn't leave the menuscreen.

Or can I just boot desktop images via PXE?

---

### Post by dino99 on 2011-07-26
[https://help.ubuntu.com/community/Desktop/PXE](https://help.ubuntu.com/community/Desktop/PXE)

---

### Post by SeaKing on 2011-07-29
What exactly do you mean with the link? I do not boot a complete system just the live cd to install ubuntu on different pc's which have own hard drives.
Booting the live cd (destop-cd-image) does not make any problems but the server-cd-image has a different structure and now I want to boot the server-cd-image with the same PXE server as normal live cd.

---

### Post by lisati on 2011-07-29
Which do you want to do? Use PXE or install Ubuntu on each machine's hard drive?

---

### Post by SeaKing on 2011-07-29
Install Ubuntu on each machine's hard drive using the network (I used the [PXEInstallMultiDistro]("https://help.ubuntu.com/community/PXEInstallMultiDistro") guide)[URL="https://help.ubuntu.com/community/PXEInstallMultiDistro"]
[/URL]

---

