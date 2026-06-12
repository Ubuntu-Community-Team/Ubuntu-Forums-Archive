---
title: "cold cloning of physical ubuntu machine to work in vmware"
date: 2011-02-17
forum: Installation &amp; Upgrades
---

### Post by step0ut on 2011-02-17
Hi,

I have a laptop running ubuntu and used it for several years, now I got a mac
and want to transfer the entire linux machine in the mac as a virtual machine.
I used partimage and made an image of the whole partition. Then in 
 vmware fusion I have an ubuntu virtual machine I enlarged its disk to 80Gb
and then booted it with an ubuntu live cd and with gparted made an extra ext3 partition.
With partimage then within the live cd I restored my original ubuntu image to this partition.
I mounted the partition (still inside the live cd which is booted in the virtual machine)  and I can
indeed see all my files from the original ubuntu machine.
Now I feel I am close, but I stuck in making it to boot.
I tried to use cfdisk still from inside the live cd and I could change this partition to be bootable,
however when I restart it, it still boots to the ubuntu that the virtual machine came with which is
in one of the other partitions even though I specified in the cfdisk that partition no to be bootable. 

So my questions are: 1) how can I make it to boot from this partition and 
2) I suspect I need to change some configuration/init files in the system that I transfered, could you guide me on which ones?

Thanks

---

