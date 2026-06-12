---
title: "Ubuntu update / nvidia driver help"
date: 2006-09-20
forum: Installation &amp; Upgrades
---

### Post by neumeka on 2006-09-20
I have been running ubuntu 6.06 with an nvidia graphics card (GeForce 5200)Y with the propritary drives.  Yesterday I installed some updates that Ubuntu  indicated that I needed by the red star thing that appears in the upper right hand side.  After I installed and rebooted, I got the X-Server cannot start messaged.

I changed my x-org configuration file so that the driver I am useing is nv instead of nvidia, but I would like to use the nvidia drivers.

I have tried to run the fixes to the Septemeber 14th problem, but updating th e package list had no effect.  Please let me know if anyone has any suggestions.

Thanks,
Kyle

---

### Post by karamba_kid on 2006-09-20
I have the same card and with the September 14th and 15th updates X server wouldn't start when I ran the 686 kernel, but it did start with the 386 kernel.  I updated yesterday, but I have been waiting to hear how the updates went before rebooting.  Sounds like I'll be waiting a little bit longer. Which kernel are you running?

---

### Post by neumeka on 2006-09-20
I am running the 386 kernel and trying to reinstall the 8774 nvidia driver

---

### Post by Skink on 2006-09-20
I had the same problem, but I figured out how to fix it. After you log in, type 

```
sudo dpkg-reconfigure xserver-xorg 
```

This allows you to reconfigure your x windows. As you go thru the list, when it comes up to the adapter you want to use, arrow down to nvida, do not use nv. For the rest, you probably can use the default settings. When your done, and back to a prompt, type

```
sudo dpkg-reconfigure gdm
```

then type startx

Hopefully this works for you as well as it did for me. I found the info to make this work [here.]("http://ubuntuforums.org/showthread.php?t=82222")

---

### Post by al_sharpe on 2006-09-20
Hello neumeka

When I installed the 386 kernel 2.6.15.27, with new nvidia update, the 
386 kernel worked fine, see if nvidia update is available.

One should not have to reconfigure the xserver or gdm.

Note: kernel update to 386 kernel updates the linux-restricted-module
which has the nvidia driver BUT
kernel update for 686 kernel does not update linux-restricted-module for
that kernel

go back to the .26 kernel, install new restricted module and reboot

Hope this helps
Al

---

