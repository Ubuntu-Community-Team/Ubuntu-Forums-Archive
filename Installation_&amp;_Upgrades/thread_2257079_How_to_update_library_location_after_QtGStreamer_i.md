---
title: "How to update library location after QtGStreamer installation"
date: 2014-12-16
forum: Installation &amp; Upgrades
---

### Post by paulmilliken on 2014-12-16
After installing the latest QtGStreamer from [http://gstreamer.freedesktop.org/src/qt-gstreamer/](http://gstreamer.freedesktop.org/src/qt-gstreamer/) and the latest QtCreator on Ubuntu 14.04 (Trusty), I could create programs and run them inside QtCreator but not from the CLI.  The problem was that the qtgstreamer libraries could not be found when running from the CLI.  To fix this:
[LIST]
[*]Navigate to /etc/ld.so.conf.d and create a new file with > sudo touch filename-of-your-choice.conf
[*]Add the line > /usr/local/lib/x86_64-linux-gnu to the new conf file.  (This path is the location of the QtGStreamer libraries)
[*]Now use ldconfig to tell the linker to look for libraries in the new location: > sudo ldconfig
[/LIST]

---

