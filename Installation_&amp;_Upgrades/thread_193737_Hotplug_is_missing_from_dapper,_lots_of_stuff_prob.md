---
title: "Hotplug is missing from dapper, lots of stuff problems related to this"
date: 2006-06-10
forum: Installation &amp; Upgrades
---

### Post by pestie on 2006-06-10
I just upgraded from Breezy to Dapper and had a whole laundry-list of problems. They included:
[LIST]
[*]My sound card's low-level drivers weren't being loaded
[*]My PCMCIA wi-fi card didn't configure itself with DHCP like it should have when I plugged it in
[*]OpenVPN failed due to the tun.ko kernel driver not being loaded and /dev/net/tun not being created
[/LIST]
Turns out all of these are related to the fact that the hotplug subsystem is gone. That's right, just plain gone. Now, unless it's been superceded by some new mechanism (and I haven't seen anything in the forums to indicate that it has), this is going to be a problem, to put it mildly.

I thought maybe I just had a hosed-up sources.list, but I tried the "clean sources list" from [this thread](http://www.ubuntuforums.org/showpost.php?p=1090438&postcount=2) as well as the list on the [official upgrade page](https://wiki.ubuntu.com/DapperUpgrades), but neither one helped. Basically, when I search for hotplug on a Breezy machine, I see it:
```

root@localhost:~ # aptitude search hotplug
i   hotplug                                                               - Linux Hotplug Scripts
v   hotplug-utils                                                         -
p   libnjb-hotplug                                                        - Creative Labs Nomad Jukebox hotplug library

```
But when I try it on my newly-upgraded Dapper machine:
```

root@localhost:~ # aptitude search hotplug
v   hotplug-utils                                                         -

```
What is going on here?

---

### Post by mlho on 2006-06-10
it's missing because it has been replaced by udev

---

### Post by pestie on 2006-06-10
OK, so my next question is - how do I make udev *work*? I've hacked around the problems I described above by loading modules and creating device nodes by hand, but I'd much rather make udev work correctly.

Also, udev is present under Breezy, but so is Hotplug. I thought they were complementary. Has udev completely replaced all the functionality of hotplug now?

---

### Post by rcarring on 2006-06-10
Yes. Hotplug is now deprecated. There is a sort of hotplug clone beginning with m, but I couldn't get it to work for me.

---

### Post by pestie on 2006-06-10
OK, never mind, I found the problem.

I was running a custom, patched 2.6.12 kernel from kernel.org sources. The udev script requires a 2.6.15 or higher kernel. Thus, it was failing to start. I only discovered this because I attempted an **aptitude reinstall udev** and saw the error. Once I booted with the new Dapper kernel, everything was fine. Of course, now my framebuffer console is *blank*, but hey, that's part of the fun, right? ](*,)

---

