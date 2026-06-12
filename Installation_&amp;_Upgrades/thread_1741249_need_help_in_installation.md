---
title: "need help in installation"
date: 2011-04-27
forum: Installation &amp; Upgrades
---

### Post by viper_srt on 2011-04-27
i am installing ubuntu 10.10 netbook right now.
i have three partition in my system
i want to install ubuntu on partition c which is my system partition right now and windw 7 installed in it. i want to install ubuntu in this partition.
please guide me how can i do this???
also i dont want other partition to get affected.
please reply soon.................
since i am installing it right now


Thanks

---

### Post by garvinrick4 on 2011-04-27
Here is a nice thread on installing. Find your linux partition sda# you want to install in
as instructed below, use manual install and put in that sda# as instructed below.
Windows uses letters C: D: E: F: and so on and Linux uses sda1, sda2 sda3 and so on.
##Just follow instructions below and you will be fine:

[http://members.iinet.net.au/~herman546/p22.html](http://members.iinet.net.au/~herman546/p22.html)

---

### Post by viper_srt on 2011-04-27
thanks for your reply 
but that was for dual booting
i dont want to keep windows i just want to overwrite ubuntu on my window partition. also i dont want to touch my other two partition in this process.
also i am installing through usb where i am not getting any option for gpartition

---

### Post by garvinrick4 on 2011-04-27
So install it in the same sda# that Windows is in. Is it a bootable USB where you can boot
it into Linux and run in a terminal and it will give you your sda#'s
```
sudo fdisk -l
``` (lower case L)

---

