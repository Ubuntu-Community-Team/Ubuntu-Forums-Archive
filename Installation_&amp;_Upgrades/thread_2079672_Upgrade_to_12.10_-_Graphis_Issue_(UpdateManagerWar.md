---
title: "Upgrade to 12.10 - Graphis Issue (UpdateManagerWarningForUnity3D)"
date: 2012-11-02
forum: Installation &amp; Upgrades
---

### Post by FernandoLB on 2012-11-02
I was starting an upgrade to 12.10, and received a warning telling
me to take a look at:
    [https://wiki.ubuntu.com/X/Bugs/UpdateManagerWarningForUnity3D](https://wiki.ubuntu.com/X/Bugs/UpdateManagerWarningForUnity3D)

It is a laptop Philco, 14H-V143LM. lspci | grep 'VGA' says:
"Intel Corporation Atom Processor D2xxx/N2xxx Integrated Graphis Controller."
(It actually shows those "x").

It is a 4BG RAM laptop, so, I can't believe it is that old...

Do all that mean that this computer will never be able to use a newer version
of Ubuntu?

---

### Post by dino99 on 2012-11-02
that means you does not have hardware 3D capable. So use an other DE like lxde (lubuntu) or xfce (xubuntu). Simple remove : ubuntu-desktop, unity, and install the other DE of your choice, or stay with Precise which have unity 2d

---

### Post by FernandoLB on 2012-11-02
> **dino99 said:**
> that means you does not have hardware 3D capable. So use an other DE like lxde (lubuntu) or xfce (xubuntu). Simple remove : ubuntu-desktop, unity, and install the other DE of your choice, or stay with Precise which have unity 2d

Well, I found a 12.04 cd here, installed it, and everything was working perfectly. On the other side, I installed 12.10 on my sony vaio, and the dash is terribly slow to when searching things (even when typing).

I used to use arch linux with gnome 2.x on this vaio, with a lot of compiz effects enabled, and it worked fine. On this philco laptop, since it worked with 12.04, I don't think it is lack of 3D capabilities (I'm not arguing, I just think so).

---

### Post by ARooster on 2012-11-16
I do believe Intel HD 4000 graphics support OpenGL 3.0 3D graphics engine so I don't believe the 3D would be an issue, after all, you're running an operating system's 3D graphical user interface, not playing the latest installment of Crysis or Call of Duty!

Having said that, I've also had a slow and buggy experience with my nVidia 8800 graphics card (that had no problems with any version of Windows or with Ubuntu 12.04) so my guess would be that it is a graphic card driver/Unity issue.

Perhaps you could try
```
sudo apt-get install --reinstall xserver-xorg-video-intel    
```

While I do agree with you about 3D graphics support not being an issue I have to say I am currently trying out xfce desktop on Ubuntu and it seems quite fast, responsive and more stable than Unity.

---

### Post by FernandoLB on 2012-11-16
I have been using arch linux with openbox and tint2 for about two years, but somtimes I miss some eye candy and some other functionality DEs usually provide. By the way, I reinstalled arch linux in my laptop, and gnome3 works smoothly. Just for the sake of context, gnome3 never worked well here. I could never get its "expose" effect to run in a smooth way. Ubuntu always did (actually now, just the dash is slow and laggy). Now that ubuntu does not any more, gnome3.6.2 does. I don't understand our beloved linux distributions any more.

---

