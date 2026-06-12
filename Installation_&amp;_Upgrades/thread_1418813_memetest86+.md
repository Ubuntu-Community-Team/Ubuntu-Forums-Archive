---
title: "memetest86+"
date: 2010-03-01
forum: Installation &amp; Upgrades
---

### Post by Cariboo1938 on 2010-03-01
Hello,
On my desktop computer I run Ubuntu 8.04 LTS.
Since last update to kernel 2.6.24-27-generic and installing a DDR3 1066 2GB memory, memetest86+ (version 1.70-3ubuntu1) gives 
[COLOR="Red"]**[SIZE="3"]Error 28: selected item cannot fit into memeory[/SIZE]**[/COLOR]
what does this mean?
My googling didn't give me a satisfying answer yet. 
Can anybody help, please?

---

### Post by dstew on 2010-03-01
It might mean that when the Ubuntu system went to load its intitial RAM file system (initramfs), or memory test code, the memory size as reported in BIOS was too small. There has to be some RAM available to load the test program. Maybe you need to go into BIOS and make sure your new memory was detected, and that the BIOS configuration was updated properly.

---

### Post by Cariboo1938 on 2010-03-01
Thanks, dstew, 
The memory test I try to start shows up in the Grub Menu, i.e. menu.lst:
>title		Ubunt 8.04 LTS, memtest86+
>root		(hd0,0)
>kernel		/boot/memtest86+.bin
>quiet

My BIOS (Award BIOS software 1984-2009) shows under Standard CMOS Features
---Base Memory  640K
---Extended Memory 1789M (This must be my 2GB 1066 Memory Card! I think?)
What else could I do?


BTW: Congrats to your Country for winning the most Olympic Medals!

---

### Post by dstew on 2010-03-02
Googling around, I found [this bug report]("https://bugs.launchpad.net/ubuntu/+source/grub/+bug/227062"). Apparently there is a problem with the memtest kernel. Some contributors said commenting-out the savedefault line in the menu.lst file helped, but I am not sure how that relates to the memtest kernel issue. Anyway, you might try it.

BTW: Congrats to your Country for winning the Hockey Gold Medals!

---

### Post by Cariboo1938 on 2010-03-06
I use the memtest from the live CD and I can live with that...
Thanks for the hint anyway!;)

---

