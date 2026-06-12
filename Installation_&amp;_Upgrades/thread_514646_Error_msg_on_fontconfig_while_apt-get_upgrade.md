---
title: "Error msg on fontconfig while apt-get upgrade"
date: 2007-08-01
forum: Installation &amp; Upgrades
---

### Post by jutirain on 2007-08-01
Every time when I am doing apt-get upgrade, I got the following error message

It seems there's some thing wrong with fontconfig package

I can always see the fontconfig on the GUI version of upgrading (Synaptic)

However, it showed in grey color and I can't select


Any help?  Thanks a lot!

=======================================

"/usr/share/fonts": error scanning
"/usr/share/X11/fonts": error scanning
"/usr/local/share/fonts": error scanning
"/var/lib/defoma/fontconfig.d": error scanning
dpkg: error processing ttf-opensymbol (--configure):
 subprocess post-installation script returned error exit status 4
dpkg: dependency problems prevent configuration of openoffice.org-core:
 openoffice.org-core depends on ttf-opensymbol; however:
  Package ttf-opensymbol is not configured yet.
dpkg: error processing openoffice.org-core (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python-uno:
 python-uno depends on openoffice.org-core (= 2.2.0-1ubuntu4); however:
  Package openoffice.org-core is not configured yet.
dpkg: error processing python-uno (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org-writer:
 openoffice.org-writer depends on openoffice.org-core (= 2.2.0-1ubuntu4); however:
  Package openoffice.org-core is not configured yet.
 openoffice.org-writer depends on python-uno (>= 2.2.0); however:
  Package python-uno is not configured yet.
dpkg: error processing openoffice.org-writer (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org-calc:
 openoffice.org-calc depends on openoffice.org-core (= 2.2.0-1ubuntu4); however:
  Package openoffice.org-core is not configured yet.
dpkg: error processing openoffice.org-calc (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org-draw:
 openoffice.org-draw depends on openoffice.org-core (= 2.2.0-1ubuntu4); however:
  Package openoffice.org-core is not configured yet.
dpkg: error processing openoffice.org-draw (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org-impress:
 openoffice.org-impress depends on openoffice.org-core (= 2.2.0-1ubuntu4); however:
  Package openoffice.org-core is not configured yet.
 openoffice.org-impress depends on openoffice.org-draw (= 2.2.0-1ubuntu4); however:
  Package openoffice.org-draw is not configured yet.
dpkg: error processing openoffice.org-impress (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org-math:
 openoffice.org-math depends on openoffice.org-core (= 2.2.0-1ubuntu4); however:
  Package openoffice.org-core is not configured yet.
dpkg: error processing openoffice.org-math (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org-base:
 openoffice.org-base depends on openoffice.org-core (= 2.2.0-1ubuntu4); however:
  Package openoffice.org-core is not configured yet.
dpkg: error processing openoffice.org-base (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org:
 openoffice.org depends on openoffice.org-core (= 2.2.0-1ubuntu4); however:
  Package openoffice.org-core is not configured yet.
 openoffice.org depends on openoffice.org-writer; however:
  Package openoffice.org-writer is not configured yet.
 openoffice.org depends on openoffice.org-calc; however:
  Package openoffice.org-calc is not configured yet.
 openoffice.org depends on openoffice.org-impress; however:
  Package openoffice.org-impress is not configured yet.
 openoffice.org depends on openoffice.org-draw; however:
  Package openoffice.org-draw is not configured yet.
 openoffice.org depends on openoffice.org-math; however:
  Package openoffice.org-math is not configured yet.
 openoffice.org depends on openoffice.org-base; however:
  Package openoffice.org-base is not configured yet.
dpkg: error processing openoffice.org (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org-evolution:
 openoffice.org-evolution depends on openoffice.org-core (= 2.2.0-1ubuntu4); however:
  Package openoffice.org-core is not configured yet.
 openoffice.org-evolution depends on openoffice.org-base; however:
  Package openoffice.org-base is not configured yet.
dpkg: error processing openoffice.org-evolution (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org-gtk:
 openoffice.org-gtk depends on openoffice.org-core (= 2.2.0-1ubuntu4); however:
  Package openoffice.org-core is not configured yet.
dpkg: error processing openoffice.org-gtk (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org-gnome:
 openoffice.org-gnome depends on openoffice.org-core (= 2.2.0-1ubuntu4); however:
  Package openoffice.org-core is not configured yet.
 openoffice.org-gnome depends on openoffice.org-gtk; however:
  Package openoffice.org-gtk is not configured yet.
dpkg: error processing openoffice.org-gnome (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org-common:
 openoffice.org-common depends on openoffice.org-core (>> 2.2.0) | openoffice.org-core-experimental (>> 2.2.0); however:
  Package openoffice.org-core is not configured yet.
  Package openoffice.org-core-experimental is not installed.
dpkg: error processing openoffice.org-common (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org-java-common:
 openoffice.org-java-common depends on openoffice.org-common; however:
  Package openoffice.org-common is not configured yet.
dpkg: error processing openoffice.org-java-common (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org-filter-mobiledev:
 openoffice.org-filter-mobiledev depends on openoffice.org-java-common (= 2.2.0-1ubuntu4); however:
  Package openoffice.org-java-common is not configured yet.
dpkg: error processing openoffice.org-filter-mobiledev (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org-l10n-en-us:
 openoffice.org-l10n-en-us depends on openoffice.org-common (= 2.2.0-1ubuntu4) | language-support-en; however:
  Package openoffice.org-common is not configured yet.
  Package language-support-en is not installed.
dpkg: error processing openoffice.org-l10n-en-us (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org-style-industrial:
 openoffice.org-style-industrial depends on openoffice.org-common (= 2.2.0-1ubuntu4); however:
  Package openoffice.org-common is not configured yet.
dpkg: error processing openoffice.org-style-industrial (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org-style-human:
 openoffice.org-style-human depends on openoffice.org-common (= 2.2.0-1ubuntu4); however:
  Package openoffice.org-common is not configured yet.
dpkg: error processing openoffice.org-style-human (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org-style-andromeda:
 openoffice.org-style-andromeda depends on openoffice.org-common (= 2.2.0-1ubuntu4); however:
  Package openoffice.org-common is not configured yet.
dpkg: error processing openoffice.org-style-andromeda (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org-style-default:
 openoffice.org-style-default depends on openoffice.org-style-andromeda (= 2.2.0-1ubuntu4); however:
  Package openoffice.org-style-andromeda is not configured yet.
dpkg: error processing openoffice.org-style-default (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 ttf-opensymbol
 openoffice.org-core
 python-uno
 openoffice.org-writer
 openoffice.org-calc
 openoffice.org-draw
 openoffice.org-impress
 openoffice.org-math
 openoffice.org-base
 openoffice.org
 openoffice.org-evolution
 openoffice.org-gtk
 openoffice.org-gnome
 openoffice.org-common
 openoffice.org-java-common
 openoffice.org-filter-mobiledev
 openoffice.org-l10n-en-us
 openoffice.org-style-industrial
 openoffice.org-style-human
 openoffice.org-style-andromeda
 openoffice.org-style-default
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by asus1 on 2007-08-01
I also have this issue - just tried a fresh install of U studio and everything was fine until I ran teh first upgrade and now have font errors!!!  I am now in a fresh install on Feisty amd64 and again everything was fine until I upgraded

Developers please note - this is a vanilla install - I have not touched anything!!!!

Have tried to fix using some suggestions on this forum but no fix yet has worked.

pleaseeeee help

---

### Post by asus1 on 2007-08-01
fixed it!!

Try touching all the offending font files and issue an apt-get -f install at the end.

sudo touch /usr/share/fonts

do the above for all (yes ALL) the other font locations (eg) /usr/share/X11/fonts

THEN

sudo apt-get -f install

NOW ALL FIXED BUT WHAT A PAINFULL SOLUTION!!!!!

---

