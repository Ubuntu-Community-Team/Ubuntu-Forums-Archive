---
title: "Intrepid Ibex Beta Release Notes"
date: 2008-10-02
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by go7Ul1ai on 2008-10-02
Hey,

The release notes have arrived..

[http://www.ubuntu.com/testing/intrepid/beta](http://www.ubuntu.com/testing/intrepid/beta)
[http://releases.ubuntu.com/releases/8.10/](http://releases.ubuntu.com/releases/8.10/)

Lee x

---

### Post by philinux on 2008-10-02
Well it's nice to see they've reduced the memory requirement compared to Hardy.

---

### Post by ELD on 2008-10-02
> **philinux said:**
> Well it's nice to see they've reduced the memory requirement compared to Hardy.

Where does it say that?

---

### Post by philinux on 2008-10-02
Sheesh it was there and it said 256meg. :confused:

---

### Post by plun on 2008-10-02
> Upgrading from Ubuntu 8.04

To upgrade from Ubuntu 8.04, press Alt+F2 and type in "update-manager -d" (without the quotes) into the command box. Update Manager should open up and tell you: New distribution release '8.10' is available. Click Upgrade and follow the on-screen instructions. 

I hope that Intel gigabyte users are blocked.

Unpolite to send those to a partly dead kernel.

```
ethtool -i eth0
```

Before upgrade maybe... or the old kernel should be there but it will
be confusing.

---

### Post by Lorenz on 2008-10-02
> **plun said:**
> I hope that Intel gigabyte users are blocked.

Unpolite to send those to a partly dead kernel.

```
ethtool -i eth0
```

Before upgrade maybe... or the old kernel should be there but it will
be confusing.

"A problem that could result in corruption of the firmware on Intel GigE ethernet hardware has led to the disabling of the e1000e driver in the Linux kernel included in Ubuntu 8.10 Beta. Ethernet devices that use this driver cannot be used with Ubuntu 8.10 Beta; support for this hardware will be re-enabled in daily builds immediately after Beta and this issue will be resolved for the Ubuntu 8.10 final release. https://bugs.launchpad.net/bugs/263555"

---

### Post by plun on 2008-10-02
> **Lorenz said:**
> "A problem that could result in corruption of the firmware on Intel GigE ethernet hardware has led to the disabling of the e1000e driver in the Linux kernel included in Ubuntu 8.10 Beta. Ethernet devices that use this driver cannot be used with Ubuntu 8.10 Beta; support for this hardware will be re-enabled in daily builds immediately after Beta and this issue will be resolved for the Ubuntu 8.10 final release. https://bugs.launchpad.net/bugs/263555"

Yes... but how many reads "known issues" ?
This is also rather unique.

So I would add a check to the upgrade description.  Or spread it !

Users can upgrade and then sitting in hours and try to figure out
why a network connection doesn't work.

---

### Post by psyke83 on 2008-10-02
> **plun said:**
> Yes... but how many reads "known issues" ?
This is also rather unique.

So I would add a check to the upgrade description.  Or spread it !

Users can upgrade and then sitting in hours and try to figure out
why a network connection doesn't work.

No they won't; they'll still be running on the Hardy kernel. If this issue isn't fixed by the final release, then yes, we need a more prominent warning - otherwise it's a waste of time ;).

---

### Post by Hobbsee on 2008-10-02
> **plun said:**
> Yes... but how many reads "known issues" ?
This is also rather unique.

So I would add a check to the upgrade description.  Or spread it !

You really expect them to read that either, if they can't be bothered to read the known issues?

---

### Post by plun on 2008-10-03
> **Hobbsee said:**
> You really expect them to read that either, if they can't be bothered to read the known issues?

Yes....  "How do I upgrade ?" ,  aha...:D

"Last time it was upgrade -d"....  I test without reading anything.

Now we have a new kernel coming along so its soon history.

Real Debian users maybe reads everything...8-)

---

### Post by ELD on 2008-10-03
Heh the beta stopped my wireless working with a netgear card? :(

---

