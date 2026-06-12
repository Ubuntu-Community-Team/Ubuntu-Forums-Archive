---
title: "Help Setting up Linux Raid Server"
date: 2011-04-29
forum: Installation &amp; Upgrades
---

### Post by lorewap3 on 2011-04-29
I just built a home computer with 3TB hard drives I wanted to set up in a RAID 5 and load Ubuntu server onto it.

The first thing I did was set up the drives in a RAID 5 using just the motherboard chipset software to do it, so a 'hardware' RAID basically.

I installed Windows first to see if all the hardware works ok (that seemed the easiest way to verify it) and with the exception of the ethernet card (which needed a driver disk to work) everything was plug n' play and worked wonderfully. After that I booted the Windows install disk again to delete the partitions, hoping Ubuntu 10.10 server would create its own.

The problem I'm having is no matter what I've tried (deleting and recreating the RAID 5 setup, departitioning the drives), whenever I try to install Ubuntu it won't recognize the RAID as a valid disk. Ironically, it did at first, because I installed windows to verify the hardware. The ethernet card wasn't working automatically in the Ubuntu setup, (although it found the unformatted RAID drive), so I installed windows and figured out it was just the drivers that needed to be installed. 

So now when I try to install Ubuntu, it finds the ethernet card perfectly and connects to the internet during the installation...but that actually stinks because it's telling me it's still accessing the drivers from the drives that I thought I formatted. Once it gets to the storage part of the installation afterwards, it can't find the RAID drive anymore. I tells me to choose a disk from the list, but the list is blank. So I can't install on it.

If I remove the RAID entirely and just keep the drives as 3 separate IDE drives, it finds every drive perfectly and can install to either one I choose. But I don't want this, I definitely need them RAIDed.

I would appreciate any advice at all on this, or even suggestions on another way of doing it. I've heard many people claim to dislike hardware RAIDs for linux servers and recommend using a software RAID instead. I am new to either, so I'd be happy to consider a software RAID if I knew it would be better/easier.

Any suggestion on a distrobution would be nice, too. I think I like the KDE interface, making me consider Kubuntu, but primarily I just want a server with the trimmings to access it from afar...LAMP,Email,SSH, and Remote Desktop.

Thanks for any advice!

Will P.

---

