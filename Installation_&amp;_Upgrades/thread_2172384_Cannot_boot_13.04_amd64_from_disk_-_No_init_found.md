---
title: "Cannot boot 13.04 amd64 from disk - No init found"
date: 2013-09-04
forum: Installation &amp; Upgrades
---

### Post by Talleyrand on 2013-09-04
I installed Ubuntu 13.04-desktop-amd64 into my ASUS P5LD2-SE, with 4 GB of RAM, on a Samsung 250 GB HD. 
It was a "pure" installation (no Windows or dual-boot involved) from an USB drive, checked with winMd5Sum in another machine. 

After installing and restarting, I got the following message: Kernel panic - not syncing: No init found. Try passing init= option to kernel. See Linux Documentation/init.txt for guidance. It's worth to mention that in trying mode, i.e. from my USB drive, Ubuntu 13.04 runs smoothly and fine. I'm even able to reach my Ethernet net, printers in that net, and other Windows and Mac computers. But I'm not being able to boot from the disk and therefore keep my configuration.

I looked at the document and checked my architecture to see if it's supported, and it seems it is, something that is also confirmed by Ubuntu's behaviour in trying mode. 

After trying a different disk for the installation, and getting the same results, I went to the Installation Forum, and ran across the boot-repair utility. I installed it in Ubuntu while running in trying mode, and executed it according to the instructions, to perform the Recommend Repair. After that, I reboot I got the same frustrating results. 

I'm totally new to Ubuntu (used to have a few years ago Ubuntu 8.0 sharing a machine with Windows XP and it worked fine), and when I got the boot info I couldn't make head or tail of it. 
So, still following the directions from the boot-repair utility, here I am in search of a wiser soul willing to give me a little help with this. =)

The following are the links passed by the boot-repair utility with my boot info, for both disks used:

1) For the Samsung 250GB
[http://paste.ubuntu.com/6064031/](http://paste.ubuntu.com/6064031/)

2) For the Seagate 20GB
[http://paste.ubuntu.com/6063973/](http://paste.ubuntu.com/6063973/)

TIA for any suggestion or recommendation

Cheers

Talleyrand

---

