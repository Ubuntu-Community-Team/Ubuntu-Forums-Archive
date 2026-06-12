---
title: "Alpha 5 not booting"
date: 2008-09-06
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by roadrash on 2008-09-06
I have just been trying Alpaha 5 & I can get it to boot fine on my desktop but It refuses to work on my Fujitsu Siemens Li1718 Laptop.

It stops dead after the boot menu with a blank screen.  I cant even run the CD check.  Straight after making a menu selection there is a small delay before it leaves the boot menu & then just stops with a blank screen.

---

### Post by Nullack on 2008-09-06
Please refer to the Intrepid howto in my sig. The kernel debugging wiki info will be useful for debugging here. Try removing quiet from the boot menu and see what the kernel messages are saying with usplash off.

---

### Post by jerrylamos on 2008-09-06
O.K., here's the last line from a failed boot on Compaq Presario, ATI graphics, with Alpha 5.  This is from the CD Live with kernel 2.6.27-2

From Launchpad Bug 265049
F6 option remove quiet and splash. In seconds all activity stops and keyboard is dead.
Last line on screen before hang is:

pci 0000:00:00.0: MSI quirk detected; MSI disabled.

So I installed Alpha 4 with kernel 2.6.26-5 and did all updates to get to Alpha 5 level.  Boot fails with kernel 2.6.27-2, runs with kernel 2.6.26-5.

Note same Alpha 5 CD 2.6.27-2 boots and installs on IBM Thinkpad R31, Intel graphics.

Jerry....

---

### Post by roadrash on 2008-09-07
> Try removing quiet from the boot menu and see what the kernel messages are saying with usplash off. 

The last line before it hangs says:

**1.057220] booting paravirtualized kernel on bare hardware.**

---

### Post by Karel-Lodewijk on 2008-09-08
I have the same issue on an ACER aspire 9410z. Adding the noapic kernel option does allow it to complete the boot process.

---

### Post by Karel-Lodewijk on 2008-09-09
I've filed a bug report about this:

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/268089](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/268089)

---

