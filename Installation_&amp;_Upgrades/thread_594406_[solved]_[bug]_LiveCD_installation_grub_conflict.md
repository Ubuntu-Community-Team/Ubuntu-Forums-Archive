---
title: "[solved] [bug] LiveCD installation grub conflict"
date: 2007-10-27
forum: Installation &amp; Upgrades
---

### Post by ucg on 2007-10-27
I ran into a weird bug in the installation process:

I tried to re-install Gutsy Gibbon (Kubuntu 7.10) from LiveCD. Before doing that I reorganized partitions. So old Linux root where Grub used to reside was gone. 

[COLOR="Lime"]When I started LiveCD[/COLOR], (first option — normal installation) it went ok untill loading desktop. It that moment it stuck with [COLOR="Lime"]the screen filled with vertical colored lines[/COLOR].

I repeated several times, the effect was here. 

The solution I found was [COLOR="Lime"]to manually fill Master boot sector with zeros except for last 66 bytes, so the Grub's rudiments would not be recognized.[/COLOR] 

I would appreciate suggestion where I should file this bug.

---

