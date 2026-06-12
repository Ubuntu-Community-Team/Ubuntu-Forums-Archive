---
title: "Graphics card problem after update"
date: 2010-09-29
forum: Installation &amp; Upgrades
---

### Post by n0c0d3 on 2010-09-29
Hi,
I just upgraded to 2.6.32.25 #44 and now I only get the command line mode when I start my Xubuntu 10.04 installation. I tried the instructions on [this help page]("https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia"), but to no avail.
Normally I should be able to get into xcfe by using the startxfce4 command, but then I get the following errors:

FATAL: Module nvidia not found
and a warning there´s no driver available.
Then:
Fatal server error: no screens found
xinit: No such file or directory (errno 2): unable to detect X server
xinit: No such process (errno 3): Server error.

Does anyone have an idea how to solve this?

Thanks in advance,
Bart

---

### Post by andrewthomas on 2010-09-29
```
sudo apt-get update && sudo apt-get install nvidia-current
```

---

### Post by n0c0d3 on 2010-09-29
> **andrewthomas said:**
> ```
sudo apt-get update && sudo apt-get install nvidia-current
```
Unfortunately this didn´t change a thing. I still boot into the command line and after startxfce4 I still get the same errors.

Thanks anyway,
Bart

---

### Post by n0c0d3 on 2010-09-29
I think the already installed Nvidia driver gave problems and I must have made a mistake in the removal of it or something like that. But I already did a fresh install and kernel update (it´s a computer I hardly ever use and had nothing important on it anyway) and installed the nvidia default driver from the Hardware Drivers menu. Things seem to be ok now.

Bart

---

### Post by n0c0d3 on 2010-10-10
> **andrewthomas said:**
> ```
sudo apt-get update && sudo apt-get install nvidia-current
```
I just updated to 10.10 and ran into the same problem again, but now on a different computer that I wouldn't like to re-install from scratch. I tried the above command command to get the nvidia driver to work and this time it worked. The driver offered on the nvidia site is 256.53, but the nvidia-current command installed 260.19.06. I still don't know how that works out though, as I've only had it installed for a couple of minutes.

I'm glad the answer helped me after all.

Thanks,
Bart

---

