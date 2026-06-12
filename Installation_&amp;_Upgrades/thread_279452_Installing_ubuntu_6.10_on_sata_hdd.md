---
title: "Installing ubuntu 6.10 on sata hdd"
date: 2006-10-18
forum: Installation &amp; Upgrades
---

### Post by omkarenator on 2006-10-18
I have seagate 80g **sata** hdd.I have /dev/sda9 (2G) free space and /dev/sda8 (1G) as swap (of prev distro). When gparted program stars, it says /dev/sda 76G **UNALLOCATED**. [U]It doesn't show my ptn table.
[/U]
when i do 
sudo parted /dev/sda9 print
it gives me info about ptn and stuff.
 One more thing, I can see all ptns in **Device Manager** from main menu. How is that?
What should i do to see my ptns in gparted??
Or should i use parted, but how then to tell ubuntu to insall on /dev/sda9 and use swap /dev/sda8 ??

---

