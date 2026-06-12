---
title: "Installing NVIDIA graphics card"
date: 2011-06-21
forum: Installation &amp; Upgrades
---

### Post by harisp on 2011-06-21
I'm running Ubuntu 11.04 and I'm trying to install drivers / control panel for my nvidia card. Ubuntu installed perfectly, but i'm having overscan issues so I'm trying to get the nvidia drivers.

I'm kind of new to linux, but i've tried using nvidia-xconfig and after that, I can't even get into X. 

What is the best way of going about this? I've searched online, but really haven't been able to get an answer.

The video card that I have is GeForce4 MX 440.

Any help is appreciated.

---

### Post by tommcd on 2011-06-22
You ahould be using the nvidia-96 driver. There have been issues using this driver in recent versions of Ubuntu with the newer Xorg packages. Anyway, the nvidia-96 driver is what you should be using.
Have you tried installing the nvidia driver from the additional drivers menu on Ubuntu?? If so, then what was the outcome?

And welcome to the Ubuntu forums!

---

### Post by harisp on 2011-06-23
The thing is when I search for additional drivers, the 96 version does not show up. 

When I try to manually install it, it gives me the following error: 

```

Package dependencies cannot be resolved.

The following packages have unmet dependencies:

nvidia-96: Depends: x11-common (>= 1:7.0.0) but 1:7.6+4ubuntu3 is to be installed
           Depends: xorg-video-abi-8.0 but it is not going to be installed
           Depends: xserver-xorg-core (>= 2:1.8.99.905-1ubuntu3) but 2:1.10.1-1ubuntu1.1 is to be installed



```

---

### Post by tommcd on 2011-06-24
How are you trying to install the driver? What commands did you run?
Are you using any third party repositories?
If you can not install the nvidia-96 driver I suppose you could try the nvidia-173 driver.

---

### Post by harisp on 2011-06-24
I'm using the Ubuntu Software Center to install the driver.

---

### Post by tommcd on 2011-06-25
Apparently the nvidia-96 driver is not working on Ubuntu 11.04:
[http://www.linuxquestions.org/questions/ubuntu-63/nvidia-96-series-drivers-for-ubuntu-11-04-a-879438/](http://www.linuxquestions.org/questions/ubuntu-63/nvidia-96-series-drivers-for-ubuntu-11-04-a-879438/)
[http://askubuntu.com/questions/33204/why-am-i-unable-to-install-the-nvidia-96-driver](http://askubuntu.com/questions/33204/why-am-i-unable-to-install-the-nvidia-96-driver)
This person reports errors similar to yours on Launchpad:
[https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-96/+bug/790660](https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-96/+bug/790660)
I would either use the default open source *nouveau* driver, or give the nvidia-173 driver a shot.

---

