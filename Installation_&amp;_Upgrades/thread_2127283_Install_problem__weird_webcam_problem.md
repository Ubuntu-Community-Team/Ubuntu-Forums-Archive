---
title: "Install problem / weird webcam problem"
date: 2013-03-19
forum: Installation &amp; Upgrades
---

### Post by vecnu on 2013-03-19
I am trying to install ubuntu studio 12.04 on my laptop (vaio vgn-fe31).

When I installed Xubuntu 12.04 I found a problem. Everything goes fine up to the "enter your username and password". Then the installation crashes as it loads the next step. I think that the installer tries to use the built-in webcam to take a picture, but it makes the installer crash since that webcam is not supported - it won't work no matter what I try.

That time I avoided the problem by using an alternate instead of a live ISO image. But there is no alternate version for ubuntu studio 12.04! Is there a way I can prevent the installer from using the webcam? 

I find it extremely annoying being unable to install ubuntu studio because of the webcam!

---

### Post by vecnu on 2013-03-19
I managed to solve it by googling.

syslog revealed a module error:
ubuntu-studio kernel: [ 3617.420553] gspca_main: ISOC data error: [0] len=0, status=-71

So I tried to disable the module gspca_main. In order to disable that module, I had to disable the module gspca_vc032x, which was using it, that is:
```

sudo modprobe -r gspca_vc032x
sudo modprobe -r gspca_main
sudo modprobe -r videodev

```

Since videodev was using gspca_main I decided to disable it, I don't know if the install would have finished without disabling it.

---

### Post by markusfrei on 2013-08-22
Another workaround is to do the installation on a PC that has no webcam, and then when finished, just move the HD back to the original PC.

---

