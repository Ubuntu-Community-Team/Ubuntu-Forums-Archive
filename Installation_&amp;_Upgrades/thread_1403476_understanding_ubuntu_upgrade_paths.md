---
title: "understanding ubuntu upgrade paths"
date: 2010-02-10
forum: Installation &amp; Upgrades
---

### Post by keithbunt1 on 2010-02-10
I'm trying to understand how the different versions of ubuntu fit together, and how to upgrade from one version to the next without a complete re-install.

Let's say I've got a machine with ubuntu 8.04 on it.  And now I've decided to ugprade.  What makes 8.04, 8.04?  What makes up the distribution?  A specific kernel version and default packages?  If I replace the kernel with a new version, is it no longer 8.04?  If I want to upgrade to 9.10, will synaptic package manager allow me upgrade from 8.04->9.10?  What will it replace?

I've got a different machine which is a core i3(clarkdale) with integrated graphics.  It requires Lucid and a replacement PPA kernel to function correctly.  I'd like to stay and keep as mainline as possible and still make sure my hardware is supported.  Once Lynx is released (with 2.6.32) -- it still won't have the 2.6.33 required kernel.

If I'm running the 10.04 alpha/beta/whatever pre-release stage its in, can I just continue to upgrade packages as they come available?

Thanks

Keith

---

### Post by iskarion on 2010-02-10
Running a mainline kernel shouldn't prevent you from upgrading to the next Ubuntu version. I have been running Kubuntu 9.04 with a custom kernel and the upgrade to Kubuntu 9.10 did work just fine.

I'm also planning on building a i5/Clarkdale based system running Kubuntu 10.04 + 2.6.33 (not only because of the improved Clarkdale support, but also due to TRIM support) and I'm certainly not concerned about the upgrade path to Kubutnu 10.10.

After all installing a more recent kernel version doesn't replace your old kernel (unless you explicitely uninstall it). The two kernel versions exist side by side and you can always choose if you want to boot the one or the other.

---

### Post by atmartens on 2010-02-26
Does this mean that under 10.04 we will have the choice of 2.6.33 in addition to 2.6.32?  How does one go about installing a non-standard kernel version, besides compiling?  I'm also interested both in Clarkdale support and Trim support.

---

