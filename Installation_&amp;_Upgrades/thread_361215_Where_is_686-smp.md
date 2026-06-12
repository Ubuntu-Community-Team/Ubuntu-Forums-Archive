---
title: "Where is 686-smp?"
date: 2007-02-14
forum: Installation &amp; Upgrades
---

### Post by rob_909 on 2007-02-14
Hi, I installed edgy and am trying to use the 686-smp kernel. I am total noob, so bare with me
I ran.

sudo apt-get update
sudo apt-get install linux-686-smp

No errors from terminal, it installed, but when I rebooted, it wasn't in the GRUB menu. I went to the synaptic package manager, and found the 686-smp, and it said it was installed, but in the description it says obsoleted by linux-image-generic, which is all I can run from the boot menu.

When I run uname -r...

it says 2.6.11-17 generic

How do I access the installed 686-smp kernel to take advantage of my duo-core processor?

---

### Post by housam on 2007-02-14
You don't need it .kernel 2.6.11-17 generic do the same as linux-686-smp regarding the core duo processor.
You should see both of them in the system monitor .
To get infos about your processors.
```
cat /proc/cpuinfo
```

---

### Post by rob_909 on 2007-02-14
see, told you i was a noob. Thanks for the help.

---

