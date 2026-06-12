---
title: "Dell Broadcom B43XX Driver"
date: 2009-03-02
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by Onyxrune on 2009-03-02
Will Jaunty keep driver support for Dell Broadcom 43XX wireless cards, as does Intrepid 8.10?  

I use a Dell 1501 laptop with this wireless card installed.  Intrepid pworks well on this computer with the free Broadcom 43XX wireless driver made available through System>Administration>Hardware Drivers.  I'd like to upgrade to Jaunty without losing my wireless connectivity.

Thank you!
Onyxrune

---

### Post by yule0 on 2009-03-03
I'm typing this on a Dell with a Broadcom 43xx card and it works just as well as with Intrepid. The only issue is, you must have wired connectivity in order to install the driver (it has to download a package and extract/install it). 

After a restart your wireless connection will be there. By the way, I recommend wicd.

---

### Post by adult swim on 2009-03-03
if youve got a flash drive or other external media, before you install jaunty copy the folder /lib/firmware/b43 from your old install.  once you have upgraded, copy that into /lib/firmware then run ```
sudo modprobe b43

sudo /etc/init.d/networking restart

sudo ifconfig wlan0 up
``` and you should have your wireless running

---

### Post by masterkoppa on 2009-03-13
> **adult swim said:**
> if youve got a flash drive or other external media, before you install jaunty copy the folder /lib/firmware/b43 from your old install.  once you have upgraded, copy that into /lib/firmware then run ```
sudo modprobe b43

sudo /etc/init.d/networking restart

sudo ifconfig wlan0 up
``` and you should have your wireless running
Thank you so much this tip, I've been trying to get it to work for hours. Something I found noteworthy is that its architecture independent, I was using Ubuntu Intrepid 32-bit and changed to Ubuntu Jaunty 64-bit.

---

### Post by Monkus on 2009-04-11
I've been reading about the broadcom driver stuff, but no matter what I do, I cannot get my 4318 to work. It see's the card, it see's the network, it just cannot connect. Any ideas?

---

