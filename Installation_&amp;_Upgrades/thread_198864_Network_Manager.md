---
title: "Network Manager"
date: 2006-06-17
forum: Installation &amp; Upgrades
---

### Post by cac007 on 2006-06-17
checking for perl... /usr/bin/perl
checking for XML::Parser... configure: error: XML::Parser perl module is required for intltool

this is what i get when i try to install Network Manager

how do i configure xml parser

---

### Post by kewldude606 on 2006-06-17
You have to install it.  Open System-->Administration-->Synaptic and do a search for perl and XML parser.

It says configure because that is the script that is calling it.  (You just did ./configure, right).

Also, before installing from source, check the Applications-->Add/Remove and see if it is there.  Then check the program's website for a .deb file.

---

