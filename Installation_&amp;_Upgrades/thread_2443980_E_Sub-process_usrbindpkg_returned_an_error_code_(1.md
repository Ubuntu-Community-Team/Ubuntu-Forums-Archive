---
title: "E: Sub-process /usr/bin/dpkg returned an error code (1)"
date: 2020-05-22
forum: Installation &amp; Upgrades
---

### Post by richoandika on 2020-05-22
I try to upgrade but i see error dpkg, whats wrong?
```

richoandika@ur:~$ sudo apt update
Get:1 http://dl.google.com/linux/chrome/deb stable InRelease [1.811 B]
Hit:2 http://packages.microsoft.com/repos/vscode stable InRelease              
Hit:3 http://ppa.launchpad.net/bovender/bovender/ubuntu focal InRelease        
Hit:4 http://archive.ubuntu.com/ubuntu focal InRelease                         
Hit:5 http://archive.ubuntu.com/ubuntu focal-updates InRelease           
Hit:6 https://assets.checkra.in/debian  InRelease
Hit:7 http://archive.ubuntu.com/ubuntu focal-backports InRelease
Hit:8 http://archive.ubuntu.com/ubuntu focal-security InRelease
Fetched 1.811 B in 2s (927 B/s)
Reading package lists... Done
Building dependency tree       
Reading state information... Done
All packages are up to date.
richoandika@ur:~$ sudo apt upgrade -y
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt --fix-broken install' to correct these.
The following packages have unmet dependencies:
 indicator-ip : Depends: python-appindicator but it is not installable
                Depends: python-gtk2 but it is not installable
                Depends: python:any (>= 2.7.5-5~)
E: Unmet dependencies. Try 'apt --fix-broken install' with no packages (or specify a solution).
richoandika@ur:~$ sudo apt --fix-broken install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  libappindicator1 libfluidsynth1 libluajit-5.1-2 libluajit-5.1-common
  libmsgpackc2 libnfs12 libpython-all-dev libpython2-dev libpython2.7-dev
  libtermkey1 libunibilium4 libvterm0 lua-luv neovim neovim-runtime python-all
  python-all-dev python-cairo python-cffi-backend python-concurrent.futures
  python-configparser python-crypto python-cryptography python-dbus
  python-entrypoints python-enum34 python-gi python-gobject python-gobject-2
  python-greenlet python-ipaddress python-keyring python-pycodestyle
  python-pysqlite2 python-six python-sqlalchemy python-sqlalchemy-ext
  python-xdg python2-dev python2.7-dev python3-greenlet python3-msgpack
  python3-neovim python3-pynvim xclip
Use 'sudo apt autoremove' to remove them.
The following packages will be REMOVED:
  indicator-ip
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
After this operation, 134 kB disk space will be freed.
Do you want to continue? [Y/n] y
(Reading database ... 311983 files and directories currently installed.)
Removing indicator-ip (2.2.0) ...
/var/lib/dpkg/info/indicator-ip.prerm: 22: indicator-ip: not found
dpkg: error processing package indicator-ip (--remove):
 installed indicator-ip package pre-removal script subprocess returned error exi
t status 127
dpkg: too many errors, stopping
Errors were encountered while processing:
 indicator-ip
Processing was halted because there were too many errors.
E: Sub-process /usr/bin/dpkg returned an error code (1)
richoandika@ur:~$ 

```

---

### Post by DuckHook on 2020-05-23
My guess is that one of your outside repos requires libraries that are incompatible with Focal. Specifically:
```
Hit:2 http://packages.microsoft.com/repos/vscode stable InRelease              
Hit:3 http://ppa.launchpad.net/bovender/bovender/ubuntu focal InRelease
Hit:6 https://assets.checkra.in/debian  InRelease
```
Aside from my standard recommendation that no outside repos be added unless you are an experienced user who knows exactly what you are up to, the clue that you are trying to install obsolete packages is: ```
 indicator-ip : Depends: python-appindicator but it is not installable
                Depends: python-gtk2 but it is not installable
                Depends: python:any (>= 2.7.5-5~)
```
These can't be "fixed". The libraries that they require are either obsolete or, worse, they will conflict with newer libraries and break your main install. Do not try to force this app to work. Attempting to do so will only result in much wailing and gnashing of teeth.

I left the external Chrome repo out of the above list of suspects because I assume that Google would build it to coexist properly with Focal. This is not always a safe assumption. Personally, I refuse to use Chrome, but I do have the FOSS equivalent Chromium installed in a highly contained LXD sandbox.

To solve your problem, uninstall this app and delete its external repo. Then sudo update sudo upgrade and hopefully, you haven't landed in dependency hell.

---

### Post by Impavidus on 2020-05-23
indicator-ip seems to rely on some obsolete packages. apt --fix-broken attempts to remove it, which is probably the right thing to to. When removing it, it begins with running the pre-remove script in /var/lib/dpkg/info/indicator-ip.prerm. This script attemps to run indicator-ip and fails, because the file isn't there. My guess is that this file belongs to the indicator-ip package, which should be reinstalled before it can be cleanly removed. But that leads to a package conflict.

What caused this issue? Have you attempted a release upgrade to 20.04 recently?

---

### Post by richoandika on 2020-05-23
Im using ubuntu 20.04 i just wanna fix that remove indicator-ip and back to normal update, now its solved dude thank for helping

---

