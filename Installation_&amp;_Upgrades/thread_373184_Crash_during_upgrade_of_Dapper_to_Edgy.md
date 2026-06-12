---
title: "Crash during upgrade of Dapper to Edgy"
date: 2007-03-01
forum: Installation &amp; Upgrades
---

### Post by alexgutteridge on 2007-03-01
I tried upgrading from Dapper to Edgy today via package-manager, but it stalled with an error message halfway through upgrading uim-utils. After leaving it for a while I decided (foolishly in retrospect) to reboot to see if I could restart the upgrade.

Now my machine refuses to boot. In recovery mode it gets to a point where it says:

Begin: Running /scripts/init-bottom ...
[17179574.528000] kjournald starting. Commit interval 5 seconds
Done.
[17179574.656000] usb 3-1: new low speed USB device using uhci_hcd and address 2
[17179575.068000] usb 3-2: new low speed USB device using uhci_hcd and address 3

And then hangs.

What steps can I take to fix a broken upgrade? Is there a way to boot into a console so I can apt-get my way back to safety? Or should I just burn an ISO and reinstall?

Thanks for any help.

AlexG

---

### Post by alexgutteridge on 2007-03-11
OK, I booted into a rescue console from an Ubuntu CD I burned, and I've been trying to fix this upgrade manually with no luck so far.

The problem seems to be something to do with the dbus package. Running:

```
dpkg --configure -a
```

From the console gives a whole load of errors from unconfigured packages. The first is dbus:

```
invoke-rc.d: initscript dbus, action "start" failed.
dpkg: error processing dbus --configure:
subprocess post-installation script returned error exit status 1
```

The other packages then fail to configure because they depend in some way on dbus. Funnily enough, running:

```
/etc/init.d/dbus start
```

Seems to work fine (no error is reported), but

```
/etc/init.d/dbus stop
```

Gives an error:

```
run-parts: run-parts: component /etc/dbus-1/event.d/25avahi-daemon is a broken symbolic link

run-parts: /etc/dbus-1/event.d/20hal exited with return code 1
```

If anyone has any ideas about how to fix this and get me back to a bootable system, it'd be greatly appreciated!

Alex Gutteridge

---

