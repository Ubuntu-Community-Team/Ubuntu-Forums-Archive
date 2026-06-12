---
title: "Partition shrinking - installing Hardy."
date: 2007-12-20
forum: Installation &amp; Upgrades
---

### Post by Edho on 2007-12-20
Downloaded Gparted LiveCD.

Booting with it seems ok.
Gparted sees my partitions.

- hda 7.8 MB  unreconnised  ??? don't know were it comes from.

- sda  240 GB ( Gutsy on it ) + a swap partition.

I will try the 240 MB partition to shrink for installing Hardy pre-release version.
In dualboot Gutsy ---  Hardy.

I suppose only shrinking is ok ?
Gutsy will stay on a smaller partition and bootable ?
The remaining partition will be unallocated ?

Hardy will during install take care on the unallocated part ?(formatting, install)

Will the swap used by both systems?

Last Question..
Can one with the beta-versions upgrade to the newer version, or you have to do a fresh install, with each newer version?

Thank You.

---

### Post by forestpixie on 2007-12-20
when I installed gutsy tribe I did exactly as you propose - shrank my partition and freed up 15 Gb - installed gutys to that and all was fine

used the same swap for both if I remember - even if I didn't I could have

and when gutsy was released I upgraded it as wwll, although I later reinstalled it fresh

---

### Post by PmDematagoda on 2007-12-20
The unallocated space is the MBR, so do not do anything to it.

The SWAP can be used for both systems(I use the swap spaces of 3 different Ubuntu OSes on my Hardy OS:)).

You do not need to do a reinstall at every release of Hardy, just an upgrade will do(I do not think it is an upgrade at all, just some updates).

And shrinking your partitions should not be a problem at all.

---

### Post by Edho on 2007-12-20
Thank You both.

---

