---
title: "Xubuntu 11.04 and VMware trouble"
date: 2011-06-03
forum: Installation &amp; Upgrades
---

### Post by kjuergen on 2011-06-03
As a refuge from CentOS (no way I will use KDE4 or gnome) I ended up with Xubuntu 11.04 x86_64 and I like it a lot.

Except for the missing screen at start-up everything went smooth until I tried to install VMware workstation 7.1.4 (I have a full license).

If I install with sudo sh VMware_____.bundle the installer makes it through just fine but if I try to start it all I get is a short splash of a screen and it's done. Starting it manually it runs through a bunch of things and shows a lot of gtk warnings until it gets stuck and that's it. No screen at all.

Out of desperation I installed it with sudo su - and then the sh VMware.....bundle. If I then start it still as root (su -, vmware &) it works just fine but it doesn't work as user.

I tried a lot of the "fixes" I found on the VMware site and googled but unfortunately no success.

Did someone get it to work????

Thanks,

Juergen

---

### Post by Toz on 2011-06-03
Have a look at: [http://communities.vmware.com/thread/308540](http://communities.vmware.com/thread/308540)

---

### Post by kjuergen on 2011-06-03
Thanks but I have been there several times. The new 7.1.4 doesn't need a patch, just some settings corrected.

I have to correct my first posting: no matter how I install it it runs just fine if I use "sudo vmware" to start it!

If I just use the menu or no sudo from CLI it runs a bit and then it stops.......

As usual VMware support is not helpful at all. They love to take your money but they never come up with anything.....

Juergen

(vmware-unity-helper:5501): GLib-WARNING **: /build/buildd/glib2.0-2.28.6/./glib/goption.c:2132: ignoring no-arg, optional-arg or filename flags (8) on option of type 0
is the line it gets stuck....

---

### Post by Toz on 2011-06-03
Can you post back error messages when starting vmware as regular user from CLI?

---

### Post by Toz on 2011-06-03
[http://communities.vmware.com/message/1725395#1725395](http://communities.vmware.com/message/1725395#1725395) suggests:

```
$ export LD_PRELOAD=/usr/lib/vmware/lib/libglib-2.0.so.0/libglib-2.0.so.0
$ vmware
```

---

### Post by kjuergen on 2011-06-03
Toz,

sure but it can't be that patch as it runs perfect as root (start with sudo vmware)!

Juergen

kjs@LinWS1:/raid/kjs$ vmware

(vmware-modconfig:2119): Gtk-WARNING **: GModule (/usr/lib/gtk-2.0/2.10.0/engines/libclearlooks.so) initialization check failed: Gtk+ version too old (micro mismatch)

(vmware-modconfig:2119): Gtk-WARNING **: GModule (/usr/lib/gtk-2.0/2.10.0/engines/libclearlooks.so) initialization check failed: Gtk+ version too old (micro mismatch)

(vmware-modconfig:2119): Gtk-WARNING **: GModule (/usr/lib/gtk-2.0/2.10.0/engines/libclearlooks.so) initialization check failed: Gtk+ version too old (micro mismatch)

(vmware-modconfig:2119): Gtk-WARNING **: GModule (/usr/lib/gtk-2.0/2.10.0/engines/libclearlooks.so) initialization check failed: Gtk+ version too old (micro mismatch)

(vmware-modconfig:2119): Gtk-WARNING **: GModule (/usr/lib/gtk-2.0/2.10.0/engines/libclearlooks.so) initialization check failed: Gtk+ version too old (micro mismatch)

(vmware-modconfig:2119): Gtk-WARNING **: GModule (/usr/lib/gtk-2.0/2.10.0/engines/libclearlooks.so) initialization check failed: Gtk+ version too old (micro mismatch)

(vmware-modconfig:2119): Gtk-WARNING **: GModule (/usr/lib/gtk-2.0/2.10.0/engines/libclearlooks.so) initialization check failed: Gtk+ version too old (micro mismatch)

(vmware-modconfig:2119): Gtk-WARNING **: GModule (/usr/lib/gtk-2.0/2.10.0/engines/libclearlooks.so) initialization check failed: Gtk+ version too old (micro mismatch)

(vmware-modconfig:2119): Gtk-WARNING **: GModule (/usr/lib/gtk-2.0/2.10.0/engines/libclearlooks.so) initialization check failed: Gtk+ version too old (micro mismatch)

(vmware-modconfig:2119): Gtk-WARNING **: GModule (/usr/lib/gtk-2.0/2.10.0/engines/libclearlooks.so) initialization check failed: Gtk+ version too old (micro mismatch)

(vmware-modconfig:2119): Gtk-WARNING **: GModule (/usr/lib/gtk-2.0/2.10.0/engines/libclearlooks.so) initialization check failed: Gtk+ version too old (micro mismatch)

(vmware-modconfig:2119): Gtk-WARNING **: GModule (/usr/lib/gtk-2.0/2.10.0/engines/libclearlooks.so) initialization check failed: Gtk+ version too old (micro mismatch)

(vmware-modconfig:2119): Gtk-WARNING **: GModule (/usr/lib/gtk-2.0/2.10.0/engines/libclearlooks.so) initialization check failed: Gtk+ version too old (micro mismatch)

(vmware-modconfig:2119): Gtk-WARNING **: GModule (/usr/lib/gtk-2.0/2.10.0/engines/libclearlooks.so) initialization check failed: Gtk+ version too old (micro mismatch)

(vmware-modconfig:2119): Gtk-WARNING **: GModule (/usr/lib/gtk-2.0/2.10.0/engines/libclearlooks.so) initialization check failed: Gtk+ version too old (micro mismatch)

(vmware-modconfig:2119): Gtk-WARNING **: GModule (/usr/lib/gtk-2.0/2.10.0/engines/libclearlooks.so) initialization check failed: Gtk+ version too old (micro mismatch)

(vmware-modconfig:2119): Gtk-WARNING **: GModule (/usr/lib/gtk-2.0/2.10.0/engines/libclearlooks.so) initialization check failed: Gtk+ version too old (micro mismatch)

(vmware-modconfig:2119): Gtk-WARNING **: GModule (/usr/lib/gtk-2.0/2.10.0/engines/libclearlooks.so) initialization check failed: Gtk+ version too old (micro mismatch)
** (vmware-modconfig:2119): DEBUG: This Gtk+ version doesn't have the GtkSettings::gtk-enable-input-feedback-sounds property.
Logging to /tmp/vmware-kjs/setup-2119.log
filename:       /lib/modules/2.6.38-8-generic/misc/vmmon.ko
supported:      external
license:        GPL v2
description:    VMware Virtual Machine Monitor.
author:         VMware, Inc.
srcversion:     E3E1CF871CA4C3D90799510
depends:        
vermagic:       2.6.38-8-generic SMP mod_unload modversions 
filename:       /lib/modules/2.6.38-8-generic/misc/vmnet.ko
supported:      external
license:        GPL v2
description:    VMware Virtual Networking Driver.
author:         VMware, Inc.
srcversion:     2B4EDE3FA7EF8212DBBF653
depends:        
vermagic:       2.6.38-8-generic SMP mod_unload modversions 
filename:       /lib/modules/2.6.38-8-generic/misc/vmblock.ko
supported:      external
version:        1.1.2.0
license:        GPL v2
description:    VMware Blocking File System
author:         VMware, Inc.
srcversion:     400149ED038D22A87322D56
depends:        
vermagic:       2.6.38-8-generic SMP mod_unload modversions 
parm:           root:The directory the file system redirects to. (charp)
filename:       /lib/modules/2.6.38-8-generic/misc/vmci.ko
supported:      external
license:        GPL v2
description:    VMware Virtual Machine Communication Interface (VMCI).
author:         VMware, Inc.
srcversion:     A332EC5BECB386E33233230
depends:        
vermagic:       2.6.38-8-generic SMP mod_unload modversions 
filename:       /lib/modules/2.6.38-8-generic/misc/vsock.ko
supported:      external
license:        GPL v2
version:        1.0.0.0
description:    VMware Virtual Socket Family
author:         VMware, Inc.
srcversion:     30E957C8B85A577264B0300
depends:        vmci
vermagic:       2.6.38-8-generic SMP mod_unload modversions 
filename:       /lib/modules/2.6.38-8-generic/misc/vmmon.ko
supported:      external
license:        GPL v2
description:    VMware Virtual Machine Monitor.
author:         VMware, Inc.
srcversion:     E3E1CF871CA4C3D90799510
depends:        
vermagic:       2.6.38-8-generic SMP mod_unload modversions 
Fontconfig error: "conf.d", line 1: no element found
Fontconfig warning: line 73: unknown element "cachedir"
Fontconfig warning: line 74: unknown element "cachedir"
/usr/lib/vmware/bin/vmware: symbol lookup error: /usr/lib/gtk-2.0/modules/libcanberra-gtk-module.so: undefined symbol: gtk_widget_is_drawable
kjs@LinWS1:/raid/kjs$ 
(vmware-tray:2146): Gtk-WARNING **: GModule (/usr/lib/gtk-2.0/2.10.0/engines/libclearlooks.so) initialization check failed: Gtk+ version too old (micro mismatch)

(vmware-tray:2146): Gtk-WARNING **: GModule (/usr/lib/gtk-2.0/2.10.0/engines/libclearlooks.so) initialization check failed: Gtk+ version too old (micro mismatch)

(vmware-tray:2146): Gtk-WARNING **: GModule (/usr/lib/gtk-2.0/2.10.0/engines/libclearlooks.so) initialization check failed: Gtk+ version too old (micro mismatch)

(vmware-tray:2146): Gtk-WARNING **: GModule (/usr/lib/gtk-2.0/2.10.0/engines/libclearlooks.so) initialization check failed: Gtk+ version too old (micro mismatch)

(vmware-tray:2146): Gtk-WARNING **: GModule (/usr/lib/gtk-2.0/2.10.0/engines/libclearlooks.so) initialization check failed: Gtk+ version too old (micro mismatch)

(vmware-tray:2146): Gtk-WARNING **: GModule (/usr/lib/gtk-2.0/2.10.0/engines/libclearlooks.so) initialization check failed: Gtk+ version too old (micro mismatch)

(vmware-tray:2146): Gtk-WARNING **: GModule (/usr/lib/gtk-2.0/2.10.0/engines/libclearlooks.so) initialization check failed: Gtk+ version too old (micro mismatch)

(vmware-tray:2146): Gtk-WARNING **: GModule (/usr/lib/gtk-2.0/2.10.0/engines/libclearlooks.so) initialization check failed: Gtk+ version too old (micro mismatch)

(vmware-tray:2146): Gtk-WARNING **: GModule (/usr/lib/gtk-2.0/2.10.0/engines/libclearlooks.so) initialization check failed: Gtk+ version too old (micro mismatch)

(vmware-tray:2146): Gtk-WARNING **: GModule (/usr/lib/gtk-2.0/2.10.0/engines/libclearlooks.so) initialization check failed: Gtk+ version too old (micro mismatch)

(vmware-tray:2146): Gtk-WARNING **: GModule (/usr/lib/gtk-2.0/2.10.0/engines/libclearlooks.so) initialization check failed: Gtk+ version too old (micro mismatch)

(vmware-tray:2146): Gtk-WARNING **: GModule (/usr/lib/gtk-2.0/2.10.0/engines/libclearlooks.so) initialization check failed: Gtk+ version too old (micro mismatch)

(vmware-tray:2146): Gtk-WARNING **: GModule (/usr/lib/gtk-2.0/2.10.0/engines/libclearlooks.so) initialization check failed: Gtk+ version too old (micro mismatch)

(vmware-tray:2146): Gtk-WARNING **: GModule (/usr/lib/gtk-2.0/2.10.0/engines/libclearlooks.so) initialization check failed: Gtk+ version too old (micro mismatch)

(vmware-tray:2146): Gtk-WARNING **: GModule (/usr/lib/gtk-2.0/2.10.0/engines/libclearlooks.so) initialization check failed: Gtk+ version too old (micro mismatch)

(vmware-tray:2146): Gtk-WARNING **: GModule (/usr/lib/gtk-2.0/2.10.0/engines/libclearlooks.so) initialization check failed: Gtk+ version too old (micro mismatch)

(vmware-tray:2146): Gtk-WARNING **: GModule (/usr/lib/gtk-2.0/2.10.0/engines/libclearlooks.so) initialization check failed: Gtk+ version too old (micro mismatch)

(vmware-tray:2146): Gtk-WARNING **: GModule (/usr/lib/gtk-2.0/2.10.0/engines/libclearlooks.so) initialization check failed: Gtk+ version too old (micro mismatch)
** (vmware-tray:2146): DEBUG: This Gtk+ version doesn't have the GtkSettings::gtk-enable-input-feedback-sounds property.

(vmware-unity-helper:2183): Gtk-WARNING **: GModule (/usr/lib/gtk-2.0/2.10.0/engines/libclearlooks.so) initialization check failed: Gtk+ version too old (micro mismatch)

(vmware-unity-helper:2183): Gtk-WARNING **: GModule (/usr/lib/gtk-2.0/2.10.0/engines/libclearlooks.so) initialization check failed: Gtk+ version too old (micro mismatch)

(vmware-unity-helper:2183): Gtk-WARNING **: GModule (/usr/lib/gtk-2.0/2.10.0/engines/libclearlooks.so) initialization check failed: Gtk+ version too old (micro mismatch)

(vmware-unity-helper:2183): Gtk-WARNING **: GModule (/usr/lib/gtk-2.0/2.10.0/engines/libclearlooks.so) initialization check failed: Gtk+ version too old (micro mismatch)

(vmware-unity-helper:2183): Gtk-WARNING **: GModule (/usr/lib/gtk-2.0/2.10.0/engines/libclearlooks.so) initialization check failed: Gtk+ version too old (micro mismatch)

(vmware-unity-helper:2183): Gtk-WARNING **: GModule (/usr/lib/gtk-2.0/2.10.0/engines/libclearlooks.so) initialization check failed: Gtk+ version too old (micro mismatch)

(vmware-unity-helper:2183): Gtk-WARNING **: GModule (/usr/lib/gtk-2.0/2.10.0/engines/libclearlooks.so) initialization check failed: Gtk+ version too old (micro mismatch)

(vmware-unity-helper:2183): Gtk-WARNING **: GModule (/usr/lib/gtk-2.0/2.10.0/engines/libclearlooks.so) initialization check failed: Gtk+ version too old (micro mismatch)

(vmware-unity-helper:2183): Gtk-WARNING **: GModule (/usr/lib/gtk-2.0/2.10.0/engines/libclearlooks.so) initialization check failed: Gtk+ version too old (micro mismatch)

(vmware-unity-helper:2183): Gtk-WARNING **: GModule (/usr/lib/gtk-2.0/2.10.0/engines/libclearlooks.so) initialization check failed: Gtk+ version too old (micro mismatch)

(vmware-unity-helper:2183): Gtk-WARNING **: GModule (/usr/lib/gtk-2.0/2.10.0/engines/libclearlooks.so) initialization check failed: Gtk+ version too old (micro mismatch)

(vmware-unity-helper:2183): Gtk-WARNING **: GModule (/usr/lib/gtk-2.0/2.10.0/engines/libclearlooks.so) initialization check failed: Gtk+ version too old (micro mismatch)

(vmware-unity-helper:2183): Gtk-WARNING **: GModule (/usr/lib/gtk-2.0/2.10.0/engines/libclearlooks.so) initialization check failed: Gtk+ version too old (micro mismatch)

(vmware-unity-helper:2183): Gtk-WARNING **: GModule (/usr/lib/gtk-2.0/2.10.0/engines/libclearlooks.so) initialization check failed: Gtk+ version too old (micro mismatch)

(vmware-unity-helper:2183): Gtk-WARNING **: GModule (/usr/lib/gtk-2.0/2.10.0/engines/libclearlooks.so) initialization check failed: Gtk+ version too old (micro mismatch)

(vmware-unity-helper:2183): Gtk-WARNING **: GModule (/usr/lib/gtk-2.0/2.10.0/engines/libclearlooks.so) initialization check failed: Gtk+ version too old (micro mismatch)

(vmware-unity-helper:2183): Gtk-WARNING **: GModule (/usr/lib/gtk-2.0/2.10.0/engines/libclearlooks.so) initialization check failed: Gtk+ version too old (micro mismatch)

(vmware-unity-helper:2183): Gtk-WARNING **: GModule (/usr/lib/gtk-2.0/2.10.0/engines/libclearlooks.so) initialization check failed: Gtk+ version too old (micro mismatch)
** (vmware-unity-helper:2183): DEBUG: This Gtk+ version doesn't have the GtkSettings::gtk-enable-input-feedback-sounds property.

(vmware-unity-helper:2183): GLib-WARNING **: /build/buildd/glib2.0-2.28.6/./glib/goption.c:2132: ignoring no-arg, optional-arg or filename flags (8) on option of type 0

(vmware-unity-helper:2183): GLib-WARNING **: /build/buildd/glib2.0-2.28.6/./glib/goption.c:2132: ignoring no-arg, optional-arg or filename flags (8) on option of type 0
/usr/lib/vmware/bin/vmware-tray: symbol lookup error: /usr/lib/gtk-2.0/modules/libcanberra-gtk-module.so: undefined symbol: gtk_widget_is_drawable

---

### Post by Toz on 2011-06-04
[http://holyhandgrenade.org/blog/2010/10/using-system-gtk-with-vmware-workstation-on-linux/](http://holyhandgrenade.org/blog/2010/10/using-system-gtk-with-vmware-workstation-on-linux/) (though I'm doubtful it will help - it may get rid of some of your error messages). 

Otherwise,I am sorry, but I am at a loss. I see you have posted at: [http://communities.vmware.com/thread/308540](http://communities.vmware.com/thread/308540) - perhaps someone else can offer some suggestions.

---

### Post by Toz on 2011-06-04
And one other thought, perhaps vmware is running but not visibile. When you execute vmware at the command line, open another terminal and type in:```
ps -ef | grep -i vmware | grep -v grep
```to see if it is.

Also, do you have the Compositor enabled? (Settings->Settings Manager->Window Manager Tweaks->Compositor tab). If so, try disabling and running vmware again.

---

### Post by kjuergen on 2011-06-04
> **Toz said:**
> [http://holyhandgrenade.org/blog/2010/10/using-system-gtk-with-vmware-workstation-on-linux/](http://holyhandgrenade.org/blog/2010/10/using-system-gtk-with-vmware-workstation-on-linux/) (though I'm doubtful it will help - it may get rid of some of your error messages)

Toz,

thank you so much! This did the trick!!!!! Now it only bugs me with the acceptance of the license every time I start it but heck, that's the price for using proprietary software.

Juergen

---

### Post by Toz on 2011-06-04
:shock: I'm surprised it worked.

EDIT: As for the license acceptance prompt, double-check that you have ownership of the .vmware directly. Maybe its unable to save you response to the configuration file.

---

### Post by kjuergen on 2011-06-04
Toz,  you saved my weekend! After I changed permission for all the files in the folder it WORKS! Still no fan of proprietary blobs......

Thank you so much!

Juergen

---

### Post by Toz on 2011-06-04
No worries. If you don't mind, can you change this tread to solved via the Thread Tools in case someone else is looking for a solution to this problem.

---

