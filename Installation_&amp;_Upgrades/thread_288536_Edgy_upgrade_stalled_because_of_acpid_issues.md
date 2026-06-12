---
title: "Edgy upgrade stalled because of acpid issues"
date: 2006-10-30
forum: Installation &amp; Upgrades
---

### Post by Emess on 2006-10-30
I followed the guide to upgrade to edgy at [https://wiki.kubuntu.org/KubuntuUpgrade](https://wiki.kubuntu.org/KubuntuUpgrade). All went well until ```
apt-get install kubuntu-desktop python-qt3 python-kde3 ubuntu-minimal
```

At this point, kubuntu-desktop tried to do something with acpid. I managed to install xserver ok, but i can't continue the upgrade because kubuntu-desktopp is missing dependencies. Here is the error it gives:
```
Setting up acpi (0.09-1) ...
Setting up acpid (1.0.4-5ubuntu4) ...
 * Loading ACPI modules...                                                                                                                                                  [ ok ]
 * Starting ACPI services...                                                                                           
acpid: can't open /proc/acpi/event: Device or resource busy
invoke-rc.d: initscript acpid, action "start" failed.
dpkg: error processing acpid (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of acpi-support:
 acpi-support depends on acpid (>= 1.0.4-1ubuntu4); however:
  Package acpid is not configured yet.
dpkg: error processing acpi-support (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of powermanagement-interface:
 powermanagement-interface depends on acpi-support (>= 0.17); however:
  Package acpi-support is not configured yet.
dpkg: error processing powermanagement-interface (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of kubuntu-desktop:
 kubuntu-desktop depends on acpi-support; however:
  Package acpi-support is not configured yet.
 kubuntu-desktop depends on acpid; however:
  Package acpid is not configured yet.
 kubuntu-desktop depends on powermanagement-interface; however:
  Package powermanagement-interface is not configured yet.
dpkg: error processing kubuntu-desktop (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 acpid
 acpi-support
 powermanagement-interface
 kubuntu-desktop
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

Any help is greatly appreciated because I don't want to reboot between a half finished upgrade.

---

### Post by aurely001 on 2006-11-04
Hello,
I have the same problem ! Did you find some help ?

---

### Post by solidphp on 2006-11-04
I found a solution here:
[https://launchpad.net/distros/ubuntu/+source/acpid/+bug/65635/comments/2](https://launchpad.net/distros/ubuntu/+source/acpid/+bug/65635/comments/2)


> I got the same problem during the upgrade, however it was resolved stopping acpid

sudo /etc/init.d/acpid stop

and then dpgk was able to configure everything

sudo dpkg --configure -a

---

### Post by gmanpsycho on 2006-11-08
Thanks solidphp this helped me out. Muchas Gracias!

---

### Post by toallpointswest on 2006-12-04
Hi all, I'm having the same problem but the above fix didn't work, any other suggestions? 
```
root@######:~# dpkg --configure -a
Setting up acpid (1.0.4-5ubuntu4) ...
 * Loading ACPI modules...                                               [ ok ]
 * Starting ACPI services...                                                    acpid: can't open /proc/acpi/event: Device or resource busy
invoke-rc.d: initscript acpid, action "start" failed.
dpkg: error processing acpid (--configure):
 subprocess post-installation script returned error exit status 1
Setting up gtk-engines-eazel (0.3-5.1) ...
dpkg (subprocess): unable to execute post-installation script: Exec format error
dpkg: error processing gtk-engines-eazel (--configure):
 subprocess post-installation script returned error exit status 2
Errors were encountered while processing:
 acpid
 gtk-engines-eazel


```

---

### Post by toallpointswest on 2006-12-04
Nevermind, turns out hald still had it locked, a "killall hald" and the instructions from this thread fixed it up!

---

