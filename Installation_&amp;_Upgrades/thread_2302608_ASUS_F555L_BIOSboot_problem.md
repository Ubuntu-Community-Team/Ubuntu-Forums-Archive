---
title: "ASUS F555L BIOS/boot problem"
date: 2015-11-11
forum: Installation &amp; Upgrades
---

### Post by gnoll1102 on 2015-11-11
I have a ASUS F555L (American Megatrends Bios version 2.15.1236, c 2012) that stated playing up in mid September.

Got the machine at start off 2015 and install 14.04 64 bit and it install and worked with no problems til September.
Since then it usually hangs in the Bios, as if it doesn't recognize the hard drive as bootable.
I've ran boot-repair, to no avail.
Have booted the machine from a live USB, could still see the disk partitions and could access files fine.

Took it to ASUS, they said it was the drive, and said that they've replaced it. (they paid for it, who am I to argue that it's a boot sector issue)

The drive has now been reimaged back to virgin Windows 8, and I tried to instill 15.10 64 bit from scratch.
Same result, hangs in the Bios, within 15 minutes of getting the machine back.
Re-ran boot-repair, no joy.

[http://paste.ubuntu.com/13231611/](http://paste.ubuntu.com/13231611/)

Any help on this would be much appreciated.

Noel

---

### Post by gnoll1102 on 2015-11-11
Ok, just looking at the 'paste' output in another thread, and have noticed that boot-repair hasn't made any partition on my drive a boot partition?  Update: But GParted does show /dev/sda1 as flag with 'boot'.

---

