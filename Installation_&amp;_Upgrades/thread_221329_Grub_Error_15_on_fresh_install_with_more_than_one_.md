---
title: "Grub Error 15 on fresh install with more than one drive."
date: 2006-07-22
forum: Installation &amp; Upgrades
---

### Post by copilot on 2006-07-22
The Hardware    - DFI Lanparty UT NF4 939, 4x WD2500JS.

The Software    - Ubuntu, Kubuntu and Xubuntu 6.06

The Error       - Grub Error 15

The Particulars - The installation will work fine if I only have one drive plugged in. I can install and use it without a hiccup. I can add additional IDE drives and mount them without a problem. If however I plug in any other sata drives the whole thing comes crashing down around my ears. This really kills my oppotunities to actually use the drives in a mirror as I planned to do when I bought them. I'm also going to ask around in the DFI forums, I suspect the board is playing games with my drive numbering. Any experience with this issue? I want YOUR feedback. Thanks in advance fellow ubuntu users!

---

### Post by theconley on 2006-07-22
Yes, I had a similar problem with grub.

I bet you are using sd0 (or whatever that grub syntax is).

Use hd0, treat it like an IDE.

Yes, grub is stupid.

~Conley

---

