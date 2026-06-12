---
title: "Display settings not saved after reboot in kubuntu 19.04"
date: 2019-08-24
forum: Installation &amp; Upgrades
---

### Post by rpra006 on 2019-08-24
Hi,
I just did a new install on Dell XPS laptop. 
I have another external monitor connected to the laptop and I want to use both laptop and external monitor at the same time.
Every time i setup all the resolution and position of the monitors and click apply. This work fine but as soon i restart everything goes back to beginning and requires reconfiguration.
How can I make it so the display setting configuration is saved.

This is my system information.

```

Operating System: Kubuntu 19.04
KDE Plasma Version: 5.15.4
KDE Frameworks Version: 5.56.0
Qt Version: 5.12.2
Kernel Version: 5.0.0-25-generic
OS Type: 64-bit
Processors: 8 × Intel® Core™ i7-4702HQ CPU @ 2.20GHz
Memory: 15.6 GiB of RAM

```

 It has following graphics card: GeForce GT 750M

Can someone please help, or suggest how I can fix this problem.

Thanks

---

### Post by SeijiSensei on 2019-08-25
Are you sure your entire home directory is writable?  In particular, what about $HOME/.kde?  I have a laptop connected to an external monitor which is configured using System Settings > Display and comes up correctly after rebooting and logging in.  Logging in is key though. Until you log in, the machine doesn't know to use the settings in your home directory.

(My system is configured to use just the external monitor.)

---

