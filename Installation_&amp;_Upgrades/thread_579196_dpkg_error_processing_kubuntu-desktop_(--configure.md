---
title: "dpkg: error processing kubuntu-desktop (--configure)"
date: 2007-10-18
forum: Installation &amp; Upgrades
---

### Post by SourceV on 2007-10-18
When Running aptitude dist-upgrade I am getting this error.

Any suggestions?

```

 $ sudo aptitude dist-upgrade
Reading package lists... Done
Building dependency tree
Reading state information... Done
Reading extended state information
Initializing package states... Done
Building tag database... Done
The following partially installed packages will be configured:
  acpi-support acpid doc-base docbook-xml kubuntu-desktop powermanagement-interface scrollkeeper
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Setting up acpid (1.0.4-5ubuntu8) ...
 * Loading ACPI modules...                                                                                                                                                  [ OK ]
 * Starting ACPI services...                                                                                                                                                       invoke-rc.d: initscript acpid, action "start" failed.
dpkg: error processing acpid (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of acpi-support:
 acpi-support depends on acpid (>= 1.0.4-1ubuntu4); however:
  Package acpid is not configured yet.
dpkg: error processing acpi-support (--configure):
 dependency problems - leaving unconfigured
Setting up docbook-xml (4.5-4) ...
update-xmlcatalog: error: entity already registered
dpkg: error processing docbook-xml (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of scrollkeeper:
 scrollkeeper depends on docbook-xml (>= 4.2-11); however:
  Package docbook-xml is not configured yet.
dpkg: error processing scrollkeeper (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of doc-base:
 doc-base depends on scrollkeeper; however:
  Package scrollkeeper is not configured yet.
dpkg: error processing doc-base (--configure):
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
 docbook-xml
 scrollkeeper
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
Setting up acpid (1.0.4-5ubuntu8) ...
 * Loading ACPI modules...                                                                                                                                                  [ OK ]
 * Starting ACPI services...                                                                                                                                                       invoke-rc.d: initscript acpid, action "start" failed.
dpkg: error processing acpid (--configure):
 subprocess post-installation script returned error exit status 1
Setting up docbook-xml (4.5-4) ...
update-xmlcatalog: error: entity already registered
dpkg: error processing docbook-xml (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of acpi-support:
 acpi-support depends on acpid (>= 1.0.4-1ubuntu4); however:
  Package acpid is not configured yet.
dpkg: error processing acpi-support (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of scrollkeeper:
 scrollkeeper depends on docbook-xml (>= 4.2-11); however:
  Package docbook-xml is not configured yet.
dpkg: error processing scrollkeeper (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of powermanagement-interface:
 powermanagement-interface depends on acpi-support (>= 0.17); however:
  Package acpi-support is not configured yet.
dpkg: error processing powermanagement-interface (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of doc-base:
 doc-base depends on scrollkeeper; however:
  Package scrollkeeper is not configured yet.
dpkg: error processing doc-base (--configure):
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
 docbook-xml
 acpi-support
 scrollkeeper
 powermanagement-interface
 doc-base
 kubuntu-desktop
Reading package lists... Done
Building dependency tree
Reading state information... Done
Reading extended state information
Initializing package states... Done
Building tag database... Done

```

---

### Post by Anicka on 2007-10-18
Can you run aptitude or is it crippled? If you can, try to cycle the commands "sudo aptiude update" and "sudo aptitude upgrade (or dist-upgrade)" and maybe "sudo aptitude -f install". (Simulate first "aptitude -s -f install" and if aptitude says that it wants to remove all of your installed packages, run "sudo aptitude keep-all".)

If you cannot run aptitude (gives errors or something) try the old "sudo dpkg --configure -a".

Good luck!

---

### Post by SourceV on 2007-10-19
> **Anicka said:**
> Can you run aptitude or is it crippled? If you can, try to cycle the commands "sudo aptiude update" and "sudo aptitude upgrade (or dist-upgrade)" and maybe "sudo aptitude -f install". (Simulate first "aptitude -s -f install" and if aptitude says that it wants to remove all of your installed packages, run "sudo aptitude keep-all".)

If you cannot run aptitude (gives errors or something) try the old "sudo dpkg --configure -a".

Good luck!

Thank you for your suggestions, however I am still getting the same error:
```

$ sudo aptitude -f install
Reading package lists... Done
Building dependency tree
Reading state information... Done
Reading extended state information
Initializing package states... Done
Building tag database... Done
The following partially installed packages will be configured:
  acpi-support acpid doc-base docbook-xml kubuntu-desktop
  powermanagement-interface scrollkeeper
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Setting up acpid (1.0.4-5ubuntu8) ...
 * Loading ACPI modules...                                               [ OK ]
 * Starting ACPI services...                                                    invoke-rc.d: initscript acpid, action "start" failed.
dpkg: error processing acpid (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of acpi-support:
 acpi-support depends on acpid (>= 1.0.4-1ubuntu4); however:
  Package acpid is not configured yet.
dpkg: error processing acpi-support (--configure):
 dependency problems - leaving unconfigured
Setting up docbook-xml (4.5-4) ...
update-xmlcatalog: error: entity already registered
dpkg: error processing docbook-xml (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of scrollkeeper:
 scrollkeeper depends on docbook-xml (>= 4.2-11); however:
  Package docbook-xml is not configured yet.
dpkg: error processing scrollkeeper (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of doc-base:
 doc-base depends on scrollkeeper; however:
  Package scrollkeeper is not configured yet.
dpkg: error processing doc-base (--configure):
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
 docbook-xml
 scrollkeeper
 doc-base
 powermanagement-interface
 kubuntu-desktop
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
Setting up acpid (1.0.4-5ubuntu8) ...
 * Loading ACPI modules...                                               [ OK ]
 * Starting ACPI services...                                                    invoke-rc.d: initscript acpid, action "start" failed.
dpkg: error processing acpid (--configure):
 subprocess post-installation script returned error exit status 1
Setting up docbook-xml (4.5-4) ...
update-xmlcatalog: error: entity already registered
dpkg: error processing docbook-xml (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of acpi-support:
 acpi-support depends on acpid (>= 1.0.4-1ubuntu4); however:
  Package acpid is not configured yet.
dpkg: error processing acpi-support (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of scrollkeeper:
 scrollkeeper depends on docbook-xml (>= 4.2-11); however:
  Package docbook-xml is not configured yet.
dpkg: error processing scrollkeeper (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of powermanagement-interface:
 powermanagement-interface depends on acpi-support (>= 0.17); however:
  Package acpi-support is not configured yet.
dpkg: error processing powermanagement-interface (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of doc-base:
 doc-base depends on scrollkeeper; however:
  Package scrollkeeper is not configured yet.
dpkg: error processing doc-base (--configure):
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
 docbook-xml
 acpi-support
 scrollkeeper
 powermanagement-interface
 doc-base
 kubuntu-desktop
Reading package lists... Done
Building dependency tree
Reading state information... Done
Reading extended state information
Initializing package states... Done
Building tag database... Done

```

---

### Post by BoneSaw on 2007-10-19
i had this sort of trouble earlier with a different package. try finding a different version of acpid or compiling it from source. then run dpkg --configure -a again.

---

### Post by Anicka on 2007-10-19
The problem seems to originate from this acpid-package not being configured properly. Did you try the dpkg-command? You can also try with exchanging the "-a"-flag with the actual name of the package.

---

### Post by stereodee on 2007-10-19
I had a similar problem solved by:

```
sudo /etc/init.d/acpid stop
sudo dpkg --configure acpid
```

---

### Post by Dritz on 2007-10-19
Hope the original poster caught that solution cause it worked for me and I get pretty much the same errors. To bad I missed this topic before creating my own. Heh I've become one of the people who annoy me on other forums I frequent. I did honestly look around here though.

---

### Post by SourceV on 2007-10-21
> **stereodee said:**
> I had a similar problem solved by:

```
sudo /etc/init.d/acpid stop
sudo dpkg --configure acpid
```

That worked for me too. Thank you guys.

---

### Post by bie on 2007-10-22
Had exactly the same problem after upgrading from Kubuntu 7.04 to 7.10. The trick above worked for me also.
Thanks a lot!

---

### Post by alanhaggai on 2008-07-21
I had the same problem while doing a dist-upgrade in my Debian Etch system. The upgrade was to Lenny / Sid. The errors were:

```

Setting up docbook-xml (4.5-5) ...
update-xmlcatalog: error: entity already registered
dpkg: error processing docbook-xml (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of scrollkeeper:
 scrollkeeper depends on docbook-xml (>= 4.2-11); however:
  Package docbook-xml is not configured yet.
dpkg: error processing scrollkeeper (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of bug-buddy:
 bug-buddy depends on scrollkeeper; however:
  Package scrollkeeper is not configured yet.
dpkg: error processing bug-buddy (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of capplets-data:
 capplets-data depends on scrollkeeper; however:
  Package scrollkeeper is not configured yet.
dpkg: error processing capplets-data (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gnome-panel-data:
 gnome-panel-data depends on scrollkeeper; however:
  Package scrollkeeper is not configured yet.
dpkg: error processing gnome-panel-data (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gnome-control-center:
 gnome-control-center depends on capplets-data (>= 1:2.22); however:
  Package capplets-data is not configured yet.
 gnome-control-center depends on capplets-data (<< 1:2.23); however:
  Package capplets-data is not configured yet.
dpkg: error processing gnome-control-center (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gnome-panel:
 gnome-panel depends on gnome-panel-data (>= 2.20); however:
  Package gnome-panel-data is not configured yet.
 gnome-panel depends on gnome-panel-data (<< 2.21); however:
  Package gnome-panel-data is not configured yet.
 gnome-panel depends on gnome-control-center (>= 1:2.8.2-3); however:
  Package gnome-control-center is not configured yet.
dpkg: error processing gnome-panel (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of fast-user-switch-applet:
 fast-user-switch-applet depends on gnome-panel; however:
  Package gnome-panel is not configured yet.
dpkg: error processing fast-user-switch-applet (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gedit:
 gedit depends on scrollkeeper; however:
  Package scrollkeeper is not configured yet.
dpkg: error processing gedit (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gnome-applets-data:
 gnome-applets-data depends on scrollkeeper; however:
  Package scrollkeeper is not configured yet.
dpkg: error processing gnome-applets-data (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gnome-applets:
 gnome-applets depends on gnome-applets-data (>= 2.22); however:
  Package gnome-applets-data is not configured yet.
 gnome-applets depends on gnome-applets-data (<< 2.23); however:
  Package gnome-applets-data is not configured yet.
 gnome-applets depends on gnome-panel (>= 2.13.4); however:
  Package gnome-panel is not configured yet.
dpkg: error processing gnome-applets (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gnome-session:
 gnome-session depends on gnome-control-center (>= 1:2.22); however:
  Package gnome-control-center is not configured yet.
dpkg: error processing gnome-session (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gnome-terminal:
 gnome-terminal depends on scrollkeeper; however:
  Package scrollkeeper is not configured yet.
dpkg: error processing gnome-terminal (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of nautilus-data:
 nautilus-data depends on scrollkeeper; however:
  Package scrollkeeper is not configured yet.
dpkg: error processing nautilus-data (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of nautilus:
 nautilus depends on nautilus-data (>= 2.20); however:
  Package nautilus-data is not configured yet.
 nautilus depends on nautilus-data (<< 2.21); however:
  Package nautilus-data is not configured yet.
 nautilus depends on gnome-control-center (>= 2.6); however:
  Package gnome-control-center is not configured yet.
dpkg: error processing nautilus (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of yelp:
 yelp depends on docbook-xml (>= 4.1.2); however:
  Package docbook-xml is not configured yet.
dpkg: error processing yelp (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gnome-core:
 gnome-core depends on gnome-control-center (>= 1:2.22.2.1); however:
  Package gnome-control-center is not configured yet.
 gnome-core depends on gedit (>= 2.22.3); however:
  Package gedit is not configured yet.
 gnome-core depends on gnome-applets (>= 2.22.2); however:
  Package gnome-applets is not configured yet.
 gnome-core depends on gnome-panel (>= 2.20.3); however:
  Package gnome-panel is not configured yet.
 gnome-core depends on gnome-session (>= 2.22.2); however:
  Package gnome-session is not configured yet.
 gnome-core depends on gnome-terminal (>= 2.22.2); however:
  Package gnome-terminal is not configured yet.
 gnome-core depends on nautilus (>= 2.20.0); however:
  Package nautilus is not configured yet.
 gnome-core depends on rarian-compat | scrollkeeper; however:
  Package rarian-compat is not installed.
  Package scrollkeeper is not configured yet.
 gnome-core depends on yelp (>= 2.22.1); however:
  Package yelp is not configured yet.
dpkg: error processing gnome-core (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gnome-accessibility:
 gnome-accessibility depends on gnome-core (= 1:2.22.2~3); however:
  Package gnome-core is not configured yet.
dpkg: error processing gnome-accessibility (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of synaptic:
 synaptic depends on scrollkeeper; however:
  Package scrollkeeper is not configured yet.
dpkg: error processing synaptic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gnome-app-install:
 gnome-app-install depends on synaptic (>= 0.57.8); however:
  Package synaptic is not configured yet.
dpkg: error processing gnome-app-install (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gnome-system-monitor:
 gnome-system-monitor depends on scrollkeeper; however:
  Package scrollkeeper is not configured yet.
dpkg: error processing gnome-system-monitor (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gnome-user-guide:
 gnome-user-guide depends on scrollkeeper; however:
  Package scrollkeeper is not configured yet.
 gnome-user-guide depends on yelp; however:
  Package yelp is not configured yet.
dpkg: error processing gnome-user-guide (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gnome-utils:
 gnome-utils depends on scrollkeeper; however:
  Package scrollkeeper is not configured yet.
dpkg: error processing gnome-utils (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gucharmap:
 gucharmap depends on scrollkeeper; however:
  Package scrollkeeper is not configured yet.
dpkg: error processing gucharmap (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of nautilus-cd-burner:
 nautilus-cd-burner depends on nautilus; however:
  Package nautilus is not configured yet.
dpkg: error processing nautilus-cd-burner (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of zenity:
 zenity depends on scrollkeeper; however:
  Package scrollkeeper is not configured yet.
dpkg: error processing zenity (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gnome-desktop-environment:
 gnome-desktop-environment depends on gnome-core (= 1:2.22.2~3); however:
  Package gnome-core is not configured yet.
 gnome-desktop-environment depends on bug-buddy (>= 2.22.0); however:
  Package bug-buddy is not configured yet.
 gnome-desktop-environment depends on fast-user-switch-applet (>= 2.22.0); however:
  Package fast-user-switch-applet is not configured yet.
 gnome-desktop-environment depends on gnome-system-monitor (>= 2.22.2); however:
  Package gnome-system-monitor is not configured yet.
 gnome-desktop-environment depends on gnome-user-guide (>= 2.22.1); however:
  Package gnome-user-guide is not configured yet.
 gnome-desktop-environment depends on gnome-utils (>= 2.20.0.1); however:
  Package gnome-utils is not configured yet.
 gnome-desktop-environment depends on gucharmap (>= 1:2.22.1); however:
  Package gucharmap is not configured yet.
 gnome-desktop-environment depends on nautilus-cd-burner (>= 2.20.0); however:
  Package nautilus-cd-burner is not configured yet.
 gnome-desktop-environment depends on zenity (>= 2.22.1); however:
  Package zenity is not configured yet.
dpkg: error processing gnome-desktop-environment (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of software-properties-gtk:
 software-properties-gtk depends on synaptic (>= 0.57.8); however:
  Package synaptic is not configured yet.
dpkg: error processing software-properties-gtk (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of update-manager:
 update-manager depends on synaptic; however:
  Package synaptic is not configured yet.
 update-manager depends on software-properties-gtk; however:
  Package software-properties-gtk is not configured yet.
dpkg: error processing update-manager (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of update-notifier:
 update-notifier depends on update-manager; however:
  Package update-manager is not configured yet.
dpkg: error processing update-notifier (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 docbook-xml
 scrollkeeper
 bug-buddy
 capplets-data
 gnome-panel-data
 gnome-control-center
 gnome-panel
 fast-user-switch-applet
 gedit
 gnome-applets-data
 gnome-applets
 gnome-session
 gnome-terminal
 nautilus-data
 nautilus
 yelp
 gnome-core
 gnome-accessibility
 synaptic
 gnome-app-install
 gnome-system-monitor
 gnome-user-guide
 gnome-utils
 gucharmap
 nautilus-cd-burner
 zenity
 gnome-desktop-environment
 software-properties-gtk
 update-manager
 update-notifier
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

I removed docbook-xml:
```

sudo apt-get remove docbook-xml

```

Then the dist-upgrade went fine. All of the above errors were caused by docbook-xml not being configured properly. Hope this helps.

---

