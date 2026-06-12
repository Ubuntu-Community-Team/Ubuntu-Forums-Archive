---
title: "XFX 8200, unable to install/sata"
date: 2008-08-28
forum: Installation &amp; Upgrades
---

### Post by putte30 on 2008-08-28
Trying to install latest version of ubuntu on my new computer(mainbord xfx 8200). First of all, i got 2 drives: 1 ide and 1 sata. I want to install ubuntu on the sata drive. 

At first the live-cd worked fine but couldnt find the sata drive. So i had to change the bios setting to compatible mode for sata. After that the live-cd acts wierd. The first menu pops up where u can choose to install/run live-cd/memorytest etc. If i choose run live-cd/install the loadingbar starts to move and after a few seconds i find my self in some kind of a terminal. 

Anyone got a solution for this?

---

### Post by fffff on 2008-08-28
i have the same problem, so now i just have it running with the ide drive, if some one could help, that would be great

---

### Post by putte30 on 2008-09-28
*bump*

---

### Post by kallistifive on 2008-10-05
I've made a basic guide where I will be detailing the installation of Ubuntu 8.10 on the XFX 8200 board. (it includes the fix for your issue)

The error associated with the SATA problem on this board is "qc timeout cmd 0xec"

Upgrading to the latest bios wont help. (yet)



[http://unixzen.com/?articles/2008/10/05/ubuntu-8-10-on-the-xfx-8200.html](http://unixzen.com/?articles/2008/10/05/ubuntu-8-10-on-the-xfx-8200.html)

I've got SATA working, and am now working on a guide for video. (which will be posted to the page above when complete)

Good luck!

---

### Post by putte30 on 2008-10-05
Thank you very much!!!

---

### Post by tydfil on 2008-10-08
I am waiting kallistifive for you to sort video.  According to the xorg error log the 8200 chipset is as yet unsupported and thus **nothing** is detected at boot.  Installing the nvidia-glx via Drivers or envy or cli results in unstable screen.  Have tried everything I have found on the net to fix it but it won't play.  

We need to wait for better support.

---

### Post by kallistifive on 2008-10-08
sorry for the delay, I've become a bit under the weather.  The guide is up.

Thanks and good luck!

---

### Post by tydfil on 2008-10-10
Thanks a lot kallistifive you got my sata working! Now can't mount pen drive despite all other USB stuf working fine.:KS

---

### Post by payableondeath on 2008-12-25
> **kallistifive said:**
> I've made a basic guide where I will be detailing the installation of Ubuntu 8.10 on the XFX 8200 board. (it includes the fix for your issue)

The error associated with the SATA problem on this board is "qc timeout cmd 0xec"

Upgrading to the latest bios wont help. (yet)



[http://unixzen.com/?articles/2008/10/05/ubuntu-8-10-on-the-xfx-8200.html](http://unixzen.com/?articles/2008/10/05/ubuntu-8-10-on-the-xfx-8200.html)

I've got SATA working, and am now working on a guide for video. (which will be posted to the page above when complete)

Good luck!
Please, i've tried to apply the guide of kallistifive, but i had a problem. When i boot ubuntu cd, and press ESC, then appears the word: boot:, and i write letter 'e', but it gets an error of command line. 

Sorry, i have no much knowledge about this, help me, So i like so much ubuntu environment, and i want to change completly to this S.O.

---

### Post by streets2311 on 2009-01-03
Thanks a bunch for posting the how-to, I have been beating my head against the wall thinking i had a bad hard drive or motherboard!

---

