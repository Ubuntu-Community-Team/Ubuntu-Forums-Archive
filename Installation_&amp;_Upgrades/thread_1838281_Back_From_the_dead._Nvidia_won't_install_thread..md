---
title: "Back From the dead. Nvidia won't install thread."
date: 2011-09-03
forum: Installation &amp; Upgrades
---

### Post by silvesj on 2011-09-03
So i had posted this a few months ago. And my understanding at the time was that nVidia was not supporting Linux drivers. But a few months later I am dying to have linux on my asus laptop. After install on reboot after grub and the OS splash screen, the screen goes black. Is there anyway to fix this, or are there updated drivers yet?

---

### Post by Hakunka-Matata on 2011-09-03
sure it can be fixed, it's Linux!

on reboot *after *grub you say, so you get the grub menu:: of different kernels to start?, and you choose?, then it goes south?

Have you already worked with editing a given grub selection, and adding /switches like nomodeset?

---

### Post by realzippy on 2011-09-03
[http://ubuntuforums.org/showthread.php?t=1657660](http://ubuntuforums.org/showthread.php?t=1657660)

---

### Post by silvesj on 2011-09-03
I have done that, but then you lose the unity interface. Which is not necessary but would be nice. Because then the graphics (unity or not) just has a bloated look. :(

---

### Post by Hakunka-Matata on 2011-09-03
what does ```
sudo lshw -C display
``` show?

---

### Post by silvesj on 2011-09-11
> **Hakunka-Matata said:**
> what does ```
sudo lshw -C display
``` show?

Sorry it took me so long to post but I was out of town. This is what i get returned....
PCI (sysfs) 

Right now I am in Linux with nomodeset. But I just had the way the display looks. Any way around this?

**UPDATE: I installed nVidia drivers via the hardware drivers tool. It now allows me to boot in normal minus nomodeset. but then boots to an interface without unity, and still looks like nomodeset.

---

### Post by wadd92 on 2011-09-12
I found the drivers from Nvidia's official website work better. Download them and hit ctrl+alt+1 and disable x server and install. Installing from the additional drivers and synaptic package manager didnt work properly for me (unity worked but low screen resoloution) but the ones from nvidia's website worked perfectly

---

### Post by realzippy on 2011-09-12
post output from

```
lspci | grep VGA
```

@wadd92

manually installing nvidia-drivers has the disadvantage that you have to repeat install when a kernel update comes.
If you want the newest drivers,it is better to add xswat ppa to your system sources.

---

