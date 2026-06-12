---
title: "Nvidia Geforce 705M"
date: 2014-04-19
forum: Installation &amp; Upgrades
---

### Post by Wilman_Darnasutisn on 2014-04-19
hi,

just a simple question. i want to install Nvidia Graphic driver. but i don't know to do that? give me a basic tutorial
this is my graphic card spec:
>Nvidia Geforce 705M 1Gb
and i'm use Ubuntu 14.04 LTS x32.
please i want to finish my 3D graphic design for school :D

thank you

---

### Post by Wilman_Darnasutisn on 2014-04-20
just give me a basic tutorial about install nvidia driver in ubuntu using terminal

---

### Post by The Dragon Master on 2014-04-20
Have you tried this?

[http://www.dedoimedo.com/computers/ubuntu-ringtail-nvidia.html](http://www.dedoimedo.com/computers/ubuntu-ringtail-nvidia.html)

I've tried all the first three methods, but they all fail for me 
(see thread [http://ubuntuforums.org/showthread.php?t=2218239](http://ubuntuforums.org/showthread.php?t=2218239))

good luck

---

### Post by ivan-janes on 2014-04-20
Do you have a hybrid graphics card ? Wiki for this is on [https://wiki.ubuntu.com/X/Config/HybridGraphics](https://wiki.ubuntu.com/X/Config/HybridGraphics) .

You can try the following
1.) Remove bumblebee package and  delete file /etc/modprobe.d/bumblebee.conf

```
sudo apt-get remove --purge bumblebee* 
sudo rm -f  /etc/modprobe.d/bumblebee.conf

```

Bumblebee blacklists nvidia driver and prevents it from loading.

2.) Install nvidia-331-updates driver and nvida-prime packages from official repositories.
```
sudo apt-get install nvidia-331-updates nvidia-prime
```


3.) Reboot machine
```
sudo reboot
```

---

