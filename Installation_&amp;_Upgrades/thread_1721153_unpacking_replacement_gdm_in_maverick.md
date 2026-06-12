---
title: "unpacking replacement gdm in maverick"
date: 2011-04-04
forum: Installation &amp; Upgrades
---

### Post by jonndoe45 on 2011-04-04
Whatever I use, synaptic, update manager, apt-get it insists on upgrading GDM  

The upgrade just 'hangs' on the upgrade with'unpacking replacement gdm' message   

All 3 still try and upgrade gdm (why does it do this even when I do not want to upgrade/update) ?????      

Please help , I've had this problem for nearly 3 days now and i am stuck can't do any package install my system is basically 'stuck' in no update/install mode until i solve this 

The gdm is: /var/cache/apt/archives/gdm_2.30.5-0ubuntu4.1_i386.deb  even if i get a new copy from ANY repo it still has this problem, any solution, anyone come accross this yet?

Thanks if you can help

---

### Post by garvinrick4 on 2011-04-04
Try:
```
sudo dpkg --configure -a
```

---

### Post by jonndoe45 on 2011-04-04
You want to do that with dpkg not apt-get, and no it doesn't solve anything.

I tried that already, also tried removing the downloaded package file and tried using a different repo, 

I have no idea why it is hanging/locking in the unpacking of the package file.

---

### Post by jonndoe45 on 2011-04-04
Using dpkg -s gdm .... 

Package: gdm
Status: install reinstreq half-installed
Priority: optional
Section: gnome
Installed-Size: 2304
Maintainer: Sebastien Bacher <seb128@ubuntu.com>
Architecture: i386
Version: 2.30.5-0ubuntu4
Config-Version: 2.30.5-0ubuntu4
Replaces: fast-user-switch-applet, gdm-snapshot
Provides: x-display-manager
Depends: libart-2.0-2 (>= 2.3.18), libatk1.0-0 (>= 1.29.3), libattr1 (>= 2.4.41-1), libbonobo2-0 (>= 2.15.0), libbonoboui2-0 (>= 2.15.1), libc6 (>= 2.4), libcairo2 (>= 1.2.4), libcanberra-gtk0 (>= 0.4), libcanberra0 (>= 0.2), libdbus-1-3 (>= 1.0.2), libdbus-glib-1-2 (>= 0.88), libfontconfig1 (>= 2.8.0), libfreetype6 (>= 2.2.1), libgconf2-4 (>= 2.31.1), libgdk-pixbuf2.0-0 (>= 2.21.6), libglib2.0-0 (>= 2.24.0), libgnome2-0 (>= 2.17.3), libgnomecanvas2-0 (>= 2.11.1), libgtk2.0-0 (>= 2.16.0), liborbit2 (>= 1:2.14.10), libpam0g (>= 0.99.7.1), libpanel-applet2-0 (>= 2.26.0), libpango1.0-0 (>= 1.14.0), libpolkit-gobject-1-0 (>= 0.94), libpopt0 (>= 1.16), libselinux1 (>= 1.32), libupower-glib1 (>= 0.9.0), libwrap0 (>= 7.6-4~), libx11-6, libxau6, libxdmcp6, libxklavier16 (>= 5.0), libxml2 (>= 2.6.27), zlib1g (>= 1:1.1.4), debconf (>= 0.5) | debconf-2.0, gconf2 (>= 2.28.1-2), upstart-job, adduser, libpam-modules (>= 0.72-1), libpam-runtime (>= 0.76-13.1), gnome-session-bin, kbd | console-tools, udev (>= 149-2)
Recommends: xserver-xorg, metacity | x-window-manager, gnome-settings-daemon | xfconf
Suggests: locales, uswsusp, libpam-gnome-keyring, gnome-power-manager, gnome-orca, gok, gnome-mag
Breaks: usplash
Conflicts: fast-user-switch-applet, gdm-snapshot, libxklavier15 (<< 4.0-0ubuntu2), xsplash (<< 0.8)
Conffiles:
 /etc/gdm/gdm.schemas f9466e1e1826546f0e400ce83b10d19a
 /etc/gdm/PostSession/Default faa25c6c7940f930d70538c673a39726
 /etc/gdm/Xsession 55cd2933fccdd18b9e85e3728541b7e1
 /etc/gdm/PostLogin/Default.sample ea12aa729c8c6c09ac7643f0dfba5726
 /etc/gdm/PreSession/Default 95f64d406870c3aef6adaddc092bfd8c
 /etc/gdm/Init/Default 8c1186a126afecd691750a99b0463735
 /etc/dbus-1/system.d/gdm.conf 936c6ecc600ba843eaae0025c6ddb942
 /etc/pam.d/gdm 02d4bd40eb6d8c03d4063da806aaf42c
 /etc/pam.d/gdm-autologin 3d4f9d79e7302b4eff2b7a00e5e4693c
 /etc/X11/Xsession.d/60xdg_path-on-session d0b3913486dad32941efe38d984f22a4
 /etc/init/gdm.conf e0bad2ee49fe42d27437d5679ed1026b


smileys put in by forum editor.... not me!!!!

---

