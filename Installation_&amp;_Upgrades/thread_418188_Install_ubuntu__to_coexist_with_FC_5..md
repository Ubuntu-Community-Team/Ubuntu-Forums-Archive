---
title: "Install ubuntu  to coexist with FC 5."
date: 2007-04-22
forum: Installation &amp; Upgrades
---

### Post by kunalhs on 2007-04-22
I have Fedora Core 5 ( using 80 GB ) on a 160 GB Hard disk. I want to install Ubuntu Feisty Fawn on the same hard disk.
I want to use Network Install method using Ubuntu repositories on Internet.  I want both FC 5 and Ubuntu to coexist on same Hard disk, and I should be able to choose what to boot.
Is this possible ? 
If not, I can download and install Ubuntu and burn CD. 
But I want both FC 5 and Ubuntu to coexist on same hard disk. Is this possible ?
Thanks for your help in advance.

---

### Post by pepsi_max2k on 2007-04-22
Yeah, should be fine. I'm not sure if Ubuntu gives you any decent partitioning options when you install (didn't look like it...) so probably best to create a seperate partition for ubuntu in feisty. Then when installing ubuntu, chose that paritition to mount "/", it'll automatically use the same swap partition as FC. If you install grub bootloader while installing ubuntu it *should* recognize both os's, though don't take my word for it.

---

### Post by ge_y_q on 2007-04-22
Hi,Where did you get the Ubuntu Feisty Fawn? Is that  Ubuntu 7.04 Feisty Fawn ?

---

### Post by pepsi_max2k on 2007-04-22
> **ge_y_q said:**
> Hi,Where did you get the Ubuntu Feisty Fawn? Is that  Ubuntu 7.04 Feisty Fawn ?

gee, where've you been buddy? :lolflag: 

[http://releases.ubuntu.com/7.04/](http://releases.ubuntu.com/7.04/)

---

### Post by ge_y_q on 2007-04-22
> **pepsi_max2k said:**
> gee, where've you been buddy? :lolflag: 

[http://releases.ubuntu.com/7.04/](http://releases.ubuntu.com/7.04/)


What do you mean?

---

