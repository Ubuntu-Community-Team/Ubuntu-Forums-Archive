---
title: "Ubuntu 10.10: Installation ok, but &quot;Operating System not found&quot; at boot"
date: 2010-12-05
forum: Installation &amp; Upgrades
---

### Post by balanza on 2010-12-05
Hi,

I'm trying to install ubuntu from scratch on my laptop, a TravelMate 4060 with 1.7ghz Intel centrino, 1gb ram, 40gb hard drive. I run the installer from cd and everithing seems fine except for this error([https://bugs.launchpad.net/ubuntu/+source/casper/+bug/539027]("https://bugs.launchpad.net/ubuntu/+source/casper/+bug/539027")), but i red it's not a blocking issue.
But, once i restart and so i reboot, the only i have is a black-scrin with my mac address and some error like:
```

PXE-E53: no boot filename received

PXE-M0F: exiting PXE ROM
Operating system not found

```

any idea? i'm really in a trouble, i can't get my laptop to work!

PS: isn't pxe the network boot? why am i using it?

PPS: I had to reinstall from scratch 'cause my previous instance crashed after a loss of power (it couldn't boot anymore). It was a Kubuntu 10.4 and it worked fine. Do you think anyting could be broken on my harware (i think ram or rom)?

thanks

---

### Post by Quackers on 2010-12-05
Welcome to UF :-)
Is your bios set to boot from a network first?

---

### Post by sikander3786 on 2010-12-06
Welcome to forums :-)

Either your Bios is not set to boot from HDD or it can't find a bootloader in MBR or HDD is not even being recongized as **Quackers** mentioned above.

If tweaking Bios settings doesn't help, bootinfoscript output will tell us exactly about your problem.

Boot an Ubuntu Live CD/USB and post the output of boot script as per instructions here.

[http://bootinfoscript.sourceforge.net](http://bootinfoscript.sourceforge.net)

And please wrap your output with proper code tags # from post menu. [/code] at the end and [code] at beginning.

---

