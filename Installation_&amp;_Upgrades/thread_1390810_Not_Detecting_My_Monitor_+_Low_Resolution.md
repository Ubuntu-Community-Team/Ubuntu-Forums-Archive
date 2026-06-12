---
title: "Not Detecting My Monitor + Low Resolution"
date: 2010-01-26
forum: Installation &amp; Upgrades
---

### Post by ni_shi2005 on 2010-01-26
I installed Ubuntu J.Jacklop Recenlty, and ma monitor waz not detected and i tried changing the resolution, and after setting it to 800x600, i cudnt change it back to 1280x1024 n all, and also i upgraded OS, to 9.10 still its like that,i do only get Resoultions like 800x600 and below!
 i am so fresh to ubuntu! someOne please help me!

ps : i have attached the xorg file too

---

### Post by ni_shi2005 on 2010-01-26
someOne help me please :(

---

### Post by rftuxuser on 2010-01-26
I am new too, and had the same problem.  I downloaded the drivers for my vid card after installing (which was a pain with the low res) Karmic koala.  this did resolve my problem and the monitor was detected afterwards.  It is very strange that Ubuntu does not use the right drivers for the video when booting from cd.  This could be a turn off for newbies to linux.

---

### Post by cpplinux on 2010-01-26
Maybe you can try the **915resolution** package from Synaptic Package Manager.

---

### Post by hhlp on 2010-01-26
we need more information, what is your vga card :

[PHP]lspci | grep VGA[/PHP] or

[PHP]sudo lshw -C video[/PHP]

---

### Post by Grenage on 2010-01-26
I have a rough guide [here]("http://www.grenage.com/xorg.html") that tackles monitor resolution problems in 9.10.

---

### Post by terrapin893 on 2010-01-26
> **cpplinux said:**
> Maybe you can try the **915resolution** package from Synaptic Package Manager.
I had a good deal of resolutions problems myself initially.  I did some research and found recommendations for 915resolution . . . . but I could not find it in the repositories.  :(

Couple of things that helped me . . . . ( I actually found 2 fixes ) 

1.)  With my first configuration, which is now my server, I had an integrated Intel 82845G graphics driver.  I had downloaded the driver from Intel but I couldnt get anything to work.  What ended up helping me here was actually shutting down the x server and then running the driver. 

```
sudo /etc/init.d/gdm stop
``` 

This will give you a terminal screen, then log into your desktop

```
cd /path/to/driver.deb
``` 

In my case the driver installed perfectly this time.  

```
sudo /etc/init.d/gdm start
```

This should give you a much higher resolution. 

2.)  With my second configuration, my current desktop PC, it was much easier.  I just installed "Envy" through synaptic and then it detected and installed the driver.  NOTE:  This will only work with nVidia and ATI cards! 

Good Luck!

---

### Post by ni_shi2005 on 2010-01-26
> **hhlp said:**
> we need more information, what is your vga card :

[PHP]lspci | grep VGA[/PHP] or

[PHP]sudo lshw -C video[/PHP]

here is what you need!! i have installed da VGA Drivers!! bt i can't get in to da VGA Control Center in adminstrator mode, givin me someErrors!


>   *-display               
       description: VGA compatible controller
       product: Mobility Radeon HD 3600 Series
       vendor: ATI Technologies Inc
       physical id: 0
       bus info: pci@0000:01:00.0
       version: 00
       width: 64 bits
       clock: 33MHz
       capabilities: pm pciexpress msi bus_master cap_list rom
       configuration: driver=fglrx_pci latency=0
       resources: irq:29 memory:d0000000-dfffffff(prefetchable) memory:fe8f0000-fe8fffff ioport:c000(size=256) memory:fe8c0000-fe8dffff(prefetchable)


---

### Post by ni_shi2005 on 2010-01-26
> **cpplinux said:**
> Maybe you can try the **915resolution** package from Synaptic Package Manager.

 i searched in Synaptic P.M for dat name, and nothing came out :(

---

### Post by ni_shi2005 on 2010-01-26
> **Grenage said:**
> I have a rough guide [here]("http://www.grenage.com/xorg.html") that tackles monitor resolution problems in 9.10.

bro, i cudnt edit the xorg.conf file :( when i try it gives me an error
> "You do not have the permissions necessary to save the file. Please check that you typed the location correctly and try again."

---

### Post by Grenage on 2010-01-26
Any modifications need to be run with root rights; e.g:

```
sudo gedit /etc/X11/xorg.conf
```

---

### Post by ni_shi2005 on 2010-01-27
> **Grenage said:**
> Any modifications need to be run with root rights; e.g:

```
sudo gedit /etc/X11/xorg.conf
```

i did edit, but its not effecting :(

---

### Post by Grenage on 2010-01-27
What happens?  Post your config.

---

### Post by duracell999 on 2010-01-27
I've had a similar problem. 
Finding the specific frequencies for my monitor and putting them into the xorg.conf file worked great for me.
I guess with some monitors ( older ones? ) the frequencies don't get detected and ubuntu only uses safe ones which forces low resolutions.

---

### Post by Grenage on 2010-01-27
That's right, if there is a problem using EDID to detect the monitor's capabilities, that's often the case.

---

