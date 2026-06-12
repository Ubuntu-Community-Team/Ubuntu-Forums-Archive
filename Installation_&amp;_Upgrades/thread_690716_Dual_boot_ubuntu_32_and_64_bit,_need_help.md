---
title: "Dual boot ubuntu 32 and 64 bit, need help"
date: 2008-02-07
forum: Installation &amp; Upgrades
---

### Post by bf2loser on 2008-02-07
Ive got 32 bit running right now, and i wanted to try out 64 bit but dont want to reinstall everything. I installed 64 bit on the same hardrive as 32 bit, but on a new partition, but Grub isnt recognizing the 64 bit install. It only shows I can boot up my 32 bit partition, any ideas?

---

### Post by overdrank on 2008-02-07
> **bf2loser said:**
> Ive got 32 bit running right now, and i wanted to try out 64 bit but dont want to reinstall everything. I installed 64 bit on the same hardrive as 32 bit, but on a new partition, but Grub isnt recognizing the 64 bit install. It only shows I can boot up my 32 bit partition, any ideas?

HI and you may look here to see if it is added to the grub menu
```
cat /boot/grub/menu.lst

```


[http://users.bigpond.net.au/hermanzone/p15.htm](http://users.bigpond.net.au/hermanzone/p15.htm)

---

### Post by bf2loser on 2008-02-07
Heres the last section, if you need the whole "default settings" section let me know

```
title           Ubuntu 7.10, kernel 2.6.22-14-generic
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.22-14-generic root=UUID=003d8732-ba0d-49b9-8b51-e32e35918c44 ro quiet splash
initrd          /boot/initrd.img-2.6.22-14-generic
quiet

title           Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.22-14-generic root=UUID=003d8732-ba0d-49b9-8b51-e32e35918c44 ro single
initrd          /boot/initrd.img-2.6.22-14-generic

title           Ubuntu 7.10, memtest86+
root            (hd0,0)
kernel          /boot/memtest86+.bin
quiet

```

---

### Post by bf2loser on 2008-02-07
oh sweet, I figured it out after reading some of the stuff off that link you posted, thanks!

---

### Post by overdrank on 2008-02-07
> **bf2loser said:**
> oh sweet, I figured it out after reading some of the stuff off that link you posted, thanks!

Great good luck! :popcorn:

---

