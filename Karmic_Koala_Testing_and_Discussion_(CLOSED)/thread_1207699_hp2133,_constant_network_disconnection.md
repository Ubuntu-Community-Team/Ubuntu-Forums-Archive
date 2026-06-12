---
title: "hp2133, constant network disconnection"
date: 2009-07-08
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by puccaso on 2009-07-08
i dont know what the problem
im usually a dab hand at fixing this stuff
but with this problem i dont know where to start

i have a hp2133, and when the screen goes blank, the network connection goes, although networkmanager doesnt show any difference in the taskbar, 
the only thing that changes is that the bullet, or the selectino circle thing next to each broadcasting essid goes. 

so its like nothing is selected, but networkmanager still shows full bars in the task bar.

when i try to reconnect, it doesnt work
and i have to restart

i try to do a fake reboot, ie - sudo init 1, then resume from the recover screen to go back to the desktop but no luck

what do i have to do?

how do i trace the cause of the problem??

heres my lspci, 

```
02:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g (rev 01)

```

---

### Post by alSee on 2009-09-16
Hi, puccaso.
I have the same laptop. And this problem is cased by interference between the Broadcom and openChrome drivers.
Which Ubuntu do you use?
If 8.10 then I recommend you using native Chrome9 drivers from VIA site.
If later version then try openChrome driver patching or pre-compiled patched package from the [Bug #331952]("https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-openchrome/+bug/331952")

---

