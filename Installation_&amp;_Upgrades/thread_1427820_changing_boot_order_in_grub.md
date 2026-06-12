---
title: "changing boot order in grub"
date: 2010-03-12
forum: Installation &amp; Upgrades
---

### Post by dodderer on 2010-03-12
I run Win 2000 and Ubuntu 8.04 on an Acer Veriton after some fiddling I lost windows from the boot list. After several unsuccessful attempts at editing the grub menu list and using startup manager I did the following ::
 1. in Sum entered Windows as the default starter
 2.changed time out And Then

#Code:

sudo apt-get update

Then after that finished, 'sudo apt-get upgrade'.
Code:

sudo apt-get upgrade

then re-installing GRUB to MBR with 'sudo grub-install /dev/sda'.
Code:

sudo grub-install /dev/sda

I do not know exactly what happened but I got the result I was after .Seems to me sum cant manage on its own.

---

