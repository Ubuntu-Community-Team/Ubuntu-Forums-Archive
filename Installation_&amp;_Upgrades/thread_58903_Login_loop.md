---
title: "Login loop"
date: 2005-08-22
forum: Installation &amp; Upgrades
---

### Post by Billyum on 2005-08-22
After a good deal of shopping around, today I installed Ubuntu in a dual boot on my Toshiba Satellite 2805 laptop. I logged on, added my printer (HP OfficeJet G95) with ease, and went to [www.grc.com](www.grc.com), where I discovered that I was stealthed, except for answering pings. So far, so good! In fact, Ubuntu was the only liveCD Linux that I could correctly configure my printer with.

All of this took about 10-15 min. But then the display went blank and came back up at the Gnome login screen. Now it does that every 80 sec. or so, whether I do anything or not. 

Please help!

Many thanks,

Bill

P. S. WindowsME takes up 3114 MB in the first partition, Ubuntu takes up 2470 MB in the second, with a swap file of 141 MB in a logical partition. I have 192 MB of RAM with a Celeron processor running at 650 MHz.

Also, I have a Wacom Graphire Tablet connected by USB, and a 7.6 GB TravelStar external HD connected by a card. All of the hardware worked well under the Ubuntu liveCD, and seems to work well now.

---

### Post by Billyum on 2005-08-22
Later thoughts:

141 MB is probably too small for a swap partition. The installation program created it and the main Linux partition. It made the suggestion and I OKed it. A larger swap partition would probably have choked the main partition, hindering or preventing installation.

Windows uses a 384 MB swap file. I am thinking that I could make a logical partition for it, and it could be shared between Windows and Linux. It seemed like the partition program used in installation would allow that, and that would free up the 141 MB partition. Or maybe I could increase the current swap partition at the expense of the Windows main partition and let Windows use it.

Back to the loop problem. Why did it not appear right away? What of crucial importance happened in those 10-15 minutes? My guess is that Firefox increased its cache, choking off memory.

What can happen in 80 sec. to crash Gnome, when the user is just sitting at the logon screen? Well, maybe some buffer is filling up and overflowing? That might not happen if there is plenty of memory. Have I accidentally discovered a bug?

Bill

---

### Post by Billyum on 2005-08-23
Update:

Last night I tried setting up for a shared swap space with Windows, using, ahem, Partition Commander 1.0.3! In the process I made the Linux swap partition visible to Windows and made Grub unusable. 

So I just clobbered all partitions except the main Windows one, almost making it unbootable in the process.

As of now I have no problems with Ubuntu, hehe.

Bill

---

