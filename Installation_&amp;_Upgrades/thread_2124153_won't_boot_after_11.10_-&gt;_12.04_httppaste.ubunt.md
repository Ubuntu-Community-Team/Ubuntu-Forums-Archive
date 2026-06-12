---
title: "won't boot after 11.10 -&gt; 12.04 http://paste.ubuntu.com/5601067/"
date: 2013-03-10
forum: Installation &amp; Upgrades
---

### Post by comp666 on 2013-03-10
Hi,

I just upgraded from 11.10 to 12.04 and now my computer won't boot. I've tried running boot repair to no avail. Here's the paste that I received. [http://paste.ubuntu.com/5601067/](http://paste.ubuntu.com/5601067/). At startup, I simply get a grub prompt and nothing else. Please help!! :(

---

### Post by dino99 on 2013-03-10
from the grub prompt: 
sudo grub-install /dev/sda
sudo update-grub

---

### Post by comp666 on 2013-03-10
sorry, it's actually a grub rescue prompt not a grub prompt. 

It says:

> error: no such device: d81a450a-ed93-47v1-a324-f505723ced3f
grub rescue>

I have no access to sudo here.

Also tried completely reinstalling ubuntu from 12.04 usb and I still get the same thing.

Fixed it: had to use gparted to create a new partition table (MBR instead of GPT). Then used boot repair to reinstall grub. I have no idea how my disk got changed to GPT but that was a nightmare.

---

