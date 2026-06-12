---
title: "Any flavour of Ubuntu still install on a Via C3 600MHz mainboard?"
date: 2015-10-22
forum: Installation &amp; Upgrades
---

### Post by jarthurs on 2015-10-22
Trying to load Ubuntu on an old Epia ME6000 600MHz mainboard to use as a data logger for a weather station. 

Ubuntu 10.10 Server (i386) fails to load with:

This kernel requires the following features not present on the CPU:
cx8 cmov

Is there another version I can use or a workaround?

Regards,
Jason.

---

### Post by tgalati4 on 2015-10-22
Try 8.04.  That's a tricky chipset to get working with modern distros.  I used 8.04 for some embedded projects, several years ago with Via chipsets. 

[http://radagast.ca/epia/epia_howto/index.html](http://radagast.ca/epia/epia_howto/index.html)

Damn Small Linux worked OK as well.

At the bottom of this thread:  [http://lockergnome.net/119793/whats-a-good-linux-distribution-for-via-processors](http://lockergnome.net/119793/whats-a-good-linux-distribution-for-via-processors)

Few more hints:

[http://crunchbang.org/forums/viewtopic.php?id=12462](http://crunchbang.org/forums/viewtopic.php?id=12462)

It might be easier to get a RaspberryPi, use less power, and get a current distro with support.

---

### Post by mörgæs on 2015-10-22
VIA is the least of your problems. Worse is that your processor does not have CMOV which further limits your choice of distro.

I doubt you will find anything still supported which installs, so your choice might be limited to unsupported distros meaning that the contents on the computer is at risk.

---

### Post by jarthurs on 2015-10-24
> **tgalati4 said:**
> Try 8.04.  That's a tricky chipset to get working with modern distros.  I used 8.04 for some embedded projects, several years ago with Via chipsets. 

[http://radagast.ca/epia/epia_howto/index.html](http://radagast.ca/epia/epia_howto/index.html)

Damn Small Linux worked OK as well.

At the bottom of this thread:  [http://lockergnome.net/119793/whats-a-good-linux-distribution-for-via-processors](http://lockergnome.net/119793/whats-a-good-linux-distribution-for-via-processors)

Few more hints:

[http://crunchbang.org/forums/viewtopic.php?id=12462](http://crunchbang.org/forums/viewtopic.php?id=12462)

It might be easier to get a RaspberryPi, use less power, and get a current distro with support.

8.04 installed on it just fine. Now to see if all the dependencies can be met when I try to build the data logger!

Many Thanks,
Jason.

---

### Post by tgalati4 on 2015-10-24
10.04 may work as well.  I think they added the CMOV requirement in 10.10.  Let us know how it turned out.

---

### Post by jarthurs on 2015-10-26
10.10 was the first version I tried (it was the oldest version I had an ISO for on my network). Unfortunately CMOV was required.

Thanks,
Jason.

---

