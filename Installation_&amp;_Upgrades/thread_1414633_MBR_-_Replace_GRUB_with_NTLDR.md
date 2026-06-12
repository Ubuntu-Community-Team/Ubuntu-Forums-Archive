---
title: "MBR - Replace GRUB with NTLDR"
date: 2010-02-23
forum: Installation &amp; Upgrades
---

### Post by rikyenns4 on 2010-02-23
I have installed Ubuntu 9.10 on my system. At the time I wasn't very familiar with boot loaders and I just left everything default at installation. Now I have the following setup on the hard drive:

- MBR: GNU GRUB
- Partition 1 (dev/sda1) Sony Vaio Recovery Partition
- Partition 2 (dev/sda2) Windows XP Home Edition
- Partition 3 (dev/sda3) Extended Partition
             -   (dev/sda5) Ubuntu 9.10
             -   (dev/sda6) Swap Space

I want to replace GNU GRUB in the MBR with NTLDR and add Linux to the NTLDR boot menu but from what I understand I have to install GNU GRUB to the Linux Partition first so NTLDR can chain load it to boot Ubuntu. I have heard of using the ' grub-install ' command in which from what I understand I should use it like this ' grub-install /dev/sda5 ' but I'm not sure. Can somebody help me with this. It would be very much appreciated. Thanks.

---

### Post by johnson.d on 2010-02-25
The following links may help you in setting up the primary boot loader as NTLDR.

[http://www.linux.com/archive/feature/113945](http://www.linux.com/archive/feature/113945)

I am just curious to know if there any specific reason why you prefer NTLDR to GRUB?

---

### Post by nitrofurano on 2012-07-26
maybe this solution can be helpful for easily installing Linux on UEFI Windows8-only machines?

---

### Post by oldfred on 2012-07-26
Necromancy.

Thread closed.

UEFI boot is totally different and link in thread is broken.

---

