---
title: "nvidia problem on laptop"
date: 2007-03-08
forum: Installation &amp; Upgrades
---

### Post by aknight_sa on 2007-03-08
hi guys, i am new to linux so please be patient with me...

i am trying to install the nvidia drivers on my laptop "Toshiba Satellite S2410" which has a Nvidia GeForce4 420 GO display addapter in it.. 

i have downloaded the driver "NVIDIA-Linux-x86-1.0-9746-pkg1.run" but its giving me problems with the kernel... does anyone have a step by step for newbies on how to do such upgrades...

also when i try the glxgears it gives me this error:
[COLOR="Blue"]
Xlib:  extension "GLX" missing on display ":0.0".
Error: couldn't get an RGB, Double-buffered visual[/COLOR]


please help me out guys

---

### Post by chewearn on 2007-03-08
Why don't you use the stable driver in the repo.  Use Synaptic, search for nvidia-glx.  Install it, then run this command in terminal:
```
sudo nvidia-glx-config enable
```

---

### Post by watson540 on 2007-03-08
in order to build the kernel module you need build-essential and kernel headers, you also need libc6-dev. the driver in the repo's never worked for me so i wouldnt bother with it. 
apt-get install build-essential libc6-dev linux-headers-2.6.17-10 linux-headers-generic

something like that :)

---

### Post by chewearn on 2007-03-08
> **watson540 said:**
> in order to build the kernel module you need build-essential and kernel headers, you also need libc6-dev. the driver in the repo's never worked for me so i wouldnt bother with it. 
apt-get install build-essential libc6-dev linux-headers-2.6.17-10 linux-headers-generic

something like that :)

I'm sure the driver in the repo works for a lot of people.  I would think this should be the first thing to try.  Next thing to try would be using Envy or Automatix2.  Then, if really desperate, we can talk about teaching compiling kernel module to newbies, no?

---

### Post by watson540 on 2007-03-08
nah, why make an extra step, i have a very similar card to his, everyone i talk to with the go series says nvidia-glx dont work. its not like its real hard work or anything. but yes i like the idea of envy or whichever one installs the driver for you

---

