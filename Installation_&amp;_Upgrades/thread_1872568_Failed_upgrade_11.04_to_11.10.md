---
title: "Failed upgrade 11.04 to 11.10"
date: 2011-10-30
forum: Installation &amp; Upgrades
---

### Post by Stewart54 on 2011-10-30
Good evening all
Decided to end my weekend by upgrading 11.04 Natty to 11.10. I read the posts and followed the directions provided and after a while got the message that due to screwed up dependencies the upgrade was aborted, do a partial upgrade.  Well I searched around for posts, I am basically an idiot newbie on to correct the following:

The following packages have unmet dependencies:

firefox: Depends: libgcc1 (>=1:4.1.1) but 1:4.5.2-ubuntu4 is to be installed

Not real comfortable with what I found in search, so I read a post to go ahead and install partial upgrade and dependencies should work out or can be easily fixed.

Tried to install partial update from update manager which stopped pretty quickly, cannot install partial updates and had the following:

The following packages have unmet dependencies:

libglib2.0-0: Depends: libffi6 (>= 3.0.4) but 3.0.11~rc1-2 is to be installed
              Depends: libpcre3 (>= 8.10) but 8.12-3ubuntu2 is to be installed
              Depends: zlib1g (>= 1:1.2.2) but 1:1.2.3.4.dfsg-3ubuntu3 is to be installed
network-manager: Depends: libc6 (>= 2.4) but 2.13-20ubuntu5 is to be installed
                 Depends: libdbus-1-3 (>= 1.0.2) but 1.4.14-1ubuntu1 is to be installed
                 Depends: libdbus-glib-1-2 (>= 0.88) but 0.94-4 is to be installed
                 Depends: libglib2.0-0 (>= 2.24.0) but 2.30.0-0ubuntu4 is to be installed
                 Depends: libgudev-1.0-0 (>= 147) but 1:173-0ubuntu4 is to be installed
                 Depends: libnl3 (>= 3.0) but 3.0-1.1ubuntu1 is to be installed
                 Depends: libpolkit-gobject-1-0 (>= 0.99) but 0.102-1 is to be installed
                 Depends: upstart-job but it is a virtual package
                 Depends: lsb-base (>= 3.2-14) but 4.0-0ubuntu16 is to be installed
                 Depends: dbus (>= 1.1.2) but 1.4.14-1ubuntu1 is to be installed
                 Depends: isc-dhcp-client (>= 4.1.1-P1-4) but 4.1.1-P1-17ubuntu10 is to be installed

If anyone has any suggestions or solutions, it sure would be appreciated.  Thanks in advance for your time and knowledge.

Stew

---

### Post by Sef on 2011-10-31
One should never install a partial upgrade as it is likely to break your system. Most of the time wait a few days, and the partial upgrade problem will be resolved.

---

