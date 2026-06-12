---
title: "Which installation type to install? Server or Desktop?"
date: 2008-06-09
forum: Installation &amp; Upgrades
---

### Post by Johhhn on 2008-06-09
hola!

So, here's the situation--

I am going to setup a 'server' for a couple of friends of mine.

Both offices are mixed environments-- Macs and PCs.

One office has around 8 computers, the other 4.

The 'servers' are Pentium 4 machines 2.X ghz.

I am not sure which version to install-- the server version of Ubuntu or the client version.  I would like the ease of use preferablly,,, and as I understand it, only the desktop version has the gui??

Also, and importantly, will the desktop version be suitable for 'serving'?

I am more familiar with OS X and from personal experience I know OS X client serves quite well (file sharing), and figured Ubuntu would as well, but thought I'd doublecheck here first.

thanks!

John

---

### Post by Rocket2DMn on 2008-06-09
Either will work.  IF you use the server version, you can install a graphical interface separately:
```
sudo aptitude install ubuntu-desktop
```
If you setup the desktop version, you can install the server software later, like LAMP.

---

