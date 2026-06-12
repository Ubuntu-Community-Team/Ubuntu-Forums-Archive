---
title: "Chromium crash when clicking upload file button."
date: 2021-11-15
forum: Installation &amp; Upgrades
---

### Post by realt3ch on 2021-11-15
funny is that it was working fine. version is: Chromium 95.0.4638.69 snap

---

### Post by realt3ch on 2021-11-15
this forum is getting old or something no? it is saying my message is too short but i enter more text then before..


ok again

when clicking upload butto on any page get this error on terminal if chromium is opened from terminal:

(chrome:200943): Gtk-WARNING **: 12:31:23.932: Could not load a pixbuf from icon theme.
This may indicate that pixbuf loaders or the mime database could not be found.
**
Gtk:ERROR:../../../../gtk/gtkiconhelper.c:494:ensure_surface_for_gicon: assertion failed (error == NULL): Failed to load /snap/chromium/1810/data-dir/icons/Adwaita/16x16/status/image-missing.png: Unable to load image-loading module: /snap/chromium/1818/gnome-platform/usr/lib/x86_64-linux-gnu/gdk-pixbuf-2.0/2.10.0/loaders/libpixbufloader-png.so: /snap/chromium/1818/gnome-platform/usr/lib/x86_64-linux-gnu/gdk-pixbuf-2.0/2.10.0/loaders/libpixbufloader-png.so: cannot open shared object file: No such file or directory (gdk-pixbuf-error-quark, 5)
Aborted (core dumped)


funny is that it was working fine. version is: Chromium 95.0.4638.69 snap

---

### Post by realt3ch on 2021-11-15
and if i download binary chrome get this error after few minutes:

[7391:7401:1115/145605.622381:ERROR:trk_protocol_handler.cc(17)] Blocked URL in TrkProtocolHandler: trk:[https://update.9oo91eapis.qjz9zk/service/update2/json](https://update.9oo91eapis.qjz9zk/service/update2/json)
[7391:7401:1115/145646.738066:ERROR:url_request.cc(591)] Block URL in URLRequest: [https://www.9oo91eapis.qjz9zk/affiliation/v1/affiliation:lookupByHashPrefix?key=dummytoken](https://www.9oo91eapis.qjz9zk/affiliation/v1/affiliation:lookupByHashPrefix?key=dummytoken)
[7391:7401:1115/145646.738283:ERROR:trk_protocol_handler.cc(17)] Blocked URL in TrkProtocolHandler: trk:[https://www.9oo91eapis.qjz9zk/affiliation/v1/affiliation:lookupByHashPrefix?key=dummytoken](https://www.9oo91eapis.qjz9zk/affiliation/v1/affiliation:lookupByHashPrefix?key=dummytoken)
Segmentation fault (core dumped)

version: Chromium 95.0.4638.54

PS: on ubuntu forums, edit post button dont work as should.!

---

### Post by ActionParsnip on 2021-11-15
Do you have any extensions / addons enabled? Have you tried disabling them all to see if it works as expected? If it does then slowly add them back in until you hit the snag

---

### Post by realt3ch on 2021-11-15
hola. thanks. 

no didnt try remove them all just some that have thinking are suspicious but didnt help. will try remove all and noticing how to works. later have download another binary and different error. then have download google-chrome binary and this one looks works. :) noticing what happen if remove all addons.

---

### Post by realt3ch on 2021-11-15
if remove all extensions bug when clicking "upload file button" filepicker.. still crash... incredible.. so google-chrome works but chromium that get installed by default with apt dont..

---

