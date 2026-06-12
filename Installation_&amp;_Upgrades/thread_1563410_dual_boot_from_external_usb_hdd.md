---
title: "dual boot from external usb hdd"
date: 2010-08-29
forum: Installation &amp; Upgrades
---

### Post by dilog on 2010-08-29
I installed ubuntu 10.04 on external usb hdd after having the internal drive disconnected. When now I try to boot i can only do it from the internal. I can see the external when in ubuntu, but no booting. Also I can see the external in the internal grub menu but when booting disappears. I suspect that it has to do whith the designation of volume names, when installing from external the disk is named sda1 but in the internal grub is sdb1.
How can I change the name to sdba1 in the external grub - should it solve
my problem?

---

### Post by sharathcshekhar on 2010-08-29
If you have Ubuntu on your internal HDD as well, just log in and with your external HDD connected but not mounted, give 
```

sudo update-grub

```
This might solve your problem I think. If not, you also boot from Live cd and give the same command with both HDDs connected

---

### Post by oldfred on 2010-08-29
Even when grub has the wrong drive hd0,0 instead of hd1,0 for example it does a search on UUID and still should boot. 

I had a similar issue when I installed to a flash drive that was seen as hd6, my installer was another flash as hd5. I removed hd5 and tried booting and I think the search stopped looking after the gap in drive numbers. I used from the grub menu e - edit and modified the hd number and it booted. Then running sudo update-grub fixed it.

---

