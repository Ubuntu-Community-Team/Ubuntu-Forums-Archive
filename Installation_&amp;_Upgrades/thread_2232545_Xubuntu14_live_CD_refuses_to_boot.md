---
title: "Xubuntu14 live CD refuses to boot"
date: 2014-07-02
forum: Installation &amp; Upgrades
---

### Post by mckilroy on 2014-07-02
Box is an Acer TM8210 and I am since days amusing myself with attempts to get Xubuntu to a desktop.

All the checks/rechecks with md5, USB-stick, burned DVD etc are made and a lot of combinations of kernel-params experimented.

The only param bringing the boot process nearly to an end is "**blacklist=firewire_ohci**"

Without that parameter booting stops before reaching the splash-screen with a simple black screen.

Why the fact, that firewire_ohci is **blacklisted** is ignored stays beyond me.

If anyone can help it would really be appreciated.


[IMG][[IMG]http://i.imgur.com/RIp8Me8.jpg[/IMG]]("http://imgur.com/RIp8Me8")[/IMG]

---

### Post by mckilroy on 2014-07-03
Nobody there who could help?

Or is it a bug, that the kernel parameter is ignored?

---

### Post by xc3RnbFO8P on 2014-07-03
Did you try Nomodeset
[http://askubuntu.com/questions/152847/how-to-access-boot-options-12-04-live-usb]("http://askubuntu.com/questions/152847/how-to-access-boot-options-12-04-live-usb")

---

### Post by mckilroy on 2014-07-03
When trying **blacklist=firewire_ohci + nomodeset** booting would just stop at the  same line (after "**starting configure network device**") but with different  msg:

"**pcmcia_socket pcmcia_socket1: unable to apply power**" 

This firewire issue is not new, its been known as bug since about 2 years. Until now could be worked around by applying "**blacklist=firewire_ohci**".

My point is: why does this kernel **NOT** respect this parameter?

---

