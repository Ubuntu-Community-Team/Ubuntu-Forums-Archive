---
title: "Macbook Pro 6,2 - The Link &quot;nvidia-graphics-drivers.conf&quot; is Broken. Move it to Trash"
date: 2013-08-01
forum: Installation &amp; Upgrades
---

### Post by jart16 on 2013-08-01
I am trying to run 12.04.2LTS. I posted [here]("http://ubuntuforums.org/showthread.php?t=2164521") yesterday about getting a black screen after installing. A user directed me to check my Xorg.0.log. In that log, it showed:


```
"(EE) Failed to load module "nv" (module does not exist, 0)"
```

I Googled this code, and I got a thread on AskUbuntu, which said:

> nv was an old open source driver for Nvidia cards, which is now deprecated. Make sure you don't have it in xorg.conf, or try blacklisting it with
echo "blacklist nv" | sudo tee -a "/etc/modprobe.d/blacklist.conf"

I navigated to the modprobe.d folder and poked around a little. I tried looking in a file called nvidia-graphics-drivers.conf. It said the link was broken, and asked if I wanted to move it to the trash. Could this be the root of the problem?

---

