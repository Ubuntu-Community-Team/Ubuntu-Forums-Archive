---
title: "i cant start my ubuntu after upgrades"
date: 2007-07-17
forum: Installation &amp; Upgrades
---

### Post by mellow estrella on 2007-07-17
i had my ubuntu run automatic upgrades and i had to restart in order for them to take effect but when i restarted my ubuntu it got locked up in the booting process, i can still reach the menu but i dont know what commands i have to write to get my upgrades running, i have feisty fawn and since it was an automatic upgrade i dont know what files where downloaded, can anybody give me the commands nessesary to run my ubuntu, thanx

---

### Post by merlinus on 2007-07-17
One thing to check is if the grub pointers are correct.  Press "e" at the menu, and make sure that (hdx,x) correspond to where grub and ubuntu are installed.

For example, if you have one hdd and ubuntu is on sda5, then it should be (hd0,4).

If you do not know, you can boot from the live cd and enter in a terminal:

[code]
sudo fdisk -l
[/code}

(l is a lowercase L)

The partition marked linux will be the one that is ubuntu.  Subtract one from that number, and use it as detailed above.

If this works, then you may need to edit /boot/grub/menu.lst to indicate the same thing.

Post back if you are still having problems, and detail everything you tried.

-merlin

---

