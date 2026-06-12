---
title: "Problem installing package openoffice 2.1.4: openoffice.org-core conflicts with openo"
date: 2008-06-25
forum: Installation &amp; Upgrades
---

### Post by zaputino on 2008-06-25
Hy


I can't install package openoffice.org from Synamptic Package Manager.
After download package on installing software an error occurre 
"openoffice.org-core_1%3a2.4.1-1ubuntu1_amd64.deb: conflicting packages - not installing openoffice.org-core"

This is log:
```
Selecting previously deselected package openoffice.org-base-core.
(Reading database ... 168944 files and directories currently installed.)
Unpacking openoffice.org-base-core (from .../openoffice.org-base-core_1%3a2.4.1-1ubuntu1_amd64.deb) ...
Selecting previously deselected package openoffice.org-style-human.
Unpacking openoffice.org-style-human (from .../openoffice.org-style-human_1%3a2.4.1-1ubuntu1_all.deb) ...
Selecting previously deselected package openoffice.org-common.
Unpacking openoffice.org-common (from .../openoffice.org-common_1%3a2.4.1-1ubuntu1_all.deb) ...
dpkg: regarding .../openoffice.org-core_1%3a2.4.1-1ubuntu1_amd64.deb containing openoffice.org-core:
 openoffice.org-core conflicts with openoffice.org-unbundled
  openoffice.org-kde-integration provides openoffice.org-unbundled and is installed.
  openoffice.org-core05u provides openoffice.org-unbundled and is installed.
  openoffice.org-pyuno provides openoffice.org-unbundled and is installed.
  openoffice.org-javafilter provides openoffice.org-unbundled and is installed.
  openoffice.org-graphicfilter provides openoffice.org-unbundled and is installed.
  openoffice.org-xsltfilter provides openoffice.org-unbundled and is installed.
  openoffice.org-testtool provides openoffice.org-unbundled and is installed.
  openoffice.org-core08 provides openoffice.org-unbundled and is installed.
  openoffice.org-core09 provides openoffice.org-unbundled and is installed.
  openoffice.org-core04 provides openoffice.org-unbundled and is installed.
  openoffice.org-core05 provides openoffice.org-unbundled and is installed.
  openoffice.org-core06 provides openoffice.org-unbundled and is installed.
  openoffice.org-core07 provides openoffice.org-unbundled and is installed.
  openoffice.org-core01 provides openoffice.org-unbundled and is installed.
  openoffice.org-core02 provides openoffice.org-unbundled and is installed.
  openoffice.org-core03 provides openoffice.org-unbundled and is installed.
  openoffice.org-gnome-integration provides openoffice.org-unbundled and is installed.
  openoffice.org-core10 provides openoffice.org-unbundled and is installed.
  openoffice.org-headless provides openoffice.org-unbundled and is installed.
  openoffice.org-core04u provides openoffice.org-unbundled and is installed.
  openoffice.org-emailmerge provides openoffice.org-unbundled and is installed.
  openoffice.org-core03u provides openoffice.org-unbundled and is installed.
dpkg: error processing /var/cache/apt/archives/openoffice.org-core_1%3a2.4.1-1ubuntu1_amd64.deb (--unpack):
 conflicting packages - not installing openoffice.org-core
Selecting previously deselected package openoffice.org-java-common.
Unpacking openoffice.org-java-common (from .../openoffice.org-java-common_1%3a2.4.1-1ubuntu1_all.deb) ...
Selecting previously deselected package openoffice.org-base.
Unpacking openoffice.org-base (from .../openoffice.org-base_1%3a2.4.1-1ubuntu1_amd64.deb) ...
Selecting previously deselected package openoffice.org-calc.
Unpacking openoffice.org-calc (from .../openoffice.org-calc_1%3a2.4.1-1ubuntu1_amd64.deb) ...
Selecting previously deselected package openoffice.org-draw.
Unpacking openoffice.org-draw (from .../openoffice.org-draw_1%3a2.4.1-1ubuntu1_amd64.deb) ...
Selecting previously deselected package openoffice.org-filter-binfilter.
Unpacking openoffice.org-filter-binfilter (from .../openoffice.org-filter-binfilter_1%3a2.4.1-1ubuntu1_amd64.deb) ...
Selecting previously deselected package openoffice.org-filter-mobiledev.
Unpacking openoffice.org-filter-mobiledev (from .../openoffice.org-filter-mobiledev_1%3a2.4.1-1ubuntu1_all.deb) ...
Selecting previously deselected package openoffice.org-impress.
Unpacking openoffice.org-impress (from .../openoffice.org-impress_1%3a2.4.1-1ubuntu1_amd64.deb) ...
Selecting previously deselected package openoffice.org-math.
Unpacking openoffice.org-math (from .../openoffice.org-math_1%3a2.4.1-1ubuntu1_amd64.deb) ...
Selecting previously deselected package openoffice.org-officebean.
Unpacking openoffice.org-officebean (from .../openoffice.org-officebean_1%3a2.4.1-1ubuntu1_amd64.deb) ...
Selecting previously deselected package python-uno.
Unpacking python-uno (from .../python-uno_1%3a2.4.1-1ubuntu1_amd64.deb) ...
Selecting previously deselected package openoffice.org-writer.
Unpacking openoffice.org-writer (from .../openoffice.org-writer_1%3a2.4.1-1ubuntu1_amd64.deb) ...
Selecting previously deselected package openoffice.org-writer2latex.
Unpacking openoffice.org-writer2latex (from .../openoffice.org-writer2latex_0.5-6_all.deb) ...
Selecting previously deselected package openoffice.org.
Unpacking openoffice.org (from .../openoffice.org_1%3a2.4.1-1ubuntu1_amd64.deb) ...
Errors were encountered while processing:
 /var/cache/apt/archives/openoffice.org-core_1%3a2.4.1-1ubuntu1_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
dpkg: dependency problems prevent configuration of openoffice.org:
 openoffice.org depends on openoffice.org-core (= 1:2.4.1-1ubuntu1); however:
  Package openoffice.org-core is not installed.
dpkg: error processing openoffice.org (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org-impress:
 openoffice.org-impress depends on openoffice.org-core (= 1:2.4.1-1ubuntu1); however:
  Package openoffice.org-core is not installed.
dpkg: error processing openoffice.org-impress (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org-officebean:
 openoffice.org-officebean depends on openoffice.org-core (= 1:2.4.1-1ubuntu1); however:
  Package openoffice.org-core is not installed.
dpkg: error processing openoffice.org-officebean (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org-base:
 openoffice.org-base depends on openoffice.org-core (= 1:2.4.1-1ubuntu1); however:
  Package openoffice.org-core is not installed.
dpkg: error processing openoffice.org-base (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org-math:
 openoffice.org-math depends on openoffice.org-core (= 1:2.4.1-1ubuntu1); however:
  Package openoffice.org-core is not installed.
dpkg: error processing openoffice.org-math (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org-draw:
 openoffice.org-draw depends on openoffice.org-core (= 1:2.4.1-1ubuntu1); however:
  Package openoffice.org-core is not installed.
dpkg: error processing openoffice.org-draw (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org-writer2latex:
 openoffice.org-writer2latex depends on openoffice.org-core (>= 1:2.3.0~oog680m1); however:
  Package openoffice.org-core is not installed.
dpkg: error processing openoffice.org-writer2latex (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org-calc:
 openoffice.org-calc depends on openoffice.org-core (= 1:2.4.1-1ubuntu1); however:
  Package openoffice.org-core is not installed.
dpkg: error processing openoffice.org-calc (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org-filter-binfilter:
 openoffice.org-filter-binfilter depends on openoffice.org-core (= 1:2.4.1-1ubuntu1); however:
  Package openoffice.org-core is not installed.
dpkg: error processing openoffice.org-filter-binfilter (--configure):
 dependency problems - leaving unconfigured
Setting up openoffice.org-base-core (1:2.4.1-1ubuntu1) ...
dpkg: dependency problems prevent configuration of openoffice.org-common:
 openoffice.org-common depends on openoffice.org-core (>> 1:2.4.1); however:
  Package openoffice.org-core is not installed.
dpkg: error processing openoffice.org-common (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org-writer:
 openoffice.org-writer depends on openoffice.org-core (= 1:2.4.1-1ubuntu1); however:
  Package openoffice.org-core is not installed.
dpkg: error processing openoffice.org-writer (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python-uno:
 python-uno depends on openoffice.org-core (= 1:2.4.1-1ubuntu1); however:
  Package openoffice.org-core is not installed.
dpkg: error processing python-uno (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org-style-human:
 openoffice.org-style-human depends on openoffice.org-common (= 1:2.4.1-1ubuntu1); however:
  Package openoffice.org-common is not configured yet.
dpkg: error processing openoffice.org-style-human (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org-java-common:
 openoffice.org-java-common depends on openoffice.org-common; however:
  Package openoffice.org-common is not configured yet.
dpkg: error processing openoffice.org-java-common (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org-filter-mobiledev:
 openoffice.org-filter-mobiledev depends on openoffice.org-java-common (>> 2.2.0-4); however:
  Package openoffice.org-java-common is not configured yet.
dpkg: error processing openoffice.org-filter-mobiledev (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 openoffice.org
 openoffice.org-impress
 openoffice.org-officebean
 openoffice.org-base
 openoffice.org-math
 openoffice.org-draw
 openoffice.org-writer2latex
 openoffice.org-calc
 openoffice.org-filter-binfilter
 openoffice.org-common
 openoffice.org-writer
 python-uno
 openoffice.org-style-human
 openoffice.org-java-common
 openoffice.org-filter-mobiledev
```

---

### Post by PmDematagoda on 2008-06-25
Remove openoffice.org-unbundled with:-
```
sudo apt-get remove openoffice.org-unbundled
```
and install openoffice.org-core with:-
```
sudo apt-get install openoffice.org-core
```
see if that fixes it.

---

### Post by zaputino on 2008-06-25
First, thanks for your help.

I try:
```
sudo apt-get remove openoffice.org-unbundled
[sudo] password for davideluppi: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package openoffice.org-unbundled is not installed, so not removed
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
```

---

### Post by zaputino on 2008-06-25
I try also with command
>sudo apt-get install -f 

But anything is changed.

There is anybody to help me??

---

