---
title: "Upgrade corrupted program"
date: 2010-08-08
forum: Installation &amp; Upgrades
---

### Post by Camilia on 2010-08-08
I have windows and ubuntu os. When I log in I choose ubuntu. Then have another row of options. When I choose the top program 2.6.31-22 I am unable to log in. Tried the restore option for the same program and it didn't work either. Thus I choose the second program. 2.6.31-14. How do I delete the top option that does not work.

---

### Post by Rubi1200 on 2010-08-08
Have you tried

```
sudo update-grub
```

from the terminal?

Then reboot and see if you still have the same issue.

You are talking about the kernel versions in the GRUB menu. But, the "top" one is the latest and should work unless there is some issue.

As I said, try the command first and let us know what happens before we take the next step of trying to diagnose why you are unable to boot the latest kernel version on your system.

---

### Post by Camilia on 2010-08-08
Pasted sudo update in terminal and got:
Found linux image: /boot/vmlinuz-2.6.31-22-generic
Found initrd image: /boot/initrd.img-2.6.31-22-generic
Found linux image: /boot/vmlinuz-2.6.31-14-generic
Found initrd image: /boot/initrd.img-2.6.31-14-generic
Found Microsoft Windows XP Home Edition on /dev/sda1
Found Windows NT/2000/XP on /dev/sda2

Still no change.
Message is:
Kernel panic no syncing Unable to mount root fs on unknown_block (8,1)
This is the one - /boot/vmlinuz-2.6.31-14-generic - that I boot up with.

---

### Post by JBAlaska on 2010-08-08
You may be able to easily fix your 2.6.31-22 (First entry) Wubi install, Follow this [Link](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Wubi_9.10)

---

### Post by Camilia on 2010-08-09
Very interesting Watson. Tis exactly what is happening. I shall try that later, for it is only 12 am.

Well I copied and pasted the program into the c drive and all is okay. Now I know why in the past I had to reload ubuntu. 

Thanks a bunch.

Well again do upgrade and to log into ubuntu have scroll down to go to program initially downloaded in windows. Get message need to load kernel. 

Tried the previous suggestion and no change.
Anybody got any suggestions?

---

