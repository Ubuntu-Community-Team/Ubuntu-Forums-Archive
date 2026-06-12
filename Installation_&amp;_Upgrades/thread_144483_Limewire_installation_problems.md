---
title: "Limewire installation problems"
date: 2006-03-14
forum: Installation &amp; Upgrades
---

### Post by ecandelas on 2006-03-14
I've  been trying to install limewire following the instruccions page found in the ubuntu documentation guide, but when i try the command: 

 *wget -c [http://frankandjacq.com/ubuntuguide/LimeWireOther.zip](http://frankandjacq.com/ubuntuguide/LimeWireOther.zip) *

the terminal displays the next error message:

[I]Resolviendo frankandjacq.com... 66.246.156.115
Connecting to frankandjacq.com|66.246.156.115|:80... conectado.
Petición HTTP enviada, esperando respuesta... 404 Not Found
10:32:42 ERROR 404: Not Found.[/I]

Somebody knows what i can do, must i try another source?, what could it be?

---

### Post by taurus on 2006-03-14
I believe you can use Automatix to install Limewire BUT why not use Frostwire since it's an open source of Limewire and there won't be any more of that annoying message about upgrading to the pro version...

---

### Post by ecandelas on 2006-03-14
Thank you, i'm going to start looking about it, i will tell how it goes.

---

### Post by s_spiff on 2006-03-15
well tired installing forstwire...using their deb package...but the damn thing won't start!

---

### Post by paul_and_ball on 2007-10-16
I ran into a similar problem. It turned out to be a simple fix.

I tried to install LimeWire, but it would never finish installing the dependencies. I then tried to install FrostWire, which also encountered errors.

At this point I ran my Terminal and typed:

sudo dpkg --configure -a

sudo apt-get install -f

That was it. Follow the on screen instructions and you are set!

Hopefully I remembered correctly, but I was able to install and run LimeWire.

---

