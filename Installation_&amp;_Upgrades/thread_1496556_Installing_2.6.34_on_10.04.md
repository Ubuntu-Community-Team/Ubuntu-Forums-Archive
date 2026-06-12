---
title: "Installing 2.6.34 on 10.04?"
date: 2010-05-29
forum: Installation &amp; Upgrades
---

### Post by gregnorc on 2010-05-29
I've been having some problems with my brightness keys, and had been told upgrading to 2.6.34-4 would solve the issue...

I ran apt-get upgrade and did a search and found two files I think should do the job:

linux-image-2.6.34-4-generic
linux-headers-2.6.34-4

So I'd do an apt-get on these two .debs and I'd be good to go, right? I have my data backed up but I'd still rather not have to reinstall because I hosed something.

---

### Post by davidmohammed on 2010-05-29
should be OK - when you install it should add a new kernel option to grub.  If the new kernel doesnt work you can always choose the standard lucid kernel from grub.

---

### Post by gregnorc on 2010-05-29
> **davidmohammed said:**
> should be OK - when you install it should add a new kernel option to grub.  If the new kernel doesnt work you can always choose the standard lucid kernel from grub.

I never see a grub menu, it just goes straight from bios to login, is there a special key combo?

---

### Post by howefield on 2010-05-29
> **gregnorc said:**
> I never see a grub menu, it just goes straight from bios to login, is there a special key combo?

You have to be quick, but the Shift key should bring up the grub menu.

---

### Post by gregnorc on 2010-05-29
> **howefield said:**
> You have to be quick, but the Shift key should bring up the grub menu.

Thanks!

---

