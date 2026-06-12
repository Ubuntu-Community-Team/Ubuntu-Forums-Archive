---
title: "How to request patches be imported into Jaunty?"
date: 2009-03-17
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by stuart.crouch on 2009-03-17
Hi

I've not been able to use linux on my main PC since I moved because of this bug

[http://bugzilla.kernel.org/show_bug.cgi?id=12110](http://bugzilla.kernel.org/show_bug.cgi?id=12110)

It looks like its finally been fixed, and I'd love to switch back - but I'm not that sure about rolling my own version of this.  Is there a process for requesting that the patch appear in Jaunty, so I can just upgrade and it will work?

thanks

---

### Post by Nullack on 2009-03-17
Put a patch request into a bug report, its all documented in the wiki

---

### Post by sgosnell on 2009-03-17
I don't know, but have you tried Jaunty?  You can also try the latest release candidate, 2.6.29-rc8, which should have all the latest stuff.  You can easily install the deb from kernel.ubuntu.com to try it, and if it doesn't help just boot from another kernel via Esc on boot.

---

### Post by castrojo on 2009-03-17
Hi!

Can you please install linux-backport-modules-jaunty (this should get you an updated driver) and see if that works?

EDIT: If you're in intrepid, the package is linux-backport-modules-intrepid.

---

### Post by stuart.crouch on 2009-03-20
I've got the latest jaunty alpha installed and I've been trying to do the backports thing but my computer locks up before I can get an internet connection.  Is there a url that I can download the .deb file onto my usb stick and then load it in ubuntu without connecting to a network?

NB. The wireless hub is on the other side of the house and I dont have a network cable long enough to reach the pc, else I'd just use an ethernet connection.

---

### Post by castrojo on 2009-03-20
[http://packages.ubuntu.com/jaunty/main/linux-backports-modules-2.6.28-11-generic](http://packages.ubuntu.com/jaunty/main/linux-backports-modules-2.6.28-11-generic)

This should be it. If your kernel is a slightly different version you should be able to just adjust the URL to find the one you need.

---

### Post by stuart.crouch on 2009-03-28
I couldnt get that to work so I dragged my pc across the house :)
Im now running jaunty alpha 6, that crashed by default, but installing the backports made everything work.

So alpha 6 with backports works correctly, and everything is back to normal 
(hooray \(^^)/)

Thanks for your help

---

