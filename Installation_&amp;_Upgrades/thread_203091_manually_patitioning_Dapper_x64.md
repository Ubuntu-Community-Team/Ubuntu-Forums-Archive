---
title: "manually patitioning Dapper x64"
date: 2006-06-24
forum: Installation &amp; Upgrades
---

### Post by elbeasto on 2006-06-24
On a clean hard drive of 120 gb, I want to use 20gb for an Ubuntu installation.
Can someone please explain how to do this.

Thanks

---

### Post by aysiu on 2006-06-24
Follow these directions and select "Manually Edit the Partition Table" instead of "Erase Entire Hard Drive."

[http://www.psychocats.net/ubuntu/installing.html](http://www.psychocats.net/ubuntu/installing.html)

---

### Post by elbeasto on 2006-06-24
[QUOTE=aysiu]Follow these directions and select "Manually Edit the Partition Table" instead of "Erase Entire Hard Drive."

[http://www.psychocats.net/ubuntu/installing.html](http://www.psychocats.net/ubuntu/installing.html)[/QUOTE]

That's what I've been trying to do.

Is there a way I can just allocate 20gb and then the installer automatically create the root, home and swap patition sizes?

---

### Post by aysiu on 2006-06-24
No.

If you do Automatically Resize, it'll automatically create root and swap, but I don't think you can specify to use 20 GB, and it definitely won't create a separate home partition for you.

---

### Post by elbeasto on 2006-06-24
Ok, afer a few installer crashes I've managed to install using roughly 20gb!

4gb for /.
13gb for /home.
3gb for swap.

Is this ok, I wasn't sure if I should give more space to '/' or '/home'

cheers

---

### Post by aysiu on 2006-06-24
3 GB of swap is too huge. Swap shouldn't be bigger than 1 GB.
Give two gigs of that to the /home partition, and you should be good.

---

