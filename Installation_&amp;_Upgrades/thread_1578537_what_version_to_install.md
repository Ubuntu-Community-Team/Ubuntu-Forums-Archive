---
title: "what version to install"
date: 2010-09-20
forum: Installation &amp; Upgrades
---

### Post by chrisclay on 2010-09-20
Hi i am new to linux and have been having trouble installing server10.4.1 but it allways fails to on the first boot just a flashing cursor then nothing untill a screen appears untill the screen displays "gave[COLOR=black] up waiting for root device" i have tried to reinstall several time but keep getting the same result .so my question is is there different edition of ubuntu server i can try ,also does it make much of a difference if i use the 32 bit version on a 64 bit cpu ,the version i have is a32 bit version and the system iam installing on is a amd 64x2 cpu,i have used the same cd to install on a virtual machine that is running on a amd x4 955 cpu on 64 bit windows.[/COLOR]
 
[COLOR=black]any ideas would be appreceated [/COLOR]

---

### Post by mörgæs on 2010-09-20
Try a live boot with 9.10:
[http://releases.ubuntu.com/](http://releases.ubuntu.com/)

If it works better than 10.04, this is the one to install. 

You could also try adding boot options to the 10.04 installation to make it work:
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

Begin with a 32 bit install. I would only consider 64 bit, if the 32 bit system is proven slow.

---

### Post by chrisclay on 2010-09-20
hi thanks for the reply i am currently downloading te 9.1 iso and will try again tomorrow after work
 
chris

---

### Post by chrisclay on 2010-09-21
hi
just a quick up date i installed 9.1 this evening and it all went ok and does boot but it takes some time and displays the message loading grub then no such disk ten if you wait a while it boots ok.the long boot time will not be a problem as it is going to replace my windows server eventually and wil not be shut down
so my next problem is to make mythtv recognise my tv card
 
chris

---

### Post by mörgæs on 2010-09-22
Good, now we at least have something that works. You can try installing a 64 bit 9.10, if you are not satisfied with the speed.

You could also try a live boot of 10.10 beta (expect some experimenting here) to see if it works better with the TV card. Which card is it? 

[http://cdimage.ubuntu.com/daily-live/current/](http://cdimage.ubuntu.com/daily-live/current/)

---

### Post by chrisclay on 2010-09-22
Hi the card is Pinnacle PCTV Dual Hybrid Pro PCI Express (3010i)innacle PCTV Dual Hybrid Pro PCI Express (3010i) 
 
chris

---

