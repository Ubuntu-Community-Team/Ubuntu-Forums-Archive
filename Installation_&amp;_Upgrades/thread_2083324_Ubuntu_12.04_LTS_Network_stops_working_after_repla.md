---
title: "Ubuntu 12.04 LTS: Network stops working after replacing the mainboard"
date: 2012-11-12
forum: Installation &amp; Upgrades
---

### Post by Mickey S. on 2012-11-12
Hi!

I have searched the web, kept bugging fellow co-workers a lot on the issue but couldn't find any solution that helped me fixing my problem so I'm asking my question here before I think I have to face reinstalling my machine taking **[this]("http://ubuntuforums.org/showthread.php?t=1946145")** into consideration.

The situation: I have run a PC-system with Ubuntu 12.04 LTS installed. The mainboard or the processor broke (told me something about it couldn't bring up core 2 and/or 3 out of 4 during booting the system - for what reason ever) hence I decided to go for new hardware as this rendered me unable to boot the machine.

Upgrading the hardware worked fine so far except for getting the network back up again. When it comes to starting the network during boot it tells me it was  waiting for the network support to come up and since this it not gonna  happen it's gonna wait for up to another 60 seconds. No luck either and  it boots '... without full network... support'. However, it gets me the login screen, lets me log in and then I'm able to fix the issue with a little command line magic. So, as root I have to do the following in turn:

```
ifdown eth0 && ifup eth0 && ip addr flush eth0 && ifdown eth0 && ifup eth0
```Only thereafter I have access to the network again ('route', for example, confirms everything is in order now). But next time I boot the machine same thing's gonna happen again.

I checked with /etc/network/interfaces, it has:

```
auto eth0
auto lo

iface eth0 inet dhcp
iface lo inet loopback
``` and I also flushed /etc/udev/rules.d/70-persistent-net.rules (a new entry for the onboard-NIC is created next time the system boots up).

BTW, booting the same very system from a 12.04 installation CD doesn't show this issue, network's available right away with no complaints during boot up or whatsoever.

So I suppose there's something gone terribly wrong with respect to the network's or the NIC's driver configuration which I can't seem to track down.

Any ideas are on what else to check on are highly appreciated.


Thanks,

 -Mike

---

### Post by fantab on 2012-11-12
Mike, to put it simply, you will have to reinstall ubuntu after major hardware upgrade, like in your case. Ubuntu or any other OS for that matter, configures hardware available to it during installation... later if you change hardware the old config finds itself incompatible with the newer hardware config. 

Just reinstall.

---

### Post by grahammechanical on 2012-11-12
I can also tell you this, Ubuntu does not make use of the /etc/netwprk/interfcase file anymore. This is what you should have in your interfaces file

> auto lo
iface lo inet loopback

Otherwise it conflicts with Network Manager. I suggest that you edit out 

> iface eth0 inet dhcp

and use Network Manager to set up a connection. There is an icon for it in the top panel.

And as fantab has said, Ubuntu detects the hardware during the install process and loads modules and drivers for your hardware during the boot process. So, a fresh install is less problematic when making such a major change as a motherboard and CPU.

On Linux ethernet adapters should work out of the box. You are using an OS without the correct modules being loaded for your hardware. This is my opinion.

Regards.

---

