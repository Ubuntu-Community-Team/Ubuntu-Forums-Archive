---
title: "Installing Alsa 1.0.15"
date: 2007-12-19
forum: Installation &amp; Upgrades
---

### Post by dema on 2007-12-19
I'm trying to install ALSA on my laptop from a danish toturial given in first comment here:
[http://linuxin.dk/forum/index.php?ops=linuxin&fmode=vis&visid=30012&grid=3](http://linuxin.dk/forum/index.php?ops=linuxin&fmode=vis&visid=30012&grid=3)

After rebooting I get this screen when trying to eg. adjust volume in volume manager:
[http://www.demaweb.dk/alsa.png](http://www.demaweb.dk/alsa.png)

I hope someone can tell me what to do?

---

### Post by Pumalite on 2007-12-19
Post:
lshw -C sound

---

### Post by dema on 2007-12-19
dennis@dennis-laptop:~$ sudo lshw -C sound
  *-multimedia UNCLAIMED  
       description: Audio device
       product: 82801G (ICH7 Family) High Definition Audio Controller
       vendor: Intel Corporation
       physical id: 1b
       bus info: pci@0000:00:1b.0
       version: 02
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0

---

### Post by Pumalite on 2007-12-19
Card not recognized. Module not loaded. Let's see if this works: in Terminal:
sudo apt-get install linux-backports-modules-generic
Reboot.
Post:
lshw -C sound

---

### Post by dema on 2007-12-20
Thanks champ! My ALSA are working now!

---

### Post by Pumalite on 2007-12-20
You are welcome. Good luck!

---

