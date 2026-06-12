---
title: "I got that graphical problem.."
date: 2013-04-17
forum: Installation &amp; Upgrades
---

### Post by ghostofdeath on 2013-04-17
Hi guys sorry if it's like the 100000000 post about graphical issue I'm not sure in which category I fall into that's why I'm posting.I have no graphic cards. Thats the photo of my screen, when I move around the mouse it keep bugging forever, can anyone tell me which of the solutions is suitable for me? 
PS: I had Win7 running fine, so it's not a motherboard or my monitor.[IMG]http://i46.tinypic.com/2larcs9.jpg[/IMG]

---

### Post by kc1di on 2013-04-17
hello ghostofdeath and welcome to Ubuntu,

first you must have a graphic/video card or your would have not display at all it's simply built into your motherboard.  What we need to know to help is what card it is using.  if you could go to a terminal and type the following command and list the output here we'll be able to tell.
```
lspci
```

---

### Post by ghostofdeath on 2013-04-17
Hey thanks! As listed in lspci:
NVIDIA Corporation C61 [GeForce 7025 / nForcec 630a]

---

### Post by grahammechanical on 2013-04-17
I suggest that since you are getting to a desktop, that you open System Settings>Software Sources>Additional Drivers tab and experiment with another video driver. I have given up using Nvidia drivers. They break things in my experience. I recommend Nouveau, the open source driver.

You are using 12.10 , are you not? It helps if you tell us the version of Ubuntu that you have. There are different instructions for 12.04. And there is a slight change in 13.04 from 12.10. Do you see how useful it is to know which version?

Regards.

---

### Post by ghostofdeath on 2013-04-17
Yes I'm using 12.10, I can't get almost anything working in desktop, if there are any instructions to make it work without it I would appreciate. I'll actually use this box just as a backup home server, I can even use windows again but I think linux is more stable and light :)
My main try would be sparkleshare and then crashplan, if you have any good suggestions besides installing desktop version (lighter for e.g) I appreciate.

---

### Post by kc1di on 2013-04-17
Hi Again,
With that card the Nvidia 310.xx driver should work.

you can install it in a terminal with the following command:

```
sudo apt-get install nvidia-experimental-310
```

---

### Post by ghostofdeath on 2013-04-18
Thanks it kinda worked out. My problem now is I don't see the common ubuntu UI, no bars (side, top) and no 'close,minimize' buttons in any window!

---

### Post by stinkeye on 2013-04-18
Reset unity to defaults and reload.
Bring up a terminal using ctrl+alt+t and run...
```
dconf reset -f /org/compiz/ && setsid unity
```

---

### Post by ghostofdeath on 2013-04-18
Xlib: extension "GLX" missing on display ":0.0"
Compiz (opengl) - Fatal: glXqueryExtensionsString is NULL for screen 0

> **stinkeye said:**
> Reset unity to defaults and reload.
Bring up a terminal using ctrl+alt+t and run...
```
dconf reset -f /org/compiz/ && setsid unity
```

---

