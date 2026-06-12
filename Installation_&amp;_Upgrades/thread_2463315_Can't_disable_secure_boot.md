---
title: "Can't disable secure boot"
date: 2021-06-08
forum: Installation &amp; Upgrades
---

### Post by brooksmm on 2021-06-08
I can not boot linux as I can not disable the secure boot. This is a computer I had been trying to dual boot, but now we have removed the one drive with win7 so that there is only a drive with linux, and the native hard drive that is inaccessible/locked

It seems like I'm getting closer to being able to boot up linux, but the remaining problem is that I can no longer disable secure boot. The option is there but it cannot be selected or changed. In addition, I have already set an administrator password (there is no supervisor option) and it is still impossible.

I'm still pretty new to all of this lol

update: the two options my prof and I are now leaning towards are 1) wiping this comp and just updating widows and running linux through a windows subshell, or building a new computer since this is the oldest work station in the lab anyway. So the problem wasn't fixed, per se, but based on how each time I fixed a problem to do with dual booting another problem popped up that took me a bunch of time and sanity to solve I'm thinking that continuing to work on this is no longer worth the time in comparison to other possible solutions, rip

---

### Post by oldfred on 2021-06-08
What brand/model system?
Do you have most current UEFI/BIOS from vendor?

Ubuntu can install with UEFI Secure boot on. But proprietary drivers like nVidia are then a bit more difficult to install as user has to certify or sign them with mokmgr for use with Secure Boot.

---

### Post by brooksmm on 2021-06-08
it's an asus my prof built in 2013--the drive we're trying to get linux working on is a PCI/NVMe drive and the BIOS version is 1908.

---

### Post by oldfred on 2021-06-08
Is that an Asus motherboard? What model?

Have seen others with various issues trying to get NVMe drive to work with adapters and old systems. For those old systems, I suggest just staying with SATA SSD. You probably need newer motherboard & chips to really take advantage of NVMe over SATA  anyway.

---

