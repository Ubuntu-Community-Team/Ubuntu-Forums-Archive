---
title: "Help with install on archlinux distro."
date: 2012-07-10
forum: Installation &amp; Upgrades
---

### Post by bwinfrey on 2012-07-10
Hello, 
I want to install Ubuntu on two systems that are currently running archlinux.  The are each configured with four partitions: "/boot", "/", "/home" and swap.  I would like to preserve the home partition.  Does the Ubuntu installer allow for that?

Thank you.

Regards,
Brian

---

### Post by SlugSlug on 2012-07-10
yes

during instal select manual partition, you can then tell it whats /dev/sd* to mount where.
Just make sure format is un-ticked!

---

### Post by bwinfrey on 2012-07-11
> **SlugSlug said:**
> yes

during instal select manual partition, you can then tell it whats /dev/sd* to mount where.
Just make sure format is un-ticked!

Thank you that worked fine.   

One note though the UIDs needed to be changed - Arch Linux started at 1001 ubuntu started at 1000.    I logged in on tty1 ([CTRL] + [ALT] + 1) as root and changed the UID(s) using ```
usermod -u arch_uid user_name
```

---

