---
title: "Firewire: &quot;class 101 doesn't match header type 01&quot;"
date: 2007-05-29
forum: Installation &amp; Upgrades
---

### Post by mac.ryan on 2007-05-29
I run Ubuntu Feisty 32 with the latest kernel and all updates.

As explained in [this thread]("http://ubuntuforums.org/showthread.php?t=454475"), I am trying to enable the possibility to download videos from a firewire device, and for this reason I bought and installed a PCI to ieee1394 (firewire) card. I think this model is sold in italy only (at least with this name) it is a 1394a with 400Mbps rate (see at the end for more details).

The problem is that although all the modules and devices are created correctly in the system, I can't get the card to work. Booting without the options "quiet" and "splash" allowed me to see a series of errors like this:

```
PCI : 0000:07:1:16.0 : class 101 doesn't match header type 01 ignoring class
```

the error repeats itself a number of times, simply incrementing the address number above (the following would be for example "PCI : 0000:07:1:16.0 : ...". Then boot sequence keeps on normally.

I already tried to change slot on the mainboard (errors change slightly, but the card keeps on not working), to boot with the "irqpoll" option and to worship the spirit of Charles Babbage... but none of this led me to a solution.

Ah, the card mounts a "Via vt6306" chipset. From the [description of this MoBo]("http://www.linuxdevices.com/news/NS3462367027.html") - however - it is not the chipset to be incompatible with linux...

Any idea on what I could try next?
Thanks!

---

