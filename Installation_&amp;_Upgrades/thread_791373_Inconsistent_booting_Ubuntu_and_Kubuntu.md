---
title: "Inconsistent booting Ubuntu and Kubuntu"
date: 2008-05-12
forum: Installation &amp; Upgrades
---

### Post by Disturbed_Genius on 2008-05-12
Hello,

I am currently using a Fujitsu Siemens Amilo Li1718 laptop and am dual booting Vista home premium and Ubuntu Hardy.  I have come across a problem and I don't really know where to look for the fault, I can only get a Ubuntu boot 1 in 5 or 6 times, the rest of the time it hangs on a black screen and I am forced to perform a hard reset.  Due to driver issues I never get a splash screen anyway, it just loads to login after a few seconds.  The laptop never hangs when loading the Windows partition, just Ubuntu.  For a while I was using Vista Home premium with Ubuntu Gutsy and KDE Sessions too where this problem was also evident.  Thanks in advance for your assistance.

---

### Post by Partyboi2 on 2008-05-12
Check /etc/usplash.conf. Open a terminal, then
```
gksudo gedit /etc/usplash.conf
``` change gedit to kate if using kubuntu.
 you should see something like
xres=1024                                                                                                                    
yres=768 
(1024x768 ) make sure these match what your screen can support, if you need to change them then after you have saved the changes in the terminal
```
sudo update-usplash-theme usplash-theme-ubuntu
```

---

