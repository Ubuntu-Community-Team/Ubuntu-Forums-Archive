---
title: "mini.iso install network issue"
date: 2010-07-12
forum: Installation &amp; Upgrades
---

### Post by Johndo1 on 2010-07-12
I've got this old IBM thinkpad which has 128mb of ram, and I'm trying to configure a small mini.iso minimized ubuntu distro set up on it. From here:  [https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD)

During the instillation, it requires that I connect to the internet to install and choose packages, the problem is the auto configuration always fails. I plugged in via Ethernet, but I'm still not exactly sure how to get it working. 

Any ideas? Thanks.

---

### Post by mörgæs on 2010-07-12
Yes, you need a wired internet connection through the process. A full Ubuntu should also be set up with wired access, by the way.

'The auto configuration always fails' - does this mean that the machine sees the network card, but you need to type some network addresses to get it working?

---

### Post by Johndo1 on 2010-07-14
> 'The auto configuration always fails' - does this mean that the machine sees the network card, but you need to type some network addresses to get it working?

The trouble is, I'm not sure. After the auto-configuration fails, (and yes I'm plugged in via Ethernet) it gives me some more options.

1.) retry
2.) manually connect (which requires manually giving the I.P)
3.) Continue without configuring, but that doesn't work...
and
4.) Type in the DCHP name. 

When I try option 2, I type in a random I.P, then when it asks for the router I type in the routers I.P, and it continues, but then when it asks to choose a mirror, the mirror never responds.

---

### Post by mörgæs on 2010-07-14
Which IP's are you typing? 

Have you verified the IP of the router using another computer on the net?

---

### Post by snowpine on 2010-07-14
> **Johndo1 said:**
> I've got this old IBM thinkpad which has 128mb of ram

You should be looking at a distro like Puppy Linux, Tiny Core, SliTaz, etc. in my opinion.

---

