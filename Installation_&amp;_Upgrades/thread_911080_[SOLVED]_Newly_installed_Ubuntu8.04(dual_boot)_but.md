---
title: "[SOLVED] Newly installed Ubuntu8.04(dual boot) but XP showing twice at startup"
date: 2008-09-05
forum: Installation &amp; Upgrades
---

### Post by yajuvendra on 2008-09-05
Hi,
I have installed Ubuntu newly.
I already have XP SP3.

After installation whenever i start i am getting two Windows XP options at the OS selection option.

How to remove one entry of XP from there.

There is no problem in performance wise.

Thanks for your help.

---

### Post by ronnielsen1 on 2008-09-05
The easiest way would be to go to Accessories > Terminal and type in the following command in the new window
[I][B]
sudo gedit /boot/grub/menu.lst[/B][/I]

Type in your password and in the window that pops up - you will see similar items like the following 

> title        Ubuntu 8.04.1, kernel 2.6.24-19-generic
root        (hd0,3)
kernel        /boot/vmlinuz-2.6.24-19-generic root=UUID=07f495c0-8ac9-4ea6-bc6d-ab135f383286 ro quiet splash
initrd        /boot/initrd.img-2.6.24-19-generic
quiet

Just delete all of the EXTRA win xp. This will take it out

---

### Post by yajuvendra on 2008-09-06
Hey ronnielsen1 thanks a lot.

i got it.
Actually i had old XP in my other HDD.
It was showing root-hd0 and root-hd1.
i have deleted the old one.
Now both XP and ubuntu in same HDD.
Thanks again.

---

