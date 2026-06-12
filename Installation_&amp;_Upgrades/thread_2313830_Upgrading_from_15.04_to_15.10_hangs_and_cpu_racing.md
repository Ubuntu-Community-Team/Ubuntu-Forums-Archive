---
title: "Upgrading from 15.04 to 15.10 hangs and cpu racing"
date: 2016-02-16
forum: Installation &amp; Upgrades
---

### Post by johnmccormack on 2016-02-16
Actually should have check the updated version which was not as i said 15.10 its 15.10 Hi just tried upgrading to the latest version by Ubuntu software centre and then via apt-get but keeps hanging and CPU racing any ideas as to how to correct this with out using the iso?
i have a dell xps laptop i5 Intel 64 8bg 
don’t know if this is an issue but i am having to use a tethered iphone via usb for internet access at the moment, and on the first attempt the connection was interrupted as it was downloading packages.
is there a command i can try to flush out any previous downloads and start fresh ? 
any more info needed just ask.
john

Sorry should have read the first sticky before posting ! Went into rescue mode and used the clean system option and after rebooting into system the install is now running and unpacking. I used the sudo apt-get district -upgrade option in stead of the GUI this time and so far so good. I will update the post once the install is finished.

---

### Post by grahammechanical on 2016-02-16
How are you upgrading to 16.04 without first upgrading to 15.10?

Also, apt-get dist-upgrade will only update/upgrade the existing version of Ubuntu. It will pull in any held back packages. It will not upgrade to the next version of Ubuntu. If you do manage to upgrade 15.04 to 15.10 and still have a working desktop, then I suggest that you remain on 15.10 until after 16.04 is released. Ubuntu 16.04 is not finished and the upgrade path has not been tested.

If anyone wants to do an early install of Ubuntu 16.04 then please download a daily ISO image and dual boot.

[http://cdimage.ubuntu.com/ubuntu/daily-live/current/](http://cdimage.ubuntu.com/ubuntu/daily-live/current/)

Regards.

---

