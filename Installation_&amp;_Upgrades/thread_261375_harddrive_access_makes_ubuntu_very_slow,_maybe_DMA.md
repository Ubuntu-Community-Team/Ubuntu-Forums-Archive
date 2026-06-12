---
title: "harddrive access makes ubuntu very slow, maybe DMA problem?"
date: 2006-09-20
forum: Installation &amp; Upgrades
---

### Post by Solid1986Snake on 2006-09-20
Hi Guys,
first off all I'm sorry for my bad English, i'am from Germany ans will try to describe my problem the best way I can. I tried in on ubuntuusers.de the german ubuntu Forum, but nobody could help me, maybe you guys here can.

My Problem:

Yesterday I downloaded the Ubuntu Updates from the last 4 weeks, everything went fine so far, but after a reboot linux is very slow! The first time it bootet there was a normal harddrive scan because it was mounted 21 times without being checked and it took 20 minutes for 12 gb!! In Gnome every program is running fine, when its loaded in Ram, but when it loads something form harddisk, or even when the program is started first time the whole machine slows down! Even the Cursor is stucking! I tired an older Kernel, but theres the same problem! I*ve installed the newest ati fglrx driver and it got a little bit better, but nor really its no fun to work with the machine! Just an Example, I can't hear music and write at the same time because everything is stucking!

I tried to enable dma, because when I type sudo hdparm -d /dev/hda in console it says 
 using_dma    =  0 (off)
When i try to enable it it says permission  denied, even if I use sudo, so I tried to enable it in /etc/hdparm.conf, but no change, after boot the console message is still the same, dma = 0!

Maybe this is the Problem may be not! I hope you have an idea!

Greetings Solid

My Machine:

Targa Traveller 826T Notebook
Ati Xpress 200 Chipset
Ati Radeon X700 Mobility
AMD Turion Mt-32
1 gb ram

installed newest ati fglrx  driver from ati homepage and newest ubuntu kernel is in use!

---

