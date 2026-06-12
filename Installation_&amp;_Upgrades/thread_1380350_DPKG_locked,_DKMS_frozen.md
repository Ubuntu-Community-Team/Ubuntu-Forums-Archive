---
title: "DPKG locked, DKMS frozen"
date: 2010-01-13
forum: Installation &amp; Upgrades
---

### Post by mcdjork on 2010-01-13
I tried to switch from the broadcom firmware extracted driver to the STA and something went wrong along the way. My system locked up, and when I restarted, Synaptic told me I had to run 

sudo dpkg --configure -a

When I do this, I get this:

First Installation: checking all kernels...
Directory for kernel 2.6.31-17-generic found in /lib/modules
Adding Module to DKMS build system

And it sits there indefinitely. Now I have no wireless and I can't install anything. Any ideas?

---

