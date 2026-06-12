---
title: "Question about VMware"
date: 2007-03-24
forum: Installation &amp; Upgrades
---

### Post by diablo75 on 2007-03-24
I am thinking about attempting to install windows XP within VMware (I have no idea how to do this yet...).  I have a problem with this piece of software that WINE isn't able to run via emulation.   The software is called AT&T Client Network.  It's used as a tunneling program that allows you internet access and intranet access to different networks, including the internet.  This is used on a large intranet when has the Internet blocked to all users by default.  It essentially connects you to an authentication server and proxy server which in turn hooks you up to the net.

So, if I install this software on a virtual windows XP install, will it share the internet connection from XP with the  Linux it's running inside of??

---

### Post by djf_jeff on 2007-03-24
One thing you can do is to run it in bridged mode, so the Windows guest have full access to the network. In Windows, install the AT&T client and configure it.

After that, create a proxy in Windows and configure your Linux host to use this local proxy. That way, all the traffic goes to the Windows guest and is handled with the AT&T client.

---

### Post by diablo75 on 2007-03-25
I'm not sure if I know how to do that.  As in, how to set it up in "bridged mode", as well as setting up a proxy in Windows...

---

### Post by djf_jeff on 2007-03-25
For the bridged mode, it's in vmware when you create a new virtual machine. You have the choice between bridged, nat and host-only. Just select bridged mode there.

For setting a proxy in windows, maybe you can do it with Putty. I don't know the software which let you do that in windows. Maybe someone more knowledgeable in the windows world can answer.

---

