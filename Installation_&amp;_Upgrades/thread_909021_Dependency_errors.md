---
title: "Dependency errors"
date: 2008-09-03
forum: Installation &amp; Upgrades
---

### Post by kasmoticus on 2008-09-03
These are the errors i'm getting. Thanks

kasmot@cliff:~/awn-extras$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
4 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Setting up python-awn-trunk (0.3.1~bzr477-hardy1-1) ...
pycentral: pycentral pkginstall: not overwriting local files
pycentral pkginstall: not overwriting local files
dpkg: error processing python-awn-trunk (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of avant-window-navigator-trunk:
 avant-window-navigator-trunk depends on python-awn-trunk (>= 0.3.1~bzr477-hardy1-1); however:
  Package python-awn-trunk is not configured yet.
dpkg: error processing avant-window-navigator-trunk (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of awn-manager-trunk:
 awn-manager-trunk depends on avant-window-navigator-trunk (>= 0.2); however:
  Package avant-window-navigator-trunk is not configured yet.
 awn-manager-trunk depends on python-awn-trunk; however:
  Package python-awn-trunk is not configured yet.
dpkg: error processing awn-manager-trunk (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of avant-window-navigator-data-trunk:
 avant-window-navigator-data-trunk depends on avant-window-navigator-trunk (>= 0.3.1~bzr477-hardy1-1); however:
  Package avant-window-navigator-trunk is not configured yet.
dpkg: error processing avant-window-navigator-data-trunk (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 python-awn-trunk
 avant-window-navigator-trunk
 awn-manager-trunk
 avant-window-navigator-data-trunk
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by cdtech on 2008-09-03
Try running:
sudo dpkg --configure -a

---

### Post by kasmoticus on 2008-09-03
> **cdtech said:**
> Try running:
sudo dpkg --configure -a

kasmot@cliff:/usr/local/bin$ sudo dpkg --configure -a
[sudo] password for kasmot: 
dpkg: status database area is locked by another process
kasmot@cliff:/usr/local/bin$ sudo dpkg --configure -a
Setting up python-awn-trunk (0.3.1~bzr477-hardy1-1) ...
pycentral: pycentral pkginstall: not overwriting local files
pycentral pkginstall: not overwriting local files
dpkg: error processing python-awn-trunk (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of awn-manager-trunk:
 awn-manager-trunk depends on python-awn-trunk; however:
  Package python-awn-trunk is not configured yet.
dpkg: error processing awn-manager-trunk (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of avant-window-navigator-trunk:
 avant-window-navigator-trunk depends on python-awn-trunk (>= 0.3.1~bzr477-hardy1-1); however:
  Package python-awn-trunk is not configured yet.
dpkg: error processing avant-window-navigator-trunk (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of avant-window-navigator-data-trunk:
 avant-window-navigator-data-trunk depends on avant-window-navigator-trunk (>= 0.3.1~bzr477-hardy1-1); however:
  Package avant-window-navigator-trunk is not configured yet.
dpkg: error processing avant-window-navigator-data-trunk (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 python-awn-trunk
 awn-manager-trunk
 avant-window-navigator-trunk
 avant-window-navigator-data-trunk

Still the same error :(

---

### Post by cdtech on 2008-09-03
wow, thats strange could you try again with:
sudo dpkg --configure -a && sudo apt-get -f install

---

