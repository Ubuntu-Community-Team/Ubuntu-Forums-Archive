---
title: "PAE not configured by installer"
date: 2011-07-01
forum: Installation &amp; Upgrades
---

### Post by jpapa on 2011-07-01
I just did an 11.04 install onto a thinkpad w520 with 16 GB RAM.

free - m shows 3.5GB

(as does top)

browsing help/forums it seems the 11.04 installer should have detected my RAM and installed the proper kernel.

any feedback on how to rectify would be appreciated.

everything functionally seems great, just missing most of my RAM.

I went with 32 bit ubuntu because most people (including canonical on their download page), recommend it. I may move to 64 bit, but would like to solve this for 32 bit first.

---

### Post by zvacet on 2011-07-06
Go to the synaptic package manager and in search box type linux-image and you will find linux-image 2.6.38.8-generic-pae:Install it and you should be fine.

---

