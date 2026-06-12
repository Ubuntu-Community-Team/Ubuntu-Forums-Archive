---
title: "Windows keeps asking for a recovery key every time I boot into it"
date: 2020-04-20
forum: Installation &amp; Upgrades
---

### Post by djdelarosa25 on 2020-04-20
Hi there!

I installed Ubuntu 19.10 alongside Windows 10 on my laptop last night after weeks of distro hopping. I noticed that, every time I boot into Windows from GRUB, it asks me for my BitLocker key, which is quite a hassle. Disabling BitLocker does, obviously, rectify this issue, but I'm curious if there is any other way to bypass the said prompt while retaining BitLocker, or am I better off keeping it off?

Thanks in advance.

---

### Post by djdelarosa25 on 2020-04-21
Hey there!

I installed regular Ubuntu last night with Secure Boot and BitLocker enabled but the problem is it keeps on asking me for my BitLocker recovery key every time I boot into Windows via GRUB. This is obviously not something I want to do regularly. Now I want to flash Kubuntu since I didn't really like GNOME all that much and thought I'd ask you guys how I could avoid the aforementioned problem. As much as possible I want to keep these two on but if I really have to turn off one (or both of them), I'm willing to do so.

Thank you in advance.

---

### Post by CelticWarrior on 2020-04-21
Bitlocker has nothing to do with Ubuntu and dual-boot. If you booted Windows directly the same would happen.

---

### Post by oldfred on 2020-04-21
Not sure you can from grub.

But if UEFI install, you should just be able to boot from UEFI boot menu.
UEFI has boot menu, grub is both a boot menu and boot loader, so just use a menu that works.

---

### Post by CelticWarrior on 2020-04-21
Duplicate thread: [https://ubuntuforums.org/showthread.php?t=2441217](https://ubuntuforums.org/showthread.php?t=2441217)

---

### Post by oldfred on 2020-04-21
Merged threads.

Please do not post duplicate threads.
We are all volunteers and need to know what has already been suggested to avoid duplicate effort.

---

