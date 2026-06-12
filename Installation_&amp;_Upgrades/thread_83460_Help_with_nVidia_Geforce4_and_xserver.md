---
title: "Help with nVidia Geforce4 and xserver"
date: 2005-10-28
forum: Installation &amp; Upgrades
---

### Post by Temple on 2005-10-28
Hi, I've installed Ubuntu 5.10 with no problems on my pc, but when I try booting into it (I dual boot) it says xserver cannot start because of 'no screens found' or something (I forget, sorry). Alot of other users had the same problems and try all sorts of things like:

sudo apt-get install linux-restricted-modules-$(uname -r)
sudo apt-get install nvidia-glx
sudo nvidia-glx-config enable

also tried reconfiguring using:
sudo dpkg-reconfigure xserver-xorg

I got it to say the bus id was wrong, which is why I came, I tried lspci and the id for my card is:

0000:02:0a.0 VGA compatible controller: nVidia Corporation NV18 [GeForce4 MX 4000] (rev c1)

What do I put in my xorg.conf  as the bus id? Thanks in advance.

---

### Post by Temple on 2005-10-28
Sorry for the double post. I fixed it. I used 02:10 as the bus id and it works. I'm now using Breezy Badger. Thanks!

---

