---
title: "ATI Drivers wont install. ATI Radeon 3450"
date: 2013-10-28
forum: Installation &amp; Upgrades
---

### Post by kyanbelger on 2013-10-28
Hi all,

I'm trying to install the ATI 13.01 CC drivers, but it comes up with this error instantly:

[IMG]http://i.imgur.com/FCTQuJd.png[/IMG]

In /usr/share/ati/fglrx-install.log it has this:

> Check if system has the tools required for installation.
fglrx installation requires that the system have kernel headers.  /lib/modules/3.8.0-32-generic/build/include/linux/version.h cannot be found on this system.
One or more tools required for installation cannot be found on the system. Install the required tools before installing the fglrx driver.
Optionally, run the installer with --force option to install without the tools.
Forcing install will disable AMD hardware acceleration and may make your system unstable. Not recommended.

Do you know what could be causing the drivers not to install? What do I need to install to get [COLOR=#0000cd]/3.8.0-32-generic/build/include/linux/version.h[/COLOR]?

Thanks a lot :)

---

### Post by kyanbelger on 2013-10-31
No answers? :(

---

### Post by Bashing-om on 2013-10-31
kyanbelger; Hi !

Here is the deal:
> 
IF its an HD 2x/3x/4x then you are out of luck as AMD announced <last> summer that it is relegating these chipsets to legacy status and will not be developing new drivers for them. Existing restricted drivers from AMD won't work either, because they require X-server v1.12 and Ubuntu 12.10 uses X-server v1.13.
That's because, starting with Ubuntu 12.04.2, the X-server version was updated to a newer version that is now incompatible with the HD 2x/3x/4x series AMD cards.
(Mark Phelps)

To see your graphics card and info:
```

sudo lshw -C display
lspci | grep VGA
lspci -nnk | grep -iA3 vga

```
Then the better recourse is to use the open source driver.

Sad.
[INDENT][INDENT]that's the way it is
[/INDENT][/INDENT]

---

