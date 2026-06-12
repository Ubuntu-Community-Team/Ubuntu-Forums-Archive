---
title: "[SOLVED] Boot splash and GDM login resolution problems."
date: 2008-09-22
forum: Installation &amp; Upgrades
---

### Post by raspark on 2008-09-22
Is there any way to decrease the resolution of the Ubuntu splash screen during boot, and also the resolution of the GDM login screen on an installed system?

I installed on an old G3 (PPC) at work and the monitor I'll be using the system on at home has a much lower high res.  The boot works, and I get an out of bounds error when these screens should be displaying.  I am still able to login after waiting and guessing when the system is ready for login, but some steps to follow, or files to change would be helpful.

Thanks,

raspark

---

### Post by Partyboi2 on 2008-09-25
For the boot splash screen you could try editing your usplash.conf file with a lower resolution that your monitor can handle
```
sudo nano /etc/usplash.conf
``````
xres=1024                                                                                                                    
yres=768 
``` change to what your monitor supports. After saving, update usplash
```
sudo update-usplash-theme usplash-theme-ubuntu
```

---

