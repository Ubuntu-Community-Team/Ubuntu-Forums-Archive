---
title: "Inkscape installation - dependencies issue"
date: 2010-01-25
forum: Installation &amp; Upgrades
---

### Post by petenz on 2010-01-25
Hi all

I've been trying to install Inkscape from the ubuntu repositories, but have been getting the following message:

inkscape:
  Depends: libglibmm-2.4-1c2a (>=2.22.0) but 2.20.0-0ubuntu2 is to be installed
  Depends: libgtkmm-2.4-1c2a (>=1:2.18.0) but 1:2.16.0-1 is to be installed
 Depends: libmagick++2  but it is not installable
 Depends: libmagickcore2  but it is not installable
 Depends: libpoppler5  but it is not installable
  Depends: libstdc++6 (>=4.4.0) but 4.3.3-5ubuntu4 is to be installed
  Depends: libxml2 (>=2.7.4) but 2.6.32.dfsg-5ubuntu4.2 is to be installed

So obviously I need to upgrade some libraries to enable Inkscape to run. Should I go ahead and install these libraries manually then try to install Inkscape again? My hesitation comes from the fact that synaptic isn't automatically installing them - what gives? Software sources?

---

### Post by petenz on 2010-01-25
Resolved - I had some extra repositories installed which were trying to install a new version (.47), but the libs provided by the repositories I had configured only had the libraries for the current Ubuntu supported version of Inkscape, version .46. All good.

---

