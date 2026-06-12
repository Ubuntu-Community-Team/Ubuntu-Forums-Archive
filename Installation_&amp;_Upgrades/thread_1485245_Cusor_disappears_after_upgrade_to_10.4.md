---
title: "Cusor disappears after upgrade to 10.4"
date: 2010-05-16
forum: Installation &amp; Upgrades
---

### Post by b00mer on 2010-05-16
I am currently using Ubuntu 10.04 after kernel upgrade. 
The pointer is visible at the login screen, but after I login, it disappears. Never had any problems with earlier distributions. 

I was still able to figure out where it was because of the hover effects (you know, the brightness change of a button or link when you hover your mouse over it) and quicky changed the settings in System>Preferences>Mouse to show where the mouse is when I pressed ctl key. 

I can get the cursor to be visible by sudo lshw -c display, but that is only temporary. If I reboot I have to do that again. 

This is the information I get when I do lshw -c display:
*-display UNCLAIMED 
description: VGA compatible controller
product: 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device
vendor: Intel Corporation
physical id: 2
bus info: pci@0000:00:02.0
version: 01
width: 32 bits
clock: 33MHz
capabilities: bus_master cap_list
configuration: latency=0
resources: memory:e8000000-efffffff(prefetchable) memory:ff680000-ff6ffff

I'm running this on an old Dell Optiplex GX260 with onboard video.

Anybody have any ideas on how to make the pointer show up on a more permanent basis?

Also, it seems screensavers are giving me problems as well when they never used to. They just blank my screen and I have to reboot.

---

### Post by eadc on 2010-05-17
I have the same problem. Can anyone help?

---

### Post by b00mer on 2010-05-20
Really would appreciate any help with this issue.  I have way to many apps etc on my machine to have to re-install a downgraded version again.

Thx

---

### Post by uRock on 2010-05-20
Have you went to System> Preferences> Appearance, then click Customize, then click the Pointer tab?

---

### Post by b00mer on 2010-05-22
> **uRock said:**
> Have you went to System> Preferences> Appearance, then click Customize, then click the Pointer tab?

Tried it, but doesn't help.  I can change cusor styles, but when I reboot, and login, the cursor is still missing, and I have to do lshw -c display to get it back again.  I know it's there and fuctioning because I can do CTL and it will give me the position.  It just isn't visible.

---

### Post by b00mer on 2010-05-27
I was hoping there might be an answer out there somewhere.
Anybody?

---

### Post by funchords on 2010-05-30
Possibly related: [https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/552058](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/552058) ???

---

### Post by grimofoz on 2010-06-02
I have a similar prob. 
after upgrading, the cursor -occasionally- becomes almost invisible. I have several operating systems, so I just swap to another, and when I swap back the cursor comes good. All other graphics are fine.
Weird.
It's an old system; amd sempron 3300, with radion 9200 se graphics.

---

### Post by funchords on 2010-06-04
> **grimofoz said:**
> I have a similar prob. 
after upgrading, the cursor -occasionally- becomes almost invisible. I have several operating systems, so I just swap to another, and when I swap back the cursor comes good. All other graphics are fine.
Weird.
It's an old system; amd sempron 3300, with radion 9200 se graphics.

It MAY be related, but as your problem is different, I would also start a new thread.  In our case, the cursor is totally invisible. It is quite possible that whatever eventually fixes our problem won't fix yours.

---

### Post by kansasnoob on 2010-06-04
> product: 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device
vendor: Intel Corporation

Noticing that from the OP I thought about this:

[https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes](https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes)

Basically loads of trouble with that graphics chip :(

---

