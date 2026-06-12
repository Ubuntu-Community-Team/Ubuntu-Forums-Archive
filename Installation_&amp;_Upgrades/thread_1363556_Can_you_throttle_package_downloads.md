---
title: "Can you throttle package downloads?"
date: 2009-12-24
forum: Installation &amp; Upgrades
---

### Post by Objekt on 2009-12-24
We have a pathetic 1.5 Mbit DSL connection and I would prefer it if my various *buntu boxes did not monopolize the connection while they are downloading packages for updates or installing software.  I can't watch streaming video in one machine while another machine is maxing out the pipe.

Is there some setting in the Ubuntu variants where I can specify the maximum download rate for apt-get, Synaptic package manager, etc.?  

I can throttle the various Ethernet ports at the router, but there are a couple of problems with that.  My router has few and inadequate QoS options.  You can only throttle traffic in rather large setps of 512 kbit/s.  This also slows transfers over the LAN, which would pretty much make Samba shares pointless.  So, I would rather change a setting in Ubuntu than use my router's lousy QoS features.

I just want to share the pipe, devoting say 60 kbit/s to package downloads while reserving the rest for streaming video or running Bittorrents on the other machines.

---

### Post by gsmanners on 2009-12-24
I would use "trickle" in that situation, although it configures (in daemon mode) by service rather than application, so I'm not sure how you'd set it up exactly.

Here's an article on it:

[http://www.linux.com/archive/feature/61293](http://www.linux.com/archive/feature/61293)

---

