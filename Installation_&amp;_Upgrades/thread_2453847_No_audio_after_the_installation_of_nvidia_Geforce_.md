---
title: "No audio after the installation of nvidia Geforce RTX"
date: 2020-11-18
forum: Installation &amp; Upgrades
---

### Post by tara_ons on 2020-11-18
I have installed nvidia-driver-455 for GeForce RTX 3070 on ubuntu 18.04.5 LTS 
After that, there is no sound over the headphone.

alsa-info is 
[http://alsa-project.org/db/?f=cf8cb96afc6dc465dd0b9e75233c6947dc7ab7cb](http://alsa-project.org/db/?f=cf8cb96afc6dc465dd0b9e75233c6947dc7ab7cb)

---

### Post by mastablasta on 2020-11-18
upgrade the kernel - version says:  [COLOR=#000000]Ubuntu 18.04.3 LTS

more here: [/COLOR]https://wiki.ubuntu.com/Kernel/LTSEnablementStack
[COLOR=#000000]and here: [/COLOR]https://ubuntu.com/about/release-cycle[COLOR=#000000]

current version of the 18.04 version is 18.04.5 LTS or if you want to stay with the kernel from 2017 you would use 18.04.1

you have latest hardware so you need latest kernel. so using 20.10 might also help. 
[/COLOR]

---

### Post by tara_ons on 2020-11-18
But before installing nvidia-driver-455, the sound over the headphone was working.

---

### Post by tara_ons on 2020-11-18
Please check alsa-info: [http://alsa-project.org/db/?f=bd609e4fbf9e108ce1b653fa491d7d0664b92010](http://alsa-project.org/db/?f=bd609e4fbf9e108ce1b653fa491d7d0664b92010)
I already have 18.04.5 LTS and 5.4.0-54-generic.

---

### Post by mastablasta on 2020-11-18
is the intel chip still set as default for audio output or did nvidia take that place? in KDE this is in system settings and i had issue getting the ouput to headphones connected to the front. until i realised it didn't switch from back output to the front one at all when i plugged them in. after correcting the settings sound works as expected.

anyway nvidia has HDMI output that is also using it's own sound chip for output. at least that's how the OS sees it.

i am not sure but maybe alsamixer can also select the default chip. oh by the way run alsamixer in terminal and make sure nothing is muted and that you have volume set to propper levels.

---

