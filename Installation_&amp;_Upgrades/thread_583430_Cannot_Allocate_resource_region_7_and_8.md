---
title: "Cannot Allocate resource region 7 and 8"
date: 2007-10-20
forum: Installation &amp; Upgrades
---

### Post by dahc2424 on 2007-10-20
I had ubuntu 7.04 64 bit installed on my compaq presario v5015 and everything worked fine.

I did a clean install of 7.10 32 bit and now when I boot I get two lines that say

cannot allocate resource region 7
cannot allocate resource region 8

Then my screen goes blank and a couple of minutes later I get the logon screen.  Usually it takes a few seconds to get to the logon screen.

I have searched the forums but it looks like no one can find a solution.

Does anyone have any idea how to fix this.

---

### Post by jarin on 2008-01-09
I have the same problem I tried addressing the slow boot up after the "cannot allocate" part by changing my usplash thing which someone advised but I still have the "cannot allocate"
I'm as new as it gets with linux and I've always used windows so I also have no idea what to do. I'm on a Compaq Presario V5000 AMD Turion 64 Ati radeon xpress. Ubuntu works good once it loads up but I'm worried about that "cannot allocate region 7 and 8" thing. I found your post and was like, woah someones in the same boat I am figured I'd let you know.

---

### Post by dca on 2008-01-10
...same problem here on an Acer Aspire laptop...

---

### Post by peabody on 2008-01-10
My guess is they're just spurious messages that don't cause any harm.

---

### Post by asixe on 2008-01-21
I'm also having this problem and it is causing issues. I'm unable to use any of the devices on my docking station. I do not receive this error message when not connected to the docking station. I have checked and the drivers for my hardware are present.:confused:

---

### Post by peabody on 2008-01-22
Well, I started seeing these messages on my machine since the gutsy kernel.  You may be able to use a previous kernel to get rid of the problem.

---

### Post by asixe on 2008-01-22
I've had the messages for the last three versions of Ubuntu. Each time a new ver comes out I install it, hoping that the issue will be fixed but it isn't and I've been unable to find anything helpful thus far. I guess I'll just have to go with another flavor.

---

### Post by simplysimple on 2008-01-22
I've got the same issue and also have the 8254 timer not connected error as well. 

I'm debating whether to add noapic to the grub but not sure if it will seriously effect anything.

I'm running a Toshiba p205d-s7436 AMD athlon 64x2 tk-53 1.7ghz, ati x1200, 4gb ram, gutsy 64

anybody have any suggestions...i'm not even sure what the error means.:(

---

