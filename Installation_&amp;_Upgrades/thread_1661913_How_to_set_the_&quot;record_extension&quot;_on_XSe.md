---
title: "How to set the &quot;record extension&quot; on XServer"
date: 2011-01-07
forum: Installation &amp; Upgrades
---

### Post by pgarrigue on 2011-01-07
I try to use the XNEE application to record and replay a scenario on Ubuntu.
I'v got this following error :

error 35: "Record memory failure - Xnee failed due to bad data received from RECORD extension".

I've read XNEE faq and it seems the "record" extension is not loaded on XServer.
The /etc/X11/xorg.conf file must be modified to resolve it.

On my ubuntu distribution, I don't have any xorg.conf file.

Do you know how to set the record extension on Xserver ?

Thanks a lot.

Philippe

---

### Post by hesa on 2011-01-22
For a while there have been problems in X (more precisely the RECORD extension). The printout you see from Xnee is related to that.

You don't need to enable the RECORD extension. That is most likely already enabled by default in Ubuntu. To check that, do:
   xdpyinfo  | grep  -c RECORD
If you get "1" back, you're ok

I suggest you update your Ubuntu as much as possible and go for the latest Xnee out there.

There is a cnee binary built every night, grab it here:

   [http://itupw056.itu.chalmers.se/xnee/install/bin/cnee](http://itupw056.itu.chalmers.se/xnee/install/bin/cnee)

Download that by either: 
   curl [http://itupw056.itu.chalmers.se/xnee/install/bin/cnee](http://itupw056.itu.chalmers.se/xnee/install/bin/cnee) -o cnee 
or 
   wget [http://itupw056.itu.chalmers.se/xnee/install/bin/cnee](http://itupw056.itu.chalmers.se/xnee/install/bin/cnee) 
and then 
   chmod a+x ./cnee 
  
and test Xnee like this:
   ./cnee --record --mouse --keyboard --data-to-record 10

---

