---
title: "encryting /home /swap - howto do it."
date: 2008-08-05
forum: Installation &amp; Upgrades
---

### Post by nicolasdiogo on 2008-08-05
hi folks,

i have installed ubuntu 8 hardy on a laptop using lvm and create partition for:
/ root
/home
/var
/opt
swap

everything worked fine.

until i then tried to encrypt my /home and /swap

according to the howto at this location.
[http://blog.gnist.org/article.php?story=EncryptedSwapAndHomeUbuntu](http://blog.gnist.org/article.php?story=EncryptedSwapAndHomeUbuntu)

the swap encryption seems to work fine.
i am failing to see how to do the /home partition mounted at login.


i followed all the advice to the letter and double checked, but no errors.
it will not mount /home at login.

but if i manually open the partition (with password) and mount it as /home it works fine.


did anyone try to do this?

could you give some idea on how to troubleshoot this?


Many thanks


Nicolas

---

### Post by tamoneya on 2008-08-05
can we see /etc/fstab.

---

### Post by nicolasdiogo on 2008-08-07
hi,


but i think i have solved the problem by fixing a misspell on the pam XML file.

for the record,

my /home is not listed on the fstab file as it is loaded via pam when i log in.


thanks a lot

Nicolas

---

