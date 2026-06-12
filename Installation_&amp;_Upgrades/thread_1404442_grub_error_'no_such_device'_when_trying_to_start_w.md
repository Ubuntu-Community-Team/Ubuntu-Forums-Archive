---
title: "grub error 'no such device' when trying to start windows"
date: 2010-02-11
forum: Installation &amp; Upgrades
---

### Post by Hansmc on 2010-02-11
I am having trouble getting a dual boot setup on Ubuntu remix on a netbook. The install went fine, but then windows would not book. I had a windows error. So I reinstalled windows, and rebuilt grub. Now when I try to launch windows from the grub menu it says "error: no such device: 0a82ff1982ff0849". How do I go about fixing that? I can boot to Ubuntu fine now. Thanks

---

### Post by darkod on 2010-02-11
First try running in terminal:
sudo update-grub

and see if that sorts it out. The windows partition UUID is not correct because it was reformatted.

---

### Post by Hansmc on 2010-02-11
> **darkod said:**
> First try running in terminal:
sudo update-grub

and see if that sorts it out. The windows partition UUID is not correct because it was reformatted.

That did it! Thanks

---

