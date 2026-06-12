---
title: "nVidia drivers in 14.10 64-bit"
date: 2015-04-18
forum: Installation &amp; Upgrades
---

### Post by stepheny on 2015-04-18
I cannot get any of the nVidia drivers, open source or proprietary, to work in Ubuntu 14.10 64-bit. The NVIDIA X Server Setting only shows very basic configuration choices such as "Show 'really quit' dialog" and offers no choice of driver or GPU. If the settings are opened via the terminal using ```
~$ /usr/bin/nvidia-settings -V
``` the follwing warnings are given:

```
WARNING: NV-CONTROL extension not found on this Display.


WARNING: Unable to determine number of NVIDIA GPUs on ':0'.


WARNING: Unable to determine number of NVIDIA Frame Lock Devices on ':0'.


WARNING: Unable to determine number of NVIDIA VCSs on ':0'.


WARNING: Unable to determine number of NVIDIA SDI Input Devices on ':0'.


WARNING: Unable to determine number of NVIDIA Fans on ':0'.


WARNING: Unable to determine number of NVIDIA Thermal Sensors on ':0'.


WARNING: Unable to determine number of NVIDIA 3D Vision Pro Transceivers on
         ':0'.


WARNING: Unable to determine number of NVIDIA Display Devices on ':0'.


WARNING: Unable to determine number of NVIDIA X Screens on ':0'.


** (nvidia-settings:7366): WARNING **: PRIME: Kindprozess »/usr/bin/prime-supported« konnte nicht ausgeführt werden (Datei oder Verzeichnis nicht gefunden)
** Message: PRIME: is it supported? no

ERROR: nvidia-settings could not find the registry key file. This file should
       have been installed along with this driver at
       /usr/share/nvidia/nvidia-application-profiles-key-documentation. The
       application profiles will continue to work, but values cannot be
       preopulated or validated, and will not be listed in the help text.
       Please see the README for possible values and descriptions.


(nvidia-settings:7366): Gtk-CRITICAL **: _gtk_widget_captured_event: assertion 'WIDGET_REALIZED_FOR_EVENT (widget, event)' failed
```

I don't think the initial "unable to determine....." warnings are the problem as they also appear when I use ```
~$ /usr/bin/nvidia-settings -V
``` on my working 14.04 32-bit OS.

I have spent a day trying out differnt nVidia drivers and repairing my X-Windows and so any help would be very much appreciated.

---

### Post by dino99 on 2015-04-18
i propose you purge the installed nvidia driver (really purging, not only deleting) then reinstall the newer available for your card model.

---

