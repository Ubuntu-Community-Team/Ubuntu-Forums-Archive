---
title: "Synaptic Package Magagement: &quot;To be removed&quot; means?"
date: 2011-01-06
forum: Installation &amp; Upgrades
---

### Post by ridethestream on 2011-01-06
Hi, 

I have one issue of Synaptic Package management program. It might be related to apt-get also.

Whenever I select packages that I do not need at all, Synaptic shows "To be removed" package list.
For example, I was going to completely remove a library file: libecal1.2-7.
It has many dependencies: gnome-applet, gnome-panel, etc.

Does Synaptic actually removes other packages that the libecal1.2-7 depends on? 

I'd like clean up irrelevant programs came with default installation. But, "To be removed:" packages really hold me back.

---

### Post by howefield on 2011-01-06
The "to be removed" packages will be removed along with the package that you want uninstalling.

So it makes sense to always look at the list of proposed removals to ensure that nothing you need for other applications is going to be uninstalled.

---

