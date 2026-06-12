---
title: "Ubuntu won't load, not even from LiveCD"
date: 2008-07-14
forum: Installation &amp; Upgrades
---

### Post by MedellinManDem on 2008-07-14
When I try and boot from the LiveCD I get a message saying:

```
BusyBox v1.1.3 (Debian 1:1.1.3-5ubuntu12) Built-in shell (ash) Enter 'help' for a list of built-in commands

(initramfs)

```

Same happens when I press "install ubuntu", too.

Any ideas on how to fix this? I have a Ubuntu partition on hd0,0.

When I boot as normal I get "Error 19: Cannot mount selected partition"

---

### Post by MedellinManDem on 2008-07-14
I'm guessing it's because the install is trying to boot from root hd0,2 (which was the ubuntu partition before I moved it)...so how do I get it to boot from hd0,0? 

I went through some command line process from GRUB's site but to no avail...

It's a dual-boot system btw. I'm using Vista and EasyBCD to help me boot into Ubuntu.

---

### Post by avtolle on 2008-07-14
I'm a bit confused here; are you trying to boot from the Live CD or from the HDD?

---

### Post by MedellinManDem on 2008-07-14
> **avtolle said:**
> I'm a bit confused here; are you trying to boot from the Live CD or from the HDD?

I was booting from the HDD..until it stopped working.

It doesn't matter now I fixed it. I went into EasyBCD and simply altered the NeoGrub configuration so that it was booting from hd0,0.

Simple as that.

This can be marked "solved."

---

