---
title: "&quot;Unable to satisfy all constraints on the partition&quot; error during installation"
date: 2014-07-07
forum: Installation &amp; Upgrades
---

### Post by Linuxour on 2014-07-07
Hello,

I have a Gigabyte H61m-s2p motherboard which has UEFI

I have formated my hard drive like the following using Gparted

 - I chose the GPT partition table
- 250 MB - FAT 32
- 30 GB - ETX4 for root
- 4 GB - Swap
- The rest for Home

[IMG]http://s28.postimg.org/ptiz86n65/image.png[/IMG]

After pressing install now I get the following


[IMG]http://s9.postimg.org/74mxhlhsv/image.png[/IMG]

So I clicked on "Free space" as the previous pic shows then "+" and chose "Reserved Bios Boot Area"

a message appeared saying

[IMG]http://s29.postimg.org/ohzovvdcn/image.png[/IMG]

Could you explain simply what else should I do ?

---

### Post by Bucky Ball on 2014-07-07
You should be clicking on /dev/sda1 and assigning that as the 'Reserved BIOS boot area'. At the moment, it's just a small FAT32 partition. That is your UEFI partition and that is what it is banging on about.

Just for future reference, please attach images with Go Advanced or Adv Reply and use the paperclip icon. Thanks. ;)

---

### Post by Linuxour on 2014-07-07
Thank you very much indeed, It worked like a charm.Thanks for the tip.

---

### Post by Bucky Ball on 2014-07-07
Great! Glad it all worked out. Enjoy and good luck. ;)

---

