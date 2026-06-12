---
title: "Ubuntu stalls on booting"
date: 2008-08-05
forum: Installation &amp; Upgrades
---

### Post by fuzzilogyc on 2008-08-05
Hi,

My ubuntu install started failing to boot one day. It gets to a certain point in the boot sequence and just stalls there. I'm not sure if i did something to it, but i don't think so. 
I've attached a screen shot of where it gets to. 
If anyone could help, it'd be much appreciated. Cheers

---

### Post by PmDematagoda on 2008-08-05
Did you try booting up Ubuntu through Recovery Mode and seeing if that shows up any extra information? Also, did you make any changes to the kernel before this happened?

---

### Post by fuzzilogyc on 2008-08-05
yep, i tried recovery mode, does the same thing.
i don't think i've made any changes to the kernel since. i've been able to boot fine recently, its just now its suddenly stopped. is there some recovery tool that i might be able to use?

---

### Post by Pumalite on 2008-08-05
Go into Recovery Mode and do a:
sudo apt-get update
sudo apt-get dist-upgrade

---

### Post by fuzzilogyc on 2008-08-05
i can't get into recovery mode. i get the same problem when trying to boot into recovery mode.

---

### Post by Pumalite on 2008-08-05
Try to get a command line:
Ctrl+Alt+F1 (2,3,4,5,6)

---

### Post by fuzzilogyc on 2008-08-05
should i try this when it stalls during the boot process? will the network have loaded by then? judging by the output, by the time it stalls, it doesn't seem like the ethernet driver has loaded yet :/
i'll try it when i get home though

---

### Post by PmDematagoda on 2008-08-05
Do you have any older kernels as well? If so, try booting from them and see if the problem persists.

---

### Post by fuzzilogyc on 2008-08-05
yeah, i had changed the grub boot entry to use different initrd and vmlinuz files i had, and it did the same thing. it doesn't seem to be booting the kernel. i'm thinking it might be a filesystem error. the hard drive is quite old and might be dying?

---

### Post by Pumalite on 2008-08-05
Get TestDisk and take a look:
[http://www.cgsecurity.org/wiki/TestDisk_Download](http://www.cgsecurity.org/wiki/TestDisk_Download)

---

