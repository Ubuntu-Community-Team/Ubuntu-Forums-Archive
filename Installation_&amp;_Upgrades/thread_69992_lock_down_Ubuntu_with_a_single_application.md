---
title: "lock down Ubuntu with a single application"
date: 2005-09-28
forum: Installation &amp; Upgrades
---

### Post by newbuntuser on 2005-09-28
We need to prevent changes to the system.  This is used in a kiosk and currently hundreds of people access this computer daily.  Several just can't help but try to break it and unfortunaltely they often succeed.

Ideally, we would see one web site only and no other toolbars or menus from Firefox.  We are open to other browsers if that will help.  Also, a customized Knoppix CD that would boot and start the browser could work work as well.  Ubuntu is so easy to use which is why it's being used now.  Where's apt-get install lock-me-down?

Any input is appreciated.

Thanks!

---

### Post by mlomker on 2005-09-28
> Any input is appreciated.

We've had a few other threads similar to this.  In my mind it'd be easy to make the system read-only but keeping it a usable state might be the hard part.  

I'd probably do a 'server' install and then add a super-light desktop manager like TWM.  You could then install just Firefox and configure a script to load it.  The advantage is that non-nerds are going to be more lost.  There are probably ways to lock that down even further but I haven't researched it...

I'd try custom partitioning and separate /tmp and /dev into their own partitions so that I could mount / as read-only in fstab.  That'd prevent anyone from making any meaninful change to the operating system as only the temp files for firefox would be able to write to disk.  I'm not sure about removing toolbars and whatnot but you could just configure a firewall that doesn't allow the box to get to any other IP address and/or disable DNS and use a Hosts file for name resolution.

There are also some threads on here about creating your own boot CD's.  There's a package called bootcd in Synaptic.

Hopefully someone will respond that has actually done a kiosk...

---

### Post by tomchuk on 2005-09-28
[http://kiosk.mozdev.org/jim-kiosk.html](http://kiosk.mozdev.org/jim-kiosk.html) will do the trick

---

