---
title: "[SOLVED] Graphics setup in Intrepid Ibex"
date: 2008-10-22
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by RJWEcology on 2008-10-22
Hello, 

I've just upgraded from 8.04 to 8.10 and everything is working very well except for my graphics setup. 

I have an ATI Radeon 9600 Pro card with an Acer AL511 Monitor. 

This is my xorg.conf file:


```
Section "Module"
	Load	"dri"
	Load	"GLcore"
EndSection

Section "Device"
	Identifier	"Default Device"
	Driver	"vesa"
EndSection
```

```
rich@Obsidian:~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: Mesa Project
OpenGL renderer string: Software Rasterizer
OpenGL version string: 1.4 (2.1 Mesa 7.2)
```

Whenever I start up, I get an error saying I have to run in low graphics mode. When I try to load EnvyNG, it says it's already loaded and installed the 8.5 drivers. Also, ATI catalyst control center doesn't work or load up now. No matter how many times I load up the screen setup box, it always says it's running on a plug and play monitor (despite telling it over and over what my monitor is).  

Sorry if this has been repeated before. Any help would be greatly appreciated.


EDIT:

I just restarted and now when I check fglrxinfo I get this:

> rich@Obsidian:~$ fglrxinfo
X Error of failed request:  BadRequest (invalid request code or no such operation)
  Major opcode of failed request:  143 (GLX)
  Minor opcode of failed request:  19 (X_GLXQueryServerString)
  Serial number of failed request:  10
  Current serial number in output stream:  10


Why has this changed!?

---

### Post by sdowney717 on 2008-10-22
I am in the same boat. I have a 9600 se 64 mb AGP card in an 82875 intel server board.
It always loads low graphics mode, cant detect hardware issue
And I tried loadig envyng

---

### Post by RJWEcology on 2008-10-22
I managed to fix it by fiddling with all the setting until it accepted.

---

