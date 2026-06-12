---
title: "Installing the nvidia drivers"
date: 2007-08-01
forum: Installation &amp; Upgrades
---

### Post by waqaskool on 2007-08-01
i want to install nvidia drivers, but only the ones on [www.nvidia.com](www.nvidia.com) not the ones in the restricted drives option & not with the automatix but the ones on [www.nvidia.com](www.nvidia.com)  
i downloaded the the file ran it after killing the x server .........
like 'sh nvidia.....run' .
it installed ok !!!!
but when i restarted, my x server crashed like a wingless plane !!!!!


i cant find any actual guides to install legacy drivers in Ubuntu....!!
please help !!!

my experience with Linux is some where b/w a noob a rookie !!!

---

### Post by Pumalite on 2007-08-01
[https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia)

---

### Post by wjp.reg on 2007-08-01
> **waqaskool said:**
> i want to install nvidia drivers, but only the ones on [www.nvidia.com](www.nvidia.com) not the ones in the restricted drives option & not with the automatix but the ones on [www.nvidia.com](www.nvidia.com)  
i downloaded the the file ran it after killing the x server .........
like 'sh nvidia.....run' .
it installed ok !!!!
but when i restarted, my x server crashed like a wingless plane !!!!!


i cant find any actual guides to install legacy drivers in Ubuntu....!!
please help !!!

my experience with Linux is some where b/w a noob a rookie !!!

If all went as well as you suggested you simply need to do the following when booting and logging on in single-user/recovery/safe mode:

```
sudo dpkg-reconfigure xserver-xorg
```

and select ´nvidia´ as the driver, and ´x´ the resolution settings your card/monitor supports.  Every other setting should work using the defaults.

Good Luck!

---

