---
title: "how to remove last done dist-upgrade ?"
date: 2014-07-04
forum: Installation &amp; Upgrades
---

### Post by ramaswamyps on 2014-07-04
i did a dist-upgrade like a fool. and my udio missing. this old kernel work fine.
how do i remove the newr kernel and its files ?
or how do i make 
Linux ramaswamy-Satellite-C855D 3.11.0-23-generic #40-Ubuntu SMP Wed Jun 4 21:05:23 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux
root@ramaswamy-Satellite-C855D:/home/ramaswamy# 

this kernel default boot ?

---

### Post by sudodus on 2014-07-04
When running the good kernel you can remove the problematic kernel (and hope the next one will work better for you, when it arrives). Double check to be sure to remove the bad one and keep the good one!

```
sudo apt-get remove linux-image-xxxxx
```

where xxxxx is the identification of the problematic kernel (maybe 3.11.0-24-generic)

---

### Post by grahammechanical on 2014-07-04
Might I add, use Software Updater to update the system.

---

### Post by Bucky Ball on 2014-07-04
Reboot and after the BIOS screen press shift. This should get you to a menu with all installed kernels. Select and boot the good kernel. In a terminal, run:

```
uname -r
```

That will tell you which kernel you are using. I use Synaptics, but probably this can be done in SCentre: search for 'linux image' and delete the ones you don't want.

Always a good idea to keep the one you are using and the one before it. BE CAREFUL NOT to remove the kernel you are using! ;)

PS: Your 'udio' is missing? What is that? I'd personally leave things as they are and just choose the kernel you want at boot. Boot into and update the new kernel in a week and try it again. Removing it directly after install is fairly drastic. These things sometimes take time to mature ...

---

