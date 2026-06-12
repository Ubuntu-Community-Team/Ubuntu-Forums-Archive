---
title: "Upgrading with an ISO"
date: 2005-06-19
forum: Installation &amp; Upgrades
---

### Post by jnoreiko on 2005-06-19
Just a tip I thought I'd share...

If you don't fancy creating yet another coaster, or you're waiting for the proper CDs in the post, you can use a mounted ISO image as a repository.

Mount it with
```
sudo mount -o loop ubuntu-5.04-install-i386.iso /media/cdmount
``` (thanks HappyFool from #ubuntu for that one)

and then just add the URI file:///media/cdmount to Synaptic, with 'hoary' for the distro and 'main restricted' for the sections.

I've not actually run the upgrade yet, but on refresh Synaptic sees the packages from the ISO.

---

