---
title: "[SOLVED] OpenOffice upgrade problem"
date: 2008-05-31
forum: Installation &amp; Upgrades
---

### Post by PANNY on 2008-05-31
I run Ubuntu Hardy Heron (Gnome) and my current version of OpenOffice is **2.4**.

Today, an upgrade for OpenOffice showed up in the Update Manager, but when I try to install it, I get the following error:

[B]Not all updates can be installed
Run a partial upgrade [...][/B]


When running the partial upgrade I get the following error:

[B]Could not calculate the upgrade
A unresolvable problem occurred while calculating the upgrade.

 This can be caused by:
 * Upgrading to a pre-release version of Ubuntu
 * Running the current pre-release version of Ubuntu
 * Unofficial software packages not provided by Ubuntu

This is most likely a transient problem, please try again later.[/B]


When I try **sudo apt-get upgrade**, I get the following error:
[B]The following packages have been kept back:
  openoffice.org openoffice.org-base
  openoffice.org-base-core openoffice.org-calc
  openoffice.org-common openoffice.org-core
  openoffice.org-draw openoffice.org-filter-binfilter
  openoffice.org-gnome openoffice.org-gtk
  openoffice.org-impress openoffice.org-math
  openoffice.org-officebean openoffice.org-style-human
  openoffice.org-writer python-uno[/B]

So the problem seems to be with OpenOffice only.
I removed all my thrid-party repositories.

What should I do? Just wait as the message suggests: ''This is most likely a transient problem, please try again later.''? :confused:

---

### Post by Seisen on 2008-05-31
Just wait like I am till they fix the problem with the packages.

---

