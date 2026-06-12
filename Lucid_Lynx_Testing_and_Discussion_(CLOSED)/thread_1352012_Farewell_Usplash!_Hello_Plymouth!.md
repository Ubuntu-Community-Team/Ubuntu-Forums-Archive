---
title: "Farewell Usplash! Hello Plymouth!"
date: 2009-12-11
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by MacUntu on 2009-12-11
Plymouth 0.8.0 got uploaded to universe yesterday. I have no KMS enabled system (currently compiling Nouveau's KMS kernel), so can anyone check if it's already doing something?

---

### Post by philinux on 2009-12-11
> **MacUntu said:**
> Plymouth 0.8.0 got uploaded to universe yesterday. I have no KMS enabled system (currently compiling Nouveau's KMS kernel), so can anyone check if it's already doing something?

I installed the new gdm which removed usplash. Are we supposed to install plymouth. Is it ready?

---

### Post by MacUntu on 2009-12-11
Installed plymouth 0.8.0~-4 + the new GDM and the Nouveau kernel with KMS support (which worked weeks ago) - not working here. Yet. :)

---

### Post by Starks on 2009-12-11
Working perfectly on Intel.

It's basically the white Ubuntu logo from Usplash with the word "Ubuntu" next to it.

It doesn't throb or do anything fancy. That may change down the line though.

---

### Post by MacUntu on 2009-12-11
Can't get it to work with the 2.6.32-based Nouveau kernel tree [0]. :-( According to Xorg.0.log, KMS should be there:

```
[    0.324475] (--) NOUVEAU(0): [drm] kernel modesetting in use
```

Framebuffer's there too:

```
$ cat /proc/fb 
0 nouveaufb

```

Can you start it from within a running session somehow (like 'sudo plymouth --show-splash'?)

[0] [http://nouveau.freedesktop.org/wiki/InstallDRM](http://nouveau.freedesktop.org/wiki/InstallDRM)

---

### Post by plun on 2009-12-11
Well, its broken also with my laptop running a crappy ATI X300 card.

I refuse to use any nouveu-crap on my desktop....:D

nVidia 8600 running a pure nVidia driver...

---

### Post by Starks on 2009-12-11
Linux Intel drivers are quite incredible right now. The i945 can now do things on Linux that were never thought possible on Windows like OpenGL 2.0 and GLSL 1.2. Need I remind you that the i945 was designed for OpenGL 1.4 and had only partial support 1.5?

---

### Post by MacUntu on 2009-12-12
For those of us that cannot yet enjoy Plymouth:

Clip from Phoronix: [http://www.youtube.com/watch?v=PtDnJP9bAXs](http://www.youtube.com/watch?v=PtDnJP9bAXs)

Clip from keybuk (of course the better one :P): [http://www.youtube.com/watch?v=rhjyYgIPFvc](http://www.youtube.com/watch?v=rhjyYgIPFvc)

---

### Post by caryb on 2009-12-12
> **plun said:**
> Well, its broken also with my laptop running a crappy ATI X300 card.

[COLOR="Red"]I refuse to use any nouveu-crap on my desktop....:D[/COLOR]

nVidia 8600 running a pure nVidia driver...

Thats a tad harsh! there are lots of kind folks who pour there heart & soul to write/test this software & to denigrate it is not the spirit of open source software. 


2c Cary

---

### Post by kevpan815 on 2009-12-12
It Removed Usplash Here 2, However I Have No Problems 2 Report While Using The NVIDIA 195.22 Beta Device Driver With My NVIDIA GeForce 8800 GT.

---

### Post by scradock on 2009-12-12
Plymouth seems to be working on my ATI graphics - Radeon Express 200M. Usplash removed, will not be missed. Haven't managed to get the fsck progress bars visible yet - but there's lots of configuration apparently possible in there......

---

### Post by caryb on 2009-12-12
Does anyone know if Plymouth is going to be used on Kubuntu as well?



Cary

Just tried it it wants to remove kde-desktop so I guess the answer is no atm

---

### Post by gnomeuser on 2009-12-13
[Phoronix writes about and videos Plymouth in Lucid](http://www.phoronix.com/scan.php?page=news_item&px=NzgwMA)

---

### Post by plun on 2009-12-13
Works for me with kernel 2.8.32-8 which is available now with Synaptic.

Dell laptop with ATI/X300 graphic.

---

### Post by red_team316 on 2009-12-13
> **caryb said:**
> Does anyone know if Plymouth is going to be used on Kubuntu as well?



Cary

Just tried it it wants to remove kde-desktop so I guess the answer is no atm

It should be, I had no problems using plymouth on Jaunty with Kubuntu. Considering it's a replacement for Usplash(which is on both ubuntu and kubuntu), and not GNOME/KDE-specific.

---

### Post by caryb on 2009-12-13
> **red_team316 said:**
> It should be, I had no problems using plymouth on Jaunty with Kubuntu. Considering it's a replacement for Usplash(which is on both ubuntu and kubuntu), and not GNOME/KDE-specific.

Works no problems. 

Thanks Cary

---

### Post by ranch hand on 2009-12-13
I installed it on my "throw away" installation and it now takes a while to boot because it has to run all the "low graphics mode" notices.

Other than that it looks pretty much the same.

---

### Post by k3lt01 on 2009-12-13
My system isn't even trying to install it in any way shape or form.:-|

---

### Post by ranch hand on 2009-12-13
I just got it from the repo in synaptic and installed it.

---

### Post by Taoye on 2009-12-13
Works on my Thinkpad w/Kubuntu... looks the same as usplash but with the word ubuntu next to the logo. I don't think they're ready for it though, since removing usplash also removes kubuntu-desktop.

---

