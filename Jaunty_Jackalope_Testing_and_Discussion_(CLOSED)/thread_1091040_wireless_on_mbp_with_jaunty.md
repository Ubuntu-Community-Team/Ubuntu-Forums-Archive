---
title: "wireless on mbp with jaunty"
date: 2009-03-09
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by inphektion on 2009-03-09
I need some pointers here, I keep having wireless issues and want to know what commands i can run to further troubleshoot or manually figure out where exactly the issue lies.  Something beyond iwconfig.

I think some of the problem might be in the gnome-network-manager cause if I use wicd some things are better (others worse).
Other issues could be in the driver but its restricted broadcom.  Is there a way to get logs of things for wireless?  Can I try a different restricted driver somehow?

The issues surround connecting to hidden wireless networks which I've connected to for 2 years now on windows and connects fine in the macosx.  Sometimes connects in ubuntu, sometimes doesn't.  Also when it connects the network manager sometimes shows 2 bars and sometimes none.  While in windows and mac it is a full 5 bars and excellent signal.

---

### Post by cyberdork33 on 2009-03-09
there is a whole networking & wireless forum. you might check in there for some tips to debug:
[http://ubuntuforums.org/forumdisplay.php?f=336](http://ubuntuforums.org/forumdisplay.php?f=336)

There is no other proprietary driver. There is the b43 semi-open driver (needs firmware) which I don't think will work on your Mac, or you can try ndiswrapper with a windows driver.

---

