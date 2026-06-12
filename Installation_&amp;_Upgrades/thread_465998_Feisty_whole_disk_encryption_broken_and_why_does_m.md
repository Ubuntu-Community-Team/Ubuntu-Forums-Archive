---
title: "Feisty whole disk encryption broken and why does my HDD device-file keep moving?"
date: 2007-06-06
forum: Installation &amp; Upgrades
---

### Post by user2037 on 2007-06-06
After failing to encrypt my whole Feisty installation using three different tutorials (all based on Dm-crypt and LUKS), there is one common blocker: "cryptsetup: Source device /dev/sda* not found". It always comes up after the first attempt to boot the encrypted system.

In all cases I tried using Feisty 2.6.20-16 though in the last two cases I was working with the Feisty live-CD (2.6.20-15).

Apparently the live CD and base installation thinks my IDE disks should be labeled /dev/sd* when most every other install and live distro thinks it should be /dev/hd*. Why the difference? Is it possible to force Linux to use /dev/hd*?

Is there any way to encrypt the whole Feisty installation now that the latest kernel is 2.6.20-16?

Is it possible to upgrade the kernel without moving all my data and re-encrypting?

---

### Post by TDK800 on 2007-06-09
Have you tried with loop-AES? Here's a link to an old post with research on the topic:

[http://ubuntuforums.org/showpost.php?p=2433247&postcount=2](http://ubuntuforums.org/showpost.php?p=2433247&postcount=2)

---

