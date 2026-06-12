---
title: "ubuntu 12.04 Blank Screen after reboot"
date: 2012-11-12
forum: Installation &amp; Upgrades
---

### Post by Unewbeginner on 2012-11-12
hi there, 

I tried to install ubuntu 12.04 on my hard drive with an usb flash drive. The install process looks fine, but when I reboot I got a black screen. 

I tried to follow the post below:

[http://ubuntuforums.org/showthread.php?t=1743535](http://ubuntuforums.org/showthread.php?t=1743535)

I get into the system with the usb flash drive and mount my hard drive. 

```
sudo mount /dev/sda2 /mnt
sudo chroot /mnt /bin/bash
sudo vi /etc/default/grub
```



and then I changed the grub options. but I'm stuck when I try to run "sudo update-grub", I got the message:
```

/usr/sbin/grub-probe: error: cannot find a device for / (is /dev mounted?)
```

How can I get this fixed?

---

### Post by Unewbeginner on 2012-11-12
```
mount proc
mount sys
mount dev
```

added the three lines after the chroot command, and then run the "update-grub", I can see the grub menu now.

---

### Post by Bashing-om on 2012-11-12
Unewbeginner; Hi ! Welcome to the forum.

At this time from the grub menu can you boot into ubuntu's desk top ?

awaiting to see what help is needed ==> BDQ

---

### Post by Unewbeginner on 2012-11-13
> **Bashing-om said:**
> Unewbeginner; Hi ! Welcome to the forum.

At this time from the grub menu can you boot into ubuntu's desk top ?

awaiting to see what help is needed ==> BDQ



hi bashing-om.  i fixed my ubuntu already. thanks! but i can't set up my dual boot grub2 for my windows drive. i already started another thread for this problem.

---

