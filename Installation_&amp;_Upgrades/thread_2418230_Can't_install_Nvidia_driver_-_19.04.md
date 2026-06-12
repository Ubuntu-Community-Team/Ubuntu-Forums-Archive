---
title: "Can't install Nvidia driver - 19.04"
date: 2019-05-03
forum: Installation &amp; Upgrades
---

### Post by leprotic on 2019-05-03
Hi anybody who is kind enough to read this, is willing to help me and has the knowledge or skills (which apparently I don't). Thanks in advance no matter the outcome.  

I've recently installed 19.04 on a laptop with GeForce GTX 660M but I'm not happy with the video performance (especially streaming in Firefox where I get slightly broken frames in scenes with fast motion). This could be a browser issue (Flash, etc.) but one thing at a time.

I've tried installing the Nvidia driver (NVIDIA-Linux-x86_64-375.39.run) but I get the error below. I've googled the warning, tried several things people suggested but none has worked for me so far.

Looking forward to any suggestion here. Thanks for your time.


 ERROR: An NVIDIA kernel module 'nvidia-drm' appears to already be loaded in  
         your kernel.  This may be because it is in use (for example, by an X  
         server, a CUDA program, or the NVIDIA Persistence Daemon), but this   
         may also happen if your kernel was configured without support for     
         module unloading.  Please be sure to exit any programs that may be    
         using the GPU(s) before attempting to upgrade your driver.  If no     
         GPU-based programs are running, you know that your kernel supports    
         module unloading, and you still receive this message, then an error   
         may have occured that has corrupted an NVIDIA kernel module's usage   
         count, for which the simplest remedy is to reboot your computer.

---

### Post by The Cog on 2019-05-03
Try this command - I think you'll find a nvidia driver already installed:
```
apt search nvidia | grep installed
```

---

### Post by Autodave on 2019-05-04
Where did you get that driver from?

---

### Post by oldos2er on 2019-05-04
Wondering why you didn't install Nvidia drivers from the repositories?

---

