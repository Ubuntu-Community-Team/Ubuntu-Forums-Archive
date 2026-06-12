---
title: "change boot menu."
date: 2010-11-01
forum: Installation &amp; Upgrades
---

### Post by sunnyag on 2010-11-01
Hi everyone,

yesterday i installed ubuntu 10.10 and has successfully.

My machine env is 
xp on primary partition
ubuntu on primary partition
windows 7 on logical partition.


I have been using dual boot for long time that is xp and windows 7. Yesterday i installed ubuntu 10.10

my issue is in boot menu it is showing as 
ubuntu 
ubuntu recovery
memory
memory recovery
windows 7

In windows 7 it is showing 
windows xp
windows 7 
as windows 7 going thru its own boot loader.

I want to remove xp from windows 7 boot loader and make it see at main boot loader. Help?

---

### Post by jrev on 2010-11-01
You can have a look at :
[http://linuxers.org/howto/how-configure-grub2-ubuntu-910](http://linuxers.org/howto/how-configure-grub2-ubuntu-910)

---

### Post by sunnyag on 2010-11-01
sorry but as i am new to this can anyone provide me simple steps.

---

### Post by oldfred on 2010-11-01
Windows boots thru a primary partition. Windows will not directly boot your install of win7 in a logical partition. It has moved the win7 boot files to the XP partition. As such grub cannot directly boot win7. If you uninstall XP, you will not be able to boot win7 at all.

To understand how windows works (lots of detail but the pictures explain a lot):
Multibooters, Pictures here worth 1000+ words
[http://www.multibooters.co.uk/multiboot.html](http://www.multibooters.co.uk/multiboot.html)

If you install win7 to a primary partition then there are ways to make windows not see the other install and be separately bootable from grub.

---

### Post by Quackers on 2010-11-01
> **oldfred said:**
> 

To understand how windows works (lots of detail but the pictures explain a lot):
Multibooters, Pictures here worth 1000+ words
[http://www.multibooters.co.uk/multiboot.html](http://www.multibooters.co.uk/multiboot.html)


Nice explanation there, oldfred :-)

---

