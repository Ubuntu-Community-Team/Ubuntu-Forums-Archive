---
title: "could not be find the libxml2"
date: 2008-06-21
forum: Installation &amp; Upgrades
---

### Post by fuatsungur on 2008-06-21
hi, when i configure dictconvert in dictconvert folder with ./configure command, then i get an error, it as follows:

[B]checking for libxml - version >= 2.5.0... no
*** The xml2-config script installed by LIBXML could not be found
*** If libxml was installed in PREFIX, make sure PREFIX/bin is in
*** your path, or set the XML2_CONFIG environment variable to the
*** full path to xml2-config.
configure: error: You must have libxml2 >= 2.5.0 installed
[/B]

would you give any advice to solve this? thanx

---

### Post by moma on 2008-06-21
Hello,

First, update the package index (package list) in your pc.
[COLOR="SeaGreen"]sudo apt-get update [/COLOR]

Then use the **apt-cache** command to search for dependencies (missing packages). In your case:

[COLOR="SeaGreen"]apt-cache search libxml[/COLOR]
[COLOR="SeaGreen"]apt-cache search libxml | grep dev[/COLOR]
libxml2-dev - Development files for the GNOME XML library
...

Install it.
[COLOR="SeaGreen"]sudo apt-get install libxml2-dev[/COLOR]

libxml2 in Ubuntu has version 2.6.31 so that's no problem.
[COLOR="SeaGreen"]apt-cache show libxml2-dev[/COLOR]

Compilation from source needs the header files (*.h), therefore you must install the **xxx-dev** package. That's why I limited the listing with [COLOR="SeaGreen"]| grep dev[/COLOR]. Dev package will in turn pull out all necessary runtime libraries.

---

