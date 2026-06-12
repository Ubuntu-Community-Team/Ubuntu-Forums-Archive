---
title: "Infra-red remote control doesn't work after upgrade to lucid"
date: 2010-04-30
forum: Installation &amp; Upgrades
---

### Post by Redspike666 on 2010-04-30
I've just upgraded my web/tv setup from 9.10 to lucid and everything seems to be working apart from my infra red remote control.

The remote was working fine in 9.10 and was used to control mythtv-frontend however after the upgrade the remote appears to be controlling ubuntu natively, i.e. right left up and down control what is selected on the desktop where as previously the remote was set to only work within mythtv. Whilst native support for my remote control is muchly appreciated(if that is what this is) where can I configure the controls so that it is usable again?

Sorry if this is a stupid post but I haven't been able to find an answer on my own.

---

### Post by angem1 on 2010-05-03
Hi, I'm experiencing this too, and I noticed that the module usbhid
creates the device node of my Af9015 remote as a keyboard device.
I made this module ignore my device by
adding this line to a file called af9015.conf in /etc/modprobe.d:

```
options usbhid  quirks=0x15a4:0x9016:0x0004
```

in order to find another module that will make the
event-ir device that disappeared from the /dev/input/by-path directory.

I'm not sure whether there is such module, or maybe it's an application,
or maybe it's just some different options as mentioned above.
any help is appreciated.

---

