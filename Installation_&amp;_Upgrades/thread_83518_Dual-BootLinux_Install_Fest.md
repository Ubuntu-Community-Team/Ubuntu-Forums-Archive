---
title: "Dual-Boot/Linux Install Fest"
date: 2005-10-28
forum: Installation &amp; Upgrades
---

### Post by skyace888 on 2005-10-28
Hey guys!  I have been dabbing in Linux and Ubuntu for a few months and will be hosting a Linux Install Fest on my college campus in a week.  I mainly use the Ubuntu Live CD for testing and troubleshooting Windows machines.  Anyways, I would like to know the best way to dual-boot Ubuntu on a typical NTFS Windows XP machine.  How can I setup the partitions, configure the boot loader, etc.  I need to make sure I have a routine down that works so I don't screw up many computers.

Thanks,
Al

P.S.  If anyone here lives in the South Florida area and would like to attend the Linux Install Fest, please email me at [email]furmansk@nova.edu[/email]. We'd love to have you!

---

### Post by darth_vector on 2005-10-28
if windows is installed on the disk you will have to downside its partition size. i've been told that partition magic is a good tool for this and costs about $90.

if there is enough space for the ubuntu install already (or if you have already resized your windows partition(s)) then thibgs are pretty easy. you will need at least 2 partitions, but i recommend 4.

/                    root partition. make it reasonably big (make it a logical partition)
swap             about twice the size of the machines RAM (make it a logical partition)
/home           your files, you decide on the size (make it a logical partition)
/boot             make it a primary partition and tick the box that says "make this partition bootable" or words to that effect

when grub (GRand Unified Bootloader) is being setup, elect for it to be installed in the Master Boot Record (MBR).

Good luck :)

---

### Post by aysiu on 2005-10-28
A combination of these tutorials should help:

[http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)
[http://www3.telus.net/linux4u/ubuntu.html](http://www3.telus.net/linux4u/ubuntu.html)

The first is a typical dual-boot install using FAT32.
The second addresses NTFS specifically (but only the resizing part, not the dual boot in general).

However, should you really be hosting install fests if you don't know what you're doing?

---

### Post by xequence on 2005-10-28
It sounds really cool =) Though... Florida = far away ;)

Basically, id say its just best to resize your NTFS partition. Make an ext3 partition for linux, mount it as / and then make a 512 MB swap partition at the end :) You can also make a FAT partition to share files in between windows and linux.

It will just ask you if you want to install the bootloader, and you can click yes or no.

---

### Post by skyace888 on 2005-10-28
thanks for the quick replies guys.  i will take a look over the things that you posted and see if there is a computer that i can make a test on.

> 
However, should you really be hosting install fests if you don't know what you're doing?

i am hosting the event because i am the president of the computer organization on campus.  there will be other linux users on-hand; however, i wanted to try and learn as many of the needed procedures myself.

---

### Post by aysiu on 2005-10-28
[QUOTE=skyace888]
i am hosting the event because i am the president of the computer organization on campus.  there will be other linux users on-hand; however, i wanted to try and learn as many of the needed procedures myself.[/QUOTE] Cool. You had me worried there. I wish you the best.

---

### Post by skyace888 on 2005-10-28
no problems man.  i appreciate your interest in wanting me to have a successful event.  would you happen to know if i will be getting the 15 cds that i ordered in time for the event?  i placed the order around october 18th.  also, are there any kind of manuals or materials that may be sent out to help promote the event and the Ubuntu project?

---

### Post by aysiu on 2005-10-28
[QUOTE=skyace888]no problems man.  i appreciate your interest in wanting me to have a successful event.[/quote] If I were in Florida, I'd join you.  

> would you happen to know if i will be getting the 15 cds that i ordered in time for the event?  i placed the order around october 18th. I highly doubt it. Mine took two months, and I've heard similar times for other people (regardless of geographic location).  

> also, are there any kind of manuals or materials that may be sent out to help promote the event and the Ubuntu project? I'd link them to these forums, honestly. The Ubuntu Guide is still being updated; otherwise, I'd give them [http://www.ubuntuguide.org/](http://www.ubuntuguide.org/)

---

