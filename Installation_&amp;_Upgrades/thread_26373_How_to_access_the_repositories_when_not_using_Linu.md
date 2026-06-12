---
title: "How to access the repositories when not using Linux?"
date: 2005-04-12
forum: Installation &amp; Upgrades
---

### Post by Ray Hamilton on 2005-04-12
I am trying to get my USB Speedtouch modem working with Ubuntu.  I have the Wiki UKSpeedtouchDSLHowTo page, but it says to install the package speedtouch from the universe repository?  Catch 22:  I need to install the package to enable me to use my modem to install the package, if I **could** install this package I wouldn't need it because my modem would already be working!  How do I break into this?  
BTW I hope this is the right forum to use!

Thanks in anticipation, I know I am close to loving Ubuntu.

---

### Post by dataw0lf on 2005-04-13
[http://prdownloads.sourceforge.net/speedtouch/speedtouch_1.3-1_i386.deb](http://prdownloads.sourceforge.net/speedtouch/speedtouch_1.3-1_i386.deb)

Download this, get it on the box you need it on,  and then install it with a 'dpkg -i speedtouch_1.3-1_i386.deb'

---

### Post by Ray Hamilton on 2005-04-13
Great, thanks for that.  I think I have managed to download the file ok.  I have a few other things to do before I venture onto "the other side" of my dual boot box.  Hopefully tomorrow I will be able to add a success story by using Firefox in Ubuntu.

---

### Post by Ray Hamilton on 2005-04-16
I tried your suggestion and got a dependency problem of the nature: "speedtouch depends on pppoe, however package ppoe not installed."  I continued anyway and it looks like everything else is ok, but perhaps not surprisingly the internet connection via Firefox doesn't work ie it says that it cannot find e.g. [www.yahoo.co.uk](www.yahoo.co.uk)

Any suggestions as to how to get the pppoe package (which I thought was part of the "normal" system, just goes to show what I know, or don't as the case may be.) would be gratefully received.  I know I am close to getting this working.

Ray

---

