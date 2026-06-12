---
title: "Small problem with upgrade -- 2 kernels installed"
date: 2005-10-14
forum: Installation &amp; Upgrades
---

### Post by Jessehk on 2005-10-14
Mostly, the upgrade went well, however in Grub, I see 2 kernals have been installed.

I seee something along the lines of:

Ubuntu kernel 142145223
Ubuntu kernel 132145223 memtest
Ubuntu kernel 13542
Ubuntu kernel 13542 memtest

with the numbers ofcourese being made-up. :)

How would I fix this? Thanks :)

---

### Post by Redindian on 2005-10-15
Same here. Two kernels. Always goes to command line. If i type /etc/init.d/gdm start, its not working.

Anyone help us.

---

### Post by Jessehk on 2005-10-15
I actually got a solution for this on another forum ( but my apt-get problem still remains :mad:...)

```


cd /boot/grub
sudo cp menu.lst menu.lst-backup
sudo gedit menu.lst


```

Edit out the repeat kernel, and you should be done :)

---

### Post by jobezone on 2005-10-15
He could also boot with the newest kernel, open up Synaptic, and from there remove the older one. It is automatically removed from the Grub menu.

---

