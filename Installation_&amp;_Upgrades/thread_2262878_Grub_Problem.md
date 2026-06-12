---
title: "Grub Problem"
date: 2015-01-27
forum: Installation &amp; Upgrades
---

### Post by penguinpete on 2015-01-27
I have a Dell Inspiron 3000 laptop that I cannot install Ubuntu 14.10 or any other version of Linux on. The problem is it errors out at the end of the install when it tries to install grub. Sorry I don't remember the exact message. I've tried installing grub on the root and in the drive partition without success. I've even tried installing Ubuntu on a SD card but it won't write grub. Any ideas?

---

### Post by Bashing-om on 2015-01-28
penguinpete; Hummm .....

GPT partitioning ? requires a separate boot partition.
Show us what we are working with;
From a live DVD(USB) -> try ubuntu mode; post back the outputs - Between code tags - of terminal commands:
```

sudo fdisk -lu
sudo parted -l

```
('fdisk' will not deal with GPT, but even that provides additional info)
code tag tutorial:
[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)
Then we know and can advise 

[INDENT][INDENT][INDENT]knowledge ->
[INDENT][INDENT][INDENT]the source of power
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

