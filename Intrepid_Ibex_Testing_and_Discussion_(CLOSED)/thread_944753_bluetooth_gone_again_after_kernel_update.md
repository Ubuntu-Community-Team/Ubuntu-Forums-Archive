---
title: "bluetooth gone again after kernel update"
date: 2008-10-11
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by techno-mole on 2008-10-11
hello all.

ive been having some issues with the beta of intrepid, mainly with the 2.6.27-6-generic kernel and the 177.80 nvidia driver, basically the issue was no display.

anyway after the kernel update to 2.6.27-7-generic the display issue has been fixed, well at least it seems to have been, im running the driver along side the newest kernel with no issues that i can see,

but, since the kernel update my bluetooth adapter doesnt work, it had stopped working since hardy, and then after i switched to intrepid it started working again, which i think is done to a new bluetooth package, but as i said since the kernel update it no longer works.

so before i post a bug report on launchpad i thought id ask if anyone else has had an issue like this with the new kernel version.

cheers

---

### Post by fiatguy85 on 2008-10-12
Yes, my bluetooth has not been working since one of the last kernel updates on two computers.

---

### Post by danwood76 on 2008-10-13
Mine neither.
There seems to be 3 or 4 changes which must have introduced a regression into the kernel.

A launchpad bug report would be the best option.

---

### Post by techno-mole on 2008-10-13
i have reported it on launchpad, feel free to subscribe to the report,
 which is - 281949  no bluetooth after kernel update to 2.6.27-7-generic, 

i reported it a day or so ago, but no one else seems to have had the same issue, either that or they have made out their own reports.
it does seem that at the moment we cant have a working set of drivers and bluetooth together, this kernel version fixed my nvidia problem and broke the bluetooth :-)

still its all good fun.

---

### Post by avb on 2008-10-13
same here. after upgrade to -7 mine dlink bluetooth dongle (generic bluetooth driver) stop working as well. 

Seems here is an issue: [http://kerneltrap.org/mailarchive/linux-netdev/2008/9/8/3233464](http://kerneltrap.org/mailarchive/linux-netdev/2008/9/8/3233464)

---

### Post by excogitation on 2008-10-13
I'm only reading about non-working bluetooth here - just fyi ```
0a12:0001 Cambridge Silicon Radio, Ltd Bluetooth Dongle (HCI mode)
``` is working (with a Microsoft bluetooth 5000 mouse attached) on 2.6.27-7-generic.

---

### Post by techno-mole on 2008-10-14
how can i check to see if the system is registering my bluetooth adapter ?
i have been wondering if the system just isnt loading the required files, applications etc when the adapter is plugged in.
cheers

---

