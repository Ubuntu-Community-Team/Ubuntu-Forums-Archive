---
title: "use swap for install?"
date: 2007-10-25
forum: Installation &amp; Upgrades
---

### Post by jackocleebrown on 2007-10-25
Hi,

My upgrade to Gutsy cam to an untimely death when glx-nvidia failed to install and the upgrade quit half way through. No matter - I was in two minds whether to do a fresh install anyway. 

I always think that it is ashame to use up a CDr just for a single use when installing. I've used a netboot in the past which works quite well but I have had problems with this when installing systems at work and I have to get the netboot installer through the fascist IT proxy. I thought I would try this method [here]("https://help.ubuntu.com/community/Installation/FromLinux") as I have a spare partition on this system.

This seems pretty straight forward and I think I'll use it in preference to netboot (if it works). My question is... would it be possible to use this method on a computer without a spare partition by turning off swap and using the swap partition to temporarily hold the livecd??

Thanks, Jack.

---

### Post by jackocleebrown on 2007-10-28
Thought a bit more about this. Clearly possible but is there any real advantage?? you'd still have to re-format the swap to ext3 (or similar) and then re-create a new swap partition on install which is a pain if your first swap is at the end of the disk. Best solution: make a new 1G partition by slightly shrinking one of your ext3 partitions.

Jack.

---

### Post by kellemes on 2007-10-28
Basically the only thing you need is room for the disk and network access.
You could also use a USB-stick to install it.. pretty cool.

---

