---
title: "Apple Aluminium Bluetooth Keyboard on Jaunty"
date: 2009-04-14
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by pete-woods on 2009-04-14
I'm trying to get an Apple Aluminium Bluetooth Keyboard
[IMG]http://images.apple.com/keyboard/images/gallery/wireless_1_20070813.jpg[/IMG]
that's previously been synced with my MacBook under OSX to work with my Jaunty based HTPC. I don't have any desktop environment setup as it directly starts up into an XBMC environment.

So that leaves me with the command-line tools. I'm trying to avoid using the hidd program from bluez-compat package, as the package description makes it sound pretty deprecated and that it could be removed at any point.

So first I try scanning for the keyboard -- it's found.
```

hcitool --scan
XX:XX:XX pete's keyboard

```

Then I connect to the keyboard:
```
hcitool cc XX:XX:XX
```
This waits a bit, then finishes. Looks like maybe it's connected?

But then if I run:
```
hcitool auth XX:XX:XX
```
it complains about not being connected.

So on a whim I tried them both together
```
hcitool cc XX:XX:XX ; hcitool auth XX:XX:XX
```
 and it sits there waiting for a while. But then it says there was a timeout.

I've tried typing a code on the keyboard and hitting enter afterwards but it doesn't seem to help with the timeout problem.

Am I doing completely the wrong thing to get it all set up? There's a config file in /etc/bluetooth/input.. or something like that which looks like it might want some input. I'm at a loss when trying to find documentation for it, though.

Any help much appreciated!

---

### Post by pete-woods on 2009-04-14
[Bug 343727]("https://bugs.launchpad.net/ubuntu/+source/bluez/+bug/343727") tells me that I'm not the only one with this problem.

Sounds like maybe installing the legacy support is the only way to make it work until that bug is fixed!

---

### Post by b3nw on 2009-04-20
sadly this still seems broken in the RC, looks like the fix isn't high priority enough for Jaunty. Sad because this has been broken since 8.04!

---

