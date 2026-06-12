---
title: "VMware won't install :(  - adwaita and murrine are missing!"
date: 2018-09-17
forum: MINT
---

### Post by drpeppercan on 2018-09-17
Hi all,

I am trying to install VMware Workstation.
Right after it printed "VMware Installer...done." it also printed some errors. I guess this explains why I don't see the actual application anywhere.

```
(vmware-installer.py:4868): Gtk-WARNING **: Unable to locate theme engine in module_path: "adwaita",
/usr/share/themes/Mint-Y/gtk-2.0/main.rc:1085: error: unexpected identifier `direction', expected character `}'

(vmware-installer.py:4868): Gtk-WARNING **: Unable to locate theme engine in module_path: "murrine",


```

I already tried this [code]("http://askubuntu.com/questions/774664/ddg#791965") for the first error, without avail:
[FONT=courier new]sudo apt install gnome-themes-standard
----------------------------------------------------------

For the 2nd error, I checked Synaptic, and found a package called: 
"gtk-engines-murrine", version: 0.98.2-2ubuntu1 (latest version), 
description: "cairo-based gtk+-2.0 theme engine"

Any ideas?

Thanks guys!

[/FONT]

---

### Post by drpeppercan on 2018-09-17
More specifically:
VMware Workstation 14.1.3 Player for Linux 64-bit.

I downloaded this file: VMware-VIX-1.17.0-6661328.x86_64.bundle

---

### Post by drpeppercan on 2018-09-18
All is good now!
As ajgringo619 from the Linux Mint forums pointed out:

*"That's not the right file. You need this one: VMware-Player-14.1.3-9474260.x86_64.bundle"*

I got it installed with the right file already ;)

---

