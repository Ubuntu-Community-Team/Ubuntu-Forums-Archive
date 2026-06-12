---
title: "problem with sources.list"
date: 2010-11-14
forum: Installation &amp; Upgrades
---

### Post by ydm39 on 2010-11-14
Hi .. I've heard many positive comments about Avant Window navigator so I installed it , but now when I want to acces to Synaptic or ubuntu software center  I got this message : 

 E: Tipo 'ain' desconocido en la línea 3 de lista de fuentes  /etc/apt/sources.list.d/awn-testing-ppa-maverick.list
 E: No se pudieron leer las listas de fuentes.

 I dont know what to do in this situation.

Thanks in advance!!!

---

### Post by sikander3786 on 2010-11-14
Hi.

I couldn't completely understand that message because it is in some other language.

However it is suggesting that their is some problem with awn testing ppa.

Go to Software Center > Edit > Software Sources > Other Software Tab and uncheck the awn ppa entry.

Reload the repository information when prompted and try to open Synaptic again. If it doesn't work, please change your language to English and post the output of

```
sudo apt-get update
```

---

