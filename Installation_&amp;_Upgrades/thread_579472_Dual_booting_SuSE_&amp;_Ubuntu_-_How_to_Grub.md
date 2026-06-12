---
title: "Dual booting SuSE &amp; Ubuntu - How to Grub?"
date: 2007-10-18
forum: Installation &amp; Upgrades
---

### Post by linuxaz on 2007-10-18
Hello,
I have Open Suse 10.3 installed and working well, but wanted to try out Ubuntu 7.10.

I have two hard drives in my laptop, Suse and Grub are on sda0.  When I install Ubuntu, where shall I have it install it's grub?  I've done this before....but it's been a while.  I'd rather have Ubuntu install it's grub someplace, and just point the Suse boot loader to it.....

So, where shall I have Ubuntu install it's GRUB.

Any information is appreciated!

Thanks,

linuxaz

---

### Post by linuxaz on 2007-10-18
Bump,
wow there is a lot of traffic on here today!

---

### Post by kellemes on 2007-10-18
Just let Ubuntu replace the Grub-install of SuSe.. You can then use [Super Grub Disk]("http://supergrub.forjamari.linex.org/") to fix Grub based on the menu.lst you have in your /boot-partition on SuSe.
SuperGrub needs only to know where the /boot-partition is to fix your Suse Grub-install. Works pretty fine.

Startup SuSe and edit /boot/grub/menu.lst on your SuSe-install to create the pointer to your Ubuntu menu.lst.
You will create a nested bootmenu, pretty cool.

This is an example.. obviously hd0,2 depends on where the Ubuntu /boot-partition is..
```
title        Ubuntu X
configfile   (hd0,2)/grub/menu.lst
```

Edit: A link that explains it all much better.
 [http://users.bigpond.net.au/hermanzone/p15.htm#1._Configfile]("http://users.bigpond.net.au/hermanzone/p15.htm#1._Configfile")

---

