---
title: "libqt5core5 versus libqt5core5a 16.04.3 Darhon Finance"
date: 2017-09-05
forum: Installation &amp; Upgrades
---

### Post by kmkwood on 2017-09-05
I have been running 16.04 for over a year on a Phenom 9750.  After experimentation, I settled on Darhon Finance for my checkbook program, and it does what I want.  I downloaded and installed 16.04.3 onto new hardware last week.  When I tried to install Darhon Finance v1.4.0, I got this message

```

# dpkg -i drfinance_1.4.0_amd64.deb
    Selecting previously unselected package drfinance.
    (Reading database ... 329639 files and directories       currently installed.)
    Preparing to unpack drfinance_1.4.0_amd64.deb ...
    Unpacking drfinance (1.4.0) ...
    dpkg: dependency problems prevent configuration of       drfinance:
     drfinance depends on libqt5core5 (>= 5.0.2); however:
      Package libqt5core5 is not installed.
    
    dpkg: error processing package drfinance (--install):
     dependency problems - leaving unconfigured
    Processing triggers for gnome-menus (3.13.3-6ubuntu3.1) ...
    Processing triggers for desktop-file-utils       (0.22-1ubuntu5.1) ...
    Processing triggers for mime-support (3.59ubuntu1) ...
    Processing triggers for hicolor-icon-theme (0.15-0ubuntu1)       ...
    Errors were encountered while processing:
     drfinance
    #

```

It appears that libqt5core5 has been replaced by libqt5core5a at some point.  I tried symlinking libqt5core5a to libqt5core5, but it didn't resolve the problem.  I contacted the vendor, but they were unable to help.  Source code is not available.  I will have to switch to another checkbook program if I can't get this one to install.  That's a pain, but not the end of the world.

Any suggestions?

---

### Post by kmkwood on 2017-10-06
I switched from drfinance to HomeBank, which has the advantage of running on multiple platforms.

Please close this thread.

---

### Post by oldos2er on 2017-10-08
Closed at your request.

---

