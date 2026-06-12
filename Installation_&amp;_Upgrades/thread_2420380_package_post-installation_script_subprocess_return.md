---
title: "package post-installation script subprocess returned error exit status 1&quot;"
date: 2019-06-04
forum: Installation &amp; Upgrades
---

### Post by katmcg on 2019-06-04
**Environment**


* Python version: 3.5 
* OS: Ubuntu 18.04




**Description**
Recently switched from python3.6 to python3.5 in order to use tensorflow. and some issues started to present themselves before the switch 
i.e. 


```

Could not find platform independent libraries <prefix>
Could not find platform dependent libraries <exec_prefix>
Consider setting $PYTHONHOME to <prefix>[:<exec_prefix>]
ImportError: No module named site

```
and 
```

  File "/usr/local/lib/python3.5/site.py", line 176
    file=sys.stderr)
        ^
SyntaxError: invalid syntax

```


and now neither pip or pip3 works on my computer. Therefore I decided to remove both pip3 and pip from my computer. However pip will not uninstall! The following error occurs when I try: ` sudo apt remove python-pip`


```

Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  apt-clone archdetect-deb busybox-static cryptsetup-bin
  dpkg-repack gir1.2-timezonemap-1.0 gir1.2-xkl-1.0 grub-common
  kde-window-manager kinit kio kpackagetool5 kwayland-data
  kwin-common kwin-data kwin-x11 libdebian-installer4
  libkdecorations2-5v5 libkdecorations2private5v5
  libkf5activities5 libkf5attica5 libkf5completion-data
  libkf5completion5 libkf5declarative-data libkf5declarative5
  libkf5doctools5 libkf5globalaccel-data libkf5globalaccel5
  libkf5globalaccelprivate5 libkf5idletime5
  libkf5jobwidgets-data libkf5jobwidgets5 libkf5kcmutils-data
  libkf5kcmutils5 libkf5kiocore5 libkf5kiontlm5
  libkf5kiowidgets5 libkf5newstuff-data libkf5newstuff5
  libkf5newstuffcore5 libkf5package-data libkf5package5
  libkf5plasma5 libkf5quickaddons5 libkf5solid5
  libkf5solid5-data libkf5sonnet5-data libkf5sonnetcore5
  libkf5sonnetui5 libkf5textwidgets-data libkf5textwidgets5
  libkf5waylandclient5 libkf5waylandserver5 libkf5xmlgui-bin
  libkf5xmlgui-data libkf5xmlgui5 libkscreenlocker5
  libkwin4-effect-builtins1 libkwineffects11 libkwinglutils11
  libkwinxrenderutils11 libpython-all-dev libqgsttools-p1
  libqt5multimedia5 libqt5multimedia5-plugins
  libqt5multimediaquick-p5 libqt5multimediawidgets5
  libqt5opengl5 libxcb-composite0 libxcb-cursor0 libxcb-damage0
  os-prober python-all python-all-dev python-asn1crypto
  python-cffi-backend python-crypto python-cryptography
  python-enum34 python-idna python-ipaddress python-keyring
  python-keyrings.alt python-secretstorage python-wheel
  python-xdg python3-dbus.mainloop.pyqt5 python3-icu python3-pam
  python3-pyqt5 python3-pyqt5.qtsvg python3-pyqt5.qtwebkit
  qml-module-org-kde-kquickcontrolsaddons
  qml-module-qtmultimedia rdate
Use 'sudo apt autoremove' to remove them.
The following packages will be REMOVED:
  python-pip
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 671 kB disk space will be freed.
Do you want to continue? [Y/n] y
(Reading database ... 158779 files and directories currently installed.)
Removing python-pip (9.0.1-2.3~ubuntu1) ...
Could not find platform independent libraries <prefix>
Could not find platform dependent libraries <exec_prefix>
Consider setting $PYTHONHOME to <prefix>[:<exec_prefix>]
ImportError: No module named site
dpkg: error processing package python-pip (--remove):
 installed python-pip package pre-removal script subprocess returned error exit status 1
Could not find platform independent libraries <prefix>
Could not find platform dependent libraries <exec_prefix>
Consider setting $PYTHONHOME to <prefix>[:<exec_prefix>]
ImportError: No module named site
dpkg: error while cleaning up:
 installed python-pip package post-installation script subprocess returned error exit status 1
Errors were encountered while processing:
 python-pip
E: Sub-process /usr/bin/dpkg returned an error code (1)

```


Even when trying to remove python3-pip a similar error occurs: 
```

Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  apt-clone archdetect-deb busybox-static cryptsetup-bin
  dpkg-repack gir1.2-timezonemap-1.0 gir1.2-xkl-1.0 grub-common
  kde-window-manager kinit kio kpackagetool5 kwayland-data
  kwin-common kwin-data kwin-x11 libdebian-installer4
  libkdecorations2-5v5 libkdecorations2private5v5
  libkf5activities5 libkf5attica5 libkf5completion-data
  libkf5completion5 libkf5declarative-data libkf5declarative5
  libkf5doctools5 libkf5globalaccel-data libkf5globalaccel5
  libkf5globalaccelprivate5 libkf5idletime5
  libkf5jobwidgets-data libkf5jobwidgets5 libkf5kcmutils-data
  libkf5kcmutils5 libkf5kiocore5 libkf5kiontlm5
  libkf5kiowidgets5 libkf5newstuff-data libkf5newstuff5
  libkf5newstuffcore5 libkf5package-data libkf5package5
  libkf5plasma5 libkf5quickaddons5 libkf5solid5
  libkf5solid5-data libkf5sonnet5-data libkf5sonnetcore5
  libkf5sonnetui5 libkf5textwidgets-data libkf5textwidgets5
  libkf5waylandclient5 libkf5waylandserver5 libkf5xmlgui-bin
  libkf5xmlgui-data libkf5xmlgui5 libkscreenlocker5
  libkwin4-effect-builtins1 libkwineffects11 libkwinglutils11
  libkwinxrenderutils11 libqgsttools-p1 libqt5multimedia5
  libqt5multimedia5-plugins libqt5multimediaquick-p5
  libqt5multimediawidgets5 libqt5opengl5 libxcb-composite0
  libxcb-cursor0 libxcb-damage0 os-prober
  python3-dbus.mainloop.pyqt5 python3-icu python3-pam
  python3-pyqt5 python3-pyqt5.qtsvg python3-pyqt5.qtwebkit
  python3-wheel qml-module-org-kde-kquickcontrolsaddons
  qml-module-qtmultimedia rdate
Use 'sudo apt autoremove' to remove them.
The following packages will be REMOVED:
  python3-pip
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 599 kB disk space will be freed.
Do you want to continue? [Y/n] y
(Reading database ... 158779 files and directories currently installed.)
Removing python3-pip (9.0.1-2.3~ubuntu1) ...
Processing triggers for man-db (2.8.3-2ubuntu0.1) ...
Setting up python-pip (9.0.1-2.3~ubuntu1) ...
Could not find platform independent libraries <prefix>
Could not find platform dependent libraries <exec_prefix>
Consider setting $PYTHONHOME to <prefix>[:<exec_prefix>]
ImportError: No module named site
dpkg: error processing package python-pip (--configure):
 installed python-pip package post-installation script subprocess returned error exit status 1
Errors were encountered while processing:
 python-pip
E: Sub-process /usr/bin/dpkg returned an error code (1)

```




Why won't pip uninstall so I can start fresh and re-install? Is there an error with apt? with dpkg?

---

### Post by Xian on 2019-06-04
See if this tutorial is helpful:

[https://itsfoss.com/dpkg-returned-an-error-code-1]("https://itsfoss.com/dpkg-returned-an-error-code-1/")

If one of the methods does not work then let us know.

---

