---
title: "Install Idea"
date: 2006-07-06
forum: Installation &amp; Upgrades
---

### Post by jsimmons on 2006-07-06
This idea is aimed squarely at those folks who have problems getting Ubuntu installed. There seems to be a lot of these people (I'm one of them).

I recently tried for four days to installl Drake on my primary machine.  During that four-day process, I found out that the kernel shipped on the Live CD is not compatible with my motherboard's SATA controller.  Anyway, here's my idea.

Allow the (advanced) user to configure their Live CD BEFORE they download it.  So, if someone wanted a 2.6.16 kernel compiled for 686 (instead of 2.6.15 compiled for 386), and/or they wanted a specific screen resolution to be used instead of the generic 1024x768), they could specify a custom built Live CD with those parameters.

This "custom" CD could be made relatively small because at the point where you start changing kernels, it could break some applications, so making it a basic system install (with only the most necessary applications included) would probably be best.  Being a "smaller" disk image would make it convenient for the user and for the website.  The iso could be deleted at the end of the suer's session, and optionally, his chosen configuration could be retained for a couple of days in case he needs to try again.

After getting Ubuntu installed (which is what this idea is all about), they could then use Synaptic to get the desired applications.

---

### Post by Jagot on 2006-07-06
Have you any idea what it would take to achieve this?  Apart from the resources required to make a custom config for everyone, part of the point of the Ubuntu idea is that it is free, and the stuff you're talking about with the resolutions would require proprietary drivers to be included on the disc which are non-free.  Oh, and Ubuntu works out of the box in 1280x1024 for me.

---

### Post by jsimmons on 2006-07-06
[QUOTE=Jagot]Have you any idea what it would take to achieve this?  Apart from the resources required to make a custom config for everyone, part of the point of the Ubuntu idea is that it is free, and the stuff you're talking about with the resolutions would require proprietary drivers to be included on the disc which are non-free.[/QUOTE]

It's just an idea, and yeah, I think I comprehend the enormity of it, and that's why I said the custome iso should be limited to the kernel, a basic gnome/xwindows config, and some necessary apps (web browser and synaptic) to get a user started.  Building an iso can be automated.

[QUOTE=Jagot]Oh, and Ubuntu works out of the box in 1280x1024 for me.[/QUOTE]

That's all well and good, but it seems to me I should be able to get 1280x1024 on my 7900GTX as well, yet it doesn't happen automatically (despite the fact that VESA has a 1280x1024 mode).  Granted, it doesn't happen under a Windows install either, but that doesn't mean that it can't be made to happen.  In any case, this is a very minor aspect of the idea as stated.

---

