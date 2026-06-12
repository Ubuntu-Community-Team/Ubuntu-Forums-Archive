---
title: "Nvidia driver install issue"
date: 2011-03-01
forum: Installation &amp; Upgrades
---

### Post by windyweather on 2011-03-01
Ubuntu 10.04 x64
I've built a new system with Nvidia 9300 graphics onboard.
Zotac Geforce 9300 mother board, Intel Core 2 Quad Q8400 CPU.

I'm trying to update the driver to the Nvidia driver via the hardware install, but it gives an error.

[IMG]http://www.windyweather.net/wp/wp-content/uploads/2011/02/Screenshot-Hardware-Drivers-451x500.png[/IMG]

Here's the error I get.

[IMG]http://www.windyweather.net/wp/wp-content/uploads/2011/02/Screenshot-SystemError_InstallArchives-failed.png[/IMG]

[LIST]
[*]Does this have something to do with System Update trying to run while I was doing this,
[*]or that I tried to install an application while it was doing this?
[/LIST]

How do I clean this out so I can try again?

Thanks,
- windy

---

### Post by windyweather on 2011-03-01
I tried a restart and then the install of "recommended" version worked fine.

BTW - This is a re-install from a system that was installed on a laptop that had an AMD video card.

I tried to just boot that system, and it came up with reduced graphics - or some warning about low graphics or something. Then I tried to install this Nvidia driver using the hardware drivers panel and it seemed to work and on restart the system when to the console rather than Xserver. I had not clue how to back out that package while sitting in a terminal interface. I'm sure there is a way, but I wasn't sure what else might not be right, so I just reinstalled the whole system.

So, apparently if you try to install an Nvidia driver over an AMD Radion driver in a configuration, you get a dead system. I had no clue how to bring that one back to life so I just reinstalled the system over it.

Things seem to be working fine now. Monitor resolution is fine and the Nvidia preferences panel shows up fine too.

When in doubt, restart.

Windy

---

### Post by sikander3786 on 2011-03-01
It might have happened because of the on-going Update-Manager tasks. You can't run 2 package managers simultaneously e.g, Software Center, Synaptic, apt-get, aptitude, Update Manager or Jockey.

Once Update Manager finishes its job, reboot your PC and try again.

If it still reports error, go to Applications > Accessories > Terminal and post the output of this command.

```
sudo apt-get update && sudo apt-get upgrade
```

---

### Post by windyweather on 2011-03-01
Yep. Like I said. A restart fixed it right up.

BTW, I was in the middle of doing the hardware driver update, and the update manager started in the background.
But that was probably not the problem.
I also tried to install another program using the Software installer at the same time the hardware thing was running.

My bad. But a restart fixed it right up.

Thanks,
windy

---

