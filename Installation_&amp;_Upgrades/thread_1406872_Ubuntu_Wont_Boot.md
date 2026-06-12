---
title: "Ubuntu Wont Boot"
date: 2010-02-14
forum: Installation &amp; Upgrades
---

### Post by fastop on 2010-02-14
I installed ubuntu 9.10 inside windows, I was told to reboot and it will continue, it continued and I got told to reboot again. 

It gets to the bootloader and tells me to choose between xp or ubuntu, I click ubuntu and this comes up..

GNU GRUB version 1.97 beta4

[ Minimal BASH-like line editing is supported. For the first word, TAB lists possible comand completions. Anywhere else TAB lists possible device/ file completions. ]

sh:grub>

Im a complete noob so I didnt know what I was doing. I typed in "boot" and it said 

error: no loaded kernel

so im guessing the kernel or something didn't get installed.
Any ideas? Thank you:)

---

### Post by darkod on 2010-02-14
This is a known wubi bug. Get the updated wubildr file from here:
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Wubi_9.10](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Wubi_9.10)

and copy it on the partition where you installed wubi ( C:, D:, etc ). It should replace the current wubildr file.
After that it should be fine.

---

