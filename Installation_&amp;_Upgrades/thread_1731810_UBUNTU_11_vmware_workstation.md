---
title: "UBUNTU 11 vmware workstation"
date: 2011-04-17
forum: Installation &amp; Upgrades
---

### Post by v.matiakis on 2011-04-17
Hi there,

After upgrading from 10.10 to 11.04 the vmware workstation is complaining about not finding kernel headers. 

"Kernel headers for version 2.6.38-8-generic-pae not found"

Is there any idea how do i install it?

"C header files matching your running kernel were not found.  Refer to your distribution's documentation for installation instructions."

Is there a solution on that matter?

---

### Post by Hedgehog1 on 2011-04-17
Right now neither VMware or Virtual Box have Natty verisons available.  Until the Vbox ones come out, I will be triple booting between Windows, 10.10 and 11.04 so I can use my Vbox's in 10.10.


***The Hedge***

:KS

---

### Post by jacano on 2011-04-29
Try this:
sudo apt-get install linux-headers-`uname -r`

then apply this patch:

[http://communities.vmware.com/message/1745502?tstart=0](http://communities.vmware.com/message/1745502?tstart=0)

This worked to me. :P

---

