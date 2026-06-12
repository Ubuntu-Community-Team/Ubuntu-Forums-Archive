---
title: "Enabling Nvidia driver from command line"
date: 2010-03-22
forum: Installation &amp; Upgrades
---

### Post by Yud Paulus on 2010-03-22
Hi,
I'm having problems with my Nvidia card. X doesn't work after installation (9.10), only command prompt. I've read the instructions at [http://www.psychocats.net/ubuntu/nvidia](http://www.psychocats.net/ubuntu/nvidia) on how to enable Nvidia drivers, but the instructions are only for GUI, which I don't have.
Anyone knows how to enable Nvidia drivers from command line ?
Thanks,
Yud.

---

### Post by oldos2er on 2010-03-22
Try ```
sudo apt-get install nvidia-glx-190
```

---

### Post by nss0000 on 2010-03-22
> **oldos2er said:**
> Try ```
sudo apt-get install nvidia-glx-190
```

I would imagine that choosing your **own** NV driver-version will land you in trouble.

---

