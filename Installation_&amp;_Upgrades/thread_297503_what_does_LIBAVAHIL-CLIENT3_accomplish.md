---
title: "what does LIBAVAHIL-CLIENT3 accomplish ??"
date: 2006-11-11
forum: Installation &amp; Upgrades
---

### Post by wpshooter on 2006-11-11
I notice this morning that there are 5 updates available for download.  The first of the 5 is **LIBAVAHI-CLIENT3**.

The description of this first update is as follows:

[B]Avahi is a fully LGPL framework for Multicast DNS Service Discovery. It allows programs to publish and discover services and hosts running on a local network with no specific configuration.
For example you can plug into a network and instantly find printers to print to, files to look at and people to talk to.
This package contains the library for Avahi's C API which
allows you to integrate mDNS/DNS-SD functionality into your application. 
[/B]
Does this actually mean what I think it does ?  

Does this mean that they have finally fixed Ubuntu so that you can share printers, etc. without having to edit a bunch of configuration files and without having to enter a bunch of commands at the terminal prompt ?

After I have downloaded these 5 updates, do I need to go into synaptic and install these or are they installed as a part of the download process ?

Is there a **help** or **how to** on utilizing the capabilities that these updates provide ?

Thanks.

Sorry, mis-spelled file name in post title.  Should be libavahi.

---

### Post by wpshooter on 2006-11-12
Well, apparently no one knows the purpose of this program and how it is supposed to be utilized !!!

---

### Post by munckfish on 2006-11-22
Hi

Avahi implements some very useful technologies called mDNS and DNS-SD, but it's more about reporting that services are there than auto-configuring them. So we're at least half the way there now :D.

For info see:

[https://help.ubuntu.com/community/HowToZeroconf](https://help.ubuntu.com/community/HowToZeroconf)
[http://avahi.org/](http://avahi.org/)

---

### Post by wpshooter on 2006-11-22
> **munckfish said:**
> Hi

Avahi implements some very useful technologies called mDNS and DNS-SD, but it's more about reporting that services are there than auto-configuring them. So we're at least half the way there now :D.

For info see:

[https://help.ubuntu.com/community/HowToZeroconf](https://help.ubuntu.com/community/HowToZeroconf)
[http://avahi.org/](http://avahi.org/)

This seems like to me like the old saying "**getting the cart before the horse**"

However, I appreciate your reply.

---

