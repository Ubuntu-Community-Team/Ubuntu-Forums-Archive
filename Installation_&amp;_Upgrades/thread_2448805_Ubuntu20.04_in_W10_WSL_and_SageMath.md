---
title: "Ubuntu20.04 in W10 WSL and SageMath"
date: 2020-08-14
forum: Installation &amp; Upgrades
---

### Post by ortollj on 2020-08-14
HI
After installing Ubuntu20.04 in W10 WSL, I installed SageMath, but SageMath cannot access the graphics functions of SageMath (which uses the Matplotlib libraries)
 Why? What is missing in Ubuntu20.04 in W10 WSL? and above all, is there  a way to remedy it ?
[https://answers.microsoft.com/en-us/insider/forum/all/wsl-ubuntu-sagemath-unusable/626dad6b-7a39-4761-a736-6b2cbc3fc884](https://answers.microsoft.com/en-us/insider/forum/all/wsl-ubuntu-sagemath-unusable/626dad6b-7a39-4761-a736-6b2cbc3fc884)

---

### Post by QIII on 2020-08-14
Hi!

If you want a nice graphical environment, you might be interested the bottom half of [this article]("https://techcommunity.microsoft.com/t5/windows-dev-appconsult/running-wsl-gui-apps-on-windows-10/ba-p/1493242") detailing how to use Xfce from RDP.

---

### Post by ortollj on 2020-08-15
thank you QIII
 I followed the directives of the site to which you gave me the link, but I encounter a problem at the step :

```
ortollj@ToshibaJPO:~$ xeyes
Error: Can't open display: 192.168.0.254
fd0f:ee:b0::1
fec0:0:0:ffff::1:0
ortollj@ToshibaJPO:~$
```

---

