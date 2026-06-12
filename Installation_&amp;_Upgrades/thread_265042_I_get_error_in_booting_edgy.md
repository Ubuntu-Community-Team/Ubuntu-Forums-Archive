---
title: "I get error in booting edgy"
date: 2006-09-25
forum: Installation &amp; Upgrades
---

### Post by meital on 2006-09-25
i have ubuntu dapper and i installed edgy by debootstrap

this is the what i added to menu.lst:
```
title           Edgy (on /dev/sda2)
root            (hd0,1)/edgy
kernel          /edgy/boot/vmlinuz-2.6.17-7-386
initrd          /edgy/boot/initrd.img-2.6.17-7-386
savedefault
boot

```
when i try to enter to edgy, it writes:
```
Begin: Waiting for root file system... ...
```
and nothing happenes after that.

any ideas why it doesn't work?

---

