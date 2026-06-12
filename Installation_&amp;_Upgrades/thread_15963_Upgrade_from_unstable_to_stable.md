---
title: "Upgrade from unstable to stable ?"
date: 2005-02-18
forum: Installation &amp; Upgrades
---

### Post by milou on 2005-02-18
Hello. I would want to know if a dist-update/upgrade will upgrade a unstable hoary distro into the "stable" one when it is available ... In other words, is the 'dist-upgrade' command only to upgrade from stable to stable, or is it ok to upgrade from a testing distro like hoary Array5 for ex. into Stable Hoary Hedgedog. 
Thank you

Eric

---

### Post by CyrilleMortreux on 2005-02-18
[QUOTE=milou]Hello. I would want to know if a dist-update/upgrade will upgrade a unstable hoary distro into the "stable" one when it is available ... In other words, is the 'dist-upgrade' command only to upgrade from stable to stable, or is it ok to upgrade from a testing distro like hoary Array5 for ex. into Stable Hoary Hedgedog. 
Thank you

Eric[/QUOTE]


apt-get dist-upgrade is used for example to upgrade all the distri from a version to another one. 

Stable --> Unstable
Warty --> Hoary


Most of time, if you don't change your distri version, you may use "apt-get update" and then run "apt-get upgrade", that going to upgrade the packages only, not the core system.

---

### Post by milou on 2005-02-18
I see for warty -> "unstable" hoary, but what about "unstable" hoary -> "stable" hoary (when it's out) ?Will you use apt-get dist upgrade ?

---

### Post by CyrilleMortreux on 2005-02-18
[QUOTE=milou]I see for warty -> "unstable" hoary, but what about "unstable" hoary -> "stable" hoary (when it's out) ?Will you use apt-get dist upgrade ?[/QUOTE]

Until someone tells me I am wrong : yes !

This the way I managed my Debian boxes and Ubuntu gets, I think, the same mechanisms.

---

