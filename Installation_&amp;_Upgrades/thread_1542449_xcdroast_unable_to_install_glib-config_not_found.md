---
title: "xcdroast unable to install glib-config not found"
date: 2010-07-30
forum: Installation &amp; Upgrades
---

### Post by rjakes on 2010-07-30
I installed cdroast that came with ubuntu and received the following:

[[img]http://a.imagehost.org/0750/Screenshot-X-CD-Roast_0_98alpha16.png[/img]](http://a.imagehost.org/view/0750/Screenshot-X-CD-Roast_0_98alpha16)

I searched and found that the root configuration was turned off in some versions and uninstalled, then found a good version at [http://www.xcdroast.org/](http://www.xcdroast.org/) but when I tried to install from a *.tar.gz and after I ran a ./config I got:

 checking for GLIB - version >= 1.2.3... no
*** The glib-config script installed by GLIB could not be found
*** If GLIB was installed in PREFIX, make sure PREFIX/bin is in
*** your path, or set the GLIB_CONFIG environment variable to the
*** full path to glib-config.
configure: error: Test for GLIB failed. See the file 'INSTALL' for help.

I downloaded glib-2.24.0.tar.gz and got a successful install, and I still receive the GLIB error. If the problem is GLIB_CONFIG environment variable, I do not know how to change that. I cannot locate glib-config either.

rjakes

---

