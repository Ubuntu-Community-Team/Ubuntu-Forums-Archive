---
title: "Installing Ubuntu difficult. Installing Ubuntu with full disk encryption impossible."
date: 2013-10-05
forum: Installation &amp; Upgrades
---

### Post by g-curio on 2013-10-05
I have being using Ubuntu for several years, have installed it multiple times with no hassel, and have run into a weird problem:

First, I needed to install Windows over Ubuntu, so I did. About a day later, I tried to reinstall Ubuntu over Windows, so I did. I chose the full disk encryption option. When I tried to boot, I was met with a black screen and a blinking cursor. I booted using a liveUSB, and used the boot-repair utility. It did not help. Then I reinstall Ubuntu again, this time with no encryption, and got the cursor again. I livebooted, used boot-repair, and rebooted. Success! But how the heck to I install with full disk encryption?

Summary: I can boot into Ubuntu, but only if I use boot-repair and don't use full disk encryption. What's up?

---

### Post by oldfred on 2013-10-06
Welcome to the forums.

Is this Windows 8 and UEFI not BIOS type install?

Full disk encryption uses LVM as logical partitions over the physical partitions. I do not know LVM as it adds a layer of complexity as does encryption.
And it will not be full disk encryption as LVM will not work with Windows.

---

