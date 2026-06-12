---
title: "Messed up gnome 3"
date: 2011-09-25
forum: Installation &amp; Upgrades
---

### Post by saviouz on 2011-09-25
Hi guys,
yesterday I tried to install gnome 3, but clearly, I followed the instructions wrong because once I rebooted the computer Ubuntu didn't load, so I loaded the recovery mode and from the terminal I switched back to gnome 2:
```
sudo apt-get install ppa-purge 
sudo ppa-purge ppa:gnome3-team/gnome3
```

but I got a whole lot of warnings, maybe due to the fact that I didn't install gnome 3 right.
Can you suggest me some way to clear everything up and reinstall gnome 3 correctly?

---

### Post by saviouz on 2011-09-25
Also, when I try to install a package from terminal that's what it comes up:
```
Setting up gnome-icon-theme (2.31.0-0ubuntu2) ...
update-alternatives: error: alternative path /usr/share/icons/gnome/scalable/places/ubuntu-logo.svg doesn't exist.
dpkg: error processing gnome-icon-theme (--configure):
 subprocess installed post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of brasero:
 brasero depends on gnome-icon-theme; however:
  Package gnome-icon-theme is not configured yet.
dpkg: error processing brasero (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of empathy:
 empathy depends on gnome-icon-theme (>= 2.30.0); however:
  Package gnome-icon-theme is not configured yet.
dpkg: error processing empathy (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of eog:
 eog depends on gnome-icon-theme (>= 2.19.1); however:
  Package gnome-icon-theme is not configured yet.
dpkg: error processing eog (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of evince:
 evince depends on gnome-icon-theme (>= 2.17.1); however:
  Package gnome-icon-theme is not configured yet.
dpkg: error processing evince (--configure):
 dependency problems - leaving unconfiguNo apport report written because the error message indicates its a followup error from a previous failure.
                                                                  No apport report written because the error message indicates its a followup error from a previous failure.
            No apport report written because MaxReports is reached already
                                                                          No apport report written because MaxReports is reached already
                                                        No apport report written because MaxReports is reached already
                                      No apport report written because MaxReports is reached already
                    No apport report written because MaxReports is reached already
  No apport report written because MaxReports is reached already
                                                                No apport report written because MaxReports is reached already
                                              No apport report written because MaxReports is reached already
                            No apport report written because MaxReports is reached already
          red
dpkg: dependency problems prevent configuration of evolution:
 evolution depends on gnome-icon-theme (>= 2.19.92); however:
  Package gnome-icon-theme is not configured yet.
dpkg: error processing evolution (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of evolution-exchange:
 evolution-exchange depends on evolution (>= 2.32.2); however:
  Package evolution is not configured yet.
 evolution-exchange depends on evolution (<< 2.33.0); however:
  Package evolution is not configured yet.
dpkg: error processing evolution-exchange (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gnome-control-center:
 gnome-control-center depends on gnome-icon-theme (>= 2.24); however:
  Package gnome-icon-theme is not configured yet.
dpkg: error processing gnome-control-center (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gnome-screensaver:
 gnome-screensaver depends on gnome-icon-theme (>= 2.15.90); however:
  Package gnome-icon-theme is not configured yet.
dpkg: error processing gnome-screensaver (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of totem:
 totem depends on gnome-icon-theme (>= 2.15.90); however:
  Package gnome-icon-theme is not configured yet.
dpkg: error processing totem (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of totem-mozilla:
 totem-mozilla depends on totem (= 2.32.0-0ubuntu10); however:
  Package totem is not configured yet.
dpkg: error processing totem-mozilla (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of totem-plugins:
 totem-plugins depends on totem (= 2.32.0-0ubuntu10); however:
  Package totem is not configured yet.
dpkg: error processing totem-plugins (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 gnome-icon-theme
 brasero
 empathy
 eog
 evince
 evolution
 evolution-exchange
 gnome-control-center
 gnome-screensaver
 totem
 totem-mozilla
 totem-plugins
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

I guess it's because of what I did when I tried to install and remove gnome 3. Any idea on how to solve this?

---

### Post by dino99 on 2011-09-25
i suppose you have used some other(s) ppa too, purge it(them)

at least make a fresh install of the system
[http://ubuntuforums.org/showpost.php?p=10161428&postcount=2](http://ubuntuforums.org/showpost.php?p=10161428&postcount=2)

---

