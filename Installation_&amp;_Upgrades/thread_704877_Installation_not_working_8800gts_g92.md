---
title: "Installation not working 8800gts g92"
date: 2008-02-22
forum: Installation &amp; Upgrades
---

### Post by littleims10 on 2008-02-22
Hello,
 I just got the Ubuntu 7.10 live cd. I tried installing today and after it loaded, I got an "X" in the center of my screen. It then told me that I have to configure my monitor and graphics card myself. So I picked the geforce 8 series driver and an LCD 1680x1050. After that, it brought me to 4 lines of text that looked like this...

(cant remember the text so i put x's)

XXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX                     [OK]
XXXXXXXXXXXXXXXXXX XXXXXXXXXXXXXXXXXX XXXXXX           [OK]
xXXXXXXXXXXXXXXXXXXXXXXX xXXXXXXXXXXXXXXX                [OK]
XXXXXXXXXXXXXXXXXXX XXXXXXXXXXXXXXXXXXXXXXX            [OK]
I

All i could do from here is type words but nothing else happened.

What should I do/try?

---

### Post by Partyboi2 on 2008-02-22
you probably need to install the driver from nvidia. Boot into recovery mode from the grub menu. If you do not see the grub menu screen when you boot you will need to press ESC when you see something like stage1_5.... . Once you have have arrived at a terminal make sure you have build-essential installed
```
apt-get install build-essential
```then download the driver from nvidia
```
wget http://us.download.nvidia.com/XFree86/Linux-x86/169.09/NVIDIA-Linux-x86-169.09-pkg1.run
``` then start the nvidia installer and follow it through 
```
sh NVIDIA-Linux-x86-169.09-pkg1.run
```then ```
startx
``` or ```
reboot
```

---

