---
title: "Problem installing from DVD ('/sbin/modprobe' abnormal exit)"
date: 2008-04-16
forum: Installation &amp; Upgrades
---

### Post by BigWoop on 2008-04-16
When trying to install from the DVD of Ubuntu 7.10 I get the following error:

udevd-event[2147]: run_program: 'sbin/modprobe' abnormal exit

This happens when trying the defualt install from the GUI boot screen, or trying the text installer or trying to install a server, or trying "check cd for defects", pretty much any option does this.

It's an old system:

Duron 800MHz
256mb RAM
20gb HD
Gigabyte ga-7ixe4_e Motherboard
3DFX Voodoo Banshee 16mb
16x DVD writer (I think BenQ)

What could be causing this? It's not perhaps anything to do with there not being free space on the HD? (Wouldn't have  thought so, I'm sure I would have the opportunity to format during installation.)

Thanks.

EDIT:

I'm using the i386 version obviously.
Just started trying an older 6.06 version CD in the system, and that older version appears to be working so far...

---

### Post by Pumalite on 2008-04-16
You can also try Xununtu Alternate CD:
[http://cdimage.ubuntu.com/xubuntu/releases/7.10/release/](http://cdimage.ubuntu.com/xubuntu/releases/7.10/release/)

---

### Post by BigWoop on 2008-04-16
How is that likely to help?

It would be nice if I could get the one I already have to work, as I did spend about 5 days downloading the thing.

---

### Post by Pumalite on 2008-04-16
With 256 MB of RAM you cannot boot a Live CD. Alternate is your best bet. I suggested Xubuntu because it is a lighter Desktop and therefore would be faster in your system.

---

### Post by BigWoop on 2008-04-17
> **Pumalite said:**
> With 256 MB of RAM you cannot boot a Live CD. Alternate is your best bet. I suggested Xubuntu because it is a lighter Desktop and therefore would be faster in your system.

Shouldn't I still be able to do a text based install or a server install? As far as I know this system meets the minimum requirements of Ubuntu, so how else can I install it on this system? Surely I must be able to?

---

### Post by Pumalite on 2008-04-17
You can actually boot a Live CD if you make a 500 MB /swap partition ahead of time. It's just that you are better off with a light Desktop. Ubuntu will be so slow, it'll kill you.

---

### Post by Pumalite on 2008-04-17
If you don't like Xubuntu, try Fluxbuntu.

---

### Post by BigWoop on 2008-04-18
> **Pumalite said:**
> If you don't like Xubuntu, try Fluxbuntu.

I'm really just wanting to run a server on this machine, wouldn't it be good enough for an Ubuntu server?

---

