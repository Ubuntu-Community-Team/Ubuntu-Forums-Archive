---
title: "How to make XP default booting OS in Ubuntu"
date: 2005-07-16
forum: Installation &amp; Upgrades
---

### Post by diffuser78 on 2005-07-16
Hello,

I have a dual boot machine with ubuntu and Win XP on my laptop as well as desktop. I was wondering if there was a way to make Windows XP as my default OS instead of Ubuntu.

I am pretty sure there must be such option. Any help is appreciated,
Thanks

---

### Post by bored2k on 2005-07-16
[QUOTE=diffuser78]Hello,

I have a dual boot machine with ubuntu and Win XP on my laptop as well as desktop. I was wondering if there was a way to make Windows XP as my default OS instead of Ubuntu.

I am pretty sure there must be such option. Any help is appreciated,
Thanks[/QUOTE]
 Download grubconf [http://www.freewebs.com/bored2k/grubconf_0.5.1-4ubuntu2_i386.deb](http://www.freewebs.com/bored2k/grubconf_0.5.1-4ubuntu2_i386.deb)
Install using the 
sudo dpkg -i *filename* command, then launch with sudo grubconf.

There simply highlight Windows and exit (the first time grubconf will freeze, reopen it and it should get done).

---

### Post by diffuser78 on 2005-07-17
Thanks a zillion bro!!!

---

