---
title: "lubuntu does not work in my Lenovo Y400"
date: 2013-10-04
forum: Installation &amp; Upgrades
---

### Post by oscarin-ch on 2013-10-04
Hi i install Lubuntu in my Laptop Lenovo Y400, when i reboot it didn't boot, i try to use boot repair, but the app don't work well on Lubuntu, i couldn't do anything with it. Help please, what should i do?

I buy a new hard drive, so it don't have any other OS than Lubuntu.

Thanks.

---

### Post by Bashing-om on 2013-10-04
oscarin-ch; Hi ! Welcome to the forum .

Show us what there us to work with;
Boot the installDVD ->try ubuntu mode -> key combination ctl+alt+t yields a terminal;.
Post back between code (#) tags the out put of terminal codes:
```

sudo fdisk -lu
sudo parted -l from live cd
sudo parted /dev/sda unit s print

```
Then we can see how to install your boot code or what else.

[INDENT][INDENT]just try'n to help
[/INDENT][/INDENT]

---

