---
title: "[SOLVED] updating grup alternatives"
date: 2008-08-15
forum: Installation &amp; Upgrades
---

### Post by sheazar on 2008-08-15
I'm just installed GoboLinux tocheck it out but I don't know how to get correct alternatives in grub.  GoboLinux is in my old Vista partition and grub still shows Longhorn vista bootloader. If selected it gives me an error.

Because of the danger involved I don't have the guts to guess :(, any ideas?

---

### Post by Elric27 on 2008-08-15
try sudo update-grub
can't you just chainload it? I used to mess a lot, now I always chainload to different partitions from grub. Never goes wrong

---

### Post by sheazar on 2008-08-16
How do I get it to chainload?

---

### Post by Herman on 2008-08-16
You need to make sure you install GoboLinux's GRUB to the first sector of GoboLinux's partition if you want to use the chainloader command. [Re-install GRUB with a GRUB shell]("http://users.bigpond.net.au/hermanzone/p15.htm#Re-install_Grub_with_Live_CD").

Then, you need to edit the /boot/grub/menu.lst file in Ubuntu, (I presume you have Ubuntu and you want to boot GoboLinux from Ubuntu's GRUB).
[Operating System entries for multibooting other Linux Systems]("http://users.bigpond.net.au/hermanzone/p15.htm#Operating_System_Entries_for_Multiple_Booting_More_Linux_Systems")

---

### Post by sheazar on 2008-08-16
thanks for the link, solved it with configfile boot entry :).

---

### Post by Herman on 2008-08-16
:) Okay, that's good. The configfile boot entry is quicker and easier and will work just as well. 

Regards, Herman :)

---

