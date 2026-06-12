---
title: "Installed wrong kernel , broke boot.list"
date: 2008-07-09
forum: Installation &amp; Upgrades
---

### Post by Jinto.Lin on 2008-07-09
Ok, so I installed the wrong kernel when I was trying to get VirtualBox to work (It was a permissions issue, even worse I had forgotten that I already knew how to fix it!) and I installed a different kernel, and I don't even know what I installed because I edited the boot.list to try and find the right one.

Well, I found the right HD to put it on, and now I need to give it the right UUID somehow. It won't boot when the UUID is not there, and I don't know how to make Ubuntu add the right one. 

This is what I have, and I think that is the correct kernel.

> title		1
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.24-19-generic=UUID=09f1f6e2-4cdc-40bc-9d17-e94fcd8e27a6 ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-generic
quiet




# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		HMS Manticore
root		(hd0,0)
savedefault
makeactive
chainloader	+1


edit: I have searched teh interweb, and have not found exactly what I've needed. Google and this site, with various terms.

---

### Post by VMC on 2008-07-09
Type this from a terminal:

```
sudo blkid
```

I will show you the current UUID's. Also output your fstab:

```
cat /etc/fstab
```

---

### Post by Jinto.Lin on 2008-07-10
Well, I did some editing of the boot.list and added an old UUID, and it boots up now! Thanks for your help!

---

