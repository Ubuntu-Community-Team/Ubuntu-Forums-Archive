---
title: "Grub Error 5"
date: 2008-06-25
forum: Installation &amp; Upgrades
---

### Post by dominion_vortar on 2008-06-25
I have done a clean install of Ubuntu 8.04 with no other OS's on the Hard Drive and I get the error

GRUB Loading stage1.5

GRUB loading, please wait...
Error 5

what can i do to fix this please?
thanks very much for your help,
john

---

### Post by earthmeLon on 2008-06-25
Sounds similar to a problem I had when I upgraded to Hardy.
What I had to do was fix the /boot/grub/menu.lst.  I opened the file and wrote down what DRIVE and what LOCATION menu.lst was telling Ubuntu to load from.

```

title           Ubuntu 8.04, kernel 2.6.24-16-generic
root            ([COLOR="Red"]hd0,1[/COLOR])
kernel          /boot/[COLOR="Red"]vmlinuz-2.6.24-16-generic[/COLOR] root=UUID=asdfasdfnasdfakdasfkajsdf ro
initrd          /boot/initrd.img-2.6.24-16-generic
quiet

```

I've highlited the parts that were wrong on mine.  First of all, the kernel changed, but the menu.lst didnt update, so I had to find the right file name, and then after that didn't work, I realized my HDD was wrong.

**hd0,1**
If I remember correctly hd0 = sda/hda & hd1 = sdb/hdb
and the number after it is the partition.  So with this example it's the SECOND partition on the FIRST drive.

Hope this helps :D

---

### Post by Pumalite on 2008-06-25
Your partition table may be invalid or corrupt:
[http://users.bigpond.net.au/hermanzone/p15.htm#5_](http://users.bigpond.net.au/hermanzone/p15.htm#5_)

---

