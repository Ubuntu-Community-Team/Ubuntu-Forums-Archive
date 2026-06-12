---
title: "Cannot boot after update :udevadm problem AND no chroot command!"
date: 2010-12-20
forum: Installation &amp; Upgrades
---

### Post by cleverbubbles123 on 2010-12-20
Hi guys. I installed Ubuntu Netbook Edition 10.10 on my Eee PC 901 (the one that has 2 SSD's). It all went fine, and I ran the update manager straight after install and config. It installed the updates (all 198 of them!) without error. I was prompted to restart, so I did. I got the error "udevadm trigger is not permitted while udev is unconfigured". I found out that this error is well documented, and I followed the guide at [http://www.art.ubuntuforums.org/showthread.php?t=1567147](http://www.art.ubuntuforums.org/showthread.php?t=1567147) (apparently it affects all variants, not just UNE).
It went O.K., until I tried the command "sudo chroot /media/newroot". I got the error that "cannot run command '/bind/bash': no such file or directory". What should I do?

NOTES: I cannot boot into and earlier kernel (problem/current one is 2.6.35-23-generic)
I can only fix it via live USB stick.

Thanks

---

### Post by cleverbubbles123 on 2010-12-20
bump, please help!

---

### Post by cleverbubbles123 on 2010-12-20
hate to keep bumping, but i really could do with some help. Please!

---

### Post by cleverbubbles123 on 2010-12-21
how have others fixed this?

---

### Post by garvinrick4 on 2010-12-21
That means you have not made a directory for /media/newroot
```
sudo mkdir /media/newroot
```

---

### Post by garvinrick4 on 2010-12-21
#You have to make a directory in this case it is just called newroot You can name  a directory whatever your want.
```
sudo mkdir /media/newroot
```#you are mounting the filesystem booting with.
If it is lets say sda5
```
sudo mount /dev/sda5 /media/newroot
``````
sudo chroot /media/newroot
```Now you will be in root of sda5.
#It is saying just to use your own install booting from be it sda1 or sda2 or sda5, just your own.
# Now follow the link you posted in post #1 seems to have worked for others.

---

### Post by cleverbubbles123 on 2010-12-21
it cant find the command "chroot"

---

### Post by garvinrick4 on 2010-12-21
> **cleverbubbles123 said:**
> it cant find the command "chroot"
Do you have the same architecture of Live Cd, 32 or 64 bit as the what you are trying to
chroot into?

---

