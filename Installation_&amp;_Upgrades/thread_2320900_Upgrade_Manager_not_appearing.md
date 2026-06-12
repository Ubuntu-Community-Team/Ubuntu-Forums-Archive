---
title: "Upgrade Manager not appearing"
date: 2016-04-18
forum: Installation &amp; Upgrades
---

### Post by GettingNowhere on 2016-04-18
I've added one ppa too many I think.

```
computer@Main:~$ update-manager
Traceback (most recent call last):
  File "/usr/bin/update-manager", line 115, in <module>
    app.start_update()
  File "/usr/lib/python3/dist-packages/UpdateManager/UpdateManager.py", line 212, in start_update
    update_backend = get_backend(self, InstallBackend.ACTION_UPDATE)
  File "/usr/lib/python3/dist-packages/UpdateManager/backend/__init__.py", line 92, in get_backend
    from .InstallBackendAptdaemon import InstallBackendAptdaemon
  File "/usr/lib/python3/dist-packages/UpdateManager/backend/InstallBackendAptdaemon.py", line 12, in <module>
    from aptdaemon.gtk3widgets import (AptCancelButton,
  File "/usr/lib/python3/dist-packages/aptdaemon/gtk3widgets.py", line 42, in <module>
    gi.require_version("Vte", "2.91")
  File "/usr/lib/python3/dist-packages/gi/__init__.py", line 83, in require_version
    (namespace, version))
ValueError: Namespace Vte not available for version 2.91
```

I also get 
```
The following packages were automatically installed and are no longer required:
  audacity-data enblend enfuse hugin-data libgif7 libimage-exiftool-perl
  libimage-exiftool-perl-doc liblept4 liblilv-0-0 libopenjp2-7 libpano13-3
  libpano13-bin libportsmf0 libsbsms10 libserd-0-0 libsord-0-0 libsratom-0-0
  libsuil-0-0 libvamp-hostsdk3 libvigraimpex5 libwxbase2.8-dev
  tesseract-ocr-eng tesseract-ocr-equ tesseract-ocr-osd wx2.8-headers
Use 'apt-get autoremove' to remove them.
```

I've lost Makerbot and Cura.  Replicator doesn't see the USB ports now, so I think I've mashed the mobo.

Any possibility of getting out of this?

---

### Post by grahammechanical on 2016-04-18
Why are you running update manager from a terminal? What version of Ubuntu or its flavours are you using? It is normal for the package manager to inform us of packages no longer required. It is not an indication of anything wrong. and the recommended command will removed them.

```
sudo apt-get autoremove
```

To update/upgrade from a terminal we run

```
sudo apt-get update
sudo apt-get upgrade
```

Do you get any error messages when you run those two commands?

Regards.

---

### Post by GettingNowhere on 2016-04-18
I use 12.04 with Gnome CLassic, or whatever they call it nowadays.
It's the autoremove that stopped the 3d printer from working. Just so many files disappeared the first time.

Update manager does not run from the GUI at all.  

on sudo apt-get update I get:
```
Ignoring Provides line with DepCompareOp for package python-cffi-backend-api-max
Ignoring Provides line with DepCompareOp for package python-cffi-backend-api-min
Ignoring Provides line with DepCompareOp for package python3-cffi-backend-api-max
Ignoring Provides line with DepCompareOp for package python3-cffi-backend-api-min
Ignoring Provides line with DepCompareOp for package pypy-cffi
Ignoring Provides line with DepCompareOp for package pypy-cffi-backend-api-max
Ignoring Provides line with DepCompareOp for package pypy-cffi-backend-api-min
Ignoring Provides line with DepCompareOp for package python-cffi-backend-api-max
Ignoring Provides line with DepCompareOp for package python-cffi-backend-api-min
Ignoring Provides line with DepCompareOp for package python3-cffi-backend-api-max
Ignoring Provides line with DepCompareOp for package python3-cffi-backend-api-min
You may want to run apt-get update to correct these problems
```

On upgrade I get no errors, it just wants me to autoremove.  I'll lose my scanner and OCR if I do.

---

