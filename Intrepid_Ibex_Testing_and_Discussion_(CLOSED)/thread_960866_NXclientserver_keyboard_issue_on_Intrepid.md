---
title: "NXclient/server keyboard issue on Intrepid"
date: 2008-10-27
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by rdoolen on 2008-10-27
I have NXserver running on my desktop, running 8.10. When I use the NX client from Windows or from 8.04 everything works fine. But, when I upgraded my client machine to 8.10, the keyboard mapping is wrong. For instance, the arrow keys don't work, the up arrow take a screen shot. 

I assume this has to do with the new way Xorg (or HAL) deals with the keyboard and the info the client is sending to the server is not properly interpreted by the server.

I looked at my Xorg.conf and all the keyboard settings are commented out claiming that HAL configures the keyboard now. I tried uncommenting the keyboard settings and restarting X, but that didn't help. 

I found a work around [_here_]("http://ph.ubuntuforums.com/showthread.php?t=945199&"), but I would rather fix it. 

Any thoughts?

---

### Post by rdoolen on 2008-10-28
Can anyone recomend a better forum for this question? NoMachine didn't seem to have one, maybe a different subject on the Ubuntu forum?

---

