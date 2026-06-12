---
title: "Kernel update on 9.04 to kernel 2.6.28.18 no nvidia?!"
date: 2010-02-05
forum: Installation &amp; Upgrades
---

### Post by dBuster on 2010-02-05
Okay, Jaunty, 9.04 this morning updated my kernel to I believe it is 2.6.28.18 and upon the reboot I had no desktop.  It booted wanting to go into low graphics.

So I drop to shell and stop the gdm and try to run the latest nvidia run file I have and it hangs saying I have a x server running.  Not sure how to stop that but if I could get a clue I would appreciate it so I can try and see if that will fix my issue.

Otherwise I am needing assistance with getting my desktop back!  I can boot into an older kernel and if need be I would like to roll back that latest update this morning, but once again I am forgetting the command line for that.

Thanks in advance for help!

---

### Post by dBuster on 2010-02-05
Now that I got home and had time to get into it.. I solved my own problem..

posting for those who may have the same issue...

```
sudo killall gdm

sudo apt-get remove --purge nvidia-glx

sudo sh ./NVIDIA-Linux-x86_64-190.53-pkg2.run 

sudo reboot
```

and that is all she wrote!  Upon reboot I was back up and running with that version of the nVidia driver mentioned.  Only drawback was that I had to re-install the madwifi drivers for my atheros card but that has to be done each time I receive a kernel update.

---

### Post by TheMiz on 2010-02-05
Thanks!  I was in a little bit of a panic!  Your post saved my day!

---

### Post by DejitaruJin on 2010-02-05
I had exactly the same problem, as did someone else I know. You'd think that would have been tested a little better.

As for the fix, is reinstalling the graphics drivers really all that is needed?

Edit: Wow, okay, I guess it is. Didn't even need to uninstall "nvidia-glx" because it wasn't there to begin with.

---

### Post by franck31 on 2010-02-10
Same problem with AMD video driver. After update, it was back to default driver (no accelaration) and  amdcccle would not run. I am back to previous version of the kernel. Will wait for a fix.

---

### Post by sleepee on 2010-02-11
if i'm not mistaken, you have to manually install those nvidia graphics drivers every time you upgrade the kernel..
i might be wrong, but i'm pretty sure that's the case..

---

