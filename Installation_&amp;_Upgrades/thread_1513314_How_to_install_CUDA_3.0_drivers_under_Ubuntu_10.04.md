---
title: "How to install CUDA 3.0 drivers under Ubuntu 10.04 ?"
date: 2010-06-19
forum: Installation &amp; Upgrades
---

### Post by archimage on 2010-06-19
Hello,

I'd like to know how to install CUDA 3.0 drivers under  linux Ubuntu 10.04

I've tried to remove the native nvidia drivers  with : sudo apt-get remove nvidia*, then I blacklisted the nouveau, nv,  rivafb... in modprobe.d\blacklist.conf file,
I've installed the GCC  4.3

i've stopped the gdm to launch : sudo sh devdriver*

but  it still tells me there's a conflit with nvidia.ko !

I've already succesfully installed them because I found the right tutorial after 2 days of searching, but now i'm stuck

can  somebody please help me ?

---

### Post by madmaze on 2010-06-23
go see this thread [http://forums.nvidia.com/index.php?showtopic=171934](http://forums.nvidia.com/index.php?showtopic=171934)

---

### Post by kOoLiNuS on 2010-07-09
> **madmaze said:**
> go see this thread [http://forums.nvidia.com/index.php?showtopic=171934](http://forums.nvidia.com/index.php?showtopic=171934)

Thanks for the link ... fighting with something since the CUDA tests to check the correct setup of my environment are failing :-/

---

