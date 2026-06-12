---
title: "Linksys Notebook Adapter"
date: 2007-04-24
forum: Installation &amp; Upgrades
---

### Post by hatewindows on 2007-04-24
I'm using ubuntu 7.4 on my dell notebook insprion 8200.. Ubuntu works 100% infact its flawless--However my LINKSYS wireless adaptor wont work.. My question is simple-Is there a quick fix for this problem? I was wondering if i can download some sort of driver. The power light comes on when the adaptor is plugged in--but thats it.. Thank you all for any help..   Mark

---

### Post by JerseyShoreComputer on 2007-04-24
Try this, it worked for me in Edgy and still works in Fiesty:


1. Install ndiswrapper (Synaptic Package Manager)
2. Put in the CD that came with the card
3. TYPE: sudo ndiswrapper -i /cdrom/linksys/drivers/w2k/lsbcmnds.inf
--> NOTE: Check the directory on your CD for the above. You will use the Win 2k or XP driver
4. TYPE: sudo ndiswrapper -m (This will make the driver auto load)
5. TYPE: sudo depmod -a (If you get no errors, all is fine)
6. TYPE: sudo modprobe ndiswrapper
7. Install WiFi Radar from the Synaptic package manager
8. Turn off the computer.
9. Turn the computer back on WITHOUT the wireless card installed. Make sure that your ETH0 if not hooked up live either.
10. After you logon and Ubuntu loads, insert the wireless card.
11. Run WiFi Radar and configure your card, then click CONNECT
12. Switch the network adapter to WLAN0

You may need to substitute the .inf file for the one that came with your adapter. Also, if you are using Fiesty, try to get it to work without WiFi Radar first. If no luck, then install it.

I hope it works for you!

---

### Post by hatewindows on 2007-04-24
WOW! I thought for sure there was an easy way....I guess i cant download a linksys driver for linux-and simply install?

---

