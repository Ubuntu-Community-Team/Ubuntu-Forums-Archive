---
title: "Accessing HDD from Live CD"
date: 2007-02-16
forum: Installation &amp; Upgrades
---

### Post by EchoBeach on 2007-02-16
I have a PC with two 20GB HDDs.  The first (hda) has FC5 installed, the second had Breezy installed.  I could run up which ever one I wanted to as I had configured Grub on the primary partition.
I used a recent live CD with Dapper to upgrade hdb.  It worked OK.  When I rebooted the PC, it booted straight into hdb - no FC5.
I then 'upgraded' FC5 to re-instate it and that worked fine.  I'm now back to square one - except that the installation on hdb (Dapper) has changed - so I can't boot into it.
I thought, 'OK, I'll use the live CD to access hdb and view the boot menu'.  However when I boot from the live CD, it can't read/access/mount the HDD (using the equivalent of Windows Explorer/'My Computer').
What do I need to do to enable me to boot up with the live CD and read the HDD?
Alternatively, can anyone tell me how the entries in menu.lst have changed from Breezy to Dapper - so I can just edit the menu.lst on hda.
Regards
Echo

---

### Post by confused57 on 2007-02-16
This guide should help you mount your Dapper from the live cd:
[http://users.bigpond.net.au/hermanzone/p10.htm](http://users.bigpond.net.au/hermanzone/p10.htm)

If it'll help, here's the latest kernel entries in my Dapper menu.lst:
```
title           Ubuntu, kernel 2.6.15-28-386
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.15-28-386 root=/dev/hda1 ro quiet splash
initrd          /boot/initrd.img-2.6.15-28-386
savedefault
boot

title           Ubuntu, kernel 2.6.15-28-386 (recovery mode)
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.15-28-386 root=/dev/hda1 ro single
initrd          /boot/initrd.img-2.6.15-28-386
boot

title           Ubuntu, kernel 2.6.15-27-386
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.15-27-386 root=/dev/hda1 ro quiet splash
initrd          /boot/initrd.img-2.6.15-27-386
savedefault
boot

title           Ubuntu, kernel 2.6.15-27-386 (recovery mode)
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.15-27-386 root=/dev/hda1 ro single
initrd          /boot/initrd.img-2.6.15-27-386
boot
```

---

### Post by EchoBeach on 2007-02-17
Thanks confused.
The link enabled me to access the HDD and extract the figures from /boot/grub/menu.lst and then edit the same on the primary partition (FC5).
I am now able to choose between FC5 and Ubuntu as before.:) 
Thanks again.
Echo

---

