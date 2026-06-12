---
title: "dhcdbd obsoleted/superseded by what?"
date: 2008-10-19
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by ShirishAg75 on 2008-10-19
Hi all, 
dhcdbd seems to be obsoleted/superseded but by what?
Is it dhcpcd or autodns-dhcp or something else altogether. I don't mind purging dhcdbd but need to know what its being superseded with, just in case network-manager dies on me while doing something. 

I am a newbie on afa dhcdbd is concerned, looking forward to know more.

---

### Post by ShirishAg75 on 2008-10-20
bumping this one up. Also it seems I'm still running on dhcdbd 

```

 /etc/init.d/dhcdbd status
 * dhcdbd is running.

```

There are number of things I would like to do :-
a. I would like to know which package is taking dhcdbd's place?

b. How can I use network manager to for setting up my router exclusively for network-manager shows for eth1 (the wired ethernet connection to the router) as never. 

c. Also how do I find if dhclient is running or not?

---

### Post by mc4100 on 2008-10-20
Don't know if this helps, but it seems to be relevant:

[http://live.gnome.org/NetworkManagerToDo](http://live.gnome.org/NetworkManagerToDo)
> KILL KILL KILL dhcdbd (DONE)

Make NM spawn /sbin/dhclient and manage the DHCP client lifecycle within NM rather than having dhcdbd do it. We want to spawn it with a custom dhclient-script that forwards the options back to NetworkManager a lot like the current dhclient-script sends them to dhcdbd. When we have this, we can also do smart things about re-acquiring leases we have had in the past for this AP, for example. (Robert Frank is looking into this...) 

---

### Post by ShirishAg75 on 2008-10-21
Hey thanx, saw this happened quite sometime back 

[http://mail.gnome.org/archives/networkmanager-list/2007-August/msg00094.html](http://mail.gnome.org/archives/networkmanager-list/2007-August/msg00094.html)

but final nail in the coffin was done in April 

[http://mail.gnome.org/archives/networkmanager-list/2008-April/msg00243.html](http://mail.gnome.org/archives/networkmanager-list/2008-April/msg00243.html)

---

