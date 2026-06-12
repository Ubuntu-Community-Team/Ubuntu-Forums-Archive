---
title: "apt-get upgrade - unpacking updates fails: xz syntax error?"
date: 2013-02-21
forum: Installation &amp; Upgrades
---

### Post by Wildscot on 2013-02-21
I'm running 12.04 Server (3.2.0-38-generic, x86_64), and I'm having the following problems with updates.

It's the same as below for all updates, they're failing to unpack and I'm not sure what to try now. I'd appreciate any help.

I don't know if the missing shared library is relevant or how to deal with that either?

> ...
Unpacking replacement libqtcore4 ...
/usr/bin/xz: 1: /usr/bin/xz: Syntax error: ")" unexpected
dpkg-deb (subprocess): subprocess data returned error exit status 2
dpkg-deb: error: subprocess <decompress> returned error exit status 2
dpkg: error processing /var/cache/apt/archives/libqtcore4_4%3a4.8.1-0ubuntu4.4_amd64.deb (--unpack):
 subprocess dpkg-deb --fsys-tarfile returned error exit status 2
No apport report written because MaxReports has already been reached

                                                                    Errors were encountered while processing:
 /var/cache/apt/archives/libqt4-qt3support_4%3a4.8.1-0ubuntu4.4_amd64.deb
 /var/cache/apt/archives/libqt4-designer_4%3a4.8.1-0ubuntu4.4_amd64.deb
 /var/cache/apt/archives/libqt4-opengl_4%3a4.8.1-0ubuntu4.4_amd64.deb
 /var/cache/apt/archives/libqt4-svg_4%3a4.8.1-0ubuntu4.4_amd64.deb
 /var/cache/apt/archives/libqtgui4_4%3a4.8.1-0ubuntu4.4_amd64.deb
 /var/cache/apt/archives/libqt4-declarative_4%3a4.8.1-0ubuntu4.4_amd64.deb
 /var/cache/apt/archives/libqt4-xmlpatterns_4%3a4.8.1-0ubuntu4.4_amd64.deb
 /var/cache/apt/archives/libqt4-network_4%3a4.8.1-0ubuntu4.4_amd64.deb
 /var/cache/apt/archives/libqt4-script_4%3a4.8.1-0ubuntu4.4_amd64.deb
 /var/cache/apt/archives/libqt4-sql-mysql_4%3a4.8.1-0ubuntu4.4_amd64.deb
 /var/cache/apt/archives/libqt4-sql_4%3a4.8.1-0ubuntu4.4_amd64.deb
 /var/cache/apt/archives/qdbus_4%3a4.8.1-0ubuntu4.4_amd64.deb
 /var/cache/apt/archives/libqt4-dbus_4%3a4.8.1-0ubuntu4.4_amd64.deb
 /var/cache/apt/archives/libqt4-xml_4%3a4.8.1-0ubuntu4.4_amd64.deb
 /var/cache/apt/archives/libqtcore4_4%3a4.8.1-0ubuntu4.4_amd64.deb

ps: error while loading shared libraries: libproc-3.2.8.so: cannot open shared object file: No such file or directory

---

