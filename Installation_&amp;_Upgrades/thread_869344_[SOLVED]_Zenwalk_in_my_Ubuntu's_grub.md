---
title: "[SOLVED] Zenwalk in my Ubuntu's grub"
date: 2008-07-24
forum: Installation &amp; Upgrades
---

### Post by aullidolunar on 2008-07-24
Hi all!

I just install Ubuntu 8.04.1 in my box. Good!
I shrunk Ubuntu partition an create another and formatted as ext3. Good!
I installes Zenwalk 5.2 in the new partition. Good!

ok:
I went to my Ubuntu's, because I want to use Ubuntu's grub, and add the following text:
```

title		Zenwalk 5.2
root		(hd0,1)
makeactive
kernel 		(hd0,1)/boot/vmlinuz-2.6.25.4

```
and doesn't boot on Zenwalk, some errors display. This is my fdisk -l:
```

/dev/sda1   *           1       28285   227199231   83  Linux
/dev/sda2           29650       30401     6040440    5  Extendida
/dev/sda3           28286       29649    10956330   83  Linux
/dev/sda5           29650       30401     6040408+  82  Linux swap / Solaris

```
I installed Zenwalk is located /dev/sd3, any ideas how to accomplish my task, have a dual boot?

Thanks

---

### Post by Pumalite on 2008-07-24
Change 'root' for Zenwalk to (hd0,2)

---

### Post by aullidolunar on 2008-07-24
Thanks, with your tip and some search did the trick :)

---

