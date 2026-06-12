---
title: "upgrade 14.04.2 Default Video Driver"
date: 2015-07-19
forum: Installation &amp; Upgrades
---

### Post by angel mike on 2015-07-19
I have after some difficulty I  managed to change the default driver ( open source) - which gave me a blank screen - to the legacy binary driver NVIDIA 304.125 after installing Ubuntu 14.04.1. I have a NVIDIA G72(GeForce 7300LE). All this has to be done using commands and being fairly new to ubuntu is very time consuming.

I have tried upgrading to 14.04.2 but it gave me a blank screen again so I reverted back to 14.04.1. I am sure this was because the video driver was changed back to the open source one.

Is there a way of preventing this?
Thanks Mike

---

### Post by Bashing-om on 2015-07-19
angel mike; Hello;

Per :
[http://www.nvidia.com/object/IO_32667.html](http://www.nvidia.com/object/IO_32667.html)
the 304 is the correct version.
How did you install the proprietary driver  ? - did you purge the old driver prior ?
It should be rather straight forward from the "Additional Drivers" tool within Software Sources.

The command line way:

This command will give information about your card + all drivers available including the open source driver.
```

sudo ubuntu-drivers devices

```
To see all the devices that need drivers (list the proprietary video drivers available for your graphic card).
```

sudo ubuntu-drivers list

```
to see all available drivers. These commands take a while to run.
```

sudo ubuntu-drivers autoinstall

```
to install the standard available proprietary video driver; This will install the latest proprietary video driver. If the proprietary video driver is already installed then this command will only read the package lists and rebuild the dependency tree. If that happens then you know you have the proprietary driver installed.

always though
[INDENT][INDENT][INDENT]keep it clean behind you
[/INDENT][/INDENT][/INDENT]

---

### Post by grahammechanical on 2015-07-19
> I am sure this was because the video driver was changed back to the open source one.

That does not happen. The upgrade from 14.04.1 to 14.04.2 will upgrade not only the kernel and the hardware modules (stack) but also the proprietary video drivers. These newer proprietary video drivers may no longer support the older video adapters we may be using. So, we have to use what is called a legacy driver.

I am in the same situation where the newest proprietary video drivers do not support my Nvidia GT220. So, I also use the 304 series driver. If the first reboot after the upgrade hits complications then Ubuntu will try to load an open source video driver as a fall back.

Regards.

---

### Post by angel mike on 2015-07-19
Hi again Bashing-om
Yes I purged the default video driver and installed the legacy Nvidia 304 using commands similar to the ones you listed. The reply from Grahammechanical is saying what I suspected that upgrading to 14.04.2 will leave with the default driver. Hopefully the second time round will less of a hassle. Thanks for replying.

---

### Post by angel mike on 2015-07-19
Thanks for that info - yes I had to install the legacy driver 304 and it looks like I will have to repeat the process. 
Regards

---

