---
title: "UBUNTU 11.04 Natty UBUNTU11.10 Oneiric apt-get update 404 Not Found error"
date: 2014-07-30
forum: Installation &amp; Upgrades
---

### Post by VIJAY_KUMAR_R on 2014-07-30
Hi,


I am trying to install below OS using ISO file in a Virtual machine.


UBUNTU11.04 32/64 bit (Natty)
UBUNTU11.10 32/64 bit (Oneiric)


When I try to do a sudo apt-get update I am getting error message "404 Not Found".


I verified the same in [http://us.archive.ubuntu.com/ubuntu/dists/](http://us.archive.ubuntu.com/ubuntu/dists/) and I don't find dists for natty and Oneiric.


I tried apt-update with older dists as well. They also fail with incompatiblity error.


Finally I tried with [http://old.archive.ubuntu.com/ubuntu/dists/](http://old.archive.ubuntu.com/ubuntu/dists/)
which also does'nt contain dists for Natty and Oneiric.


Kindly let me know ho I could install
UBUNTU11.04 32/64 bit (Natty) and
UBUNTU11.10 32/64 bit (Oneiric)


With Thanks & Regards
Vijay.R

---

### Post by stephenmichaelphotography on 2014-07-30
For 11.04 [http://old-releases.ubuntu.com/releases/11.04/](http://old-releases.ubuntu.com/releases/11.04/)

For 11.10 [http://old-releases.ubuntu.com/releases/11.10/](http://old-releases.ubuntu.com/releases/11.10/)

That will at least get you installation images.  Do you mind if I ask why you'd want to install such an outdated release?

---

### Post by ibjsb4 on 2014-07-30
This is a VM, save yourself some grief, just install 12.04 (supported till 2017) or 14.04 (supported till 2019).  This would be up to your VM capabilities.

---

### Post by coffeecat on 2014-07-30
> **VIJAY_KUMAR_R said:**
> Kindly let me know ho I could install
UBUNTU11.04 32/64 bit (Natty) and
UBUNTU11.10 32/64 bit (Oneiric)


No, we can't do that. They are obsolete releases, no longer supported. What we can do is to help you install a supported release, either 12.04 or 14.04. Or we can help you find an alternative derivative of Ubuntu, if you would prefer that. But again, they would need to be currently-supported versions.

[http://ubuntuforums.org/showthread.php?t=2229730](http://ubuntuforums.org/showthread.php?t=2229730)

---

### Post by VIJAY_KUMAR_R on 2014-07-31
Thanks for your reply. I will try to install the GOS with images mentioned by you.
 To answer your query, I am from a QE team and we need to test all flavors  of Ubuntu GOS for backward compatibily of our features.

---

### Post by plucky on 2014-08-02
GOS = TLA what does GOS mean?  TLA = three letter abbreviation

Why would you want to test against an obsolete release?

---

