---
title: "(Ubuntu 10.04) Nvidia drivers installation problem"
date: 2010-05-06
forum: Installation &amp; Upgrades
---

### Post by maKiaveL on 2010-05-06
Well, after some ubuntu upgrades to my nvidia-current I started to have problems everytime I suspended or locked the screen since it crashes while checking my password when i'm trying to log back in.
So, i tried to reinstall my nvidia drivers. I deleted all nvidia drivers, and then i tried to reinstall the nvidia-current. 
I added blacklist nouveau to blacklist.conf, then I installed nvidia-current using apt-get (after update) and when I typed:

```
[COLOR=Black][COLOR=#c20cb9]**sudo**[/COLOR][/COLOR] modprobe nvidia-current
```This error pops up in the terminal: 

```
FATAL: Error inserting nvidia_current (/lib/modules/2.6.32-22-generic/updates/dkms/nvidia-current.ko): No such device
```How can I fix it? Am I doing something wrong?
Thank you very much!

---

### Post by dino99 on 2010-05-06
" sudo modprobe nvidia-current"

never do that :mad:

sudo dpkg --configure -a
sudo apt-get update
sudo apt-get install -f

---

### Post by maKiaveL on 2010-05-06
after I install nvidia-current in my hardware drivers it says:
"the driver is activated but not currently in use"

?

---

### Post by maKiaveL on 2010-05-06
how can i activate the vga? this is so annoying! lool

---

