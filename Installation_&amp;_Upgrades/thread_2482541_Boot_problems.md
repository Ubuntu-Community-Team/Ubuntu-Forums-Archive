---
title: "Boot problems"
date: 2023-01-03
forum: Installation &amp; Upgrades
---

### Post by socktooths on 2023-01-03
Hi! I’m very new to Ubuntu, and using it mostly because my laptop is too old and slow to properly run Windows. Unfortunately, this means I’m running into a lot of issues — I’ve described the issues below, but I mostly just need some feedback before I use boot-repair. The link it gave me is at the bottom of the post.

My laptop is booting into a black screen after logging in on Xorg. I would try to log in to the default Ubuntu, but Xorg works better with my Huion tablet, and I’m logged in automatically so there’s no way to change it. The black screen is not entirely black — there are a few red blobs of pixels that react to my invisible cursor.

I can log into my computer just fine if I boot up the GRUB menu and open the Recovery version of Ubuntu. I’m on my desktop right now on the Recovery startup. I installed boot-repair, and I’d like to get some feedback from more experienced Ubuntu users before I go through with its recommended repairs.

[https://paste.ubuntu.com/p/6qbBSyb55C/](https://paste.ubuntu.com/p/6qbBSyb55C/)

Thanks!
Elliot

---

### Post by oldfred on 2023-01-03
If you can get to grub menu, then Boot-Repair usually cannot fix it. 
It will offer to re-install grub. And defaults to install grub in same mode as you boot live installer, BIOS or UEFI.
You show Boot-Repair in BIOS/CSM/Legacy boot mode. But show both grub in MBR for BIOS boot and ESP - efi system partition mount in fstab.
Since ESP in fstab, last install of grub was in UEFI boot mode. You may need to make sure system is set to default boot in UEFI mode.

Black screen is often a graphics issue.
Report says you have an Intel low performance chip. Video should just work.

But with old low end system, you probably should not use Ubuntu but a light weight flavor.
I tried installing Ubuntu on an old 2006 laptop & it would not install. I did install server & fallback gui. Later installed Kubuntu and was surprised it worked as it is more of a midweight flavor.

[https://ubuntu.com/download/flavours](https://ubuntu.com/download/flavours)
Light weight flavors:
Lubuntu, xubuntu, Ubuntu MATE, Budgie

---

### Post by tea for one on 2023-01-03
From the info in the boot-repair report, this laptop is a Netbook style device.
Celeron processor with 2GB (possibly 4GB) ram and a 32GB MMC/SD disk.

As suggested by oldfred, try Xubuntu in UEFI mode with GPT.

---

