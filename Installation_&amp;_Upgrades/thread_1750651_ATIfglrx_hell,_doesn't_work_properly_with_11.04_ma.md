---
title: "ATI/fglrx hell, doesn't work properly with 11.04 manual or pkg"
date: 2011-05-05
forum: Installation &amp; Upgrades
---

### Post by faldrich on 2011-05-05
I have a new installation of 11.04 with an ATI Radeon HD 2400 video card that previously worked fine under an earlier release.

I tried installing the proprietary drivers through the Additional Drivers section, rebooted and the video is choppy (dragging windows, etc).

From other reports around the Internet I've read, it's clear I'm not the only one experiencing this issue.   

I tried the manual instructions, which turned out to be a mess and ultimately didn't work, either.

So I'm curious what the issue is and whether it's going to be fixed?  Is there any other work around for the problem?

Thanks.

---

### Post by alphacrucis2 on 2011-05-05
> **faldrich said:**
> I have a new installation of 11.04 with an ATI Radeon HD 2400 video card that previously worked fine under an earlier release.

I tried installing the proprietary drivers through the Additional Drivers section, rebooted and the video is choppy (dragging windows, etc).

From other reports around the Internet I've read, it's clear I'm not the only one experiencing this issue.   

I tried the manual instructions, which turned out to be a mess and ultimately didn't work, either.

So I'm curious what the issue is and whether it's going to be fixed?  Is there any other work around for the problem?

Thanks.

This Catalyst driver from the repos works fine with the HD 3400 I have with Ubuntu 11.04. Maybe problem is specific to the HD 2400. If you do the manual install of the driver using the installer from the AMD website, always use the buildpkg method so that your package manager knows that the driver is installed.

---

### Post by faldrich on 2011-05-05
I did use the --buildpkg option.  I got the same result.

It may be a chipset issue, too.  There's just not enough data, all I know is it doesn't work.  

Thanks.

---

### Post by alphacrucis2 on 2011-05-05
> **faldrich said:**
> I did use the --buildpkg option.  I got the same result.

It may be a chipset issue, too.  There's just not enough data, all I know is it doesn't work.  

Thanks.


Do you get the issue if you login to the classic desktop or does it just go bad with unity running?

---

