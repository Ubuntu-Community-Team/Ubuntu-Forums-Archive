---
title: "Please help.. New laptop wireless problem"
date: 2010-02-08
forum: Installation &amp; Upgrades
---

### Post by schwabdale on 2010-02-08
I have ubuntu 9.1 installed. 
it is a inspiron 1545 from best buy. I think its a Intel chipset. Can someone who knows how to get this work give me a step by step please

---

### Post by phillw on 2010-02-08
Hi, I've just had a quick look, it seems you may have a Broadcom chip set for your wireless. If you type ```
lspci -nn
```You may well see something like

>  0c:00.0 Network controller [0280]: Broadcom Corporation BCM4312  802.11b/g [14e4:4315] (rev 01)Now, the easy way is ....

> 
Connected with an ethernet cable to your  router....

Try this open up a terminal and type

```
sudo apt-get update
```
Then, select System --> Administration --> Hardware Drivers

It will say searching for hardware drivers.  Then when it comes up click  on your wireless driver which I am assuming it is the Broadcom STA  wireless driver.

Click on it and on the bottom right of the box there will be a button  that says activate.  It is very important that you are connected to your  router with an ethernet cable so that you can download the driver and  it will activate it once it is downloaded and you will be able to use  your wireless.
That should get you up & running with a broadcom device in your spec of machine.

Regards,

Phill.

---

### Post by schwabdale on 2010-02-08
that worked. Thank you so much

---

