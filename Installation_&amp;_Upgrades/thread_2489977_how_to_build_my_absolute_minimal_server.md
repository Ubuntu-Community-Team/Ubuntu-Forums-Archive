---
title: "how to build my absolute minimal server"
date: 2023-08-16
forum: Installation &amp; Upgrades
---

### Post by oui on 2023-08-16
how to do that with the new version?

what is better:

- start with debootstrap from some live version?
- or start some regular install CD (which on if they are differences?) and terminate the installation earlier refusing to install the desktop (is that continuing to be possible)?

---

### Post by ian-weisser on 2023-08-16
I think you will want to define what "absolute minimal" means to you, since it seems to mean something different to everyone who uses similar terms.

A considers Foo to be bloat, but B considers Foo to be essential. And they are both right.

All my "minimal" servers are in containers, so the install method is neither of those.

There's also [Chiseled Containers]("https://ubuntu.com/blog/craft-custom-chiselled-ubuntu-distroless"), another buzzy-project-of-the-week for folks who have lots of free time to squeeze out a few more MB.

---

### Post by TheFu on 2023-08-17
If you want a truly minimal server, don't use Ubuntu.  There are many lighter distros.
I think the smallest Ubuntu Server is that provided through lxd, but I don't know if it has enough to boot on real hardware.  
You can look over the available images with 
```
lxc image list images:ubuntu
```
The smallest Ubuntu ones I see are 120-150MB.
Debian are between 75MB and 410MB.
But alpine has images that are 3-140MB.  The current ISO for install on hardware is 190MB. [https://dl-cdn.alpinelinux.org/alpine/v3.18/releases/x86_64/](https://dl-cdn.alpinelinux.org/alpine/v3.18/releases/x86_64/)

How small, if that matters?
Might be easier to use other distros if small is the requirement.  

Arch or Slackware can be made fairly small.  Of course, with less size, there are less features pre-installed.

There are very small distros for use in Kiosks. If that's your need, something like TinyCore which was 15MB without a GUI and 25MB with a GUI, last time I checked. They only make 32-bit releases, so 4GB of RAM would be the limit there.  OTOH, they load into RAM and run really, really, fast on almost any hardware for simple websites like a kiosk would have.

---

### Post by MAFoElffen on 2023-08-18
"MINIMAL"

^^^ That is subjective.

I do a lot of testing. I do installs of ISO's, images, deboostrap, rsynch of the Live Image Environment... And install what I need to do what I want.

If you go in steps or levels, there is debootstrap, base, minimal server, server, minimal desktop, desktop. Core is a misnomer. (Is heavily dependent on Snaps.)

---

