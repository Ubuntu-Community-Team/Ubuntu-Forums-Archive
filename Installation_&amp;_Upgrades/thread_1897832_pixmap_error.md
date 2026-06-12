---
title: "pixmap error"
date: 2011-12-20
forum: Installation &amp; Upgrades
---

### Post by bigtel on 2011-12-20
Hi there

I am once again encountering errors while trying to install various programs. In this instance, like many others, I get the error message within the installation code - **Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap", at /usr/share/perl5/Debconf/FrontEnd/Gnome.pm line 103.** - any idea what this refers to and how I can fix it..?

Thanks.

Here is the full 'OPERA' installation code, but I get the same error for many installations.


```
rl5/Debconf/FrontEnd/Gnome.pm line 103.
Processing triggers for software-center ...
Updating software catalog...this may take a moment.
^CTraceback (most recent call last):
  File "/usr/sbin/update-software-center", line 169, in <module>
    result = rebuild_database(pathname)
  File "/usr/share/software-center/softwarecenter/db/update.py", line 832, in rebuild_database
    update(db, cache)
  File "/usr/share/software-center/softwarecenter/db/update.py", line 383, in update
    update_from_app_install_data(db, cache, datadir)
  File "/usr/share/software-center/softwarecenter/db/update.py", line 450, in update_from_app_install_data
    index_app_info_from_parser(parser, db, cache)
  File "/usr/share/software-center/softwarecenter/db/update.py", line 648, in index_app_info_from_parser
    if pkgname in cache and cache[pkgname].candidate:
  File "/usr/share/software-center/softwarecenter/db/pkginfo.py", line 59, in candidate
    return self.pkginfo.get_candidate(self.name)
  File "/usr/share/software-center/softwarecenter/db/pkginfo_impl/aptcache.py", line 147, in get_candidate
    not self._cache[pkgname].candidate):
  File "/usr/lib/python2.7/dist-packages/apt/cache.py", line 174, in __getitem__
    pkg = self._weakref[key] = Package(self, self._cache[key])
KeyboardInterrupt
dpkg: error processing software-center (--install):
 subprocess installed post-installation script was interrupted
Errors were encountered while processing:
 software-center
(Reading database ... 210119 files and directories currently installed.)
Preparing to replace opera 11.60.1185 (using .../opera_11.60.1185_i386.deb) ...
Unpacking replacement opera ...
Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap", at /usr/share/perl5/Debconf/FrontEnd/Gnome.pm line 97.
Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap", at /usr/share/perl5/Debconf/FrontEnd/Gnome.pm line 97.
Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap", at /usr/share/perl5/Debconf/FrontEnd/Gnome.pm line 97.
Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap", at /usr/share/perl5/Debconf/FrontEnd/Gnome.pm line 97.
Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap", at /usr/share/perl5/Debconf/FrontEnd/Gnome.pm line 103.
Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap", at /usr/share/perl5/Debconf/FrontEnd/Gnome.pm line 103.
Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap", at /usr/share/perl5/Debconf/FrontEnd/Gnome.pm line 103.
Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap", at /usr/share/perl5/Debconf/FrontEnd/Gnome.pm line 103.
Setting up opera (11.60.1185) ...
Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap", at /usr/share/perl5/Debconf/FrontEnd/Gnome.pm line 97.
Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap", at /usr/share/perl5/Debconf/FrontEnd/Gnome.pm line 97.
Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap", at /usr/share/perl5/Debconf/FrontEnd/Gnome.pm line 97.
Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap", at /usr/share/perl5/Debconf/FrontEnd/Gnome.pm line 97.
Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap", at /usr/share/perl5/Debconf/FrontEnd/Gnome.pm line 103.
Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap", at /usr/share/perl5/Debconf/FrontEnd/Gnome.pm line 103.
Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap", at /usr/share/perl5/Debconf/FrontEnd/Gnome.pm line 103.
Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap", at /usr/share/perl5/Debconf/FrontEnd/Gnome.pm line 103.
Updating software catalog...this may take a moment.
Software catalog update was successful.
Processing triggers for shared-mime-info ...
Unknown media type in type 'all/all'
Unknown media type in type 'all/allfiles'
Unknown media type in type 'uri/mms'
Unknown media type in type 'uri/mmst'
Unknown media type in type 'uri/mmsu'
Unknown media type in type 'uri/pnm'
Unknown media type in type 'uri/rtspt'
Unknown media type in type 'uri/rtspu'
Unknown media type in type 'interface/x-winamp-skin'
Processing triggers for desktop-file-utils ...
Processing triggers for gnome-menus ...
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Processing triggers for hicolor-icon-theme ...
Processing triggers for man-db ...
Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap", at /usr/share/perl5/Debconf/FrontEnd/Gnome.pm line 97.
Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap", at /usr/share/perl5/Debconf/FrontEnd/Gnome.pm line 97.
Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap", at /usr/share/perl5/Debconf/FrontEnd/Gnome.pm line 97.
Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap", at /usr/share/perl5/Debconf/FrontEnd/Gnome.pm line 97.
Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap", at /usr/share/perl5/Debconf/FrontEnd/Gnome.pm line 103.
Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap", at /usr/share/perl5/Debconf/FrontEnd/Gnome.pm line 103.
Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap", at /usr/share/perl5/Debconf/FrontEnd/Gnome.pm line 103.
Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap", at /usr/share/perl5/Debconf/FrontEnd/Gnome.pm line 103.
```

---

