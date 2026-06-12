---
title: "Blank screen on boot [Graphics Drivers for Radeon 6850]"
date: 2011-01-18
forum: Installation &amp; Upgrades
---

### Post by zJerrik on 2011-01-18
I just installed Ubuntu 10.10 fresh. My graphics card is the HD Radeon 6850 (Sapphire).

When I rebooted after updating everything I would be stuck at a black screen. I instead went into the root console and changed my xorg.conf file to do "vesa" instead of "fglrx". It now boots no problem.

However when I do "aticonfig" I get:

```
aticonfig: No supported adapters detected
```

And if I try to load the "Catalyst Control Center" it tells me:

> There was a problem initializing Catalyst Control Center Linux edition. It could be caused by the following.
No ATI graphics driver is installed, or the ATI driver is not functioning properly.
Please install the ATI driver appropriate for you ATI hardware, or configure using aticonfig.

After the default didn't work, I tried to get the drivers from ATI/AMD.

[http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx](http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx)

I ran this, it had no errors. I rebooted, nothing was different. I used the "Additional Drivers" application, and it showed me that I needed to "Activate" my ATI driver again. I guess this changes the xorg.conf file, because when I rebooted after activating, I had the same problem as before with the blank screen. I changed it back to "vesa" and that's where I am now.

Does anyone know what I can do to get the drivers working, or can I even get working drivers for the 6850?

---

### Post by dino99 on 2011-01-18
actual kernel directly deal with X, so no need of xorg.conf by default (it often cause issue)

sudo rm /etc/X11/xorg.conf

you might try booting with either: nomodeset or noacpi (to see what happen when booting, replace "quiet splash" by one of these)

---

### Post by zJerrik on 2011-01-18
> **dino99 said:**
> actual kernel directly deal with X, so no need of xorg.conf by default (it often cause issue)

sudo rm /etc/X11/xorg.conf

you might try booting with either: nomodeset or noacpi (to see what happen when booting, replace "quiet splash" by one of these)

Thanks for the reply.

Removing xorg.conf still allowed me to boot, but it didn't use the ati drivers.

I tried nomodeset and noacpi. If the xorg.conf file is set to "fglrx" it still hangs. I can't even use 'CTRL+ALT+F1' to go into console. Nothing responds. My monitor goes into standby.

If it isn't set, then I boot normally (without the splash screen) but `aticonfig` still gives the same error.

Any other ideas?

---

### Post by Mark Phelps on 2011-01-18
Just went to the AMD drivers site -- and they don't even list Linux drivers for the 6xxxx series of cards. The most currejnt series they list is the 5xxx set. So, any driver you install from AMD is most likely NOT going to work.

---

### Post by zJerrik on 2011-01-18
I have it semi-working. I did a lot, and I honestly am not sure what really made it work.

My main source of information was this page:
[http://wiki.cchtml.com/index.php/Ubuntu_Lucid_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Lucid_Installation_Guide)

I removed everything I could ATI related. I used the downloaded *.run file mentioned in previous posts. I then used the "Additional Drivers" program to install it, and it worked when I rebooted.

I do now have a watermark on both monitors that says "AMD  Unsupported Hardware" so I'm going to see if I can fix that, and if not maybe hte 6xxx series isn't supported like Mark says.

aticonfig still gives the same error, but at least the ATI Catalyst Control Center works (With both monitors).

fglrxinfo works though:

```
$ fglrxinfo 
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: AMD Radeon HD 6800 Series
OpenGL version string: 4.1.10362 Compatibility Profile Context
```

I'll post again if I can remove the watermark.

---

### Post by zJerrik on 2011-01-18
I can't get rid of the Watermark that says "AMD Unsupported hardware". I used this hack:

```
#!/bin/sh
DRIVER=/usr/lib/xorg/modules/drivers/fglrx_drv.so
for x in $(objdump -d $DRIVER|awk '/call/&&/EnableLogo/{print "\\x"$2"\\x"$3"\\x"$4"\\x"$5"\\x"$6}'); do
   sed -i "s/$x/\x90\x90\x90\x90\x90/g" $DRIVER
done
```

I'll just have to suffer it for now I guess =)

---

### Post by sujitn on 2011-01-18
Aw man this really sucks. I just bought a 6950 and i've got the same problems as you do. So simply put is it impossible to install the driver for the card? Because atm i'm running a TV tuner as well and since the drivers aren't installed its really jumpy when watching. Any ideas?

---

### Post by javajeff1 on 2011-04-01
Black screen here as well.

---

