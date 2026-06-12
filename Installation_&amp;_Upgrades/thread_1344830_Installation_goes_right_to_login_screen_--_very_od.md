---
title: "Installation goes right to login screen -- very odd"
date: 2009-12-03
forum: Installation &amp; Upgrades
---

### Post by Anton32828 on 2009-12-03
I built a PC from scratch last night and tried to use a Live CD to install Ubuntu 9.10 desktop edition.
The PC has an unformatted disk, an Athlon II processor and 2GB of memory. It's very bare-bones and basic.
 
The live CD booted and gave me the usual menu. I selected "Install Ubuntu." Instead of pogressing to the disk-partition menu, it proceeded to load an Ubuntu desktop login screen and ask me for a userID and password.
 
Has anyone seen this behavior before?
 
I switched to an Ubuntu server CD which behaved normally. Unfortunately that particular CD had corrupt files on it so the kernel couldn't load. 
 
I will try again tonight after burning a new image to a USB stick (to eliminate media-corruption considerations), so I'm not really looking for a solution --- I'm just curious if anyone else has seen this behavior. Perhaps it was an error in the LiveCD build on one particular day?

---

### Post by Anton32828 on 2009-12-04
Solved --- I had hardware RAID enabled in BIOS but only one hard drive installed. The desktop installer couldn't see the drive, but the server installer could see it. I corrected the RAID setting, wiped the drive clean with a Gparted live CD, and then installed 9.10 desktop from a USB stick without a problem. 
 
Building a PC from scratch is more of an education than I bargained for....  Heh.

---

