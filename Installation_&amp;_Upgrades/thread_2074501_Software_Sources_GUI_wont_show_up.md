---
title: "Software Sources GUI wont show up"
date: 2012-10-21
forum: Installation &amp; Upgrades
---

### Post by gennoz on 2012-10-21
Ubuntu 12.10

No matter what i try the software sources suddenly refuses to open, remove reinstall didnt solve the problem.

The logs showing are:

sudo software-properties-gtk
[sudo] password for : 
gpg: /tmp/tmpkvf3mn/trustdb.gpg: trustdb created
Traceback (most recent call last):
  File "/usr/lib/python3/dist-packages/UbuntuDrivers/detect.py", line 162, in packages_for_modalias
    cache_map = packages_for_modalias.cache_maps[apt_cache_hash]
KeyError: -1061816414

During handling of the above exception, another exception occurred:

Traceback (most recent call last):
  File "/usr/bin/software-properties-gtk", line 103, in <module>
    app = SoftwarePropertiesGtk(datadir=options.data_dir, options=options, file=file)
  File "/usr/lib/python3/dist-packages/softwareproperties/gtk/SoftwarePropertiesGtk.py", line 178, in __init__
    self.init_drivers()
  File "/usr/lib/python3/dist-packages/softwareproperties/gtk/SoftwarePropertiesGtk.py", line 1097, in init_drivers
    self.devices = detect.system_device_drivers()
  File "/usr/lib/python3/dist-packages/UbuntuDrivers/detect.py", line 415, in system_device_drivers
    for pkg, pkginfo in system_driver_packages(apt_cache).items():
  File "/usr/lib/python3/dist-packages/UbuntuDrivers/detect.py", line 319, in system_driver_packages
    for p in packages_for_modalias(apt_cache, alias):
  File "/usr/lib/python3/dist-packages/UbuntuDrivers/detect.py", line 164, in packages_for_modalias
    cache_map = _apt_cache_modalias_map(apt_cache)
  File "/usr/lib/python3/dist-packages/UbuntuDrivers/detect.py", line 129, in _apt_cache_modalias_map
    m = package.candidate.record['Modaliases']
  File "/usr/lib/python3/dist-packages/apt/package.py", line 429, in record
    return Record(self._records.record)
UnicodeDecodeError: 'utf-8' codec can't decode byte 0xeb in position 114: invalid continuation byte

---

### Post by gennoz on 2012-10-22
Bump! sorry but i cant find any resolution anywhere.

---

### Post by peripateticus on 2012-10-23
Same deal here since upgrading from 12.04 to 12.10:

> gksudo software-properties-gtk

Fontconfig warning: "/etc/fonts/conf.d/39-clear.conf", line 155: Having multiple values in <test> isn't supported and may not works as expected
Fontconfig warning: "/etc/fonts/conf.d/39-clear.conf", line 176: Having multiple values in <test> isn't supported and may not works as expected
Fontconfig warning: "/etc/fonts/conf.d/39-clear.conf", line 176: Having multiple values in <test> isn't supported and may not works as expected
gpg: /tmp/tmp1vpom8/trustdb.gpg: trustdb created
Traceback (most recent call last):
  File "/usr/lib/python3/dist-packages/UbuntuDrivers/detect.py", line 162, in packages_for_modalias
    cache_map = packages_for_modalias.cache_maps[apt_cache_hash]
KeyError: 3587437

During handling of the above exception, another exception occurred:

Traceback (most recent call last):
  File "/usr/bin/software-properties-gtk", line 103, in <module>
    app = SoftwarePropertiesGtk(datadir=options.data_dir, options=options, file=file)
  File "/usr/lib/python3/dist-packages/softwareproperties/gtk/SoftwarePropertiesGtk.py", line 178, in __init__
    self.init_drivers()
  File "/usr/lib/python3/dist-packages/softwareproperties/gtk/SoftwarePropertiesGtk.py", line 1097, in init_drivers
    self.devices = detect.system_device_drivers()
  File "/usr/lib/python3/dist-packages/UbuntuDrivers/detect.py", line 415, in system_device_drivers
    for pkg, pkginfo in system_driver_packages(apt_cache).items():
  File "/usr/lib/python3/dist-packages/UbuntuDrivers/detect.py", line 319, in system_driver_packages
    for p in packages_for_modalias(apt_cache, alias):
  File "/usr/lib/python3/dist-packages/UbuntuDrivers/detect.py", line 164, in packages_for_modalias
    cache_map = _apt_cache_modalias_map(apt_cache)
  File "/usr/lib/python3/dist-packages/UbuntuDrivers/detect.py", line 129, in _apt_cache_modalias_map
    m = package.candidate.record['Modaliases']
  File "/usr/lib/python3/dist-packages/apt/package.py", line 429, in record
    return Record(self._records.record)
UnicodeDecodeError: 'utf-8' codec can't decode byte 0xeb in position 114: invalid continuation byte

---

### Post by gennoz on 2012-10-26
is that a bug? should i report one?!

---

### Post by dino99 on 2012-10-26
which python version are installed on your system ?

---

### Post by dino99 on 2012-10-26
> peripateticus  

your issue is very different, dont post on that thread.
you need to clean the settings:

sudo rm -rf .fontconfig
sudo rm -rf .fonts 
(if it still exist)

then logout/in, most of the fonts errors should be gone then.

---

### Post by peripateticus on 2012-10-26
Python is 2.7.3.

---

### Post by dino99 on 2012-10-26
> peripateticus    Python is 2.7.3.

it was a question for gennoz, its not your thread here.

---

### Post by peripateticus on 2012-10-26
> **dino99 said:**
> it was a question for gennoz, its not your thread here.

The font *warnings* have nothing to do with the exceptions that python is throwing.  They happen regardless.

---

### Post by gennoz on 2012-10-26
alright, after checking the bugs section i ve got it fixed, some genius guys over there eh:)

sudo gedit /var/lib/dpkg/status

Just execute this, and the save the file despite the warning, this will fix your issue.

---

### Post by peripateticus on 2012-10-26
> **gennoz said:**
> alright, after checking the bugs section i ve got it fixed, some genius guys over there eh:)

sudo gedit /var/lib/dpkg/status

Just execute this, and the save the file despite the warning, this will fix your issue.

Yep, that did the trick! Thank you gennoz!

---

### Post by Netraam on 2013-02-21
> **gennoz said:**
> alright, after checking the bugs section i ve got it fixed, some genius guys over there eh:)

sudo gedit /var/lib/dpkg/status

Just execute this, and the save the file despite the warning, this will fix your issue.

Thanks I had the same issue and this fixed it in no time... could I maybe ask for a link to the bug report in which you found this solution so I can add my two cents?

Thanks again :)

---

