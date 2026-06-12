---
title: "Problems with updating Kubuntu 7.10"
date: 2008-02-17
forum: Installation &amp; Upgrades
---

### Post by stafi on 2008-02-17
I've installed Kubuntu 7.10 on my laptop at Jan, 20 2008 and decided to do automatic update of the system. After download was completed, the installing of the updates started. But suddenly something went wrong and it told me: "There was an error committing changes....". I've found that the problem is in upgrading 'libqt3-mt'. Something with overwriting configuration file (/etc/qt3/qt_plugins_3.3rc). I decided this problem by manually installing this package, giving the installing program right answers when it asked something. Then I restarted autoupdate and everything is ok.
The other problem was with installing nvidia-xconfig_1.0+20070502-1_i386.deb. But I haven't tried to solve this problem.

---

### Post by Porrly on 2008-02-24
I too have seen this problem.
I was updating using:
```
sudo apt-get upgrade
```
and the following message stopped the upgrade
```
Setting up libqt3-mt (3:3.3.8really3.3.7-0ubuntu11.1) ...

Configuration file `/etc/qt3/qt_plugins_3.3rc'
 ==> File on system created by you or by a script.
 ==> File also in package provided by package maintainer.
   What would you like to do about it ? Your options are:
    Y or I : install the package maintainer's version
    N or O : keep your currently-installed version
      D : show the differences between the versions
      Z : background this process to examine the situation
 The default action is to keep your current version.
*** qt_plugins_3.3rc (Y/I/N/O/D/Z) [default=N] ? y
Installing new version of config file /etc/qt3/qt_plugins_3.3rc ...

```

until I pressed 'y' - 'enter'.

It seems the script thinks the config file has been modified, even though this is a new install of kubuntu.

---

