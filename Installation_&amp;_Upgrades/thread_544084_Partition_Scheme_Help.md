---
title: "Partition Scheme Help"
date: 2007-09-05
forum: Installation &amp; Upgrades
---

### Post by progger on 2007-09-05
Hi everyone,

I would like some advice on how to set up the best partitioning scheme for my needs. I checked a lot of threads on partitioning schemes but as these are system/needs specific I am making my own thread for advice.

My harddisks:
150GB HD (OS/Apps)
500GB HD (Storage)

Currently I have Ubuntu 7.04 64 bit installed on the 150GB HD (swap partition + rest of disk = Ubuntu). I don't mind reinstalling / repartitioning.

My needs:

[B]Option 1
Ubuntu 7.04 64 bit + Ubuntu Studio[/B]
How should I set up my 150GB HD to accomodate both? I am not sure how many and what type of partitions to create for these. Size is not really important, I am mainly curious as to what type of partitions (primary vs extended) and how many I would need to have both of these OS installed. The reason I want both is that Studio is only a 32 bit OS currently. I am really hoping they will release a 64 bit version soon.

[B]Option 2 (desired)
Ubuntu 7.04 64 bit + Ubuntu Studio + Gentoo[/B]
I would also like to know what sort of partitioning scheme would be best to have both Ubuntu 7.04 64, Ubuntu Studio and also Gentoo. My first foray into Linux was actually Gentoo but I did not feel I had a deep enough knowledge to truly set it up as I like, so I would love to have it installed and play around with it. I am hoping some Gentoo users here may be able to provide me with some advice. The last time I used Gentoo it installed itself on 3 primary partitions. Do they have to be primary partitions, or could this be done on 2 or even 1?

Thank you in advance for any advice or suggestions you can offer me. If you can also direct me to some in-depth online information about what sorts of partitioning/drive requirements these distros require I would really appreciate it.

---

### Post by progger on 2007-09-06
Hm.. bumped down to page 4.. 23 views no replies. .nobody has any suggestions on this? Should this be in another forum?

Maybe I should simplify this.. What partitions does Ubuntu have to be on, do I have to install it on two primary partitions or are there other options..

Thank you

---

### Post by leedsdevil on 2007-09-06
sorry to hear no one replyed but this is an ongoing question . i know i have asked my self . if u want to run more than one O/S (linux make sure you share the swap file) then just name your other partions / /home /linux swap . make sure you use ext 3 for primary . im not sure if i was able to help but also try gparted for partions

---

### Post by progger on 2007-09-06
Well thank you for your response leedsdevil, but sadly that does not answer my question. I am inquiring about the number and types of partitions I need to have both Ubuntu 7.04 and Ubuntu Studio installed, or Ubuntu 7.04 and Studio and Gentoo (ideal). 

Thanks anyway :) Maybe someone else can provide some information...........

---

### Post by SpiritIsReality on 2007-09-09
howdy
no specific info, just some links

[https://help.ubuntu.com/7.04/advanced-topics/C/index.html](https://help.ubuntu.com/7.04/advanced-topics/C/index.html)
[https://help.ubuntu.com/7.04/installation-guide/](https://help.ubuntu.com/7.04/installation-guide/)
[https://help.ubuntu.com/7.04/installation-guide/i386/partitioning.html](https://help.ubuntu.com/7.04/installation-guide/i386/partitioning.html)

[http://www.debian.org/releases/stable/installmanual](http://www.debian.org/releases/stable/installmanual)
[http://www.debian.org/releases/stable/i386/](http://www.debian.org/releases/stable/i386/)
[http://www.debian.org/releases/stable/i386/apc.html.en](http://www.debian.org/releases/stable/i386/apc.html.en)

I'm workin' on getting this sorted too

trails

---

### Post by SpiritIsReality on 2007-09-09
there's this guide for multi-boot setups
[http://www.justlinux.com/forum/showthread.php?t=147959](http://www.justlinux.com/forum/showthread.php?t=147959)
then there's virtualbox
[http://ubuntuforums.org/showthread.php?t=340113&highlight=virtualbox](http://ubuntuforums.org/showthread.php?t=340113&highlight=virtualbox)
[http://en.wikipedia.org/wiki/Virtualbox](http://en.wikipedia.org/wiki/Virtualbox)

---

### Post by SpiritIsReality on 2007-09-14
howdy
found what we're lookin' for
[http://ubuntuforums.org/showthread.php?&t=282018&](http://ubuntuforums.org/showthread.php?&t=282018&)

trails

---

