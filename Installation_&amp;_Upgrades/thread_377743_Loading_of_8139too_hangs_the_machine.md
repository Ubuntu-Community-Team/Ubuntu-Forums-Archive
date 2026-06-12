---
title: "Loading of 8139too hangs the machine"
date: 2007-03-06
forum: Installation &amp; Upgrades
---

### Post by tsaarni on 2007-03-06
I'm trying to install Ubuntu on a PC that hangs when loading 8139too kernel module (driver for Realtek ethernet chip). I've tried even with the latest development snapshot CD of Feisty.

I can actually get the system installed with an alternate install CD by [removing 8139too.ko from the filesystem]("http://ubuntuforums.org/showpost.php?p=1844744&postcount=18") before it gets loaded. Unfortunately the machine then hangs on first boot when it tries to load 8139too from the initrd image.


Is there any possibility of **preventing 8139too from loading at the boot?**  Possibly some boot parameter?


The machine is a new Philips Freevents X55 laptop and from what I've [read about this problem]("http://www.linuxquestions.org/questions/showthread.php?t=475612") the 8139too driver would need to be compiled with CONFIG_8139TOO_OLD_RX_RESET and possibly CONFIG_8139TOO_PIO enabled in order to boot successfully.

---

### Post by agent_paul on 2007-04-23
Hi Tsaarni, ive also got this problem with the latest release of ubuntu 7.04. I've got a Philips Freevents X52 though.

I've tried to install openSuse on this laptop too and it also hangs during load up. So at the moment i cant really play with feisty fawn on this laptop :((

---

### Post by ppan76 on 2007-04-24
THis is a known problem. To install Ubuntu use the link below for instructions:

[http://ubuntuforums.org/showpost.php?p=1844744&postcount=18](http://ubuntuforums.org/showpost.php?p=1844744&postcount=18)

You guys are lucky I responded I spent like 50 hours trying to get this to work.

You need to remove 8139too.ko from the /target/libs/modules/kernel version/kernel/drivers/net/

---

### Post by agent_paul on 2007-04-25
Hi there ppan76,

thanks for the link. i'll give it a go once im free. did you manage for sort out out completly in the end?

---

### Post by ppan76 on 2007-04-25
Feisty is working great.  I currently dont have the network card enabled.  But I dont need it as I have wireless.  

I heard some people compiled a new Kernel to get the 8139 card to work.  

So follow the instructions to install linux.

---

