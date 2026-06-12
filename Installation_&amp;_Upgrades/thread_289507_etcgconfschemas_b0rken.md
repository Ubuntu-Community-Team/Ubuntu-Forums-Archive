---
title: "/etc/gconf/schemas b0rken"
date: 2006-10-31
forum: Installation &amp; Upgrades
---

### Post by kennywest on 2006-10-31
Hi,

I've managed to remove all contents from /etc/gconf. According to [http://ftp.belnet.be/mirror/ubuntu.com/ubuntu/dists/dapper/Contents-i386.gz](http://ftp.belnet.be/mirror/ubuntu.com/ubuntu/dists/dapper/Contents-i386.gz) /etc/gconf is contained in the following packages:
etc/gconf/1/path                                            universe/gnome/gconf
etc/gconf/gconf.xml.defaults/desktop/gnome/url-handlers/peercast/%gconf.xml universe/sound/peercast-handlers
etc/gconf/gconf.xml.defaults/schemas/desktop/gnome/url-handlers/peercast/%gconf.xml universe/sound/peercast-handlers
etc/gconf/schemas/desktop.schemas                           universe/gnome/gconf
etc/gconf/schemas/gpass.schemas                             universe/gnome/gpass
etc/gconf/schemas/grdesktop.schemas                         universe/x11/grdesktop
etc/gconf/schemas/magicdev.schemas                          universe/gnome/magicdev
etc/gconf/schemas/neutrino.schemas                          universe/gnome/neutrino
etc/gconf/schemas/quick-lounge.schemas                      universe/gnome/quick-lounge-applet
etc/gconf/schemas/teg.schemas                               universe/gnome/teg
etc/gconf/schemas/xpenguins-applet.schemas                  universe/gnome/xpenguins-applet
etc/gconf/schemas/yank.schemas                              universe/gnome/yank

So, reinstalling gconf should do the trick ... it doesn't. Any possibility to force gconf being reinstalled?

---

