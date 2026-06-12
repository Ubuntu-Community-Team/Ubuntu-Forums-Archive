---
title: "Ugrade hoary &gt; breezy, but no new kernel!"
date: 2006-04-06
forum: Installation &amp; Upgrades
---

### Post by johnpipe on 2006-04-06
Hi, I upgraded from the CD install of hoary, to breezy via synapatic.  My system has 6 distributions, including ubuntu, and ubuntu is not the primary system. Booting is configured by lilo on the primary partition under redhat 6.1.
When I finished, I did not have the 2.6.12-10 kernel installed; must have answered the kernel install prompt incorrectly.

I tried installing the new kernel via synaptic, but I'm doing something wrong, because when I get done and try to boot via the new kernel from lilo, instead of initrd booting ubuntu, it tries to boot redhat instead, with the 2.6 kernel, and all the text messages have lots of extra characters around the screen, looks quite messy!

I've checked my boot directory for ubuntu on the redhat partiton v.s. the /boot/ dir on ubuntu on hdb9, and everything there checks out, identical for both.

I've been searching around, but haven't found info on kernel upgrading from the package, everything I've found seems to concentrate on custom kernel building and installing with dpkg; I build my redhat 2.2.x kernels custom, since it's my main working distribution, and I'm not experienced installing packaged kernels with a gui. 
 
ubuntu breezy will still boot OK with the original installed hoary kerenel (2.6.10-5).

Does anyone know where there is good howto info on upgrading this kernel from package with synaptic?  Or, what answers to give to the install script prompts to get a correct installation?  Unbuntu lives on hdb9, and redhat lives on hda, the bootable partition.
 
If I can't get this kernel installed properly, I may have to download the breezy iso and re-install, which I'd like to avoid!

Thanks in advance,

johnpipe

---

