---
title: "Nvidia driver activation fails"
date: 2010-06-12
forum: Installation &amp; Upgrades
---

### Post by Rabendoktor on 2010-06-12
Hi, there,

after a brand new 10.0.4-installation on my x86, the system proposes me to activate the nvidia-drivers for my gc - trying this, I get the following bug report:

**SystemError: Failed to lock /var/cache/apt/archives/lock**

What to do now?

Thanks 4 help an a wonderful weekend!

---

### Post by tommcd on 2010-06-12
Do you have synaptic package manager open or the Ubuntu software center open when you are trying to install the nvidia driver?
If so, you should only be running one package manager at a time.
What nvidia card do you have ???
If you have a recent nvidia card, try running:
```

sudo apt-get update
sudo apt-get install nvidia-current
sudo nvidia-xconfig

```
and then reboot.

---

### Post by Rabendoktor on 2010-06-12
... it was the thing with the multiple package apps...

Thanks a lot!!!

Wonderful summereve,

Rabendoktor

---

### Post by topet2k12001 on 2010-06-12
> **tommcd said:**
> Do you have synaptic package manager open or the Ubuntu software center open when you are trying to install the nvidia driver?
If so, you should only be running one package manager at a time.
What nvidia card do you have ???
If you have a recent nvidia card, try running:
```

sudo apt-get update
sudo apt-get install nvidia-current
sudo nvidia-xconfig

```
and then reboot.
Thanks for this, I encountered the same problem earlier.

---

