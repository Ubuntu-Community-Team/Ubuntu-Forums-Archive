---
title: "Help to correct unrecognised UUID when using grub2"
date: 2016-08-05
forum: Installation &amp; Upgrades
---

### Post by bojam on 2016-08-05
I have tried to installed 16.04.   But after rebooting grub reports seeing UUID dc5fba3b-a040-44a9-9af7-ceb52441b151 but I have checked the blkid and fstab but there is no mention of the UUID so I ran boot-repair but it does not fix it because of a 'Close all package managers running error' I don't think I'm running any ...

But boot-repair did show up the UUID in a boot sector on /dev/sdc but I'm booting off /dev/sdb so I'm puzzled.

I also tried manually updating grub but get either the /cow message or /dev not available arrrggh.

Heres the boot params link [http://paste2.org/GNOeY3V7](http://paste2.org/GNOeY3V7)  thanks in advance.

Toby

---

