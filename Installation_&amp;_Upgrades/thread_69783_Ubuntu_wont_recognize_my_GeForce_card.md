---
title: "Ubuntu wont recognize my GeForce card?"
date: 2005-09-27
forum: Installation &amp; Upgrades
---

### Post by phlawed on 2005-09-27
in xorg.conf it says NVIDIA Corporation NV40? [Unknown nVidia Card]

its a PNY GeForce 6200 Verto why is ubuntu not recognizing it even after nvidia drivers installed

---

### Post by brentoboy on 2005-09-27
which driver is your xorg.conf loading?
nvidia
nv
vesa
?
It would be listed right after the vidio card name where you got the other info.

---

### Post by phlawed on 2005-09-27
[QUOTE=brentoboy]which driver is your xorg.conf loading?
nvidia
nv
vesa
?
It would be listed right after the vidio card name where you got the other info.[/QUOTE]

it began with nv after the nvidia driver install with NO errors i changed it to nvidia, nothing, gdm wouldnt load even tried rebooting nothing, so i changed it back to nv, nothing still wouldnt start gdm

---

### Post by FLeiXiuS on 2005-09-27
What's your Xorg.0.log say? 

cat /var/log/Xorg.0.log|grep EE

---

### Post by phlawed on 2005-09-27
[QUOTE=FLeiXiuS]What's your Xorg.0.log say? 

cat /var/log/Xorg.0.log|grep EE[/QUOTE]

nothing i did a reinstall, was trying to solve this before reinstalling agian

---

### Post by brentoboy on 2005-09-27
change it to "vesa" (just for now) it will make you feel better.  vesa is the driver that has no optimizations, so it works in most scenarios.  gdm will start to work again.

once you feel the rush of relief, let it soak in before you push forward.  functional desktops are a wonderful thing :)

dont let it worry you too much, I have a 6200 nvidia chip and I got the nvidia driver pumping and all the games and stuff work, but before you get started with that, lets get your desktop up again.

When you are ready, follow these directions...  they worked great for me with the same graphics card.

[http://www.ubuntuforums.org/showthread.php?t=57368](http://www.ubuntuforums.org/showthread.php?t=57368)

---

### Post by phlawed on 2005-09-27
k driver installed and got the splash screen BUT!

glx gears seems really crappy. A friend of mine is running a card 1-2 years older than mine and is getting twice the fps.

without cheating im only getting like 1800fps. he is well into the 3000 mark. 

we both are running amd 2400+

i have 512mb ram, oh his card is only 64mb and mine is 128mb why so crappy on glxgears :confused:

---

### Post by darkmatter on 2005-09-28
[QUOTE=phlawed]k driver installed and got the splash screen BUT!

glx gears seems really crappy. A friend of mine is running a card 1-2 years older than mine and is getting twice the fps.

without cheating im only getting like 1800fps. he is well into the 3000 mark. 

we both are running amd 2400+

i have 512mb ram, oh his card is only 64mb and mine is 128mb why so crappy on glxgears :confused:[/QUOTE]

glxgears is not a benchmarking utility, don't let the numbers bother you. All it is really good for is testing to see if  3D acceleration is enabled.

---

### Post by Biased turkey on 2005-09-28
A sure way to check that 3D acceleration is enabled is to run the "glxinfo" command.
If you see "direct rendering Yes" that's because 3D acceleration is enabled.

---

