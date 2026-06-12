---
title: "sharing internet connections with network manager 0.7"
date: 2008-08-27
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by waster on 2008-08-27
one feature I was looking forward to in NM0.7 was being able to share an internet connection. The option is now available, but as far as the very limited documentation tells, the feature is limited to the GUI.

What I expected was:

1) choose connection to share (i.e. non-internet connected)
2) nothing else

in fact, NM doesn't give that interface an IP address, doesn't hook up with DHCP server or provide DHCP server on that address, and doesn't allow any further configuration.

Is there code behind this option, and if so how does it work?

---

### Post by Nico0020 on 2008-08-27
this is something i've always been waiting for.  As im not network techy enough to get ICS working in linux for my lappy.  I'd love something a lot easier to be able to share my wireless connection by plugging something into my ethernet port.

---

### Post by cariboo on 2008-08-27
Sharing an internet connection is pretty easy to set up, have a look here:

[http://ubuntuforums.org/showthread.php?t=91370](http://ubuntuforums.org/showthread.php?t=91370)

Follow the directions in order and you you should have a working connection in about 5 minutes.

Jim

---

### Post by waster on 2008-08-28
yep - i already had it working with firestarter and nm6, not using the horrifying set of command line instructions... 5 seconds not 5 minutes should be the target for an absolute beginner, no? it may not be technically straightforward behind the scenes, but to the beginner, they just want to plumb the internet "pipes" together.

network manager 0.7 kept resetting the shared interface, losing its IP, so firestarter would fail. the whole point of network manager is that it should deal with this, and obviate the swarm of mini applications each of which partly deals with some of the every day networking tasks people have.

And I've never had dhcp working with firestarter in about five years.

---

### Post by waster on 2008-09-15
the completely undocumented connection sharing feature can be activated by installing the dnsmasq-base package. Not the dnsmasq package, because you do not want the daemon to run.

It only lets one interface share the internet connection, though. And good luck if you want to do ad-hoc wireless networking with encryption on a broadcom card...

---

