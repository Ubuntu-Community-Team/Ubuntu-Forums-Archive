---
title: "Dell PowerEdge 2900"
date: 2007-03-15
forum: Installation &amp; Upgrades
---

### Post by vdpollm on 2007-03-15
Hi there,

I have a new PE2900 with 3x500GB SATA drives, with PERC 5.0.1.

I am trying to install 6.06.1 LTS Server (have tried both 32 and 64bit). [LTS because this will be a procuction box]

The installation goes well, until the reboot. Where it gets stuck

Googling got me a few ideas about modifying the kernel before reboot, which i tried but did not help and i got a grub 21 error.  It seems that the problem is with the default kernal that comes with 6.06.1 LTS.

The way I see it, I have three options, in order of preference:

1) Change the ISO image of 6.06.1 LTS to have one of the latest kernels that will work, 
2) Upgrade to a new kernel before reboot
3) Try a FAI for 6.06.1 LTS with the newest kernels.

The thing is I don't know how to do any of the above, so if anyone can point me somewhere to go and look for step by step instructions, i will be gratefull.

Regards

Marc van der Poll:mad:

---

### Post by vdpollm on 2007-03-15
It seems that the following link refers to and sorts the problem:

[http://www.ubuntuforums.org/showpost.php?p=1575949&postcount=20](http://www.ubuntuforums.org/showpost.php?p=1575949&postcount=20)

I am trying it now and will let you know if it works

regards

Marc van der Poll

---

### Post by vdpollm on 2007-03-15
hooray!!!!

The link above works beautifully.

I am now going to try it with a few modifications, like using LVM, etc.

But the problem has essentially been solved - i will continue to worship at the temple of Ubuntu (hehehehe):lolflag:

---

