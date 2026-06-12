---
title: "Some dpkg help needed"
date: 2007-10-23
forum: Installation &amp; Upgrades
---

### Post by satbunny on 2007-10-23
I did a standard upgrade from Xubuntu Feisty to Xubuntu Gutsy.
Sadly I left my machine on an the screensaver started, and voila, you can't get in again since the PAM authentication doesn't work. So, one reboot and a corrupt xorg.conf later and I have a system that is working quite well again but is obviously a bit broken.
When I try to fix the 4 packages that seem to be poorly I get a rather nasty error message that frankly I don't know how to fix.. Should I re-install, can I force these packages to configure?
Mucho help requested, I have got away quite lightly so far!

> 
thomas@Vaio:~$ sudo dpkg --configure -a
[sudo] password for thomas:
Setting up acpid (1.0.4-5ubuntu8) ...
 * Loading ACPI modules...                                             [ OK ] 
 * Starting ACPI services...                                                  invoke-rc.d: initscript acpid, action "start" failed.
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
dpkg: dependency problems prevent configuration of xubuntu-desktop:
 xubuntu-desktop depends on acpi-support; however:
  Package acpi-support is not configured yet.
 xubuntu-desktop depends on acpid; however:
  Package acpid is not configured yet.
 xubuntu-desktop depends on powermanagement-interface; however:
  Package powermanagement-interface is not configured yet.
dpkg: error processing xubuntu-desktop (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 acpid
 acpi-support
 powermanagement-interface



---

### Post by stixguy on 2007-10-23
Did you try:

```
sudo apt-get install -f
```

See if that fixes your broken dependencies.

---

### Post by satbunny on 2007-10-24
'Fraid it also falls over: I have tried re-installing using synaptic but that also fails. 

> thomas@Vaio:~$ sudo apt-get install -f
[sudo] password for thomas:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
4 not fully installed or removed.
Need to get 0B of archives.
After unpacking 0B of additional disk space will be used.
Setting up acpid (1.0.4-5ubuntu8) ...
 * Loading ACPI modules...                                                                                                                                     [ OK ] 
 * Starting ACPI services...                                                                                                                                          invoke-rc.d: initscript acpid, action "start" failed.
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
dpkg: dependency problems prevent configuration of xubuntu-desktop:
 xubuntu-desktop depends on acpi-support; however:
  Package acpi-support is not configured yet.
 xubuntu-desktop depends on acpid; however:
  Package acpid is not configured yet.
 xubuntu-desktop depends on powermanagement-interface; however:
  Package powermanagement-interface is not configured yet.
dpkg: error processing xubuntu-desktop (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 acpid
 acpi-support
 powermanagement-interface
 xubuntu-desktop


---

### Post by satbunny on 2007-10-24
When I try and remove acpi using synaptic I get this:

> E: acpid: subprocess post-installation script returned error exit status 1
E: acpi-support: dependency problems - leaving unconfigured
E: powermanagement-interface: dependency problems - leaving unconfigured

---

### Post by satbunny on 2007-10-24
In the end I was able to uninstall each package one by one and then reinstall them one by one. Looks like I am saved. Thanks.

---

