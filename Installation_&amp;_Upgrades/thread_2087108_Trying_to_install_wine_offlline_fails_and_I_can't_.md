---
title: "Trying to install wine offlline fails and I can't find why"
date: 2012-11-22
forum: Installation &amp; Upgrades
---

### Post by Laeirbag on 2012-11-22
Hello Everyone. As you can guess I'm one of those offline guys trying to use linux via Ubuntu. Problem comes when trying to install wine. I've already installed dependencies with name different than "wine" (libc6, libncurses5, etc.) but they are still being mentioned and I can't figure out why. I thougth I just needed to install all necessary and interdependant packages with only one command (dpkg -i wine*.deb), but this was the result. Can someone guide me? Thanks for everything

(Reading database ... 168959 files and directories currently installed.)
Preparing to replace wine 1.4-0ubuntu4 (using wine_1.4-0ubuntu4_amd64.deb) ...
Unpacking replacement wine ...
Preparing to replace wine1.4 1.4-0ubuntu4 (using wine1.4_1.4-0ubuntu4_amd64.deb) ...
Unpacking replacement wine1.4 ...
Preparing to replace wine1.4-amd64 1.4-0ubuntu4 (using wine1.4-amd64_1.4-0ubuntu4_amd64.deb) ...
Unpacking replacement wine1.4-amd64 ...
Preparing to replace wine1.4-common 1.4-0ubuntu4 (using wine1.4-common_1.4-0ubuntu4_all.deb) ...
Unpacking replacement wine1.4-common ...
Preparing to replace wine1.4-dev 1.4-0ubuntu4 (using wine1.4-dev_1.4-0ubuntu4_amd64.deb) ...
Unpacking replacement wine1.4-dev ...
Preparing to replace wine1.4-i386:i386 1.4-0ubuntu4 (using wine1.4-i386_1.4-0ubuntu4_i386.deb) ...
Unpacking replacement wine1.4-i386:i386 ...
dpkg: dependency problems prevent configuration of wine1.4-i386:i386:
 wine1.4-i386:i386 depends on libasound2 (>= 1.0.23).
 wine1.4-i386:i386 depends on libc6 (>= 2.9).
 wine1.4-i386:i386 depends on libglib2.0-0 (>= 2.16.0).
 wine1.4-i386:i386 depends on libgphoto2-2 (>= 2.4.10.1).
 wine1.4-i386:i386 depends on libgphoto2-port0 (>= 2.4.10.1).
 wine1.4-i386:i386 depends on libgstreamer-plugins-base0.10-0 (>= 0.10.22).
 wine1.4-i386:i386 depends on libgstreamer0.10-0 (>= 0.10.26).
 wine1.4-i386:i386 depends on liblcms1 (>= 1.15-1).
 wine1.4-i386:i386 depends on libldap-2.4-2 (>= 2.4.7).
 wine1.4-i386:i386 depends on libmpg123-0 (>= 1.6.2).
 wine1.4-i386:i386 depends on libopenal1 (>= 1:1.13).
 wine1.4-i386:i386 depends on libsm6.
 wine1.4-i386:i386 depends on libx11-6.
 wine1.4-i386:i386 depends on libxext6.
 wine1.4-i386:i386 depends on libxml2 (>= 2.7.4).
 wine1.4-i386:i386 depends on zlib1g (>= 1:1.1.4).
 wine1.4-i386:i386 depends on libncurses5.
dpkg: error processing wine1.4-i386:i386 (--install):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of wine1.4:
 wine1.4 depends on wine1.4-i386 (= 1.4-0ubuntu4); however:
  Package wine1.4-i386 is not installed.
  Package wine1.4-i386:i386 is not configured yet.
dpkg: error processing wine1.4 (--install):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of wine1.4-common:
 wine1.4-common depends on wine1.4 (= 1.4-0ubuntu4); however:
  Package wine1.4 is not configured yet.
dpkg: error processing wine1.4-common (--install):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of wine:
 wine depends on wine1.4; however:
  Package wine1.4 is not configured yet.
dpkg: error processing wine (--install):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of wine1.4-amd64:
 wine1.4-amd64 depends on wine1.4-common (= 1.4-0ubuntu4); however:
  Package wine1.4-common is not configured yet.
dpkg: error processing wine1.4-amd64 (--install):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of wine1.4-dev:
 wine1.4-dev depends on wine1.4-amd64 (= 1.4-0ubuntu4); however:
  Package wine1.4-amd64 is not configured yet.
dpkg: error processing wine1.4-dev (--install):
 dependency problems - leaving unconfigured
Processing triggers for man-db ...
Processing triggers for desktop-file-utils ...
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Processing triggers for gnome-menus ...
Processing triggers for hicolor-icon-theme ...
Errors were encountered while processing:
 wine1.4-i386:i386
 wine1.4
 wine1.4-common
 wine
 wine1.4-amd64
 wine1.4-dev

---

### Post by ibjsb4 on 2012-11-22
My guess is your still missing some dependences.  May want to try doing it with Synaptic Package Manager.

[https://help.ubuntu.com/community/InstallingSoftware#Installing_packages_without_an_Internet_connection](https://help.ubuntu.com/community/InstallingSoftware#Installing_packages_without_an_Internet_connection)

[http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=synaptic+package+manager&as_qdr=all&sa=Google+Search&lang=en]("http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=synaptic+package+manager&as_qdr=all&sa=Google+Search&lang=en")

In terminal:  sudo apt-get install synaptic

Also check out code tags.

```
(Reading database ... 168959 files and directories currently installed.)
Preparing to replace wine 1.4-0ubuntu4 (using wine_1.4-0ubuntu4_amd64.deb) ...
Unpacking replacement wine ...
Preparing to replace wine1.4 1.4-0ubuntu4 (using wine1.4_1.4-0ubuntu4_amd64.deb) ...
Unpacking replacement wine1.4 ...
Preparing to replace wine1.4-amd64 1.4-0ubuntu4 (using wine1.4-amd64_1.4-0ubuntu4_amd64.deb) ...
Unpacking replacement wine1.4-amd64 ...
Preparing to replace wine1.4-common 1.4-0ubuntu4 (using wine1.4-common_1.4-0ubuntu4_all.deb) ...
Unpacking replacement wine1.4-common ...
Preparing to replace wine1.4-dev 1.4-0ubuntu4 (using wine1.4-dev_1.4-0ubuntu4_amd64.deb) ...
Unpacking replacement wine1.4-dev ...
Preparing to replace wine1.4-i386:i386 1.4-0ubuntu4 (using wine1.4-i386_1.4-0ubuntu4_i386.deb) ...
Unpacking replacement wine1.4-i386:i386 ...
dpkg: dependency problems prevent configuration of wine1.4-i386:i386:
 wine1.4-i386:i386 depends on libasound2 (>= 1.0.23).
 wine1.4-i386:i386 depends on libc6 (>= 2.9).
 wine1.4-i386:i386 depends on libglib2.0-0 (>= 2.16.0).
 wine1.4-i386:i386 depends on libgphoto2-2 (>= 2.4.10.1).
 wine1.4-i386:i386 depends on libgphoto2-port0 (>= 2.4.10.1).
 wine1.4-i386:i386 depends on libgstreamer-plugins-base0.10-0 (>= 0.10.22).
 wine1.4-i386:i386 depends on libgstreamer0.10-0 (>= 0.10.26).
 wine1.4-i386:i386 depends on liblcms1 (>= 1.15-1).
 wine1.4-i386:i386 depends on libldap-2.4-2 (>= 2.4.7).
 wine1.4-i386:i386 depends on libmpg123-0 (>= 1.6.2).
 wine1.4-i386:i386 depends on libopenal1 (>= 1:1.13).
 wine1.4-i386:i386 depends on libsm6.
 wine1.4-i386:i386 depends on libx11-6.
 wine1.4-i386:i386 depends on libxext6.
 wine1.4-i386:i386 depends on libxml2 (>= 2.7.4).
 wine1.4-i386:i386 depends on zlib1g (>= 1:1.1.4).
 wine1.4-i386:i386 depends on libncurses5.
dpkg: error processing wine1.4-i386:i386 (--install):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of wine1.4:
 wine1.4 depends on wine1.4-i386 (= 1.4-0ubuntu4); however:
  Package wine1.4-i386 is not installed.
  Package wine1.4-i386:i386 is not configured yet.
dpkg: error processing wine1.4 (--install):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of wine1.4-common:
 wine1.4-common depends on wine1.4 (= 1.4-0ubuntu4); however:
  Package wine1.4 is not configured yet.
dpkg: error processing wine1.4-common (--install):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of wine:
 wine depends on wine1.4; however:
  Package wine1.4 is not configured yet.
dpkg: error processing wine (--install):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of wine1.4-amd64:
 wine1.4-amd64 depends on wine1.4-common (= 1.4-0ubuntu4); however:
  Package wine1.4-common is not configured yet.
dpkg: error processing wine1.4-amd64 (--install):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of wine1.4-dev:
 wine1.4-dev depends on wine1.4-amd64 (= 1.4-0ubuntu4); however:
  Package wine1.4-amd64 is not configured yet.
dpkg: error processing wine1.4-dev (--install):
 dependency problems - leaving unconfigured
Processing triggers for man-db ...
Processing triggers for desktop-file-utils ...
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Processing triggers for gnome-menus ...
Processing triggers for hicolor-icon-theme ...
Errors were encountered while processing:
 wine1.4-i386:i386
 wine1.4
 wine1.4-common
 wine
 wine1.4-amd64
 wine1.4-dev     
```Makes it easy on the eyes.

[http://ubuntuforums.org/showthread.php?t=890901](http://ubuntuforums.org/showthread.php?t=890901)

And welcome to the forums.  :)

---

