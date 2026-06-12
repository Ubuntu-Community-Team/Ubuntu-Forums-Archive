---
title: "Cannot launch Ubuntu Software Center after installing 20.04"
date: 2020-04-23
forum: Installation &amp; Upgrades
---

### Post by Deleted20200712 on 2020-04-23
I just installed 20.04.  Every time I click on the Ubuntu Software Center icon in the left-hand dock, the tab shows up in the top tray with the waiting animation, then disappears.

I finally figured out that the command is snap-store (not software-center), and in a terminal I get this:

01:41:16:0845 Gtk Failed to load module "canberra-gtk-module"
01:41:16:0848 Gtk Failed to load module "canberra-gtk-module"
01:41:16:0922 Gs  enabled plugins: desktop-categories, fwupd, os-release, packagekit, packagekit-local, packagekit-offline, packagekit-proxy, packagekit-refine-repos, packagekit-refresh, packagekit-upgrade, packagekit-url-to-app, appstream, desktop-menu-path, hardcoded-blacklist, hardcoded-popular, modalias, odrs, packagekit-refine, rewrite-resource, packagekit-history, provenance, snap, systemd-updates, generic-updates, provenance-license, icons, key-colors, key-colors-metadata
01:41:16:0922 Gs  disabled plugins: dpkg, dummy, fedora-langpacks, fedora-pkgdb-collections, repos
01:41:17:0090 Gs  /etc/PackageKit/Vendor.conf file not found
01:41:17:0618 Gtk Could not load a pixbuf from icon theme.
This may indicate that pixbuf loaders or the mime database could not be found.
**
Gtk:ERROR:../gtk/gtkiconhelper.c:494:ensure_surface_for_gicon: assertion failed (error == NULL): Failed to load /snap/snap-store/433/data-dir/icons/Yaru/16x16/status/image-missing.png: Unrecognized image file format (gdk-pixbuf-error-quark, 3)
Bail out! Gtk:ERROR:../gtk/gtkiconhelper.c:494:ensure_surface_for_gicon: assertion failed (error == NULL): Failed to load /snap/snap-store/433/data-dir/icons/Yaru/16x16/status/image-missing.png: Unrecognized image file format (gdk-pixbuf-error-quark, 3)
Aborted (core dumped)


Any solutions?

---

### Post by Dennis N on 2020-04-24
Suggestion: You could remove the snap version of Ubuntu Software and replace it with the apt package from the Ubuntu repository. The snap was named 'Snap Store' in the 20.04 beta. Check that this is still the case in the final release (I don't know since I removed it before the final release).
Use your terminal:
```
snap list
```
If you see snap-store, remove it with the command:
```
snap remove snap-store
```
Then, install from the Ubuntu repository:
```
sudo apt install ubuntu-software
```
Note: This really installs gnome-software (and appears as 'Software' in your applications).
This may work better for you.

---

### Post by P-I H on 2020-04-24
In Ubuntu 20.04 the software store is changed from gnome-software to Snap Store. Snap Store is also renamed to Ubuntu Software. The new Ubuntu Software works OK in most case, but it doesn't support flatpaks and there might be othe problems not discovered yet.
Perhaps installation of gnome-software will solve your problem.
Use the terminal to install gnome-software. 
sudo apt install gnome-software.
After the installation you will have two software stores, one called Software a.k.a gnome-software and one called Ubuntu Software a.k.a Snap Store.

---

