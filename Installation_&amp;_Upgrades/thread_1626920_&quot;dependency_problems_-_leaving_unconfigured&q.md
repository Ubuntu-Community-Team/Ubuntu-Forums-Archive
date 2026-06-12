---
title: "&quot;dependency problems - leaving unconfigured&quot; after upgrade to 10.04"
date: 2010-11-20
forum: Installation &amp; Upgrades
---

### Post by gaines2166 on 2010-11-20
After running 9.04 for a year, I upgraded from 9.04 to 9.10 and then to 10.04 using Update Manager.   My Dell computer crashed several times during the upgrade to 10.04.  I restarted each time from a recovery version of 10.04, and eventually the upgrade was completed.

As far as I can tell after a few days, everything I normally use seems to be working.  However, when I add a package with Synaptic I get the error message below.  Is the message significant?  Do I need to address each error?

E: libpango1.0-common: subprocess installed post-installation script  returned error exit status 1 
E: libpango1.0-0: dependency problems - leaving unconfigured 
E: libglade2-0: dependency problems - leaving unconfigured 
E: libgnomecanvas2-0: dependency problems - leaving unconfigured 
E: libbonoboui2-0: dependency problems - leaving unconfigured 
E: libgucharmap7: dependency problems - leaving unconfigured 
E: libpanel-applet2-0: dependency problems - leaving unconfigured 
E: libwnck22: dependency problems - leaving unconfigured 
E: libcanberra-gtk0: dependency problems - leaving unconfigured 
E: libedataserverui1.2-8: dependency problems - leaving unconfigured 
E: librsvg2-2: dependency problems - leaving unconfigured 
E: libgnomekbd4: dependency problems - leaving unconfigured 
E: libmetacity-private0: dependency problems - leaving unconfigured 
E: gnome-settings-daemon: dependency problems - leaving unconfigured 
E: python-gtk2: dependency problems - leaving unconfigured 
E: python-gmenu: dependency problems - leaving unconfigured 
E: gnome-menus: dependency problems - leaving unconfigured 
E: librsvg2-common: dependency problems - leaving unconfigured 
E: gnome-icon-theme: dependency problems - leaving unconfigured 
E: gnome-control-center: dependency problems - leaving unconfigured 
E: python-gnomecanvas: dependency problems - leaving unconfigured 
E: libgnomeui-0: dependency problems - leaving unconfigured 
E: python-gnome2: dependency problems - leaving unconfigured 
E: gnome-about: dependency problems - leaving unconfigured 
E: gnome-panel: dependency problems - leaving unconfigured 
E: gnome-applets: dependency problems - leaving unconfigured 
E: ttf-sazanami-gothic: subprocess installed post-installation script  returned error exit status 1 
E: ttf-sazanami-mincho: subprocess installed post-installation script  returned error exit status 1 
E: xulrunner-1.9.2: dependency problems - leaving unconfigured 
E: yelp: dependency problems - leaving unconfigured 
E: gnome-user-guide: dependency problems - leaving unconfigured 
E: ubuntu-docs: dependency problems - leaving unconfigured 
E: adobe-flashplugin: dependency problems - leaving unconfigured 
E: gnome-games-common: dependency problems - leaving unconfigured 
E: aisleriot: dependency problems - leaving unconfigured 
E: alacarte: dependency problems - leaving unconfigured 
E: apport-gtk: dependency problems - leaving unconfigured 
E: libgksu2-0: dependency problems - leaving unconfigured 
E: libgcr0: dependency problems - leaving unconfigured 
E: gnome-keyring: dependency problems - leaving unconfigured 
E: gksu: dependency problems - leaving unconfigured 
E: python-glade2: dependency problems - leaving unconfigured 
E: libwebkit-1.0-2: dependency problems - leaving unconfigured 
E: python-webkit: dependency problems - leaving unconfigured 
E: libvte9: dependency problems - leaving unconfigured 
E: python-vte: dependency problems - leaving unconfigured 
E: synaptic: dependency problems - leaving unconfigured 
E: software-properties-gtk: dependency problems - leaving unconfigured 
E: apturl: dependency problems - leaving unconfigured 
E: at-spi: dependency problems - leaving unconfigured 
E: libbrasero-media0: dependency problems - leaving unconfigured

---

### Post by mörgæs on 2010-11-21
It sounds like your system is not stable. Might be possible to rescue it, but I would go for a fresh install.

[http://ubuntuforums.org/showthread.php?t=1580857](http://ubuntuforums.org/showthread.php?t=1580857)


If you want to try fixing it, booting the machine and running 

```
sudo apt-get update
sudo apt-get upgrade
```

maybe solves the problem (or points you to a solution), but again: Consider the fresh install before wasting to much time.

---

### Post by sikander3786 on 2010-11-21
If you prefer not to re-install, these commands might help.

```
sudo apt-get install -f
```

```
sudo dpkg --configure -a
```

And if successful,

```
sudo apt-get update && sudo apt-get upgrade
```

Please post the output if you plan to go this way :-)

---

### Post by gaines2166 on 2010-11-22
> **sikander3786 said:**
> If you prefer not to re-install, these commands might help.

```
sudo apt-get install -f
``````
sudo dpkg --configure -a
```And if successful,

```
sudo apt-get update && sudo apt-get upgrade
```Please post the output if you plan to go this way :-)

Thanks for offering help!

When I tried sudo apt-get install -f, I got the response below, and looking through it I noticed this: 

E: /var/lib/defoma/locked exists. 
E: Another defoma process seems running, or you aren't root. 
E: If you are root and defoma process isn't running undoubtedly, 
E: it is possible that defoma might have aborted. 
E: Please run defoma-reconfigure -f to fix its broken status. 

Here is the response to running defoma-reconfigure -f

rm: cannot remove `/var/lib/defoma/locked': Permission denied 
virginia@virginia:~$ 

I tried rebooting and running defoma-reconfigure -f again, but no luck

Here is the full initial response:

virginia@virginia:~$ sudo apt-get install -f 
Reading package lists... Done 
Building dependency tree 
Reading state information... Done 
The following packages were automatically installed and are no longer  required: 
  libstrigiqtdbusclient0 plasma-dataengines-workspace kdepim-runtime 
  linux-headers-2.6.31-22 python-ldap libqimageblitz4 libdmraid1.0.0.rc15 
  libicu40 kdebase-runtime-data-common python-gamin  plasma-widgets-workspace 
  libboost-program-options1.38.0 libindicate-gtk1 latex-xft-fonts libdns53 
  libknotificationitem1 libcompress-bzip2-perl kdebase-workspace-libs4+5 
  kde-icons-oxygen libexiv2-5 librasqal1 python-gtksourceview libisccc50 
  binutils-static kpartx liblzma0 libopal3.6.4 redland-utils 
  mysql-server-core-5.1 libgssdp-1.0-1 libparted1.8-12 
  kdebase-runtime-bin-kde4 liblwres50 kdebase-workspace-bin python-sip4 
  libbind9-50 libpt2.6.4-plugins libgdata5 kdebase-workspace-data  libpt2.6.4 
  libisccfg50 kdebase-workspace-kgreet-plugins libgupnp-1.0-2 libqt4-phonon 
  khelpcenter4 libxklavier15 libpq5 akonadi-server libindicate3  libpolkit-qt0 
  libconfig-tiny-perl dmraid python-nautilusburn libisc50 gnome-blackjack 
  raptor-utils libntfs-3g54 linux-headers-2.6.31-22-generic 
Use 'apt-get autoremove' to remove them. 
0 upgraded, 0 newly installed, 0 to remove and 2 not upgraded. 
633 not fully installed or removed. 
After this operation, 0B of additional disk space will be used. 
Setting up libpango1.0-common (1.28.0-0ubuntu2) ... 
E: /var/lib/defoma/locked exists. 
E: Another defoma process seems running, or you aren't root. 
E: If you are root and defoma process isn't running undoubtedly, 
E: it is possible that defoma might have aborted. 
E: Please run defoma-reconfigure -f to fix its broken status. 
Failed to clean up for defoma: 256 at /usr/sbin/update-pangox-aliases  line 48. 
dpkg: error processing libpango1.0-common (--configure): 
 subprocess installed post-installation script returned error exit status 1 
dpkg: dependency problems prevent configuration of libpango1.0-0: 
 libpango1.0-0 depends on libpango1.0-common (>= 1.28.0-0ubuntu2); however: 
  Package libpango1.0-common is not configured yet. 
dpkg: error processing libpango1.0-0 (--configure): 
 dependency problems - leaving unconfigured 
dpkg: dependency problems prevent configuration of libglade2-0: 
 libglade2-0 depends on libpango1.0-0 (>= 1.14.0); however: 
  Package libpango1.0-0 is not configured yet. 
dpkg: error processing libglade2-0 (--configure): 
 dependency No apport report written because the error message  indicates its a followup error from a previous failure. 
                                      No apport report written because  the error message indicates its a followup error from a previous failure. 
                                                                No  apport report written because MaxReports is reached already 
                                              No apport report written  because MaxReports is reached already 
                            No apport report written because MaxReports  is reached already 
          No apport report written because MaxReports is reached already 
                                                                         No apport report written because MaxReports is reached already 
                                                      problems -  leaving unconfigured 
dpkg: dependency problems prevent configuration of libgnomecanvas2-0: 
 libgnomecanvas2-0 depends on libglade2-0 (>= 1:2.6.1); however: 
  Package libglade2-0 is not configured yet. 
 libgnomecanvas2-0 depends on libpango1.0-0 (>= 1.14.0); however: 
  Package libpango1.0-0 is not configured yet. 
dpkg: error processing libgnomecanvas2-0 (--configure): 
 dependency problems - leaving unconfigured 
dpkg: dependency problems prevent configuration of libbonoboui2-0: 
 libbonoboui2-0 depends on libglade2-0 (>= 1:2.6.1); however: 
  Package libglade2-0 is not configured yet. 
 libbonoboui2-0 depends on libgnomecanvas2-0 (>= 2.11.1); however: 
  Package libgnomecanvas2-0 is not configured yet. 
 libbonoboui2-0 depends on libpango1.0-0 (>= 1.14.0); however: 
  Package libpango1.0-0 is not configured yet. 
dpkg: error processing libbonoboui2-0 (--configure): 
 dependency problems - leaving unconfigured 
dpkg: dependency problems prevent configuration of libgucharmap7: 
 libgucharmap7 dNo apport report written because MaxReports is reached  already 
                                                                               No apport report written because MaxReports is reached already 
                                                            No apport  report written because MaxReports is reached already 
                                          No apport report written  because MaxReports is reached already 
                        No apport report written because MaxReports is  reached already 
      No apport report written because MaxReports is reached already 
                                                                    No  apport report written because MaxReports is reached already 
                                                  No apport report  written because MaxReports is reached already 
                                No apport report written because  MaxReports is reached already 
              No apport report written because MaxReports is reached  already 
                                                                             No apport report written because MaxReports is reached already 
                                                          No apport  report written because MaxReports is reached already 
                                        No apport report written  because MaxReports is reached already 
                      epends on libpango1.0-0 (>= 1.14.0); however: 
  Package libpango1.0-0 is not configured yet. 
dpkg: error processing libgucharmap7 (--configure): 
 dependency problems - leaving unconfigured 
dpkg: dependency problems prevent configuration of libpanel-applet2-0: 
 libpanel-applet2-0 depends on libbonoboui2-0 (>= 2.15.1); however: 
  Package libbonoboui2-0 is not configured yet. 
dpkg: error processing libpanel-applet2-0 (--configure): 
 dependency problems - leaving unconfigured 
dpkg: dependency problems prevent configuration of libwnck22: 
 libwnck22 depends on libpango1.0-0 (>= 1.14.0); however: 
  Package libpango1.0-0 is not configured yet. 
dpkg: error processing libwnck22 (--configure): 
 dependency problems - leaving unconfigured 
dpkg: dependency problems prevent configuration of libcanberra-gtk0: 
 libcanberra-gtk0 depends on libpango1.0-0 (>= 1.14.0); however: 
  Package libpango1.0-0 is not configured yet. 
dpkg: error processing libcanberra-gtk0 (--configure): 
 dependency problems - leaving uncNo apport report written because  MaxReports is reached already 
                No apport report written because MaxReports is reached  already 
                                                                              onfigured 
dpkg: dependency problems prevent configuration of libedataserverui1.2-8: 
 libedataserverui1.2-8 depends on libglade2-0 (>= 1:2.6.1); however: 
  Package libglade2-0 is not configured yet. 
 libedataserverui1.2-8 depends on libpango1.0-0 (>= 1.14.0); however: 
  Package libpango1.0-0 is not configured yet. 
dpkg: error processing libedataserverui1.2-8 (--configure): 
 dependency problems - leaving unconfigured 
dpkg: dependency problems prevent configuration of librsvg2-2: 
 librsvg2-2 depends on libpango1.0-0 (>= 1.14.0); however: 
  Package libpango1.0-0 is not configured yet. 
dpkg: error processing librsvg2-2 (--configure): 
 dependency problems - leaving unconfigured 
dpkg: dependency problems prevent configuration of libgnomekbd4: 
 libgnomekbd4 depends on libpango1.0-0 (>= 1.22.0); however: 
  Package libpango1.0-0 is not configured yet. 
dpkg: error processing libgnomekbd4 (--configure): 
 dependency problems - leaving unconfigured 
dpkg: dependency problems prevent configuration of libmetacity-private0: 
 libmetacity-private0 depends on libcanberra-gtk0 (>= 0.2); however: 
  Package libcanberra-gtk0 is not configured yet. 
 libmetacity-private0 depends on libpango1.0-0 (>= 1.14.0); however: 
  Package libpango1.0-0 is not configured yet. 
dpkg: error processing libmetacity-private0 (--configure): 
 dependency problems - leaving unconfigured 
dpkg: dependency problems prevent configuration of gnome-settings-daemon: 
 gnome-settings-daemon depends on libcanberra-gtk0 (>= 0.2); however: 
  Package libcanberra-gtk0 is not configured yet. 
 gnome-settings-daemon depends on libgnomekbd4 (>= 2.29.5); however: 
  Package libgnomekbd4 is not configured yet. 
 gnome-settings-daemon depends on libpango1.0-0 (>= 1.14.0); however: 
  Package libpango1.0-0 is not configured yet. 
dpkg: error processing gnome-settings-daemon (--configure): 
 dependency problems - leaving unconfigured 
dpkg: dependency problems prevent configuration of python-gtk2: 
 python-gtk2 depends on libpango1.0-0 (>= 1.22.0); however: 
  Package libpango1.0-0 is not configured yet. 
dpkg: error processing python-gtk2 (--configure): 
 dependency problems - leaving unconfigured 
dpkg: dependency problems prevent configuration of python-gmenu: 
 python-gmenu depends on python-gtk2; however: 
  Package python-gtk2 is not configured yet. 
dpkg: error processing python-gmenu (--configure): 
 dependency problems - leaving unconfigured 
dpkg: dependency problems prevent configuration of gnome-menus: 
 gnome-menus depends on python-gmenu (= 2.30.0-0ubuntu4); however: 
  Package python-gmenu is not configured yet. 
dpkg: error processing gnome-menus (--configure): 
 dependency problems - leaving unconfigured 
dpkg: dependency problems prevent configuration of librsvg2-common: 
 librsvg2-common depends on librsvg2-2 (= 2.26.3-0ubuntu1); however: 
  Package librsvg2-2 is not configured yet. 
dpkg: error processing librsvg2-common (--configure): 
 dependency problems - leaving unconfigured 
dpkg: dependency problems prevent configuration of gnome-icon-theme: 
 gnome-icon-theme depends on librsvg2-common; however: 
  Package librsvg2-common is not configured yet. 
dpkg: error processing gnome-icon-theme (--configure): 
 dependency problems - leaving unconfigured 
dpkg: dependency problems prevent configuration of gnome-control-center: 
 gnome-control-center depends on libcanberra-gtk0 (>= 0.2); however: 
  Package libcanberra-gtk0 is not configured yet. 
 gnome-control-center depends on libgnomekbd4 (>= 2.29.5); however: 
  Package libgnomekbd4 is not configured yet. 
 gnome-control-center depends on libmetacity-private0 (>= 1:2.26.0);  however: 
  Package libmetacity-private0 is not configured yet. 
 gnome-control-center depends on libpango1.0-0 (>= 1.17); however: 
  Package libpango1.0-0 is not configured yet. 
 gnome-control-center depends on librsvg2-2 (>= 2.26.0); however: 
  Package librsvg2-2 is not configured yet. 
 gnome-control-center depends on gnome-settings-daemon (>= 2.26); however: 
  Package gnome-settings-daemon is not configured yet. 
 gnome-control-center depends on gnome-menus (>= 2.12.0); however: 
  Package gnome-menus is not configured yet. 
 gnome-control-center depends on gnome-icon-theme (>= 2.24); however: 
  Package gnome-icon-theme is not configured yet. 
dpkg: error processing gnome-control-center (--configure): 
 dependency problems - leaving unconfigured 
dpkg: dependency problems prevent configuration of python-gnomecanvas: 
 python-gnomecanvas depends on libgnomecanvas2-0 (>= 2.11.1); however: 
  Package libgnomecanvas2-0 is not configured yet. 
 python-gnomecanvas depends on libpango1.0-0 (>= 1.14.0); however: 
  Package libpango1.0-0 is not configured yet. 
dpkg: error processing python-gnomecanvas (--configure): 
 dependency problems - leaving unconfigured 
dpkg: dependency problems prevent configuration of libgnomeui-0: 
 libgnomeui-0 depends on libbonoboui2-0 (>= 2.15.1); however: 
  Package libbonoboui2-0 is not configured yet. 
 libgnomeui-0 depends on libglade2-0 (>= 1:2.6.1); however: 
  Package libglade2-0 is not configured yet. 
 libgnomeui-0 depends on libgnomecanvas2-0 (>= 2.11.1); however: 
  Package libgnomecanvas2-0 is not configured yet. 
 libgnomeui-0 depends on libpango1.0-0 (>= 1.17.5); however: 
  Package libpango1.0-0 is not configured yet. 
dpkg: error processing libgnomeui-0 (--configure): 
 dependency problems - leaving unconfigured 
dpkg: dependency problems prevent configuration of python-gnome2: 
 python-gnome2 depends on python-gnomecanvas; however: 
  Package python-gnomecanvas is not configured yet. 
 python-gnome2 depends on python-gtk2 (>= 2.10.3); however: 
  Package python-gtk2 is not configured yet. 
 python-gnome2 depends on python2.6-gnomecanvas; however: 
  Package python2.6-gnomecanvas is not installed. 
  Package python-gnomecanvas which provides python2.6-gnomecanvas is  not configured yet. 
 python-gnome2 depends on python2.6-gtk2; however: 
  Package python2.6-gtk2 is not installed. 
  Package python-gtk2 which provides python2.6-gtk2 is not configured yet. 
 python-gnome2 depends on libbonoboui2-0 (>= 2.15.1); however: 
  Package libbonoboui2-0 is not configured yet. 
 python-gnome2 depends on libgnomecanvas2-0 (>= 2.11.1); however: 
  Package libgnomecanvas2-0 is not configured yet. 
 python-gnome2 depends on libgnomeui-0 (>= 2.22.0); however: 
  Package libgnomeui-0 is not configured yet. 
 python-gnome2 depends on libpango1.0-0 (>= 1.14.0); however: 
  Package libpango1.0-0 is not configured yet. 
dpkg: error processing python-gnome2 (--configure): 
 dependency problems - leaving unconfigured 
dpkg: dependency problems prevent configuration of gnome-about: 
 gnome-about depends on python-gtk2; however: 
  Package python-gtk2 is not configured yet. 
 gnome-about depends on python-gnome2; however: 
  Package python-gnome2 is not configured yet. 
dpkg: error processing gnome-about (--configure): 
 dependency problems - leaving unconfigured 
No apport report written because MaxReports is reached already 
                                                              dpkg:  dependency problems prevent configuration of gnome-panel: 
 gnome-panel depends on libbonoboui2-0 (>= 2.15.1); however: 
  Package libbonoboui2-0 is not configured yet. 
 gnome-panel depends on libcanberra-gtk0 (>= 0.17); however: 
  Package libcanberra-gtk0 is not configured yet. 
 gnome-panel depends on libedataserverui1.2-8 (>= 2.28.3.1); however: 
  Package libedataserverui1.2-8 is not configured yet. 
 gnome-panel depends on libpanel-applet2-0 (>= 2.26.0); however: 
  Package libpanel-applet2-0 is not configured yet. 
 gnome-panel depends on libpango1.0-0 (>= 1.18.0); however: 
  Package libpango1.0-0 is not configured yet. 
 gnome-panel depends on librsvg2-2 (>= 2.26.0); however: 
  Package librsvg2-2 is not configured yet. 
 gnome-panel depends on libwnck22 (>= 2.22.0); however: 
  Package libwnck22 is not configured yet. 
 gnome-panel depends on gnome-control-center (>= 1:2.8.2-3); however: 
  Package gnome-control-center is not configured yet. 
 gnome-panel depends on gnome-menus (>= 2.16.1); hNo apport report  written because MaxReports is reached already 
                                owever: 
  Package gnome-menus is not configured yet. 
 gnome-panel depends on gnome-about (>= 2.10.0-1); however: 
  Package gnome-about is not configured yet. 
dpkg: error processing gnome-panel (--configure): 
 dependency problems - leaving unconfigured 
dpkg: dependency problems prevent configuration of gnome-applets: 
 gnome-applets depends on libbonoboui2-0 (>= 2.15.1); however: 
  Package libbonoboui2-0 is not configured yet. 
 gnome-applets depends on libgucharmap7 (>= 1:2.24.0); however: 
  Package libgucharmap7 is not configured yet. 
 gnome-applets depends on libpanel-applet2-0 (>= 2.26.0); however: 
  Package libpanel-applet2-0 is not configured yet. 
 gnome-applets depends on libpango1.0-0 (>= 1.14.0); however: 
  Package libpango1.0-0 is not configured yet. 
 gnome-applets depends on libwnck22 (>= 2.22.0); however: 
  Package libwnck22 is not configured yet. 
 gnome-applets depends on gnome-panel (>= 2.13.4); however: 
  Package gnome-panel is not configured yet. 
 gnome-applets depends on gnome-icon-theme (>= 2.15.91); however: 
  Package gnome-icon-theme is not configured yet. 
dpkg: error processing gnome-applets (--configure): 
 dependency problems - leaving unconfigured 
No apport report written because MaxReports is reached already 
                                                              Setting  up ttf-sazanami-gothic (20040629-7ubuntu2) ... 
E: /var/lib/defoma/locked exists. 
E: Another defoma process seems running, or you aren't root. 
E: If you are root and defoma process isn't running undoubtedly, 
E: it is possible that defoma might have aborted. 
E: Please run defoma-reconfigure -f to fix its broken status. 
dpkg: error processing ttf-sazanami-gothic (--configure): 
 subprocess installed post-installation script returned error exit status 1 
No apport report written because MaxReports is reached already 
                                                              Setting  up ttf-sazanami-mincho (20040629-7ubuntu2) ... 
E: /var/lib/defoma/locked exists. 
E: Another defoma process seems running, or you aren't root. 
E: If you are root and defoma process isn't running undoubtedly, 
E: it is possible that defoma might have aborted. 
E: Please run defoma-reconfigure -f to fix its broken status. 
dpkg: error processing ttf-sazanami-mincho (--configure): 
 subprocess installed post-installation script returned error exit status 1 
No apport report written because MaxReports is reached already 
                                                              dpkg:  dependency problems prevent configuration of xulrunner-1.9.2: 
 xulrunner-1.9.2 depends on libpango1.0-0 (>= 1.14.0); however: 
  Package libpango1.0-0 is not configured yet. 
dpkg: error processing xulrunner-1.9.2 (--configure): 
 dependency problems - leaving unconfigured 
No apport report written because MaxReports is reached already 
                                                              dpkg:  dependency problems prevent configuration of yelp: 
 yelp depends on libpango1.0-0 (>= 1.14.0); however: 
  Package libpango1.0-0 is not configured yet. 
 yelp depends on xulrunner-1.9.2; however: 
  Package xulrunner-1.9.2 is not configured yet. 
dpkg: error processing yelp (--configure): 
 dependency problems - leaving unconfigured 
No apport report written because MaxReports is reached already 
                                                              dpkg:  dependency problems prevent configuration of gnome-user-guide: 
 gnome-user-guide depends on yelp; however: 
  Package yelp is not configured yet. 
dpkg: error processing gnome-user-guide (--configure): 
 dependency problems - leaving unconfigured 
No apport report written because MaxReports is reached already 
                                                              dpkg:  dependency problems prevent configuration of ubuntu-docs: 
 ubuntu-docs depends on gnome-user-guide; however: 
  Package gnome-user-guide is not configured yet. 
 ubuntu-docs depends on yelp; however: 
  Package yelp is not configured yet. 
dpkg: error processing ubuntu-docs (--configure): 
 dependency problems - leaving unconfigured 
No apport report written because MaxReports is reached already 
                                                              dpkg:  dependency problems prevent configuration of adobe-flashplugin: 
 adobe-flashplugin depends on libpango1.0-0 (>= 1.14.0); however: 
  Package libpango1.0-0 is not configured yet. 
dpkg: error processing adobe-flashplugin (--configure): 
 dependency problems - leaving unconfigured 
No apport report written because MaxReports is reached already 
                                                              dpkg:  dependency problems prevent configuration of gnome-games-common: 
 gnome-games-common depends on libcanberra-gtk0 (>= 0.17); however: 
  Package libcanberra-gtk0 is not configured yet. 
 gnome-games-common depends on libpango1.0-0 (>= 1.14.0); however: 
  Package libpango1.0-0 is not configured yet. 
 gnome-games-common depends on librsvg2-2 (>= 2.26.0); however: 
  Package librsvg2-2 is not configured yet. 
dpkg: error processing gnome-games-common (--configure): 
 dependency problems - leaving unconfigured 
No apport report written because MaxReports is reached already 
                                                              dpkg:  dependency problems prevent configuration of aisleriot: 
 aisleriot depends on libcanberra-gtk0 (>= 0.17); however: 
  Package libcanberra-gtk0 is not configured yet. 
 aisleriot depends on librsvg2-2 (>= 2.26.0); however: 
  Package librsvg2-2 is not configured yet. 
 aisleriot depends on gnome-games-common (>= 1:2.30.0-0ubuntu6); however: 
  Package gnome-games-common is not configured yet. 
dpkg: error processing aisleriot (--configure): 
 dependency problems - leaving unconfigured 
No apport report written because MaxReports is reached already 
                                                              dpkg:  dependency problems prevent configuration of alacarte: 
 alacarte depends on python-gtk2 (>= 2.13.0); however: 
  Package python-gtk2 is not configured yet. 
 alacarte depends on python-gmenu (>= 2.27.92); however: 
  Package python-gmenu is not configured yet. 
 alacarte depends on gnome-menus (>= 2.27.92); however: 
  Package gnome-menus is not configured yet. 
dpkg: error processing alacarte (--configure): 
 dependency problems - leaving unconfigured 
No apport report written because MaxReports is reached already 
                                                              dpkg:  dependency problems prevent configuration of apport-gtk: 
 apport-gtk depends on python-gtk2 (>= 2.12); however: 
  Package python-gtk2 is not configured yet. 
dpkg: error processing apport-gtk (--configure): 
 dependency problems - leaving unconfigured 
No apport report written because MaxReports is reached already 
                                                              No apport  report written because MaxReports is reached already 
                                            No apport report written  because MaxReports is reached already 
                          dpkg: dependency problems prevent  configuration of libgksu2-0: 
 libgksu2-0 depends on libpango1.0-0 (>= 1.14.0); however: 
  Package libpango1.0-0 is not configured yet. 
dpkg: error processing libgksu2-0 (--configure): 
 dependency problems - leaving unconfigured 
dpkg: dependency problems prevent configuration of libgcr0: 
 libgcr0 depends on libpango1.0-0 (>= 1.18.0); however: 
  Package libpango1.0-0 is not configured yet. 
dpkg: error processing libgcr0 (--configure): 
 dependency problems - leaving unconfigured 
dpkg: dependency problems prevent configuration of gnome-keyring: 
 gnome-keyring depends on libgcr0 (>= 2.29.90git20100216); however: 
  Package libgcr0 is not configured yet. 
 gnome-keyring depends on libpango1.0-0 (>= 1.14.0); however: 
  Package libpango1.0-0 is not configured yet. 
dpkg: error processing gnome-keyring (--configure): 
 dependency problems - leaving unconfigured 
No apport report written because MaxReports is reached already 
                                                              dpkg:  dependency problems prevent configuration of gksu: 
 gksu depends on libgksu2-0 (>= 2.0.8); however: 
  Package libgksu2-0 is not configured yet. 
 gksu depends on libpango1.0-0 (>= 1.14.0); however: 
  Package libpango1.0-0 is not configured yet. 
 gksu depends on gnome-keyring; however: 
  Package gnome-keyring is not configured yet. 
dpkg: error processing gksu (--configure): 
 dependency problems - leaving unconfigured 
No apport report written because MaxReports is reached already 
                                                              dpkg:  dependency problems prevent configuration of python-glade2: 
 python-glade2 depends on libglade2-0 (>= 1:2.6.1); however: 
  Package libglade2-0 is not configured yet. 
 python-glade2 depends on libpango1.0-0 (>= 1.16.0); however: 
  Package libpango1.0-0 is not configured yet. 
 python-glade2 depends on python-gtk2 (= 2.17.0-0ubuntu2); however: 
  Package python-gtk2 is not configured yet. 
dpkg: error processing python-glade2 (--configure): 
 dependency problems - leaving unconfigured 
No apport report written because MaxReports is reached already 
                                                              dpkg:  dependency problems prevent configuration of libwebkit-1.0-2: 
 libwebkit-1.0-2 depends on libpango1.0-0 (>= 1.22.0); however: 
  Package libpango1.0-0 is not configured yet. 
dpkg: error processing libwebkit-1.0-2 (--configure): 
 dependency problems - leaving unconfigured 
No apport report written because MaxReports is reached already 
                                                              dpkg:  dependency problems prevent configuration of python-webkit: 
 python-webkit depends on libpango1.0-0 (>= 1.14.0); however: 
  Package libpango1.0-0 is not configured yet. 
 python-webkit depends on libwebkit-1.0-2 (>= 1.1.14); however: 
  Package libwebkit-1.0-2 is not configured yet. 
 python-webkit depends on python-gtk2; however: 
  Package python-gtk2 is not configured yet. 
dpkg: error processing python-webkit (--configure): 
 dependency problems - leaving unconfigured 
No apport report written because MaxReports is reached already 
                                                              dpkg:  dependency problems prevent configuration of libvte9: 
 libvte9 depends on libpango1.0-0 (>= 1.22.0); however: 
  Package libpango1.0-0 is not configured yet. 
dpkg: error processing libvte9 (--configure): 
 dependency problems - leaving unconfigured 
No apport report written because MaxReports is reached already 
                                                              dpkg:  dependency problems prevent configuration of python-vte: 
 python-vte depends on libpango1.0-0 (>= 1.22.0); however: 
  Package libpango1.0-0 is not configured yet. 
 python-vte depends on libvte9 (>= 1:0.22.0); however: 
  Package libvte9 is not configured yet. 
 python-vte depends on python-gtk2; however: 
  Package python-gtk2 is not configured yet. 
dpkg: error processing python-vte (--configure): 
 dependency problems - leaving unconfigured 
No apport report written because MaxReports is reached already 
                                                              dpkg:  dependency problems prevent configuration of synaptic: 
 synaptic depends on libglade2-0 (>= 1:2.6.1); however: 
  Package libglade2-0 is not configured yet. 
 synaptic depends on libpango1.0-0 (>= 1.14.0); however: 
  Package libpango1.0-0 is not configured yet. 
 synaptic depends on libvte9 (>= 1:0.22.0); however: 
  Package libvte9 is not configured yet. 
dpkg: error processing synaptic (--configure): 
 dependency problems - leaving unconfigured 
No apport report written because MaxReports is reached already 
                                                              dpkg:  dependency problems prevent configuration of software-properties-gtk: 
 software-properties-gtk depends on synaptic (>= 0.57.8); however: 
  Package synaptic is not configured yet. 
 software-properties-gtk depends on gksu; however: 
  Package gksu is not configured yet. 
 software-properties-gtk depends on python-glade2; however: 
  Package python-glade2 is not configured yet. 
 software-properties-gtk depends on python-gtk2; however: 
  Package python-gtk2 is not configured yet. 
dpkg: error processing software-properties-gtk (--configure): 
 dependency problems - leaving unconfigured 
No apport report written because MaxReports is reached already 
                                                              dpkg:  dependency problems prevent configuration of apturl: 
 apturl depends on gksu (>= 2.0.0-1ubuntu3); however: 
  Package gksu is not configured yet. 
 apturl depends on gnome-icon-theme (>= 2.14.0-1); however: 
  Package gnome-icon-theme is not configured yet. 
 apturl depends on python-glade2 (>= 2.6.3-2); however: 
  Package python-glade2 is not configured yet. 
 apturl depends on python-gtk2 (>= 2.6.3-2); however: 
  Package python-gtk2 is not configured yet. 
 apturl depends on python-webkit; however: 
  Package python-webkit is not configured yet. 
 apturl depends on python-vte (>= 1:0.11.15-4); however: 
  Package python-vte is not configured yet. 
 apturl depends on software-properties-gtk; however: 
  Package software-properties-gtk is not configured yet. 
 apturl depends on synaptic; however: 
  Package synaptic is not configured yet. 
dpkg: error processing apturl (--configure): 
 dependency problems - leaving unconfigured 
No apport report written because MaxReports is reached already 
                                                              dpkg:  dependency problems prevent configuration of at-spi: 
 at-spi depends on libpango1.0-0 (>= 1.14.0); however: 
  Package libpango1.0-0 is not configured yet. 
dpkg: error processing at-spi (--configure): 
 dependency problems - leaving unconfigured 
No apport report written because MaxReports is reached already 
                                                              dpkg:  dependency problems prevent configuration of libbrasero-media0: 
 libbrasero-media0 depends on libcanberra-gtk0 (>= 0.2); however: 
  Package libcanberra-gtk0 is not configured yet. 
 libbrasero-media0 depends on libpango1.0-0 (>= 1.14.0); however: 
  Package libpango1.0-0 is not configured yet. 
dpkg: error processing libbrasero-media0 (--configure): 
 dependency problems - leaving unconfigured 
dpkg: too many errors, stopping 
No apport report written because MaxReports is reached already 
                                                              Errors  were encountered while processing: 
 libpango1.0-common 
 libpango1.0-0 
 libglade2-0 
 libgnomecanvas2-0 
 libbonoboui2-0 
 libgucharmap7 
 libpanel-applet2-0 
 libwnck22 
 libcanberra-gtk0 
 libedataserverui1.2-8 
 librsvg2-2 
 libgnomekbd4 
 libmetacity-private0 
 gnome-settings-daemon 
 python-gtk2 
 python-gmenu 
 gnome-menus 
 librsvg2-common 
 gnome-icon-theme 
 gnome-control-center 
 python-gnomecanvas 
 libgnomeui-0 
 python-gnome2 
 gnome-about 
 gnome-panel 
 gnome-applets 
 ttf-sazanami-gothic 
 ttf-sazanami-mincho 
 xulrunner-1.9.2 
 yelp 
 gnome-user-guide 
 ubuntu-docs 
 adobe-flashplugin 
 gnome-games-common 
 aisleriot 
 alacarte 
 apport-gtk 
 libgksu2-0 
 libgcr0 
 gnome-keyring 
 gksu 
 python-glade2 
 libwebkit-1.0-2 
 python-webkit 
 libvte9 
 python-vte 
 synaptic 
 software-properties-gtk 
 apturl 
 at-spi 
 libbrasero-media0 
Processing was halted because there were too many errors. 
E: Sub-process /usr/bin/dpkg returned an error code (1) 
virginia@virginia:~$

---

### Post by oldos2er on 2010-11-22
First of all I would run **sudo apt-get autoremove** like it's telling you. You might want to check your sources (/etc/apt/sources.list, and anything in /etc/apt/sources.list.d) and make sure there aren't any references to any version except Lucid.

---

### Post by gaines2166 on 2010-11-22
> **sikander3786 said:**
> If you prefer not to re-install, these commands might help.

```
sudo apt-get install -f
``````
sudo dpkg --configure -a
```And if successful,

```
sudo apt-get update && sudo apt-get upgrade
```Please post the output if you plan to go this way :-)

When I began trying your suggested commands, I didn't realize I needed apparently to be using the root terminal (actually, I had been wondering what the root terminal was for, as I had only noticed it recently).

I tried the commands in root, and got a much more encouraging result (but unfortunately, I didn't set the lines to unlimited, so only the last 512 are below).

I rebooted and so far it seems to be running normally.  I installed gthumb using Synaptic, and didn't get any error messages.

I do notice though that the size of "home" appears to have doubled to 39GB (it was at 19GB when I made a backup before trying the suggestions).  Any thoughts about the current size?

Again, thanks for you help!

Here's where the terminal output started:
Setting up xfonts-100dpi (1:1.0.1) ...
 
Setting up xfonts-75dpi (1:1.0.1) ...
 
Setting up xfonts-base (1:1.0.1) ...
 
Setting up xfonts-scalable (1:1.0.1-1) ...
 
Setting up xorg-docs-core (1:1.5-1) ...
Setting up xterm (256-1ubuntu1) ...
Installing new version of config file /etc/X11/app-defaults/KOI8RXTerm ...
Installing new version of config file /etc/X11/app-defaults/UXTerm ...
Installing new version of config file /etc/X11/app-defaults/XTerm ...
Installing new version of config file /etc/X11/app-defaults/XTerm-color ...
 
Setting up xscreensaver-gl (5.10-3ubuntu4) ...
Installing new version of config file 
/etc/X11/app-defaults/XScreenSaver-gl ...
 
Setting up xsplash (0.8.5-0ubuntu2) ...
Setting up acroread (9.4-1lucid1) ...
No LSB modules are available.
No LSB modules are available.
 
Setting up cups-bsd (1.4.3-1ubuntu1.3) ...
 
Setting up dcraw (8.86-1build1) ...
Setting up festvox-kallpc16k (1.4.0-5) ...
Setting up fglrx-modaliases (2:8.723.1-0ubuntu5) ...
Setting up inputattach (20051019-9) ...
Setting up libprotoc5 (2.2.0a-0.1ubuntu1) ...
 
Setting up protobuf-compiler (2.2.0a-0.1ubuntu1) ...
Setting up python-gtkglext1 (1.1.0-4) ...
 
Setting up xfonts-mathml (4ubuntu1) ...
 
Processing triggers for python-central ...
Setting up apturl (0.4.1ubuntu4) ...
 
Setting up gnome-codec-install (0.4.2ubuntu2) ...
 
Setting up onboard (0.93.0-0ubuntu4) ...
 
Setting up python-farsight (0.0.17-2ubuntu2) ...
Setting up python-papyon (0.4.8-0ubuntu2) ...
 
Setting up python-twisted-names (10.0.0-1) ...
 
Setting up python-twisted-web (10.0.0-1) ...
 
Setting up python-ubuntuone-storageprotocol (1.2.0-0ubuntu1) ...
 
Setting up software-center (2.0.7) ...
 
Setting up telepathy-butterfly (0.5.11-0ubuntu1) ...
 
Setting up totem-plugins (2.30.2-0ubuntu1) ...
 
Setting up update-notifier (0.99.3) ...
Installing new version of config file 
/etc/xdg/autostart/update-notifier.desktop ...
 
Processing triggers for python-central ...
Setting up python-ubuntuone-client (1.2.2-0ubuntu2) ...
Installing new version of config file /etc/xdg/ubuntuone/syncdaemon.conf ...
Installing new version of config file 
/etc/xdg/ubuntuone/oauth_registration.d/ubuntuone ...
 
Setting up ubufox (0.9~rc2-0ubuntu2.1) ...
 
Processing triggers for python-central ...
Setting up ubuntuone-client (1.2.2-0ubuntu2) ...
Setting up ubuntuone-client-gnome (1.2.2-0ubuntu2) ...
Setting up xserver-xorg-core (2:1.7.6-2ubuntu7.4) ...
 
Setting up foomatic-db-engine (4.0.4-0ubuntu1) ...
 
Setting up foomatic-db (20100216-0ubuntu3) ...
 
Setting up gamin (0.1.10-1ubuntu3) ...
Setting up kdelibs-bin (4:4.4.2-0ubuntu4) ...
Setting up language-pack-en (1:10.04+20100714) ...
Setting up language-pack-en-base (1:10.04+20100714) ...
Generating locales...
   en_AG.UTF-8... up-to-date
   en_AU.UTF-8... up-to-date
   en_BW.UTF-8... up-to-date
   en_CA.UTF-8... up-to-date
   en_DK.UTF-8... up-to-date
   en_GB.UTF-8... up-to-date
   en_HK.UTF-8... up-to-date
   en_IE.UTF-8... up-to-date
   en_IN.UTF-8... up-to-date
   en_NG.UTF-8... up-to-date
   en_NZ.UTF-8... up-to-date
   en_PH.UTF-8... up-to-date
   en_SG.UTF-8... up-to-date
   en_US.UTF-8... up-to-date
   en_ZA.UTF-8... up-to-date
   en_ZW.UTF-8... up-to-date
Generation complete.
 
Setting up console-setup (1.34ubuntu15) ...
Your console font configuration will be updated the next time your system
boots. If you want to update it now, run 'setupcon' from a virtual console.
update-initramfs: deferring update (trigger activated)
 
Setting up kbd (1.15-1ubuntu3) ...
update-initramfs: deferring update (trigger activated)
 
Setting up tasksel-data (2.73ubuntu26) ...
Setting up desktopcouch (0.6.4-0ubuntu3.1) ...
Setting up python-desktopcouch (0.6.4-0ubuntu3.1) ...
 
Setting up odbcinst (2.2.11-21) ...
Setting up mono-2.0-gac (2.4.4~svn151842-1ubuntu4) ...
Setting up mono-gac (2.4.4~svn151842-1ubuntu4) ...
* Installing 6 assemblies from libart2.0-cil into Mono
* Installing 1 assembly from libavahi1.0-cil into Mono
* Installing 1 assembly from libflickrnet2.2-cil into Mono
* Installing 6 assemblies from libgconf2.0-cil into Mono
* Installing 1 assembly from libglade2.0-cil into Mono
* Installing 1 assembly from libglib2.0-cil into Mono
* Installing 1 assembly from libgmime2.2a-cil into Mono
* Installing 1 assembly from libgmime2.4-cil into Mono
* Installing 2 assemblies from libgnome2.24-cil into Mono
* Installing 1 assembly from libgnome-keyring1.0-cil into Mono
* Installing 1 assembly from libgnomepanel2.24-cil into Mono
* Installing 6 assemblies from libgnome-vfs2.0-cil into Mono
* Installing 5 assemblies from libgtk2.0-cil into Mono
* Installing 1 assembly from liblaunchpad-integration1.0-cil into Mono
* Installing 7 assemblies from libmono-addins0.2-cil into Mono
* Installing 3 assemblies from libmono-addins-gui0.2-cil into Mono
* Installing 1 assembly from libndesk-dbus1.0-cil into Mono
* Installing 1 assembly from libndesk-dbus-glib1.0-cil into Mono
* Installing 6 assemblies from libnunit2.4-cil into Mono
 
Setting up mono-runtime (2.4.4~svn151842-1ubuntu4) ...
Installing new version of config file /etc/mono/config ...
Installing new version of config file /etc/mono/2.0/machine.config ...
Installing new version of config file 
/etc/mono/2.0/DefaultWsdlHelpGenerator.aspx ...
update-binfmts: warning: current package is mono-runtime , but binary format
already installed by mono-common
 
Setting up libmono-corlib2.0-cil (2.4.4~svn151842-1ubuntu4) ...
Setting up libmono-cairo2.0-cil (2.4.4~svn151842-1ubuntu4) ...
Setting up firefox-branding (3.6.12+build1+nobinonly-0ubuntu0.10.04.1) ...
Setting up libmono-i18n-west2.0-cil (2.4.4~svn151842-1ubuntu4) ...
Setting up libmono-i18n2.0-cil (2.4.4~svn151842-1ubuntu4) ...
Setting up xserver-xorg-video-apm (1:1.2.2-1) ...
Setting up xserver-xorg-video-ark (1:0.7.2-1) ...
Setting up xserver-xorg-video-r128 (6.8.1-2ubuntu1) ...
Setting up xserver-xorg-video-mach64 (6.8.2-2) ...
Setting up xserver-xorg-video-radeon (1:6.13.0-1ubuntu5) ...
 
Setting up xserver-xorg-video-ati (1:6.13.0-1ubuntu5) ...
Setting up xserver-xorg-video-chips (1:1.2.2-1) ...
Setting up xserver-xorg-video-cirrus (1:1.3.2-1ubuntu1) ...
Setting up xserver-xorg-video-fbdev (1:0.4.1-1ubuntu1) ...
Setting up xserver-xorg-video-geode (2.11.8-4) ...
Setting up xserver-xorg-video-i128 (1:1.3.3-1) ...
Setting up xserver-xorg-video-i740 (1:1.3.2-1) ...
Setting up xserver-xorg-video-intel (2:2.9.1-3ubuntu5) ...
 
Setting up xserver-xorg-video-mga (1:1.4.11.dfsg-2ubuntu1) ...
Setting up xserver-xorg-video-neomagic (1:1.2.4-2) ...
Setting up xserver-xorg-video-nouveau 
(1:0.0.15+git20100219+9b4118d-0ubuntu5) ...
Setting up xserver-xorg-video-nv (1:2.1.15-1ubuntu3) ...
Setting up xserver-xorg-video-rendition (1:4.2.3-1) ...
Setting up xserver-xorg-video-s3 (1:0.6.3-1) ...
Setting up xserver-xorg-video-s3virge (1:1.10.4-1) ...
Setting up xserver-xorg-video-savage (1:2.3.1-1ubuntu1) ...
Setting up xserver-xorg-video-siliconmotion (1:1.7.3-1) ...
Setting up xserver-xorg-video-sis (1:0.10.2-2) ...
Setting up xserver-xorg-video-sisusb (1:0.9.3-1) ...
Setting up xserver-xorg-video-tdfx (1:1.4.3-1) ...
Setting up xserver-xorg-video-trident (1:1.3.3-1) ...
Setting up xserver-xorg-video-tseng (1:1.2.3-1) ...
Setting up xserver-xorg-video-vesa (1:2.3.0-1ubuntu1) ...
Setting up xserver-xorg-video-openchrome (1:0.2.904+svn827-1) ...
 
Setting up xserver-xorg-video-voodoo (1:1.2.3-1) ...
Setting up xserver-xorg-video-vmware (1:10.16.9-1) ...
Setting up xserver-xorg-video-v4l (1:0.2.0-4) ...
Setting up xserver-xorg-video-all (1:7.5+5ubuntu1) ...
Setting up xserver-xorg-input-evdev (1:2.3.2-5ubuntu1) ...
Setting up xserver-xorg-input-synaptics (1.2.2-1ubuntu4) ...
 
Setting up xserver-xorg-input-mouse (1:1.5.0-1) ...
Setting up xserver-xorg-input-vmmouse (1:12.6.5-4ubuntu2) ...
 
Setting up xserver-xorg-input-wacom (1:0.10.5-0ubuntu4) ...
 
Setting up xserver-xorg-input-all (1:7.5+5ubuntu1) ...
Setting up xserver-xorg (1:7.5+5ubuntu1) ...
 
Setting up xorg (1:7.5+5ubuntu1) ...
Setting up libgamin0 (0.1.10-1ubuntu3) ...
 
Setting up libgnomevfs2-0 (1:2.24.2-1ubuntu2) ...
 
Setting up libgnome2-0 (2.30.0-0ubuntu1) ...
 
Setting up libbonoboui2-0 (2.24.3-0ubuntu1) ...
 
Setting up libpanel-applet2-0 (1:2.30.2-0ubuntu0.2) ...
 
Setting up libgnomeui-0 (2.24.3-1) ...
 
Setting up python-gnome2 (2.28.0-1ubuntu1) ...
 
Setting up gnome-about (1:2.30.2-0ubuntu1) ...
Setting up gnome-panel (1:2.30.2-0ubuntu0.2) ...
Installing new version of config file 
/etc/xdg/autostart/indicator-applet.desktop ...
 
Setting up gnome-applets (2.30.0-0ubuntu2) ...
 
Setting up kdelibs5 (4:4.4.2-0ubuntu4) ...
 
Setting up tasksel (2.73ubuntu26) ...
 
Setting up ubuntu-minimal (1.197) ...
Setting up odbcinst1debian1 (2.2.11-21) ...
 
Setting up unixodbc (2.2.11-21) ...
 
Setting up libpt2.6.5 (2.6.5-1ubuntu1) ...
 
Setting up libopal3.6.6 (3.6.6~dfsg-4ubuntu1) ...
 
Setting up libpt2.6.5-plugins (2.6.5-1ubuntu1) ...
Setting up ekiga (3.2.6-1ubuntu1) ...
 
Setting up libgnome-pilot2 (2.0.17-0ubuntu5) ...
 
Setting up liblpint-bonobo0 (0.1.35) ...
 
Setting up evolution (2.28.3-0ubuntu10) ...
Installing new version of config file 
/etc/xdg/autostart/evolution-alarm-notify.desktop ...
 
Setting up evolution-couchdb (0.4.5-0ubuntu1) ...
Setting up evolution-exchange (2.28.3-0ubuntu1) ...
 
Setting up evolution-plugins (2.28.3-0ubuntu10) ...
Setting up libmono-system2.0-cil (2.4.4~svn151842-1ubuntu4) ...
Setting up libmono-security2.0-cil (2.4.4~svn151842-1ubuntu4) ...
Setting up libmono-data-tds2.0-cil (2.4.4~svn151842-1ubuntu4) ...
Setting up libmono-system-data2.0-cil (2.4.4~svn151842-1ubuntu4) ...
Setting up libmono-sqlite2.0-cil (2.4.4~svn151842-1ubuntu4) ...
Setting up libmono-posix2.0-cil (2.4.4~svn151842-1ubuntu4) ...
Setting up libmono-sharpzip2.84-cil (2.4.4~svn151842-1ubuntu4) ...
Setting up libmono2.0-cil (2.4.4~svn151842-1ubuntu4) ...
Setting up libglib2.0-cil (2.12.9-4) ...
* Installing 1 assembly from libglib2.0-cil into Mono
 
Setting up libgconf2.0-cil (2.24.1-6ubuntu1) ...
* Installing 6 assemblies from libgconf2.0-cil into Mono
 
Setting up libgtk2.0-cil (2.12.9-4) ...
* Installing 5 assemblies from libgtk2.0-cil into Mono
 
Setting up libglade2.0-cil (2.12.9-4) ...
* Installing 1 assembly from libglade2.0-cil into Mono
 
Setting up libgnome-keyring1.0-cil (1.0.0-3) ...
* Installing 1 assembly from libgnome-keyring1.0-cil into Mono
 
Setting up libgnome-vfs2.0-cil (2.24.1-6ubuntu1) ...
* Installing 6 assemblies from libgnome-vfs2.0-cil into Mono
 
Setting up libart2.0-cil (2.24.1-6ubuntu1) ...
* Installing 6 assemblies from libart2.0-cil into Mono
 
Setting up libgnome2.24-cil (2.24.1-6ubuntu1) ...
* Installing 2 assemblies from libgnome2.24-cil into Mono
 
Setting up libmono-addins0.2-cil (0.4-6) ...
* Installing 7 assemblies from libmono-addins0.2-cil into Mono
 
Setting up libmono-addins-gui0.2-cil (0.4-6) ...
* Installing 3 assemblies from libmono-addins-gui0.2-cil into Mono
 
Setting up libndesk-dbus1.0-cil (0.6.0-4) ...
* Installing 1 assembly from libndesk-dbus1.0-cil into Mono
 
Setting up libndesk-dbus-glib1.0-cil (0.4.1-3) ...
* Installing 1 assembly from libndesk-dbus-glib1.0-cil into Mono
 
Setting up firefox (3.6.12+build1+nobinonly-0ubuntu0.10.04.1) ...
Installing new version of config file /etc/apparmor.d/usr.bin.firefox ...
Installing new version of config file /etc/firefox/pref/firefox.js ...
Please restart all running instances of firefox, or you will experience 
problems.
 
Setting up firefox-gnome-support 
(3.6.12+build1+nobinonly-0ubuntu0.10.04.1) ...
update-alternatives: using /usr/bin/firefox to provide 
/usr/bin/gnome-www-browser (gnome-www-browser) in auto mode.
 
Setting up libplasma3 (4:4.4.2-0ubuntu4) ...
 
Setting up plasma-scriptengine-javascript (4:4.4.2-0ubuntu4.1) ...
Setting up kdepimlibs5 (4:4.4.2-0ubuntu2.1) ...
 
Setting up python-gnomeapplet (2.30.0-0ubuntu1) ...
 
Setting up gnome-mag (1:0.16.1-0ubuntu1) ...
Setting up python-pyatspi (1.30.1-0ubuntu1) ...
 
Setting up gnome-utils (2.30.0-0ubuntu1) ...
 
Setting up libavahi1.0-cil (0.6.19-4.1) ...
* Installing 1 assembly from libavahi1.0-cil into Mono
 
Setting up gshare (0.94-10) ...
 
Setting up gstreamer0.10-gnomevfs (0.10.28-1) ...
Setting up libkfontinst4 (4:4.4.2-0ubuntu14) ...
 
Setting up libkscreensaver5 (4:4.4.2-0ubuntu14) ...
 
Setting up libkworkspace4 (4:4.4.2-0ubuntu14) ...
 
Setting up libplasmagenericshell4 (4:4.4.2-0ubuntu14) ...
 
Setting up libprocesscore4 (4:4.4.2-0ubuntu14) ...
 
Setting up libprocessui4 (4:4.4.2-0ubuntu14) ...
 
Setting up libsolidcontrol4 (4:4.4.2-0ubuntu14) ...
 
Setting up libplasma-applet-system-monitor4 (4:4.4.2-0ubuntu14) ...
 
Setting up libplasmaclock4 (4:4.4.2-0ubuntu14) ...
 
Setting up libksgrd4 (4:4.4.2-0ubuntu14) ...
 
Setting up libtaskmanager4 (4:4.4.2-0ubuntu14) ...
 
Setting up libweather-ion4 (4:4.4.2-0ubuntu14) ...
 
Setting up liblsofui4 (4:4.4.2-0ubuntu14) ...
 
Setting up libksignalplotter4 (4:4.4.2-0ubuntu14) ...
 
Setting up kdebase-workspace-libs4+5 (4:4.4.2-0ubuntu14) ...
Setting up libgail-gnome-module (1.20.1-2) ...
Setting up libgmime2.2a-cil (2.2.22-5) ...
* Installing 1 assembly from libgmime2.2a-cil into Mono
 
Setting up libgmime2.4-cil (2.4.14-1+nmu1) ...
* Installing 1 assembly from libgmime2.4-cil into Mono
 
Setting up libgnome2-vfs-perl (1.081-1build1) ...
Setting up libgnome2-perl (1.042-2build1) ...
Setting up libgnomepanel2.24-cil (2.26.0-2ubuntu1) ...
* Installing 1 assembly from libgnomepanel2.24-cil into Mono
 
Setting up libgnomevfs2-bin (1:2.24.2-1ubuntu2) ...
Setting up liblaunchpad-integration1.0-cil (0.1.35) ...
* Installing 1 assembly from liblaunchpad-integration1.0-cil into Mono
 
Setting up libmono-data2.0-cil (2.4.4~svn151842-1ubuntu4) ...
Setting up libmono-getoptions2.0-cil (2.4.4~svn151842-1ubuntu4) ...
Setting up mousetweaks (2.30.0-0ubuntu1) ...
 
Setting up nautilus-share (0.7.2-12build1) ...
Setting up pessulus (2.30.0-1) ...
 
Setting up pybackpack (0.5.8-1) ...
 
Setting up python-gamin (0.1.10-1ubuntu3) ...
 
Setting up python-gnome2-desktop (2.30.0-0ubuntu1) ...
Setting up rhythmbox (0.12.8-0ubuntu7) ...
 
Setting up rhythmbox-plugin-cdrecorder (0.12.8-0ubuntu7) ...
Setting up rhythmbox-plugins (0.12.8-0ubuntu7) ...
 
Setting up seahorse-plugins (2.30.0-0ubuntu2) ...
Installing new version of config file 
/etc/X11/Xsession.d/60seahorse-plugins ...
 
Setting up system-config-printer-gnome (1.2.0+20100408-0ubuntu5.2) ...
Installing new version of config file 
/etc/xdg/autostart/print-applet.desktop ...
 
Setting up tomboy (1.2.1-0ubuntu1) ...
 
Setting up tsclient (0.150-3ubuntu1) ...
 
Setting up vinagre (2.30.2-0ubuntu1) ...
 
Setting up evolution-indicator (0.2.8-0ubuntu1) ...
 
Setting up gnome-pilot (2.0.17-0ubuntu5) ...
 
Setting up libmono-system-web2.0-cil (2.4.4~svn151842-1ubuntu4) ...
Setting up libflickrnet2.2-cil (1:2.2.0-3) ...
* Installing 1 assembly from libflickrnet2.2-cil into Mono
 
Setting up libmono-system-runtime2.0-cil (2.4.4~svn151842-1ubuntu4) ...
Setting up libnunit2.4-cil (2.4.7+dfsg-5) ...
* Installing 6 assemblies from libnunit2.4-cil into Mono
 
Setting up f-spot (0.6.1.5-2ubuntu7) ...
 
Setting up kdebase-runtime (4:4.4.2-0ubuntu4.1) ...
 
Setting up python-kde4 (4:4.4.2-0ubuntu2) ...
 
Setting up kdesudo (3.4.2.3-0ubuntu1) ...
update-alternatives: using /usr/bin/kdesudo to provide 
/usr/lib/kde4/libexec/kdesu (kdesu) in auto mode.
 
Setting up gdebi-kde (0.6.0ubuntu2) ...
 
Setting up libkcddb4 (4:4.4.2-0ubuntu3) ...
 
Setting up libk3b6 (1.91.0~rc2-0ubuntu3) ...
 
Setting up polkit-kde-1 (0.95.1-2ubuntu1) ...
Setting up k3b (1.91.0~rc2-0ubuntu3) ...
 
Setting up kdebase-runtime-bin-kde4 (4:4.4.2-0ubuntu4.1) ...
Setting up plasma-dataengines-workspace (4:4.4.2-0ubuntu14) ...
Setting up kdepim-runtime (4:4.4.2-0ubuntu1) ...
 
Setting up plasma-widgets-workspace (4:4.4.2-0ubuntu14) ...
Setting up kdebase-workspace-data (4:4.4.2-0ubuntu14) ...
Setting up kdebase-workspace-kgreet-plugins (4:4.4.2-0ubuntu14) ...
Setting up kdebase-workspace-bin (4:4.4.2-0ubuntu14) ...
 
Setting up khelpcenter4 (4:4.4.2-0ubuntu4.1) ...
Setting up update-manager-kde (1:0.134.11) ...
 
Processing triggers for python-central ...
Setting up sabayon (2.29.5-0ubuntu1) ...
 
Setting up python-desktopcouch-records (0.6.4-0ubuntu3.1) ...
 
Setting up gnome-orca (2.30.2-0ubuntu1) ...
 
Setting up install-package (0.5.2) ...
Setting up software-properties-kde (0.75.10.1) ...
 
Processing triggers for python-central ...
Setting up kpackagekit (0.5.4-0ubuntu4.3) ...
Setting up kubuntu-debug-installer (10.04ubuntu4) ...
Processing triggers for menu ...
Setting up sbackup (0.10.5ubuntu2.1) ...
 
Processing triggers for python-gmenu ...
Rebuilding /usr/share/applications/desktop.en_US.utf8.cache...
Setting up language-pack-gnome-en (1:10.04+20100714) ...
Setting up language-pack-gnome-en-base (1:10.04+20100714) ...
 
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
Processing triggers for python-support ...
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-2.6.32-25-generic
Processing triggers for menu ...
Processing triggers for python-gmenu ...
Rebuilding /usr/share/applications/desktop.en_US.utf8.cache...
Processing triggers for python-support ...
root@virginia:/home/virginia# sudo apt-get update
Hit [http://archive.canonical.com]("http://archive.canonical.com/") lucid Release.gpg
Ign [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) lucid/partner Translation-en_US
Hit [http://security.ubuntu.com]("http://security.ubuntu.com/") lucid-security Release.gpg
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/main Translation-en_US
Hit [http://archive.canonical.com]("http://archive.canonical.com/") lucid Release
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/restricted 
Translation-en_US
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/universe 
Translation-en_US
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/multiverse 
Translation-en_US
Hit [http://security.ubuntu.com]("http://security.ubuntu.com/") lucid-security Release
Hit [http://archive.canonical.com]("http://archive.canonical.com/") lucid/partner Packages
Hit [http://security.ubuntu.com]("http://security.ubuntu.com/") lucid-security/main Packages
Hit [http://security.ubuntu.com]("http://security.ubuntu.com/") lucid-security/restricted Packages
Hit [http://security.ubuntu.com]("http://security.ubuntu.com/") lucid-security/main Sources
Hit [http://security.ubuntu.com]("http://security.ubuntu.com/") lucid-security/restricted Sources
Hit [http://security.ubuntu.com]("http://security.ubuntu.com/") lucid-security/universe Packages
Hit [http://security.ubuntu.com]("http://security.ubuntu.com/") lucid-security/universe Sources
Hit [http://security.ubuntu.com]("http://security.ubuntu.com/") lucid-security/multiverse Packages
Hit [http://security.ubuntu.com]("http://security.ubuntu.com/") lucid-security/multiverse Sources
Hit [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") lucid Release.gpg
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/main Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/universe Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/multiverse Translation-en_US
Hit [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") lucid-updates Release.gpg
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates/main 
Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates/restricted 
Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates/universe 
Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates/multiverse 
Translation-en_US
Hit [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") lucid Release
Hit [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") lucid-updates Release
Hit [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") lucid/main Packages
Hit [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") lucid/restricted Packages
Hit [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") lucid/main Sources
Hit [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") lucid/restricted Sources
Hit [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") lucid/universe Packages
Hit [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") lucid/universe Sources
Hit [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") lucid/multiverse Packages
Hit [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") lucid/multiverse Sources
Hit [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") lucid-updates/main Packages
Hit [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") lucid-updates/restricted Packages
Hit [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") lucid-updates/main Sources
Hit [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") lucid-updates/restricted Sources
Hit [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") lucid-updates/universe Packages
Hit [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") lucid-updates/universe Sources
Hit [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") lucid-updates/multiverse Packages
Hit [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") lucid-updates/multiverse Sources
Reading package lists... Done
root@virginia:/home/virginia# sudo apt-get upgrade
Reading package lists... Done
Building dependency tree
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
root@virginia:/home/virginia#

---

### Post by sikander3786 on 2010-11-23
The sudo command gives you root access so you don't need to be in a root teminal to do them.

Glad to know it is all working now.

> I do notice though that the size of "home" appears to have doubled to 39GB (it was at 19GB when I made a backup before trying the suggestions). Any thoughts about the current size?

I don't think if that should have grown double in size by these commands. You can check in your home folder for anything that is taking more space than you feel it should. Press Ctrl + H to see the hidden files.

Might be you recently saved some personal files to that folder....

And apt-get autoremove will also help you remove the un-needed packages and free up some space. However that is not related to /home.

---

