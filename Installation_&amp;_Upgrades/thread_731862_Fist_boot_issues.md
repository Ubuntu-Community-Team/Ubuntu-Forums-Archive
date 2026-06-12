---
title: "Fist boot issues"
date: 2008-03-22
forum: Installation &amp; Upgrades
---

### Post by Terminating.proprietary on 2008-03-22
When I first attempted to boot Unbuntu 7.10 64 bit I had a brief error mesage which was so fast i could hardly read it. Something like can not allocated and bridge with a number and about 8 lines of this. I booted into windows, did some research, I found out it was related to acpi. The hardware on my notebook supports acpi because I can put it to sleep by closing it when using windows, among other things. In order to get Ubuntu to boot I had to edit I guess what you would call a boot parameter. I had to change the end of the parameter from quiet splash to acpi=off, at which point I was able to boot. Unfortunately, I have to do this everytime I boot. What does quiet splash mean anyhow? So after the 64 bit flash issues that are plaguing all 64 bit newbs such as myself I deleted the ubuntu partition via windows vista disk management. I understand that the flash players are limited to 64 bit and I shouldn't have a time of things with a 32 bit install. I am wondering will I have problems with acpi at boot time with the 32 bit install? I am downloading 32 bit 7.10 right now.

---

