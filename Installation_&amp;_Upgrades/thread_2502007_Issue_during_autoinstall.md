---
title: "Issue during autoinstall"
date: 2024-10-29
forum: Installation &amp; Upgrades
---

### Post by deathpickle2 on 2024-10-29
Hello.

I have a Ubuntu server up and serving PXE installs on my network and as a whole, the autoinstall (well cloud-init) works fine .. however I get the below messages towards the end of the process:

start: subquity/Network/_send_update: CHANGE enp1s0
finish: subquity/Network/_send_update: CHANGE enp1s0

The above messages repeat about 10 times and continue on, but takes up a lot of time to complete and I am unsure what is causing it.  Can anyone point me to what is wrong and what to do to resolved? The config file I use is pretty limited.. it seems like it's resetting the network adapter for some reason at that point.

This is on a VM (if that matters) but as I said other than the message and it's process slowing things down quite a bit, it over all works.

Thanks.

---

