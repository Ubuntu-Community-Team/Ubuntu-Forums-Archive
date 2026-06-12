---
title: "Tahr - Black Screen After System Startup"
date: 2014-04-19
forum: Installation &amp; Upgrades
---

### Post by magikarp2 on 2014-04-19
On booting I'm told which kernel version we're using followed by 'loading initial ramdisk'. After that comes the ubuntu loading screen which then brings me to a black screen stating what other things it's loading. Such as gnome display manager, network connection manager, blutooth services etc. Once it's done it then goes to a entirely black screen. It won't go anywhere from here on in. I cannot switch tty. The only thing I can do is press shutdown on my tower which it will then go and do.

I'm currently using the desktop mode on steam os on the same machine so I can retrieve logs etc. I'm not entirely sure which ones to get.

[http://pastebin.com/tfWvhc4C](http://pastebin.com/tfWvhc4C) boot.log
[http://pastebin.com/JMDdDawx](http://pastebin.com/JMDdDawx) xsession-errors (lots of processes exiting with status 1)

---

### Post by magikarp2 on 2014-04-19
I removed catalyst and now I no longer get frozen. My cursor appears and a window (no window manager) appears asking to report a problem. I can now switch to a different tty.

I tried to install the latest catalyst driver but I got this error message.```
Supported adapter detected.Detected a previous installation, /usr/share/ati/amd-uninstall.sh
Dryrun uninstall succeeded continuing with installation.
Check if system has the tools required for installation.
fglrx installation requires that the system have kernel headers for 3.7 release.  /lib/modules/3.11.0-12-generic/build/include/generated/uapi/linux/version.h cannot be found on this system.
One or more tools required for installation cannot be found on the system. Install the required tools before installing the fglrx driver.
Optionally, run the installer with --force option to install without the tools.
Forcing install will disable AMD hardware acceleration and may make your system unstable. Not recommended.
```
I attempted this with the 14.3 beta driver from AMD which supports trusty's 3.11 kernel. Why does it want headers for 3.7?

---

### Post by magikarp2 on 2014-04-19
I didn't realise but after upgrading to trusty I was still using the same 3.11 kernel from raring. I updated to 3.13 and re-installed my catalyst driver. Everything is back to normal now.

Ubuntu kernels are available at [http://kernel.ubuntu.com/~kernel-ppa/mainline/](http://kernel.ubuntu.com/~kernel-ppa/mainline/)

---

### Post by grahammechanical on 2014-04-19
You have just confirmed an opinion of mine. Before upgrading de-activate the proprietary video driver. By the way, this is what we see when we select Recovery Mode

> [COLOR=#000000]On booting I'm told which kernel version we're using followed by 'loading initial ramdisk'. After that comes the ubuntu loading screen which then brings me to a black screen stating what other things it's loading.[/COLOR]

Are you sure that the upgrade to 14.04 is complete? The present 14.04 kernel is Linux 3.13.0-24-generic.

```
uname -a
```

will tell you what you have.

Regards.

---

### Post by magikarp2 on 2014-04-19
Once it was done upgrading it said to reboot so I presume it finished without error. Upon un-installing the driver (so it no longer froze and I could switch tty) I discovered it was still using the same kernel from raring (3.11). I installed 3.13.10 manually (currently using that) re-installed catalyst and now everything's working. It seems it just left the kernel when updating to trusty?

---

