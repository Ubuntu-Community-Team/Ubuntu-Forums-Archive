---
title: "can not upgrade"
date: 2018-07-31
forum: Installation &amp; Upgrades
---

### Post by okkadiroglu on 2018-07-31
Hi,

I am using Ubuntu 18.04LTS, after the most recent upgrade I started to get errors. For a while fligthgear gave error message but few days later I was able to upgrade it. Now when I ran sudo apt full-upgrade I get:

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
35 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Do you want to continue? [Y/n] 
```

If I type y I get a very long list starting with

S```
etting up python3 (3.6.5-3ubuntu1) ...
running python rtupdate hooks for python3.6...
E: py3compile:183: cannot create directory /usr/share/hplip/ui5/__pycache__: FileNotFoundError(2, 'No such file or directory')
[Errno 2] No such file or directory: '/usr/share/hplip/ui5/aboutdialog.py'
[Errno 2] No such file or directory: '/usr/share/hplip/ui5/aboutdialog_base.py'


```
and continuing w&#305;th error messages like

```
dpkg: error processing package python3 (--configure):
 installed python3 package post-installation script subprocess returned error exit status 4
dpkg: dependency problems prevent configuration of python3-update-manager:
 python3-update-manager depends on python3:any (>= 3.3.2-2~); however:
  Package python3 is not configured yet.

```
I can not install or uninstall software or do backups. What is going on? How can I correct this?

Best regards

---

### Post by #&amp;thj^% on 2018-07-31
what dose this produce:
```
sudo apt install -f
```
This is one of the problems so far that I can see:
```
python3-update-manager depends on python3:any (>= 3.3.2-2~); however:
Package python3 is not configured yet.
```

---

### Post by okkadiroglu on 2018-07-31
Thanks for your reply. I ran apt install -f but got the same error messages. I

---

### Post by #&amp;thj^% on 2018-07-31
Please bear with us/me this could get tedious. :)
```
sudo apt-get --reinstall install python3
```

---

### Post by okkadiroglu on 2018-07-31
This is what I get if I want to reinstall a package:

```
python3
installed python3 package post-installation script subprocess returned error exit status 4

python3-update-manager
dependency problems - leaving unconfigured

software-properties-kde
dependency problems - leaving unconfigured

netplan.io
dependency problems - leaving unconfigured

ubuntu-release-upgrader-core
dependency problems - leaving unconfigured

software-properties-gtk
dependency problems - leaving unconfigured

ubuntu-release-upgrader-qt
dependency problems - leaving unconfigured

nplan
dependency problems - leaving unconfigured

unattended-upgrades
dependency problems - leaving unconfigured

update-manager
dependency problems - leaving unconfigured

python3-software-properties
dependency problems - leaving unconfigured

python3-dbg
dependency problems - leaving unconfigured

gnome-menus
dependency problems - leaving triggers unprocessed

python3-distupgrade
dependency problems - leaving unconfigured

software-properties-common
dependency problems - leaving unconfigured

python3-cryptography
dependency problems - leaving unconfigured

ubuntu-release-upgrader-gtk
dependency problems - leaving unconfigured

update-manager-core
dependency problems - leaving unconfigured

gconf2
dependency problems - leaving triggers unprocessed

python3-apt
dependency problems - leaving unconfigured

gconf2
dependency problems - leaving triggers unprocessed

gconf2
dependency problems - leaving triggers unprocessed

gconf2
dependency problems - leaving triggers unprocessed

gconf2
dependency problems - leaving triggers unprocessed

gconf2
dependency problems - leaving triggers unprocessed

gconf2
dependency problems - leaving triggers unprocessed

gconf2
dependency problems - leaving triggers unprocessed

gconf2
dependency problems - leaving triggers unprocessed

gconf2
dependency problems - leaving triggers unprocessed

gconf2
dependency problems - leaving triggers unprocessed

gconf2
dependency problems - leaving triggers unprocessed

gconf2
dependency problems - leaving triggers unprocessed

gconf2
dependency problems - leaving triggers unprocessed

gconf2
dependency problems - leaving triggers unprocessed

gconf2
dependency problems - leaving triggers unprocessed

gconf2
dependency problems - leaving triggers unprocessed

gconf2
dependency problems - leaving triggers unprocessed

gconf2
dependency problems - leaving triggers unprocessed

gconf2
dependency problems - leaving triggers unprocessed

gconf2
dependency problems - leaving triggers unprocessed

gconf2
dependency problems - leaving triggers unprocessed

gconf2
dependency problems - leaving triggers unprocessed

gconf2
dependency problems - leaving triggers unprocessed

gconf2
dependency problems - leaving triggers unprocessed

gconf2
dependency problems - leaving triggers unprocessed

gconf2
dependency problems - leaving triggers unprocessed

gconf2
dependency problems - leaving triggers unprocessed

gconf2
dependency problems - leaving triggers unprocessed

gconf2
dependency problems - leaving triggers unprocessed

gconf2
dependency problems - leaving triggers unprocessed

gconf2
dependency problems - leaving triggers unprocessed
```

---

### Post by okkadiroglu on 2018-07-31
This what I get for the aabove command:

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following package was automatically installed and is no longer required:
  guile-2.0-libs
Use 'sudo apt autoremove' to remove it.
0 upgraded, 0 newly installed, 1 reinstalled, 0 to remove and 0 not upgraded.
35 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
E: Internal Error, No file name for python3:amd64

```

---

### Post by lisati on 2018-07-31
@okkadiroglu: please use [Code tags]("https://ubuntuforums.org/misc.php?do=bbcode") instead of making use of a font size that has me reaching for my reading glasses.

---

### Post by okkadiroglu on 2018-08-01
Sorry about it. I am  not too familiar with the code tags but I will try them in the future.

---

### Post by oldos2er on 2018-08-01
> **okkadiroglu said:**
> Sorry about it. I am  not too familiar with the code tags but I will try them in the future.

Please see [https://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](https://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)

---

