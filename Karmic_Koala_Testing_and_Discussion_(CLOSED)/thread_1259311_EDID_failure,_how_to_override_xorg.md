---
title: "EDID failure, how to override xorg?"
date: 2009-09-06
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by bobince on 2009-09-06
OK, so Karmic A5 works surprisingly well so far. It finally makes compiz 'just work' on my two-screen Intel G45 desktop.(Previously EXA wouldn't allow a 2560-wide texture and UXA just made a mess of the screen. I don't think we're quite there with the 3D yet, as flicking through the screensavers hung the box completely whilst trying to show GLBlur, but for normal desktop use it seems workable.)

Unfortunately my messages log is full of:

```
kernel: [ 4160.609042] i2c-adapter i2c-3: unable to read EDID block.
kernel: [ 4160.609044] i915 0000:00:02.0: VGA-1: no EDID data
```which may be connected to [bug 394354]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/394354"), except that that is supposed to be fixed (though from the patches list I can't see that it actually got applied).

This happened to me once in Jaunty, as well. (It mysteriously cleared itself up and started detecting the monitor again after a while there; no such luck here.) The result is that it refuses to run the VGA-connected monitor at its native resolution. I fixed this in Jaunty by dropping xorg a hint that the monitor could actually run fast enough to achieve 1280x1024:

```
Section "Screen"
    Identifier  "Configured Screen Device"
    Device      "Configured Video Device"
    SubSection  "Display"
        Virtual 2560 1024
    EndSubSection
EndSection

Section "Device"
    Identifier  "Configured Video Device"
    Option      "monitor-VGA" "vga0"
EndSection

Section "Monitor"
    Identifier  "vga0"
    HorizSync   31-101
EndSection
```However, Karmic appears to be ignoring this, or anything else I try to put in /etc/X11/xorg.conf. From the way gnome-display-properties manages to set a virtual display without touching xorg.conf, I guess there is some new way of configuring it. But where? I can't see any obvious files it's writing to either in /etc or in /home/user.

(A reminder of how to persuade GNOME Panel to stick to the right screen would also be handy! I'm sure I used to be able to just move them across; now they seem to be glued to the secondary VGA screen, bah.)

---

### Post by bobince on 2009-09-07
Right, so. Virtual screens are now configured through xrandr and stored in ~/.config/monitors.xml. That seems reasonable.

The default monitor identifiers seem to have changed, so now the right xorg.conf contents to work around the EDID bug is just:

```
Section "Monitor"
    Identifier  "VGA1"
    HorizSync   31-101
EndSection
```

If there is a way to persuade X that it has the primary and secondary displays the wrong way round I have yet to find it, but GNOME can be peruaded to create panels on the secondary by creating a panel, editing properties, unticking 'Expand', dragging it to the other display and making it expand again. Obviously. (ahem)

---

