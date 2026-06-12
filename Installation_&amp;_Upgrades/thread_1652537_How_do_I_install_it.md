---
title: "How do I install it?"
date: 2010-12-25
forum: Installation &amp; Upgrades
---

### Post by zombrax on 2010-12-25
Hey guys,
 
Been a while here but good to see that things are almost the same as before, good community, lots of knowledgable members!
 
I got a small problem. I got a Samsung N150 netbook that came with Window$ 7 light preinstalled. 
 
Question is how can I install the netbook remix on it? It doesnt have a cd/dvd rom so i dont know how you can install it?
 
What are some ways you can install the os on the netbook? Also how can I check the compatability of N150 before the installation?
 
Thirdly, how can i go back to windows 7 if everything fails? The os came pre-installed with the netbook and has no software as such.
 
thanks in advance
Zombrax.

---

### Post by Verbeck on 2010-12-25
you could make a live usb using [unetbootin]("http://unetbootin.sourceforge.net/"),  boot from it
and select 'try without installing'

---

### Post by zombrax on 2010-12-25
so does this mean that the entire version of netbook remix is copied on to the usb thumb drive?

---

### Post by Sef on 2010-12-25
> Question is how can I install the netbook remix on it? It doesnt have a cd/dvd rom so i dont know how you can install it?


You can install from a [Live USB]("https://help.ubuntu.com/community/Installation/FromUSBStick").

> What are some ways you can install the os on the netbook? Also how can I check the compatability of N150 before the installation?

Run the Live USB without installing. If you have a problem with the Live USB, then almost certainly the same problem will exist upon install.

> Thirdly, how can i go back to windows 7 if everything fails? The os came pre-installed with the netbook and has no software as such.

Make a clone of Windows 7 with [Clonezilla's Live USB]("http://clonezilla.org/").

> you could make a live usb using unetbootin, boot from it
and select 'try without installing'

Easier to go to the Netbook remix and go to '[Create a USB Drive]("http://www.ubuntu.com/netbook/get-ubuntu/download")'. (It's number 2.)

---

### Post by Verbeck on 2010-12-25
> **zombrax said:**
> so does this mean that the entire version of netbook remix is copied on to the usb thumb drive?[s]
you could say that... but any configuration you do would be lost on the next reboot. so in that case, a persistent live usb could solve it
[https://wiki.ubuntu.com/LiveUsbPendrivePersistent](https://wiki.ubuntu.com/LiveUsbPendrivePersistent)[/s]

or install ubuntu using wubi from windows. 
[https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)

edit: see the link by sef, it gives the option to make it persistent

---

