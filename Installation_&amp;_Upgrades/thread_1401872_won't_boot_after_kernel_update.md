---
title: "won't boot after kernel update"
date: 2010-02-08
forum: Installation &amp; Upgrades
---

### Post by beatanga on 2010-02-08
here's the problem:

update manager reported some updates including kernel update to version 2.6.31-19.

after update system won't boot. it crashes into bash shell. i've manually loaded kernel version 16 with following command:

```
linux /boot/vmlinuz-2.6.31.16-generic root=/dev/sdc1 loop=/ubuntu/disks/root.disk ro

initrd /boot/initrd.img-2.6.31-16-generic

boot
```

in my case sdc1 is ubuntu drive. i also run 

```
sudo update-grub
```

in terminal. it didn't help. after restart it fall into bash shell.

same thing hapend when version 17 came up. I definetlly NEVER again going to update kernel. What do I need to do now? should I uninstall latest kernel...if that is posible?

thnx

I'm running ubuntu 9.10 (via wubi) and windows xp.

---

### Post by beatanga on 2010-02-08
I've found that edward morris is having the similar problem.


[http://ubuntuforums.org/showthread.php?t=1401711](http://ubuntuforums.org/showthread.php?t=1401711)

anybody?

---

### Post by beatanga on 2010-02-09
solution found on this topic

[http://ubuntuforums.org/showthread.php?t=1376781](http://ubuntuforums.org/showthread.php?t=1376781)

with this patch for wubildr

[https://bugs.launchpad.net/ubuntu/+source/lupin/+bug/477169/comments/210](https://bugs.launchpad.net/ubuntu/+source/lupin/+bug/477169/comments/210)

:)

---

