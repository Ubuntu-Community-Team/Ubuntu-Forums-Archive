---
title: "Failed to authenticate packages!"
date: 2010-08-20
forum: Installation &amp; Upgrades
---

### Post by Blackylol on 2010-08-20
While running the command sudo apt-get upgrade I get this msg

            "Failed to authenticate the following packages"
AVISO: ¡No se han podido autenticar los siguientes paquetes!
  libnautilus-extension1 libndesk-dbus1.0-cil libsoup2.4-1 libsoup-gnome2.4-1
  libwebkit-1.0-common libwebkit-1.0-2 nautilus nautilus-data notify-osd

Fixd

---

### Post by cabez0n on 2010-10-13
This might be because your are using custom repositories and you haven't included the keys for those, or perhaps the keyserver is taking too long to answer and your update times out.

---

