---
title: "Fiesty installation nVidia GeForce2 driver problem"
date: 2007-05-03
forum: Installation &amp; Upgrades
---

### Post by fable on 2007-05-03
I did a fresh install of Fiesty last week.  Everything went well using the nVidia legacy driver installed with Synpatic.  For some reason I can only get maximum 1024x768 resolution.  So I downloaded the nVidia driver from the nVidia.com site.  I ran the nVidia installer per instruction but the installation failed.  I tried to go back to the nVidia legacy driver with Synpatic but now I got the following error message and it also failed:

```
E: /var/cache/apt/archives/nvidia-glx-legacy_1.0.7184+2.6.20.5-15.20_i386.deb: subprocess pre-installation script returned error exit status 2
```

Now I cannot use my nVidia video card.  Anyone knows what caused this problem and how can I fix it?

---

### Post by fable on 2007-05-03
UPDATE:  Re-installing the driver using Synaptic did not solve this problem.  Instead, I use Automatix2 to install the new nVidia driver.  Automatix2 installation went without error.  It seems like Automatix2 rebuilt a nVidia kernel.  However, the new driver did not work with my card and I cannot start X.  I have to manually install the legacy driver (sudo get-apt install nvidia-glx-legacy).  Now the nvidia card works again on my PC.

---

