---
title: "Neither 10.10 CD or USB install works"
date: 2010-12-05
forum: Installation &amp; Upgrades
---

### Post by dbclinton on 2010-12-05
Hi,
This is an existing bug ([https://bugs.launchpad.net/ubuntu/+bug/636711](https://bugs.launchpad.net/ubuntu/+bug/636711)) but since there doesn't seem to be too much happening over there, I thought I'd post this development here to see if anyone can make something out of it.
Basically, any attempt to launch a (MDSUM-confirmed) CD or USB image of 10.10 will fail on certain computers. The install process fails, leaving a message like: 

> mount: mounting /dev/loop0 on /filesystem.squashfs failed: input/output error

Now here's the new development. I have two nearly identical Compaq Evo desktops at the office and one fails as above while the other loads and installs 10.10 perfectly (using the same USB disk). I would imagine that this would make a good test case for the bug, so I've posted the lshw output from both machines (one running 10.10 and other running 8.10) here

[http://www.ncf.ca/~es625/usb_install_non_working_compaq](http://www.ncf.ca/~es625/usb_install_non_working_compaq)

and here:

[http://www.ncf.ca/~es625/usb_install_working_compaq](http://www.ncf.ca/~es625/usb_install_working_compaq)

Maybe someone can figure out what's going on.
Thanks,
David

---

### Post by dbclinton on 2010-12-07
I've also uploaded the BIOS data from the two computers here (this is the Compaq that doesn't load 10.10):

[http://web.ncf.ca/es625/usb_install_non_working_compaq_bios_data]("http://web.ncf.ca/es625/usb_install_non_working_compaq_bios_data")

and here (this is the Compaq that DOES load 10.10):

[http://web.ncf.ca/es625/usb_install_working_compaq_bios_data]("http://web.ncf.ca/es625/usb_install_working_compaq_bios_data")

---

### Post by dbclinton on 2011-03-09
I was never able to solve the bug, but I did finally apply a simple work-around:
I installed 10.10 on another computer, then just transferred the hard drive to the Compaq that was giving me such trouble. 
Just try doing *that* with Windows!

---

