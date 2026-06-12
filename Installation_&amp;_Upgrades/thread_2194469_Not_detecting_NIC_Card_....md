---
title: "Not detecting NIC Card ..."
date: 2013-12-18
forum: Installation &amp; Upgrades
---

### Post by ntrovato on 2013-12-18
Installing Ubuntu v10.04 on a Dell PowerEdge R420 and it is not detecting the built-in Broadcom NetXtreme Network Cards for some reason. Running ifconfig - I'm only seeing the Local Loopback interface. Running LSHW does show the Broadcom devices however. How do I go about installing the necessary drivers to get the NIC interfaces up and running?

---

### Post by tfrue on 2013-12-18
Here is a link to the Broadcom driver page with a README.txt for installation:[http://www.broadcom.com/support/802.11/linux_sta.php](http://www.broadcom.com/support/802.11/linux_sta.php)

Try something like:
 ```
lspci | grep Broadcom
``` or simply
```
lspci #for a more general view
```
to see if your computer has detected the hardware. 

If you did find Broadcom Hardware, then check out this site. It may have the appropriate help for you:[http://wireless.kernel.org/en/users/Drivers/b43](http://wireless.kernel.org/en/users/Drivers/b43)

Good luck.

---

### Post by tfrue on 2013-12-18
You don't have to have the drivers from the first page that I linked to do the "lspci" command

---

### Post by ntrovato on 2013-12-18
So my PCI-ID shows up as 14e4:165f ... this does not show up on the chart at the link you sent me. Does that mean I'm outta luck with this card? BTW - the 
sudo apt-get install firmware-b43-installer command returns "E: Couldn't find package firmware-b43-installer".

---

### Post by fantab on 2013-12-18
> **ntrovato said:**
> **Installing Ubuntu v10.04 **on a Dell PowerEdge R420 and it is not detecting the built-in Broadcom NetXtreme Network Cards for some reason. Running ifconfig - I'm only seeing the Local Loopback interface. Running LSHW does show the Broadcom devices however. How do I go about installing the necessary drivers to get the NIC interfaces up and running?

Ubuntu 10.04 is NOT supported anymore, it has reached its end of support. It is NOT maintained anymore.
I'd suggest that you install the latest supported version of Ubuntu, ie either 12.04 or 13.10.
That should take care of your problem.

---

### Post by ntrovato on 2013-12-19
v12.04 detected the NIC card just fine ... Thanks!!

---

