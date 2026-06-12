---
title: "Installation help on external hdd"
date: 2010-01-07
forum: Installation &amp; Upgrades
---

### Post by abhimanyu101 on 2010-01-07
I am a total newb with that said.... I have 1 Tb external Hdd with 33Gb (NTSF) and 873 Gb (NTSF) partations . I want to install ubuntu 9.04 on my 33Gb partation without losing any data on 873 Gb partition (mind you the figure is approximated). Need help to do so. By the way dont tell me 1st to get the new 9.10 version pls just tell the steps and it would help if you provide picture also dont assume anything on my behalf. I would like to use the graphical installer so pls guide me Thank you

---

### Post by darkod on 2010-01-07
1. Copy everything you need from the 33GB partition.
2. Using windows disk management or ubuntu gparted, delete the 33GB partition and leave the space as unallocated.
3. Boot with the ubuntu cd/usb and start the install process. At step 4 tell it to Use Largest Free Space available. That will set it up in the 33GB unallocated space creating the necessary root and swap partitions. Remember how your ext hdd is called, for example /dev/sdb.
4. Before clicking Install at the last screen, click Advanced and set the bootloader to install on the ext hdd (/dev/sdb if that's what it was called), if that's what you want. Usually you would do this with ext hdd. Screenshot attached.

That should be it. Your int hdd would still work as normal with the ext disconnected, and with the ext hdd connected you will need to select it to be first in boot order either with some Quick Boot menu, or in BIOS.

---

### Post by abhimanyu101 on 2010-01-09
Thank you it worked fine.

---

