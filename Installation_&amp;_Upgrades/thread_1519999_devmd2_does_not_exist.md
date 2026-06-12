---
title: "/dev/md2 does not exist?"
date: 2010-06-29
forum: Installation &amp; Upgrades
---

### Post by sunrex on 2010-06-29
Orginally I was getting this:

[IMG]http://filesmelt.com/dl/imsad.JPG[/IMG]

Then I reinstalled using ext3, got something similar to the above.

Spent a few hours reading online, finally disabled UUID in fstab and grub. Rebooted.

Funny thing, now its reporting /dev/md2 does not exist, but /dev/md1 does.

/dev/md1 = 4 drives - raid 1 /boot
/dev/md2 = 4 drives - raid 10 /

Yet, I can mount /dev/md2 fine in the recovery shell.

So basically my entire issue is now its not mounting my / partition. How do I go about fixing this? I'm stuck in initramfs until its fixed =(

---

