---
title: "[solved] Ubuntu Shutsdown after NVidia Driver Update"
date: 2022-12-05
forum: Installation &amp; Upgrades
---

### Post by holysword on 2022-12-05
My system started to show strange behaviour concerning fans i.e. they turn on way more often than before and at a clearly higher speed. I already checked the temperatures when this happens and it feels like there is something wrong with the sensors: running the laptop with the chassis open, the CPU and GPU were barely above room temperature but lm-sensors were indicating consistently ~90°C.

I first suspected that this was hardware related (I did clean up/change the thermal paste a few times in the past, and I was afraid that I had ruined something). But my most recent test was with some Steam games. The laptop turns off immediately when the game "Stray" shows the "Start Game" option. Another game, "Nier Automata" runs on 1600x900. The computer shutdown the moment I select 1920x1080 in the game menu. Most games will shutdown the laptop abruptly when I try a specific thing, independent on temperature.

This started happening after a mini-cleanup of the system, where I also updated from nvidia-drivers-410. I'm trying to rollback to this version but it does not exist anymore. nvidia-driver-418 installs 470 instead, and the behaviour is the same. I already tried 525, 515 and 470. I tried to use the nvidia-installer from their website, but it fails to compile the kernel modules.

I re-installed everything to Ubuntu 22.04. Still the same. The graphic card is RTX 2060 and if you must know, the machine is this:
[https://www.amazon.com/Acer-i7-9750H-MaxxAudio-Keyboard-AN515-54-728C/dp/B08777BH1B](https://www.amazon.com/Acer-i7-9750H-MaxxAudio-Keyboard-AN515-54-728C/dp/B08777BH1B)


Any ideas?

---

### Post by holysword on 2022-12-06
Okay, I have a very unsatisfactory update: I opened the laptop once again, double checked all cables, closed it again and now it does not crash anymore. Nothing was looking poorly connected, so I am assuming some cables are not in the best shape.

I'm still having some strange issues though:
 - sensors report temperature close to 95°C quite often for CPU. Fans are working, but the CPU is not hot on touch. 
 - I am using an external monitor (4K). It works but there is a barely noticeable sluggishness.
 - if I disable the laptop screen (either in KDE or Enlightenment or Gnome) the 4K screen becomes unusable (something like 1 frame per 3 or 4 seconds). I need to keep both screens on
 - games are painfully slow now, in comparison to pre-update

---

### Post by holysword on 2022-12-07
Okay... prime-select nvidia solved the problems...

---

