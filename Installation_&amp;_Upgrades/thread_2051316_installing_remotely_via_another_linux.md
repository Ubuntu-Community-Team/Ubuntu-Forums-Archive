---
title: "installing remotely via another linux"
date: 2012-09-01
forum: Installation &amp; Upgrades
---

### Post by rkleemann on 2012-09-01
Hi,

I want to install Ubuntu Server on a machine that's running Fedora.

However, I only have kvm access to the server. I can't use USB or CD methods.

Can I mount the ISO volume and attempt to install that way?

Any help is appreciated, thanks!

---

### Post by Lars Noodén on 2012-09-01
It should be possible to boot an ISO-9660 image directly using Grub.  Here are the directions for Ubuntu, but they might be close for Fedora or lead to a relevant HowTo:

[https://help.ubuntu.com/community/Grub2/ISOBoot](https://help.ubuntu.com/community/Grub2/ISOBoot)

---

### Post by rkleemann on 2012-09-01
> **Lars Noodén said:**
> It should be possible to boot an ISO-9660 image directly using Grub.  Here are the directions for Ubuntu, but they might be close for Fedora or lead to a relevant HowTo:

[https://help.ubuntu.com/community/Grub2/ISOBoot](https://help.ubuntu.com/community/Grub2/ISOBoot)

thank you. This is very helpful.

Unfortunately the existing installation does not have Grub 2, it is an old version of grub.

Is it possible to somehow force a reboot via the ISO from the command line?

---

### Post by Lars Noodén on 2012-09-01
> **rkleemann said:**
> Is it possible to somehow force a reboot via the ISO from the command line?

Not without involving the bootloader.   If you can't upgrade to Grub2 for those instructions, it might still be possible with old Grub.  I've found this clue but not tried it:

[http://www.neowin.net/forum/topic/305843-use-lilo-or-grub-to-mount-and-boot-from-iso/](http://www.neowin.net/forum/topic/305843-use-lilo-or-grub-to-mount-and-boot-from-iso/)

The possible solution is further down on that page in #4.

---

### Post by rkleemann on 2012-09-01
Thanks, I'll investigate further

---

