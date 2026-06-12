---
title: "Need help to compile driver for wireless"
date: 2012-12-01
forum: Installation &amp; Upgrades
---

### Post by milpat on 2012-12-01
Hi,

What I try to do is compile the driver for a PCE-N10 Wireless Adapter. I'd like to know what I miss to make it work. I downloaded th source for the driver, copied and unzipped it in my home folder ant tried a make, here is the output ...

milpat@ubuntu:~/rtl_92ce_92se_92de_8723ae_linux_mac80211_0007.0809.2012$ make
make -C /lib/modules/3.5.0-17-generic/build M=/home/milpat/rtl_92ce_92se_92de_8723ae_linux_mac80211_0007.0809.2012 modules
make[1]: Entering directory `/lib/modules/3.5.0-17-generic/build'
make[1]: *** No rule to make target `modules'.  Stop.
make[1]: Leaving directory `/lib/modules/3.5.0-17-generic/build'
make: *** [all] Error 2
milpat@ubuntu:~/rtl_92ce_92se_92de_8723ae_linux_mac80211_0007.0809.2012$ 

Can someone help me to get make working

Thank you

---

### Post by steeldriver on 2012-12-01
do I see a space in the name of your working directory? try removing that (or replacing with an underscore)

---

### Post by milpat on 2012-12-01
Hi,

Thanks for the answer.

No there's no space in my working directory.

I'm sorry, pretty new to this so, I don't really know what to give for infos.

Pat

---

### Post by Cheesemill on 2012-12-01
What version of Ubuntu are you running?

---

### Post by milpat on 2012-12-01
Ubuntu 12.10 - fresh install

---

### Post by Cheesemill on 2012-12-01
The driver that you're trying to compile is meant for older versions of Linux, what you are trying to do probably wont work.

However, I believe that the driver is now already built into the kernel and just needs the firmware installing.

With your machine plugged into the network with a cable can you go to Software Sources > Additional Drivers and see if it offers to install anything for you.

---

### Post by milpat on 2012-12-01
I'm actually wired because my wireless adapter is always dropping the connections. I did go to 'Software Source', to the 'Additionnal Driver' but nothing is offered.

Did I mention that I have a ASUS PCE-N10 Wireless adapter.

Is there a wireless (N) adapter model that is working out of the box ?

Thank You

Pat

---

