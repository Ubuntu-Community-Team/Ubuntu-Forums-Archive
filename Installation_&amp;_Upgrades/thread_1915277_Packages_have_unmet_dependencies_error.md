---
title: "Packages have unmet dependencies error"
date: 2012-01-25
forum: Installation &amp; Upgrades
---

### Post by mlpfw on 2012-01-25
I am  new to Ubuntu and I just installed Version 11.10.  After installing many packages, I started getting the erros as show below. I would appreciate any help I could get to resolve it and thanks in advance for your help.

The following packages have unmet dependencies:

e2fsprogs: PreDepends: e2fslibs (= 1.41.14-1ubuntu3) but 1.41.14-1ubuntu3 is installed
           PreDepends: libblkid1 (>= 2.17.2) but 2.19.1-2ubuntu3 is installed
           PreDepends: libc6 (>= 2.12) but 2.13-20ubuntu5 is installed
           PreDepends: libuuid1 (>= 2.16) but 2.19.1-2ubuntu3 is installed
           PreDepends: util-linux (>= 2.15~rc1-1) but 2.19.1-2ubuntu3 is installed
ibus-pinyin: Depends: ibus-pinyin-db-android (= 1.3.99.20110706-1) but 1.3.99.20110706-1 is installed
             Depends: python (>= 2.7.1-0ubuntu2) but 2.7.2-7ubuntu2 is installed
             Depends: libc6 (>= 2.4) but 2.13-20ubuntu5 is installed
             Depends: libgcc1 (>= 1:4.1.1) but 1:4.6.1-9ubuntu3 is installed
             Depends: libglib2.0-0 (>= 2.24.0) but 2.30.0-0ubuntu4 is installed
             Depends: libsqlite3-0 (>= 3.6.11) but 3.7.7-2ubuntu2 is installed
             Depends: libstdc++6 (>= 4.5) but 4.6.1-9ubuntu3 is installed
             Depends: libuuid1 (>= 2.16) but 2.19.1-2ubuntu3 is installed
             Depends: ibus (>= 1.3.99.20110419) but it is not installed
ibus-table: Depends: python (>= 2.7.1-0ubuntu2) but 2.7.2-7ubuntu2 is installed
            Depends: ibus (>= 1.3) but it is not installed
libgssapi-krb5-2: Depends: libc6 (>= 2.7) but 2.13-20ubuntu5 is installed
                  Depends: libcomerr2 (>= 1.34) but 1.3.99.20110419-1ubuntu3 is installed
                  Depends: libkrb5-3 (= 1.9.1+dfsg-1ubuntu2.2) but 1.9.1+dfsg-1ubuntu2.2 is installed
libkrb5-3: Depends: libc6 (>= 2.9) but 2.13-20ubuntu5 is installed
           Depends: libcomerr2 (>= 1.34) but 1.3.99.20110419-1ubuntu3 is installed
           Depends: libkrb5support0 (= 1.9.1+dfsg-1ubuntu2.2) but 1.9.1+dfsg-1ubuntu2.2 is installed

---

### Post by techvish81 on 2012-01-25
Connect to internet , open update manager, click on check button and update.

---

### Post by mlpfw on 2012-01-25
I did. That was when I got the message,

---

### Post by williejones on 2012-01-25
Run synaptics package manager, select edit fix broken packages.

---

### Post by mlpfw on 2012-01-25
Did that too and got the following messages


Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap", at /usr/share/perl5/Debconf/FrontEnd/Gnome.pm line 97, <> line 4.
Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap", at /usr/share/perl5/Debconf/FrontEnd/Gnome.pm line 97, <> line 4.
Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap", at /usr/share/perl5/Debconf/FrontEnd/Gnome.pm line 97, <> line 4.
Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap", at /usr/share/perl5/Debconf/FrontEnd/Gnome.pm line 97, <> line 4.
Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap", at /usr/share/perl5/Debconf/FrontEnd/Gnome.pm line 103, <> line 4.
Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap", at /usr/share/perl5/Debconf/FrontEnd/Gnome.pm line 103, <> line 4.
Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap", at /usr/share/perl5/Debconf/FrontEnd/Gnome.pm line 103, <> line 4.
Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap", at /usr/share/perl5/Debconf/FrontEnd/Gnome.pm line 103, <> line 4.
dpkg: error: parsing file '/var/lib/dpkg/status' near line 18489 package 'radeontool':
 field name `Priorit/defoma/hints/ttf-unfonts-core.hints' must be followed by colon
E: Sub-process /usr/bin/dpkg returned an error code (2)
A package failed to install.  Trying to recover:
dpkg: error: parsing file '/var/lib/dpkg/status' near line 18489 package 'radeontool':
 field name `Priorit/defoma/hints/ttf-unfonts-core.hints' must be followed by colon

---

### Post by williejones on 2012-01-25
> **mlpfw said:**
> Did that too and got the following messages


Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap", at /usr/share/perl5/Debconf/FrontEnd/Gnome.pm line 97, <> line 4.
Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap", at /usr/share/perl5/Debconf/FrontEnd/Gnome.pm line 97, <> line 4.
Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap", at /usr/share/perl5/Debconf/FrontEnd/Gnome.pm line 97, <> line 4.
Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap", at /usr/share/perl5/Debconf/FrontEnd/Gnome.pm line 97, <> line 4.
Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap", at /usr/share/perl5/Debconf/FrontEnd/Gnome.pm line 103, <> line 4.
Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap", at /usr/share/perl5/Debconf/FrontEnd/Gnome.pm line 103, <> line 4.
Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap", at /usr/share/perl5/Debconf/FrontEnd/Gnome.pm line 103, <> line 4.
Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap", at /usr/share/perl5/Debconf/FrontEnd/Gnome.pm line 103, <> line 4.
dpkg: error: parsing file '/var/lib/dpkg/status' near line 18489 package 'radeontool':
 field name `Priorit/defoma/hints/ttf-unfonts-core.hints' must be followed by colon
E: Sub-process /usr/bin/dpkg returned an error code (2)
A package failed to install.  Trying to recover:
dpkg: error: parsing file '/var/lib/dpkg/status' near line 18489 package 'radeontool':
 field name `Priorit/defoma/hints/ttf-unfonts-core.hints' must be followed by colon


You can ignore the GTK-WARNING about theme engine.  I am not familiar with radontool.
Is your graphics card radon? Maybe radontool needs to be uninstalled/reinstalled.

---

### Post by williejones on 2012-01-25
A google search of radeontool shows

**[*Radeontool* - ThinkWiki]("http://www.thinkwiki.org/wiki/Radeontool")**

[www.thinkwiki.org/wiki/]("http://www.thinkwiki.org/wiki/")**Radeontool**
Apr 20, 2009 &#8211; *radeontool*  is a hack to turn on and off the panels background light and external  video. NOTE! **This tool should no longer be used**, please use [B]...


Try to remove radeontool.
[/B]

---

### Post by mlpfw on 2012-01-25
Radeontool is a small utility to control ATI Radeon based laptops' backlight
and external output functions. I selected/marked it for reinstall but got more abends. I might just wipe the whole OS and start from beginning if I can not get this resolved soon,

---

### Post by mlpfw on 2012-01-25
When I mark it for complete removal and apply changes, I get the following:


Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap", at /usr/share/perl5/Debconf/FrontEnd/Gnome.pm line 97, <> line 2.
Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap", at /usr/share/perl5/Debconf/FrontEnd/Gnome.pm line 97, <> line 2.
Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap", at /usr/share/perl5/Debconf/FrontEnd/Gnome.pm line 97, <> line 2.
Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap", at /usr/share/perl5/Debconf/FrontEnd/Gnome.pm line 97, <> line 2.
Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap", at /usr/share/perl5/Debconf/FrontEnd/Gnome.pm line 103, <> line 2.
Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap", at /usr/share/perl5/Debconf/FrontEnd/Gnome.pm line 103, <> line 2.
Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap", at /usr/share/perl5/Debconf/FrontEnd/Gnome.pm line 103, <> line 2.
Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap", at /usr/share/perl5/Debconf/FrontEnd/Gnome.pm line 103, <> line 2.
dpkg: error: parsing file '/var/lib/dpkg/status' near line 18489 package 'radeontool':
 field name `Priorit/defoma/hints/ttf-unfonts-core.hints' must be followed by colon
E: Sub-process /usr/bin/dpkg returned an error code (2)
A package failed to install.  Trying to recover:
dpkg: error: parsing file '/var/lib/dpkg/status' near line 18489 package 'radeontool':
 field name `Priorit/defoma/hints/ttf-unfonts-core.hints' must be followed by colon

---

