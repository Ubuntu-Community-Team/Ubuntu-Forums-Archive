---
title: "Software Sources crashes"
date: 2009-03-15
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by n3had on 2009-03-15
```
tru3m0sl3m@tru3m0sl3m-desktop:~$ software-properties-gtk

(software-properties-gtk:14669): Gtk-WARNING **: Unable to locate theme engine in module_path: "ubuntulooks",
Traceback (most recent call last):
  File "/usr/bin/software-properties-gtk", line 44, in <module>
    from softwareproperties.gtk.SoftwarePropertiesGtk import SoftwarePropertiesGtk
ImportError: No module named softwareproperties.gtk.SoftwarePropertiesGtk

```

I've been having this problem since upgrading to alpha5 and the problem still persists

---

### Post by taavikko on 2009-03-15
First of all, you need to run that program with "gksudo"
For being a graphical program allowing you to modify config files.

Are you using custom theme? 
That can cause the first error (shouldn't still cause it to crash)

Have you updated your system?


Every aspect you can tune in software-properties, you can manually edit in 
/etc/apt/sources.list
/etc/update-manager/release-upgrades

Hmm, where's that file that contains update-frequency...?

---

### Post by n3had on 2009-03-15
> **taavikko said:**
> First of all, you need to run that program with "gksudo"
For being a graphical program allowing you to modify config files.

Are you using custom theme? 
That can cause the first error (shouldn't still cause it to crash)

Have you updated your system?


Every aspect you can tune in software-properties, you can manually edit in 
/etc/apt/sources.list
/etc/update-manager/release-upgrades

Hmm, where's that file that contains update-frequency...?

using custom theme yes but it has been always like that

yes i've updated the system and i've no option but to edit the sources list via terminal or text editor.

THankyou

nehad

---

