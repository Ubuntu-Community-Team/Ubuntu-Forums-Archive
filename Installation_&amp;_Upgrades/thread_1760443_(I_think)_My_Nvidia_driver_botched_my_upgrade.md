---
title: "(I think) My Nvidia driver botched my upgrade"
date: 2011-05-16
forum: Installation &amp; Upgrades
---

### Post by schwim on 2011-05-16
hi there everyone,

I upgraded my desktop from 10.10 to 11.04.  On restart, it booted to the terminal.  On startx, I got the following error(s):

> 
FATAL: Module nvidia not found.
(EE) NVIDIA: Failed to load the NVIDIA kernel module. Please check your system's kernel log for additional error messages.
(EE) Failed to load module "nvidia" (module-specific error, 0)
(EE) No drivers available.

Fatal server error: no screens found


I imagine I need to revert to a standard driver to get x working and then install the nvidia driver again, but I'm not sure how to do this.

Any help would be greatly appreciated!

---

### Post by VanR on 2011-05-17
I would just type in the terminal

sudo apt-get install nvidia-current

That should install your video driver.

---

### Post by schwim on 2011-05-17
Thanks very much for your reply.

I tried what you suggested, but apt-get responds:

> nvidia-current is already the newest version.
nvidia-current set to manually installed.

Any other thoughts are most welcome.

thanks,
json

---

### Post by schwim on 2011-05-17
I have tried:

> sudo apt-get install --reinstall nvidia-current 

but x continues to refuse to start, citing the same errors.

[EDIT][this post](http://ubuntuforums.org/showpost.php?p=10819991&postcount=19) got me up and running.[/EDIT]

---

