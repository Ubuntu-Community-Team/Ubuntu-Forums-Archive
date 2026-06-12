---
title: "Weird Screen and System Lockup with Nvidia Driver"
date: 2010-04-11
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by rgutierrez on 2010-04-11
The only driver I've been able to use is the "nv" driver. According to lspci, this is my graphics card:

```
01:00.0 VGA compatible controller: nVidia Corporation G86 [GeForce 8600M GS] (rev a1)
```

Although the nouveau driver is installed, I don't believe it's loading:

```
daddy@mommy-laptop:~$ lsmod | grep -i nouveau
daddy@mommy-laptop:~$
```

But, I don't have it blacklisted. See attached xorg conf and log files. Also, see attached jpg for what my screen looks like when it freezes. System locks up completely. CTRL+ALT+F1 either does nothing or actually causes a reboot. Not sure about that.

Any suggestions?

---

### Post by dino99 on 2010-04-11
your card might work fine with 195.36.15

replace nv by nvidia

goto system admin hardware drivers and select nvidia-current

of course you have to install the required packages with synaptic

As lucid dont need xorg.conf by default, remove yours or rename it (often old xorg.conf or tweated one drop user into troubles)

Let you know that kernel 32.20 is out now and fixed a bunch of bugs, so install it.

(there is a jockey bug now fixed and it might be pushed into repo soon)

---

### Post by rgutierrez on 2010-04-11
Okay, I tried just removing xorg.conf. Same result. I also uninstalled the Nvidia driver and installed via command-line (per another post I found). No luck. When I go to install linux-image-2.6.32.20-generic through synaptics, the package description says:

```
You likely do not want to install this package directly. Instead, install
the linux-generic meta-package, which will ensure that upgrades work
correctly, and that supporting packages are also installed.
```

Can you tell me what this means? Should I just go ahead and install it? Are there post install steps I need to take to configure the kernel to load at boot?

---

### Post by rgutierrez on 2010-04-11
logged bug:

[https://bugs.launchpad.net/ubuntu/+bug/560816](https://bugs.launchpad.net/ubuntu/+bug/560816)

---

