---
title: "Kubuntu LiveCD won't load, stuck in &quot;BusyBox&quot;"
date: 2008-06-07
forum: Installation &amp; Upgrades
---

### Post by jamieh on 2008-06-07
My computer has two hard drives:

60GB Maxtor(Windows XP)
250GB Seagate (Empty, want to put Kubuntu on)

I keep all my data on an external drive.

Whenever I try to load the Kubuntu LiveCD, it get's stuck at some "BusyBox" screen right after the bouncing loading bar.

Here's what it says:

```
BusyBox v1.1.3 (Debian 1:1.1.3-5ubuntu12) Built-in shell (ash)
Enter 'help' for a list of built-in commands.

(initramfs)_
```

Whenever I unplug the Seagate drive, it boots fine, even though Windows sees the drive just fine, and has no problems with it.

Are Seagate drives not Linux compatible?

---

### Post by Pumalite on 2008-06-07
You might need a boot parameter such as 'all_generic_ide'. Place it at the end of the boot line:
[http://grumpymole.blogspot.com/2007/05/ubuntu-how-to-edit-grub-boot-parameters.html](http://grumpymole.blogspot.com/2007/05/ubuntu-how-to-edit-grub-boot-parameters.html)

---

### Post by phicloray on 2008-08-12
all_generic_ide worked for me when I had the same problem, although I put it with noapic and nolapic as well - don't know which one solved it because I'm new to Linux!

Cheers though :)

---

