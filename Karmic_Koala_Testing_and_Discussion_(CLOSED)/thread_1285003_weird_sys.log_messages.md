---
title: "weird sys.log messages"
date: 2009-10-07
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by raiwo on 2009-10-07
```
 gnome-session[1419]: devkit-power-gobject-WARNING: unhandled property 'IsPresent'
Oct  7 16:42:07 mika-laptop gnome-session[1419]: devkit-power-gobject-WARNING: unhandled property 'RecallNotice'
Oct  7 16:42:07 mika-laptop gnome-session[1419]: devkit-power-gobject-WARNING: unhandled property 'Percentage'
Oct  7 16:42:07 mika-laptop gnome-session[1419]: devkit-power-gobject-WARNING: unhandled property 'RecallVendor'
Oct  7 16:42:07 mika-laptop gnome-session[1419]: devkit-power-gobject-WARNING: unhandled property 'RecallUrl'
Oct  7 16:42:07 mika-laptop gnome-session[1419]: devkit-power-gobject-WARNING: unhandled property 'UpdateTime'
Oct  7 16:42:07 mika-laptop gnome-session[1419]: devkit-power-gobject-WARNING: unhandled property 'Type'
Oct  7 16:42:07 mika-laptop gnome-session[1419]: devkit-power-gobject-WARNING: unhandled property 'TimeToEmpty'
Oct  7 16:42:07 mika-laptop gnome-session[1419]: devkit-power-gobject-WARNING: unhandled property 'Online'
Oct  7 16:42:07 mika-laptop gnome-session[1419]: devkit-power-gobject-WARNING: unhandled property 'EnergyRate'
Oct  7 16:42:07 mika-laptop gnome-session[1419]: devkit-power-gobject-WARNING: unhandled property 'NativePath'
Oct  7 16:42:07 mika-laptop gnome-session[1419]: devkit-power-gobject-WARNING: unhandled property 'Model'
Oct  7 16:42:07 mika-laptop gnome-session[1419]: devkit-power-gobject-WARNING: unhandled property 'Serial'
Oct  7 16:42:07 mika-laptop gnome-session[1419]: devkit-power-gobject-WARNING: unhandled property 'HasStatistics'
Oct  7 16:42:07 mika-laptop gnome-session[1419]: devkit-power-gobject-WARNING: unhandled property 'EnergyFull'
Oct  7 16:42:07 mika-laptop gnome-session[1419]: devkit-power-gobject-WARNING: unhandled property 'HasHistory'
Oct  7 16:42:07 mika-laptop gnome-session[1419]: devkit-power-gobject-WARNING: unhandled property 'EnergyFullDesign'
Oct  7 16:42:07 mika-laptop gnome-session[1419]: devkit-power-gobject-WARNING: unhandled property 'Vendor'
Oct  7 16:42:07 mika-laptop gnome-session[1419]: devkit-power-gobject-WARNING: unhandled property 'PowerSupply'
Oct  7 16:42:07 mika-laptop gnome-session[1419]: devkit-power-gobject-WARNING: unhandled property 'State'
Oct  7 16:42:07 mika-laptop gnome-session[1419]: devkit-power-gobject-WARNING: unhandled property 'TimeToFull'
Oct  7 16:42:07 mika-laptop gnome-session[1419]: devkit-power-gobject-WARNING: unhandled property 'EnergyEmpty'
Oct  7 16:42:07 mika-laptop gnome-session[1419]: devkit-power-gobject-WARNING: unhandled property 'IsRechargeable'
Oct  7 16:42:07 mika-laptop gnome-session[1419]: devkit-power-gobject-WARNING: unhandled property 'Technology'
Oct  7 16:42:07 mika-laptop gnome-session[1419]: devkit-power-gobject-WARNING: unhandled property 'Energy'
Oct  7 16:42:07 mika-laptop gnome-session[1419]: devkit-power-gobject-WARNING: unhandled property 'Voltage'
Oct  7 16:42:07 mika-laptop gnome-session[1419]: devkit-power-gobject-WARNING: unhandled property 'Capacity'
```

sys log is full of these, anyone know WTF are these? something to do with my battery?

---

### Post by tekstr1der on 2009-10-07
I believe it has to do with this:

```
devicekit-power (011-1) unstable; urgency=low

  [ Michael Biebl ]
  * New upstream release.
  * debian/control
    - Add Recommends on pm-utils and policykit-1.

  [ Martin Pitt ]
  * debian/control:  This version changes the internal D-BUS API. Make library
    and daemon break each other for versions prior to 011, to avoid partial
    upgrades.

```

AFAICT gnome-session hasn't been updated to work with the new dbus api?

---

