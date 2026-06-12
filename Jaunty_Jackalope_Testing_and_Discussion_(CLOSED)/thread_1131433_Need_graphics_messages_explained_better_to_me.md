---
title: "Need graphics messages explained better to me"
date: 2009-04-20
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by DougieFresh4U on 2009-04-20
I am gonna try again to get a better understanding of my graphics, so please bear with me:
Machine is: AMD Athlon dual 5200 with an ATI Radeon HD 3200 onboard graphics.
Messages from terminal are as follows:
```
dougie@DougiesLeanMachine:~$ lspci -nn | grep VGA
01:05.0 VGA compatible controller [0300]: ATI Technologies Inc Radeon HD 3200 Graphics [1002:9610]
```
```
dougie@DougiesLeanMachine:~$ glxinfo |grep vendor
unknown chip id 0x9610, can't guess.
server glx vendor string: SGI
client glx vendor string: SGI
OpenGL vendor string: Mesa Project
```
```
dougie@DougiesLeanMachine:~$  glxinfo | grep "direct rendering"
unknown chip id 0x9610, can't guess.
direct rendering: Yes
```
Direct Rendering I have - thats good
Questions:
What does 'unknown chip' mean, as I see it twice from terminal?
What is my graphics chipset considered, as I see where it's mentioned some times '5xx or 6xx series etc. Therefore, when I am trying to gather info, I know what to look for as far as installing drivers because I see nothing in 'Synaptic' saying 'ATI 3200' or 'Radeon 3200'.
Sorry for asking 'stupid' questions, but I have always worked with 'Intel' and I am new to this AMD and ATI and Radeon stuff.
Thanks and I hope some one can explain it in 'simple' terms

---

### Post by ktp on 2009-04-20
This might help:

[http://www.phoronix.com/scan.php?page=article&item=amd_780g_linux&num=1](http://www.phoronix.com/scan.php?page=article&item=amd_780g_linux&num=1)
[http://www.amd.com/us-en/0,,3715_15532,00.html](http://www.amd.com/us-en/0,,3715_15532,00.html)

---

