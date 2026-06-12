---
title: "Blank partition table"
date: 2008-07-16
forum: Installation &amp; Upgrades
---

### Post by Chris H on 2008-07-16
I was resizing a spare partition and pulled the plug before the resized partition had been written to disk.

Now when I start the pc it bombs out with a can't find startx error. However if I then type reboot from the command line it brings me to the xubuntu login screen and all seems ok. No other partitions are available in the file manager and running gparted shows a completely blank /dev/sda.

Any ideas on getting it back to what it was?

/dev/sda1 xp
/dev/sda3 xubuntu
/dev/sda6 linspire
/swap

Thanks!

---

### Post by Pumalite on 2008-07-16
Use rescuecd:
[http://www.sysresccd.org/Download](http://www.sysresccd.org/Download)
Fix your partitions and/or Partition Table.(TestDisk)

---

### Post by Chris H on 2008-07-16
Ta, downloading now

---

### Post by Chris H on 2008-07-17
Not gone well there!

The reason I was resizing partitions was to make more room. Didn't have enough to download rescuecd :(

So bit the bullet, copied my data to a usb stick and installed Ubuntu using the complete drive.

Now I have plenty of room and for the first time in ages no Windows taking up valuable hd space!

---

### Post by Pumalite on 2008-07-17
Congrats!

---

