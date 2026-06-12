---
title: "Partitioning layout is messed up, possibly fatally"
date: 2008-02-25
forum: Installation &amp; Upgrades
---

### Post by DJ Wings on 2008-02-25
Here's how my partitioning layout should look:
-sda1-3: various small VFAT partitions
-sda4: logical volume
-sda5: swap (2GB)
-sda6: Arch (soon to be replaced by Xubuntu 8.04a if I get this solved) (10GB)
-sda7: Zenwalk (10GB)
-sda8: SimplyMepis (10GB)
-sda9: /home (40GB)
And here's how it *does* look, according to both Xubuntu 7.10 and Fedora 8 Live:
-sda: completely unused, 80GB
I think that if I try to make any changes to my partition mapping, there will be data loss, and lots of it. Could someone help me? It all looks OK from on Mepis.
UPDATE: I can mount the partitions, but GParted still doesn't recognize them (from any distro), which is the real problem.

---

### Post by DJ Wings on 2008-03-26
I managed to install PCLinuxOS successfully (other OSes boot, but PCLOS turns up a kernel panic, but who cares about PCLOS?), but Ubuntu still won't recognize that I have any partitions at all. Can someone help me? This problem is driving me crazy.

---

