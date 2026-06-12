---
title: "is this really necessary?"
date: 2007-07-23
forum: Installation &amp; Upgrades
---

### Post by bullgr on 2007-07-23
hi...

in a fresh install of ubuntu feisty 64bit, my two ntfs disks are sawn in /dev folder as sd*
so, i install ntfs-3g and done the needed configuration in fstab to automount the ntfs drives for read & write.

after 1,5-2 months there was a kernel update. after the update the ntfs drives was no more automounted.
i found that after the kernel update the ntfs drives was sawn in /dev folder as hd*.
so i change again the needed configuration in fstab to automount the ntfs drives for read & write.

the last week i done the last kernel update... and guess what happens... right!!! the disks are again sawn in /dev folder as sd*.
so i change again the needed configuration... bla,bla,bla,bla,bla.

my question: is this really necessary? where is the problem? is it my problem (motherboard?) or in kernel development?

have other users too this (how to name it?) deja vu?

---

### Post by madmetal on 2007-07-24
> **bullgr said:**
> hi...


i have searched launchpad bugs and didnt find something similar..
kernel updates are from synaptic or custom made kernels?

---

### Post by kidders on 2007-07-24
Hi there,

There do seem to be a small number of situations where the naming conventions used for particular devices is a little uncertain/inconsistent. I suppose it could be down to changes to the Ubuntu kernel configuration or udev rules. Either way, it's bound to be a bit irritating!

Do bear in mind however that, just because a kernel update becomes available, that doesn't automatically mean you should blindly install it. In the specific case of updates that can fundamentally impact the way your box operates, it's good practice to at least check out what's been changed. If, on investigation, you were to discover for instance that the only alteration is a bugfix for weird hardware you'd never heard of, it could be worth at least *considering* not installing the update right away.

Your particular problem may *seem* perfectly straightforward, but the more I think about it, the more I realise you'd want quite an eye to immediately spot what happened! Well done. :-) As a piece of practical advice, I suggest uninstalling any old kernels that use the "wrong" device naming convention for your hardware. The reason I say that is, should you ever need to boot using a kernel other than the most recent one on your system, it would be nice to _know_ that your /etc/fstab will be compatible with it.

To answer your question directly: Is such name fiddling really necessary? NO! I can't imagine what the reason for causing you this headache was, but hopefully it ends with your most recent upgrade.

[COLOR=Gray]**Edit:** Oops... hello madmetal![/COLOR]

---

