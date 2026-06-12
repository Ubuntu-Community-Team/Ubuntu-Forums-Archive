---
title: "No new kernel?"
date: 2006-10-27
forum: Installation &amp; Upgrades
---

### Post by digimars on 2006-10-27
I was wanting to run a k7 kernel (on an AMD Athlon) on Edgy.  I tried installing from the Adept Package Manager, and supposedly it installed.  I rebooted, but only the generic i386 kernel showed up in GRUB.  So I tried again:

```

me@laptop:~/Desktop$ sudo apt-get install linux-k7
Reading package lists... Done
Building dependency tree
Reading state information... Done
linux-k7 is already the newest version.

```

Well, I'll see if it's there:

```

me@laptop:/boot$ ls
abi-2.6.17-10-generic     initrd.img-2.6.17-10-generic  vmlinuz-2.6.17-10-generic
config-2.6.17-10-generic  memtest86+.bin
grub                      System.map-2.6.17-10-generic

```

No K7 kernel?  What's wrong here?

---

### Post by XaZuRy on 2006-10-28
Have you tried "sudo update-grub"?

---

### Post by digimars on 2006-10-28
Yep, and this is all I get:

```

Testing for an existing GRUB menu.list file ... found: /boot/grub/menu.lst
Searching for splash image ... none found, skipping ...
Found kernel: /boot/vmlinuz-2.6.17-10-generic
Found kernel: /boot/memtest86+.bin
Updating /boot/grub/menu.lst ... done

```

---

