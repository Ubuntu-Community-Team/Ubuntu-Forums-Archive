---
title: "how do i edit the ./configure options in the beryl sourse package."
date: 2007-06-30
forum: Installation &amp; Upgrades
---

### Post by kakashi on 2007-06-30
i want to biuld the beryl package with the option --enable-xgl but i can't find where to edit it. usually to do this sort of thinf its the debian/rules file but this time the debian/ruiles file only has 

```
  GNU nano 2.0.2                               File: debian/rules                                                                    

#!/usr/bin/make -f


include /usr/share/cdbs/1/class/autotools.mk
include /usr/share/cdbs/1/rules/debhelper.mk


export CFLAGS += -fPIC

DEB_DH_INSTALL_ARGS = --sourcedir=debian/tmp
DEB_INSTALL_DOCS_ALL := README NEWS

DEB_INSTALL_MANPAGES_beryl-core := doc/beryl.1
DEB_INSTALL_MANPAGES_beryl-dev :=  doc/beryl-settings-dump.1
DEB_INSTALL_MANPAGES_libberylsettings-dev := doc/beryl_settings_context_new.3 doc/beryl_settings_context_destroy.3




```

any help is appreciated.

---

