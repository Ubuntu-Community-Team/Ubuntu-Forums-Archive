---
title: "After install nvidia drivers my screen has problems"
date: 2007-09-19
forum: Installation &amp; Upgrades
---

### Post by ili on 2007-09-19
After re-install feisty fawn by 7th time i could install properly the drivers of nvidia using this guide: [http://albertomilone.com/latest_nvidia_udsf_feisty.html](http://albertomilone.com/latest_nvidia_udsf_feisty.html), well that is what i think because i can see the animation typing the "glxgears".My problem is if i open firefox or any other application i gete this [[IMG]http://img207.imageshack.us/img207/9344/97978026xd5.th.jpg[/IMG]](http://img207.imageshack.us/my.php?image=97978026xd5.jpg).
Editing th xorg file i could get more resolution to my screen but then my keyboard config change to us when i had it in  latin:(:( 
My video card is an old one GeForce2 MX Integrated Graphics with 32 MB... 
can anyone help to me???

---

### Post by w4ett on 2007-09-20
Change your xorg.conf manually like this:

```
sudo dpkg-reconfigure [COLOR="Red"]-phigh[/COLOR] xserver-xorg
```

The [COLOR="Red"]-phigh[/COLOR] toggle enables reconfiguration of the video driver and resolutions only, without affecting your keyboard or mouse settings

Good Luck.

---

### Post by ili on 2007-09-21
that doesn´t work :( maybe i will unistall the nvidia and just will work without the eye candys..
if i update  the pc restarts...damn

---

