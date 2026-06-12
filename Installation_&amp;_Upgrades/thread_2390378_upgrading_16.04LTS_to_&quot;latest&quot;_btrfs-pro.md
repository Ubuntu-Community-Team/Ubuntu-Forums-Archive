---
title: "upgrading 16.04LTS to &quot;latest&quot; btrfs-progs"
date: 2018-04-28
forum: Installation &amp; Upgrades
---

### Post by David_Partridge on 2018-04-28
Hi folks I'm having some btrfs problems and the btrfs folks are telling me that kernel 4.8.13 and btrfs-progs 4.7.3-1 are a bit "old" and they would like me to upgrade.

Are there prebuilt packages that will let me do this are am I left to build all from source (I so hope not).

If yes please guide me through the process.

Many thanks
David

---

### Post by David_Partridge on 2018-04-30
I installed:

linux-base_4.5ubuntu1~16.04.1_all.deb,
linux-tools-4.15.0-15-generic, 
linux-image-4.15.0-15-generic, linux-image-extra-4.15.0-15-generic,
linux-headers-4.15.0-15, linux-headers-4.15.0-15-generic,
btrfs-progs 4.15.1-1build1

Hope this helps someone
David

---

### Post by Impavidus on 2018-04-30
I don't know why you were on the 4.8 kernel. It has been dead for quite a while. On 16.04 one would normally use the 4.4 kernel that it originally came with. Updates would be automatically pulled in via the package **linux-generic**. If you installed using the 16.04 or 16.04.1 installer or upgraded from a previous release, that's the one you should expect.

Or use the kernel coming with the HWE stack, which will currently give you 4.13 (used to be 4.8, later 4.10). Updates can be pulled in automatically via the package **linux-generic-hwe-16.04**. If you installed using the 16.04.2, 16.04.3 or 16.04.4 installer, that's the one you should expect.

Finally there's **linux-generic-hwe-16.04-edge**, which apparently pulls in kernel 4.15 and updates. I'm not so familiar with the ***-edge** packages, I guess they're meant to pull in the latest kernels.

Your method will not give you automatic security patches.

---

### Post by David_Partridge on 2018-04-30
4.8.13 was applied to fix a rather nasty problem with my hardware raid.   

I removed the manually installed headers and images and installed the vitrual packege linux-generic-hwe-16.04-edge which appears to do what I want.  Though how I was supposed to know of its existence and that I needed to install it if I needed to be closer to bleeding edge (as the btrfs follks told me) I don't quite know...

D.

---

### Post by Impavidus on 2018-04-30
I found out by browsing/searching [https://packages.ubuntu.com/](https://packages.ubuntu.com/)

---

