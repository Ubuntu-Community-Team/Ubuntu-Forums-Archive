---
title: "Cannot boot LVM on SSD after inserting hard drive with Windows/Linux operating system"
date: 2015-06-29
forum: Installation &amp; Upgrades
---

### Post by Pocc on 2015-06-29
Hi all,

I have a 40GB SSD, a 2TB drive, and a 1TB drive. The 1TB drive has Windows 7/Ubuntu 11.10, while the 40GB SSD has Linux Mint 17 in an LVM. I can't boot off of the LVM and can't make the grub from the 1TB drive recognize the LVM. 

This is the error I get when I try to boot the 40GB SSD: 

```
Missing operating system. 

BOOTMGR is missing
Press Ctrl+Alt+Del to restart
```

What should I do?

---

### Post by oldfred on 2015-06-29
Your 11.10 is obsolete, you repositories are closed. You cannot update it anymore.
But you need to add lvm2 driver for a standard Ubuntu install to recognize another install with LVM. That driver is not in the standard install

Best to upgrade or re-install to a current version. Then you can update it.
 [https://wiki.ubuntu.com/Releases](https://wiki.ubuntu.com/Releases)
[http://en.wikipedia.org/wiki/List_of_Ubuntu_releases](http://en.wikipedia.org/wiki/List_of_Ubuntu_releases)

---

### Post by Pocc on 2015-06-30
Thank you! I'll do that once I get back from camping.

---

