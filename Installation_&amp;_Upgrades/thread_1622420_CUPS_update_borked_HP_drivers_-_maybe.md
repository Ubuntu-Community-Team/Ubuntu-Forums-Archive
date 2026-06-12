---
title: "CUPS update borked HP drivers - maybe"
date: 2010-11-15
forum: Installation &amp; Upgrades
---

### Post by lptr on 2010-11-15
Hi,

sorry if I am cross posting. I posted to hardware forum yesterday, too. Got no answer until now. So ignore the other post as this has to do more with upgrades than with hardware.

Currently having heavy problems in using my HP Laserjet 4250 dtn. The printing jobs are copied to printing queue but get stuck there forever. 

At the beginning (last weekend and some days ago) I was not very upsat because usually printing from OSX and during last week I was on the road at customers. Yesterday I had to do some office work - again recognized that problems - but thought I did reconfigure anything by accident so, that printing support temporarily went out of business. Since today I know that there must be deeper problems. Spent several hours to find a solution.
 
The strange thing I am recognizing now is, that obviously the same problem appears under OSX since last system patches, too. I do remember that the last patches in Ubuntu fixed some things in CUPS. As we all know, Apple uses the same codebase - at least partially. 

I assume that something got broken inside CUPS in conjunction with HP universal drivers. I am generalizing things, because I have another HP color Laserjet 2550n here. This also does not work not with Ubuntu (10.04) nor OSX 10.6.5.

On the OSX machine I have VMware installed. In one guest there is XP installed. Strangely the printing from this installation is possible as in the past. 

Anyone recognized same or similar? Is there already a solution in sight?

rob*

---

### Post by wilee-nilee on 2010-11-15
Have you opened the printer link in admin used to load drivers and made sure it is ticked on?

Have you just tried removing the driver and reloading?

Have you looked on the web for problems associated with this printer?

---

### Post by lptr on 2010-11-16
Thanks for reply:
> **wilee-nilee said:**
> Have you opened the printer link in admin used to load drivers and made sure it is ticked on?
Yes, did that.

> **wilee-nilee said:**
> Have you just tried removing the driver and reloading?
This to. I reloaded the hp driver stuff (reinstallation), too. The test page (that printed in the past) does not. Printer properties say that LJ4250dtn is possibly not connected. During reinstallation of this printer it detected the device correctly as HP Laserjet 4250.

> **wilee-nilee said:**
>  Have you looked on the web for problems associated with this printer?

Yes of course. That was my first step.

Having a LJ 2550n here, too. This does print. It has no duplex unit built into. The properties dialog is simpler. 

device URI from LJ4250 is:
lpd://192.168.10.99/PASSTHRU

however from LJ2550:
hp:/net/hp_color_LaserJet_2550_series?ip=192.168.10.98

The strange thing is that printing from inside a XP virtual machine using VMware on this Ubuntu host DOES PRINT! I double checked this on this box again. 

Under XP I tried PCL6 but also Postscript drivers to print on 4250. Both are working as expected. So this printer device is definitively clean and ok. I don't know how VMware pipes the print job from the client (XP) to the underlying host (Ubuntu here). But it seems NOT using LPD.

4250 has an own webserver. It shows, that it simply gets no print job.
Maybe the URI line is simply wrong?

Any ideas?

---

### Post by wilee-nilee on 2010-11-16
Not really, I have had problems with my setup at times, with a ancient HP b/w printer, I hope somebody sees the thread though as it should be working. I figured out my problem was in the right side window where you choose cups or hp, but my memory may be faulty here.

---

### Post by lptr on 2010-11-16
I played around with URI:
socket://192.168.10.99:9100
works!

hp:/net/hp_LaserJet_4250?ip=192.168.10.99
this too!

That passthrough line not. Cannot say how this line:
lpd://192.168.10.99/PASSTHRU

came there. Seems to be that this is a detection thing that did that in a wrong assumption.

Now I need to fix the OSX machine(s), too.

Thanks for help

rob*

---

