---
title: "safe to remove devicekit?"
date: 2009-07-31
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by scradock on 2009-07-31
The latest (07/30/09) updates offer to upgrade devicekit-power and gnome-power-manager, but claim that it will be necessary to remove devicekit itself to do that. I am unsure if this is just a transitional state before an upgrade to devicekit is available, or is in fact safe.

Does anyone have any information?

---

### Post by autocrosser on 2009-07-31
I've updated without problems. so I would say that it is OK....Devicekit has moved from 003 to 005--its a rather major change, but it went without problems "for me" (your mileage of course may vary.....)

---

### Post by papangul on 2009-07-31
I have undergone that update a couple of days ago, faced some issues(which I think are unrelated to devicekit) but everything is back to normal now.
Take a look here:
[http://ubuntuforums.org/showthread.php?t=1226492](http://ubuntuforums.org/showthread.php?t=1226492)

---

### Post by scradock on 2009-07-31
> **autocrosser said:**
> I've updated without problems. so I would say that it is OK....Devicekit has moved from 003 to 005--its a rather major change, but it went without problems "for me" (your mileage of course may vary.....)
I'm curious - devicekit is not marked as upgradeable - no mention of any 005 version as far as I can see using Synaptic and Update Manager. I guess I'll try it and see what happens.....

---

### Post by scradock on 2009-07-31
well, I'm still running, but I haven't logged out yet....

The upgrade of devicekit-power and gnome-power-manager went through, but there was a warning that "devicekit-power depends on devicekit - but I'll remove devicekit anyway because you asked me to".

I tried immediately to re-install devicekit, but only the 003 version is available, and that will only install if I remove devicekit-power and gnome-power-manager....

I'm using the US repository, as far as I know - switching to Main repo - nope, same version.

So now I don't have devicekit and I can't re-install it.

---

### Post by papangul on 2009-07-31
Thats ok if you don't have any side effects after removing devicekit.

---

### Post by dino99 on 2009-07-31
i've done it with success after reading comment's change & googling about (i do that each time a package need to uninstall an other)

all is ok with that upgrade

---

### Post by scradock on 2009-07-31
> **papangul said:**
> Thats ok if you don't have any side effects after removing devicekit.
Yes, it seems it's OK - I'm back after re-booting with no devicekit installed. It looks as if the package got split into devicekit-disks and devicekit-power, and the devicekit package itself is no longer needed.

No mention of any of this in the man pages - the dk-disks and dk-power man pages are March 2008 versions, and of course I don't have the devicekit man page anymore!

---

### Post by gnomeuser on 2009-07-31
DeviceKit (the base package, not the additional dk modules such as -power and -disks) is no more, the package upstream has been replaced by udev-extras. I believe Karmic is just following upstream.

---

### Post by Kow on 2009-07-31
It looks like devicekit-power is marked as a conflict/replace for devicekit. So, it should be safe to do the upgrade (upgrade/install devicekit-power, remove devicekit).

---

### Post by pressureman on 2009-07-31
Read the changelog guys...

```

devicekit-power (010-0ubuntu1) karmic; urgency=low

  * New upstream release:
    - Port to PolicyKit 1 API.
    - Port from DeviceKit to gudev.
    - Bug fixes.
  * debian/control: 
    - libpolkit-dbus-dev &#8594; libpolkit-gobject-1-dev build dependency.
    - libdevkit-gobject-dev &#8594; libgudev-1.0-dev build dependency.
    - Drop devicekit dependency.
    - Add Conflicts to devicekit. This is not really true in the packaging
      sense, but devicekit only started to exist in earlier karmic and will
      cease to exist now, so clean it up for the benefit of Karmic testers.
      This will be dropped in some weeks.
  * Drop 0001-Add-a-notify-flag-to-set_lid_is_closed.patch, fixed upstream.
  * Add Breaks to gnome-power-manager versions which aren't ported to new
    PolicyKit API yet.

 -- Martin Pitt <martin.pitt@ubuntu.com>  Wed, 22 Jul 2009 18:08:28 +0200

```

[http://changelogs.ubuntu.com/changelogs/pool/main/d/devicekit-power/devicekit-power_010-0ubuntu1/changelog](http://changelogs.ubuntu.com/changelogs/pool/main/d/devicekit-power/devicekit-power_010-0ubuntu1/changelog)

---

### Post by scradock on 2009-07-31
> **pressureman said:**
> Read the changelog guys...

```

devicekit-power (010-0ubuntu1) karmic; urgency=low

  * New upstream release:
    - Port to PolicyKit 1 API.
    - Port from DeviceKit to gudev.
    - Bug fixes.
  * debian/control: 
    - libpolkit-dbus-dev &#8594; libpolkit-gobject-1-dev build dependency.
    - libdevkit-gobject-dev &#8594; libgudev-1.0-dev build dependency.
    - Drop devicekit dependency.
    - Add Conflicts to devicekit. This is not really true in the packaging
      sense, but devicekit only started to exist in earlier karmic and will
      cease to exist now, so clean it up for the benefit of Karmic testers.
      This will be dropped in some weeks.
  * Drop 0001-Add-a-notify-flag-to-set_lid_is_closed.patch, fixed upstream.
  * Add Breaks to gnome-power-manager versions which aren't ported to new
    PolicyKit API yet.

 -- Martin Pitt <martin.pitt@ubuntu.com>  Wed, 22 Jul 2009 18:08:28 +0200

```

[http://changelogs.ubuntu.com/changelogs/pool/main/d/devicekit-power/devicekit-power_010-0ubuntu1/changelog](http://changelogs.ubuntu.com/changelogs/pool/main/d/devicekit-power/devicekit-power_010-0ubuntu1/changelog)
Thanks - that's what I should have done!

---

