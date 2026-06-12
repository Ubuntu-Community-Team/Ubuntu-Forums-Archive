---
title: "No network card in Ubuntu on new PC?  Help!"
date: 2006-09-17
forum: Installation &amp; Upgrades
---

### Post by princemackenzie on 2006-09-17
Well, I have just tried to install ubuntu with no luck on my new PC.

Everything works and is detected with the critical exception of my network card.  I can't see my cheap Zyxel router, but the network monitor indicates I am sending out a lot of packets and receiving none.

The system is a 3500+ AMD64 with 1 GB DDR2 800mhz.  The motherboard has an Nvidia North/Southbridge, GeForce6100/430 respectively.

According to the manual, its a Marvell 88E1116 Gigabit Ethernet chipset, but windows sees it as "nvidia networking device".  Any help is appreciated... I can't wait to start with Ubuntu now that I have a new machine to run it on!! :)

---

### Post by baldy1324 on 2006-09-17
hmmm thats weird that it wont recognize it, google says it regularly works. maybe its supported in a newer kernel, ubuntus next release should be coming out in about 1-2 months, which will a new kernel (recognizes hardware). if you are anxious download, the new alpha release of edgy is here [http://cdimage.ubuntu.com/releases/edgy/knot-3/](http://cdimage.ubuntu.com/releases/edgy/knot-3/).

---

### Post by princemackenzie on 2006-09-17
I'm not really ready to move to the alpha edgy, so I googled around a bit and found

[http://www.killminus9.net/index.php?article=15](http://www.killminus9.net/index.php?article=15)

He seems to indicate forcedeth might work, so I'm gonna go give that a shot before going alpha.  Any other suggestions would be appreciated!

EDIT: **Nope!**  Any ideas???

---

