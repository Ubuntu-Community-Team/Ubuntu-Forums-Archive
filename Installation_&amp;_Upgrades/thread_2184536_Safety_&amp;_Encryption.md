---
title: "Safety &amp; Encryption"
date: 2013-10-29
forum: Installation &amp; Upgrades
---

### Post by nickrichu on 2013-10-29
After lots of research i only came across one thread on here that had remotely the information i wanted so ill ask it here.


I'm planning on getting a laptop for school and in the event i get it,i want to know if the following is possible. I want to install the /boot in an sd card and /home in an encrypted partition in the hdd. I want it like this so that the ONLY way to literally boot into ubuntu with my laptop would be to have the sd card in.


Is it possible? Can i also encrypt the sd card with the /boot? Are there any security flaws other than the sd card getting lost and copied? Can i set up a /boot or grub password in addition?

---

### Post by papibe on 2013-10-29
Hi nickrichu.

Yes to all of that.

A few thoughts

The idea of the SD card would sure stop regular users from booting your computer. However, it won't stand for a delivered targeted attempt to boot it. Since the root partition is not encrypted, it could be relatively easy to install kernels and update grub.

You can encrypt your /home partition. It would be offered as an option as a part of the installation process. In most cases, that's all you need for privacy.

You can also do a full disk encryption (root partition and all) here are a couple of guides: [EFF: Privacy in Ubuntu 12.10. Full Disk Encryption]("https://www.eff.org/deeplinks/2012/11/privacy-ubuntu-1210-full-disk-encryption"), and [rationallyPARANOID: Ubuntu Desktop 12.04 LTS security configuration guide]("http://www.rationallyparanoid.com/articles/ubuntu-12-lts-security.html").

Hope it helps. Let us know how it goes.
Regards.

---

### Post by sandyd on 2013-10-29
> **nickrichu said:**
> After lots of research i only came across one thread on here that had remotely the information i wanted so ill ask it here.


I'm planning on getting a laptop for school and in the event i get it,i want to know if the following is possible. I want to install the /boot in an sd card and /home in an encrypted partition in the hdd. I want it like this so that the ONLY way to literally boot into ubuntu with my laptop would be to have the sd card in.


Is it possible? Can i also encrypt the sd card with the /boot? Are there any security flaws other than the sd card getting lost and copied? Can i set up a /boot or grub password in addition?

A better idea would  be to install Ubuntu with an encrypted LVM, and use a extra long random password with special characters

Then, buy a YubiKey, store the password on it, and your done

---

### Post by nickrichu on 2013-10-29
> **papibe said:**
> Hi nickrichu.

Yes to all of that.

A few thoughts

The idea of the SD card would sure stop regular users from booting your computer. However, it won't stand for a delivered targeted attempt to boot it. Since the root partition is not encrypted, it could be relatively easy to install kernels and update grub.

You can encrypt your /home partition. It would be offered as an option as a part of the installation process. In most cases, that's all you need for privacy.

You can also do a full disk encryption (root partition and all) here are a couple of guides: [EFF: Privacy in Ubuntu 12.10. Full Disk Encryption]("https://www.eff.org/deeplinks/2012/11/privacy-ubuntu-1210-full-disk-encryption"), and [rationallyPARANOID: Ubuntu Desktop 12.04 LTS security configuration guide]("http://www.rationallyparanoid.com/articles/ubuntu-12-lts-security.html").

Hope it helps. Let us know how it goes.
Regards.

So as long as /root and /home are encrypted,no one can access my info provided the sd card with /boot is safely with me?

> **sandyd said:**
> A better idea would  be to install Ubuntu with an encrypted LVM, and use a extra long random password with special characters

Then, buy a YubiKey, store the password on it, and your done
What is a yubi key? Does 13.10 allow lvm encryption?

---

### Post by nickrichu on 2013-10-29
@papibe,i checked out the links and **_&#8203;YOU ARE AMAZING._**

---

### Post by sandyd on 2013-10-29
> **nickrichu said:**
> So as long as /root and /home are encrypted,no one can access my info provided the sd card with /boot is safely with me?


What is a yubi key? Does 13.10 allow lvm encryption?

13.10 allows LVM encryption (from the installer) if you allow it to use the whole disk

YubiKey -> [http://www.yubico.com/products/yubikey-hardware/yubikey/](http://www.yubico.com/products/yubikey-hardware/yubikey/)

Basically a (actual) physical key that when pressed, emulates a USB keyboard and sends the password. That allows you to set very complex passwords without needing to remember

---

