---
title: "no wireless connection with 2.6.32-25-generic"
date: 2010-09-28
forum: Installation &amp; Upgrades
---

### Post by kevingtonbeare on 2010-09-28
I upgraded to 2.6.32-25-generic and have not been able to establish connection with the wi-fi modem/router.  Went back to 2.6.32-24-generic and wireless connection established OK.

---

### Post by mikewhatever on 2010-09-29
Applications->Accessories->Terminal, and post the outputs of the of the following command:

sudo lshw -C network

---

### Post by ptn107 on 2010-09-29
Are you using a third-party wireless driver or a driver provided by the hardware drivers applet?

---

### Post by krnkris on 2010-09-30
Ok. 

There is the hint:    

Because the package not properly installed you should do it on right way.

Go to System  
Go to Administration  
Klick Synaptic Package Manager  
Look for &#8222;2.6.32-25&#8220; and choose  Install the following packages:  

linux-headers-2.6.32-25 (2.6.32-25.44  - new install, it was not installed 
linux-headers-2.6.32-25-generic (2.6.32-25.44 - new install, it was not installed  
linux-image-2.6.32-25-generic (2.6.32-25.44 - it was installed, then reinstall after it

After reboot both driver, the ATI and the Broadcom wifi will work again.  

Good day:  Kris

---

### Post by patogon.cl on 2010-10-03
> **krnkris said:**
> Ok. 

There is the hint:    

Because the package not properly installed you should do it on right way.

Go to System  
Go to Administration  
Klick Synaptic Package Manager  
Look for „2.6.32-25“ and choose  Install the following packages:  

linux-headers-2.6.32-25 (2.6.32-25.44  - new install, it was not installed 
linux-headers-2.6.32-25-generic (2.6.32-25.44 - new install, it was not installed  
linux-image-2.6.32-25-generic (2.6.32-25.44 - it was installed, then reinstall after it

After reboot both driver, the ATI and the Broadcom wifi will work again.  

Good day:  Kris

I had the same problem booting ubuntu 10.04 under 2.6.32-25 

on the contrary, i have _uninstalled_ linux-headers-2.6.32-25 in package manager. So, when i restart it boot with kernel 2.6.32-24, and wireless turns OK :P.
It makes me sense when I checked in [www.kernel.org](www.kernel.org) that the stable version of kernel 2.6.32 is 2.6.32-24.

---

### Post by medad on 2010-10-03
@ krnkris

I am glad the you noted what you did.  I reinstalled all three packages and everything came up okay.:guitar:

Hold that thought....  :confused:

On the next boot up- I had the same issue again. :-k So I went ahead and used patogon.cl's idea. :) I removed 2.6.32-25 and locked in 2.6.32-24.  I will wait until 2.6.32-26 comes out and try again.):P

---

