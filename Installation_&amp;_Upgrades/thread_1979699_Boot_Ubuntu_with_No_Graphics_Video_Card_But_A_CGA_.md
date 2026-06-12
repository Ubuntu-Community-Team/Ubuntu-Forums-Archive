---
title: "Boot Ubuntu with No Graphics Video Card But A CGA Text-mode Video Card"
date: 2012-05-13
forum: Installation &amp; Upgrades
---

### Post by fredfsh on 2012-05-13
Hi,

I'm deploying Ubuntu as a guest OS on [Palacios the VMM]("http://www.v3vee.org/palacios/") and encountered the following error when booting:

[B]graphics initialization failed
Error setting up gfxboot
boot:[/B]

And the prompt "boot:" even repeated endlessly and went unstoppable. The reason behind this may be that the VMM is configured as not having any Graphics video card but a CGA text-mode video card. I'm using *ubuntu-12.04-server-amd64.iso*.

My question is that, **a)** is there any option for me to boot Ubuntu/Ubuntu Server with this hardware configuration, or **b)** do other distribution variants like Lubuntu work? Thanks.

Best wishes,

fredfsh

---

