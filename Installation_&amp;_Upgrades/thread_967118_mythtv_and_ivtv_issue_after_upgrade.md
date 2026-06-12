---
title: "mythtv and ivtv issue after upgrade"
date: 2008-11-01
forum: Installation &amp; Upgrades
---

### Post by jtonk on 2008-11-01
Hi,

just updated my mythtvbox from 8.04 to 8.10. Now the tv recordings do not work.

I have two capture cards pvr 150 and 500 (double tuner). The ivtv modules are loading fine on boot, and I can use them on screen:

mplayer /dev/video1

but when I start recording in mythtv I get the following error on the backend (and nothing is recorded):

*********************** WARNING ***********************
 ivtv drivers prior to 0.10.0 can cause lockups when
 reading VBI. Drivers between 0.10.5 and 1.0.3+ do not  
 properly capture VBI data on PVR-250 and PVR-350 cards.

2008-11-01 23:50:56.098 MPEGRec(/dev/video2) Error: select timeout - ivtv driver has stopped responding

The /dev/video2 device is from this point on broken

Any ideas, is it the kernel update, does 8.10 have different ivtv drivers in the kernel or is mythtv the problem in this case

any suggestion is welcome

regards

Jasper

---

### Post by ian dobson on 2008-11-02
Hi,

Just to let you know I'm seeing the same problem.

Regards
Ian Dobson

---

### Post by KvZ on 2008-11-03
Hi

I've seen the same error. In my case I resolved the issue by installing the Bleeding Edge version of the ivtv drivers see: 

[http://www.ivtvdriver.org/index.php/Download](http://www.ivtvdriver.org/index.php/Download)

Thanks
Karsten

---

