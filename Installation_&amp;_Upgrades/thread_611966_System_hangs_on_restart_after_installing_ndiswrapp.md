---
title: "System hangs on restart after installing ndiswrapper for Atheros 5707EG"
date: 2007-11-13
forum: Installation &amp; Upgrades
---

### Post by gregmundy on 2007-11-13
Hi, 

I recently bought an Acer Extensa 4620Z notebook and installed Ubuntu 7.10. After lots of trial and error, I finally got the internal wireless card working (it happens to be an Atheros 5707EG) using ndiswrapper...from what I understand, there's no support for this model via madwifi as yet. 

The problem that I have is that whenever I restart Gutsy, it hangs at the Acer startup screen; however, if I shut the machine down, it will reboot just fine. I did notice that my wireless card wasn't detected until after I had disabled the Acer disk recovery feature in the BIOS (pretty odd). Any suggestions?

---

### Post by Lackofabox on 2008-05-12
I've got the same problem.  I have had this with both Gutsy and Hardy.  I was hope'n to ditch ndiswrapper with Hardy, but no luck with madwifi and atheros yet.

I've got a Toshiba Satalite A-215-S5818.  If I restart it hangs towards the end of the Toshiba Bios page.

Here's the output to ndiswrapper -l

net5211 : driver installed
	device (168C:001C) present (alternate driver: ath_pci)

---

