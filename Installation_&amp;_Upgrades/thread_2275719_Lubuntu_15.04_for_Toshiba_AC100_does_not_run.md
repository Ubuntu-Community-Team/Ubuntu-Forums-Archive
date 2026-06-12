---
title: "Lubuntu 15.04 for Toshiba AC100 does not run"
date: 2015-04-28
forum: Installation &amp; Upgrades
---

### Post by iourine2 on 2015-04-28
That is all about a very specific Lubuntu distribution for an ARMv7-based machine. Unfortunately, its support seems to be decaying in every new version.

Trying to upgrade from 14.10 to 15.04. After completion and reboot, I get the message

```
starting version 219 
[[COLOR=#ff0000]FAILED[/COLOR]] Failed to start Load Kernel Modules
```

(followed by an advice to view the logs, yet how can I do this without a running system?) Then, in a few seconds, the blue Lubuntu start screen comes, sometimes with a few more error messages, sometimes with only a cursor blinking. And the system hangs finally.

For purity of the experiment, tried to upgrade from a clean, out-of-the-box 14.10 installation that I had backed up in the past. Things are the same, that is, a bricked device. The only peculiarity of my system is that I had repartitioned it, merging the partitions 8 and higher in a single partition.

Surely, it might be helpful to try installing 15.04 from the ground up, but the installer is not provided to the public since many versions ago...

For me personally, this is not a catastrophe as I have backups and can reload my current 14.10 system and stay with it for some time. (Until this on-the-go machine is eventually broken, lost or stolen.) But for other people it may be a problem. I think 15.04-armhf should be withdrawn for further testing and debugging. Generally, it is a great pity that such a brilliant piece of hardware is loosing support. Hopefully, LXQTbuntu will support Samsung Chromebooks one day...

Ready to provide any assistance and debugging info.

---

### Post by david465 on 2015-11-19
I'd just like to add my vote for an upgrade to this brilliant little machine. I've just installed Lubuntu 12.10 by following the Ubuntu guide; didn't know you could put 14:10 on it.
Today I spent a couple of hours on a crowded bus, happily working on a Go programming language project and I don't think anything bigger would have allowed me to do that.
I do have WIFI disconnection problems at the moment so perhaps 14:10 would fix this?

---

### Post by Bucky Ball on 2015-11-19
Firstly, welcome to you both. :)

12.10 reached end-of-life ages ago and you should be upgrading to a supported release. NOT 14.10. That is also unsupported.

FYI: Current supported releases are 12.04 LTS and 14.04 LTS, both long-term support with five years support, 2017 and 2019 respectively. Available interim releases with nine months support are 15.04 which is not worth it as dies in January 2016, and 15.10. 14.04 LTS and 15.10 can both be upgraded directly to the next LTS, 16.04 LTS, later next year.

So, backup and install a supported release. We can't help much with unsupported ones.

As this thread is old and hasn't moved in a long time,

*Thread closed.*

Please post a new thread with a descriptive title for any further issues.

---

