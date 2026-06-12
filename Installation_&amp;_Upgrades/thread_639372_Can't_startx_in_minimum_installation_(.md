---
title: "Can't startx in minimum installation :("
date: 2007-12-13
forum: Installation &amp; Upgrades
---

### Post by nmt on 2007-12-13
Hi everybody!
I followed the tutorial here :
[HTML]https://help.ubuntu.com/community/Installation/LowMemorySystems[/HTML]
but after installed xorg, I can't startx. This is the message :
[IMG]http://i250.photobucket.com/albums/gg244/galachachomato/asd.jpg[/IMG]
What should I do now ?:confused:
Thx, goodluck and have fun :KS

---

### Post by Pumalite on 2007-12-13
Post your specs.

---

### Post by nmt on 2007-12-13
Here my specs:
MSI k9n6gm, AMD Athlon 64 X2 4400+, VGA onboard NV Ge 6100 nforce 405
and I used Ubuntu alternate x86_64.

---

### Post by PmDematagoda on 2007-12-13
Did you do:-

```
sudo dpkg-reconfigure xserver-xorg
```

or if that does not work:-

```
sudo dpkg-reconfigure -phigh xserver-xorg
```

Also did you ensure that the Nvidia drivers are installed properly?

---

### Post by nmt on 2007-12-13
> **PmDematagoda said:**
> Did you do:-

```
sudo dpkg-reconfigure xserver-xorg
```

or if that does not work:-

```
sudo dpkg-reconfigure -phigh xserver-xorg
```

Also did you ensure that the Nvidia drivers are installed properly?

I tried but it didn't work :(
btw, how can I know that the Nvidia drivers are installed properly? I didn't see any error message during the installation.

---

### Post by PmDematagoda on 2007-12-13
How did you install the Nvidia drivers?

---

### Post by nmt on 2007-12-13
I installed command-line system from alternate 64bits CD and it didn't prompt me to install driver.

---

### Post by PmDematagoda on 2007-12-13
Ok, so then you will need to use the vesa drivers.

Do:-

```
sudo dpkg-reconfigure -phigh xserver-xorg
```

---

### Post by nmt on 2007-12-15
It worked great.
Thank you very much.:KS

---

### Post by PmDematagoda on 2007-12-15
I was glad to help:).

But there is one problem when you are using the vesa drivers, that being the fact that you cannot use eye-candy such as Compiz-Fusion and you may not be able to use some graphics applications, so if you do want to use the Nvidia driver then I can help you with process of getting the Nvidia drivers installed.

---

### Post by nmt on 2007-12-15
I appreciate it. I want to build a simple, light system that contains only softwares which I need. So I think nvidia driver isn't too necessary.
After all, thank you very much for helping me.:KS

---

### Post by PmDematagoda on 2007-12-15
Ok, no problem, and once again, it was my pleasure to help:).

Wish you a Happy Holiday Season and a Merry Christmas:lolflag:.

---

### Post by nmt on 2007-12-15
Best wishes for you <:-p

---

