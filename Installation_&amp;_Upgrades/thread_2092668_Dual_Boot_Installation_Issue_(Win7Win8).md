---
title: "Dual Boot Installation Issue (Win7/Win8)"
date: 2012-12-08
forum: Installation &amp; Upgrades
---

### Post by nikRbokR on 2012-12-08
I am trying to dual boot Windows 7 and Ubuntu 12.10. I've done this before without much issue, but this time around I may have made a mistake

My HD has 3 partitions on it: (1)Windows 7, (2)Files, and (3)Free Space. In that 3rd partition, I had Windows 8 Consumer Preview installed. However, since the full version is out, I decided that I wanted to go back to trying Ubuntu. Rather than looking up how to "uninstall" the OS, I just reformatted the partition. I restored the MBR for Windows 7, and deleted the Windows 8 boot option in msconfig. From what I can see in Windows 7, Windows 8 is no longer anywhere on my HD.

However, when I try to install Ubuntu 12.10 from the Live CD, it only gives me the option of installing Ubuntu alongside Windows 8. So that leads me to two questions:
1) How can I fix this? Windows 8 isn't present, and I want it to install alongside Windows 7.
2)Will choosing the "install alongside" option affect the partition in which I keep files?

---

### Post by Isamu715 on 2012-12-08
Just use the "Something else" option and assign the partitions manually so you can be sure on which partition you're installing Ubuntu on and what changes are made.

---

### Post by oldfred on 2012-12-08
When you installed Windows 8, your Windows 7 partition was the primary partition with the boot flag. Windows installs all of its boot files to the primary partition with boot flag, so Windows 8 upgraded your boot files in Windows 7. There must be enough difference that Ubuntu can see the difference.

While Vista, still the same.
       Multibooters, Pictures here worth 1000+ words
[http://www.multibooters.co.uk/multiboot.html](http://www.multibooters.co.uk/multiboot.html)

---

