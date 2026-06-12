---
title: "Nvidia woes"
date: 2014-05-08
forum: Installation &amp; Upgrades
---

### Post by btolman on 2014-05-08
upgraded to 14.05, updated to Nvidia 331, no more x-server.

purged, reinstalled.  Next step is tearing down x-config.

Nouveu drivers (or however that's spelled) seem to work, but don't support / see my dual monitors.

I think I know what to do, I just wanted to whine about it.

Thanks for reading.:cool:

---

### Post by dannyboy79 on 2014-05-08
purge all signs of nvidia driver installation, reboot and hoopefully you're using nouveu, now open a web browser and go to nvidia website and download latest nvidia driver that supports your gpu. save it to your home directory and change it's permissions to be executable. now go to tty1, then kill your x server using sudo service light stop, then using sudo run the nvidia run file, when it's all done reboot your machine with sudo shutdown -r now. You should boot up using the nvidia driver from their website. 

I haven't used the nvidia repo drivers in years. I have a GTX 760 and am running 331.67 or something like that

---

### Post by btolman on 2014-05-08
Yeah, been doing that.  THis time I'm adding the nvida-xconfig thingy.  It told me there was not x-file.

sigh...

---

### Post by btolman on 2014-05-12
Finally solved it by doing a reinstall from the Live CD.

Now I just have to reinstall, well, everything.

---

### Post by btolman on 2014-05-13
Okay, I fixed this. This is how I fixed it.

1. Create a Live Bootable USB of 14.04
2. Boot from it
3. Select Install Ubuntu
4. When asked, Select "Reinstall Ubuntu 14.04 LTS"
5. Reinstall all applications.

This will fix any nvidia woes. :)

---

