---
title: "Upgraded from Ubuntu 9.10 to 10.04. “No any drive found”"
date: 2011-06-14
forum: Installation &amp; Upgrades
---

### Post by davidynamic on 2011-06-14
I did an upgrade on the weekend from Ubuntu 9.10 to 10.04 (karmic to lucid). Now, when I restart my computer, it goes through the regular load screen showing my P5K Asus motherboard, just like before but instead of showing the Ubuntu load screen, it tries to start grub ("Grub loading stage 1.5") but fails and then says "No any drive found" and the screen goes black.

I've tried changing the drive configuration in the BIOS to AHCI or RAID and that didn't work. I've tried disabling JMICRON but to no avail. I'm running out of options here.

What do I do?

---

### Post by mörgæs on 2011-06-14
How does the machine work in a 10.04.2 live boot?

---

### Post by davidynamic on 2011-06-14
Update. I can get into the boot menu by hitting ESC and it gives me options for 

Ubuntu 10.4.2 LTS, kernel 2.6.32-32-generic
Ubuntu 10.4.2 LTS, kernel 2.6.32-32-generic (recovery mode)
Ubuntu 10.4.2 LTS, kernel 2.6.24-29-generic
Ubuntu 10.4.2 LTS, kernel 2.6.24-29-generic (recovery mode)
Ubuntu 10.4.2 LTS, memtest86+


The line...

Ubuntu 10.4.2 LTS, kernel 2.6.32-32-generic (recovery mode)

is the only option that worked. But I don't know what to do now to fix it.

---

### Post by davidynamic on 2011-06-14
@mörgæs 

Yes, I can boot fine using a live CD.

---

### Post by ajgreeny on 2011-06-14
If I were you, I would use the 10.04 live CD and restore grub2.

You only have legacy grub at the moment, as that is what you must have chosen in the upgrade process, and I am not sure if you need to remove legacy grub before moving to grub2, so I suggest you have a good read through the grub2 links in my signature, and see what is suggested as necessary there.

Grub2, once you get it working, and also once you forget the ways of legacy grub, is a brilliant bootloader which detects all OSs on a machine with a single command, and updates the grub menu accordingly.

---

### Post by davidynamic on 2011-06-14
OK. Thanks. I'll check it out.

---

### Post by mörgæs on 2011-06-14
Since the live CD works, I would go for a clean install. This will also give you a working Grub2 automatically.

The computer has been running since Ubuntu 8.04. It deserves something fresh!

---

